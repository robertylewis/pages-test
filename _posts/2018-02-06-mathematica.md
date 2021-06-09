---

title:  "A bi-directional extensible interface between Lean and Mathematica"
date:   2018-02-06 10:00:00 +100
categories: paper
comments: false
permalink: /leanmm/index.html
---

Minchao Wu and I have been working on a project that connects the computer algebra system
Mathematica to the Lean theorem prover. Here you will find the supplementary materials corresponding
to [our paper draft](lean_mm.pdf).



An [early version of this work](https://arxiv.org/abs/1712.09288) was presented at PxTP.
For more information, contact [Robert Y.
Lewis](https://robertylewis.com) and [Minchao Wu](mailto:logic.mcwu@gmail.com).

## Versioning

These tools and examples are compatible with various versions of Lean.
In any of the GitHub repositories, look for the `lean-x.y.z` branch
for a version of the project compatible with Lean x.y.z.
The core tool will automatically be updated to new versions of Lean
as long as compatibility is maintained.
Unfortunately this automatic upgrading is not possible for the example repositories
due to licensing issues,
but we will do it manually;
please contact the authors if you need a fresh update on short notice,
or try running `leanproject up` yourself.

The link is known to work with Mathematica versions 11 and 12,
and perhaps with earlier versions.

The `lean-3.17.1` branches, and any below, are frozen as of August 19, 2020.
All claims in our paper draft have been tested to be true of this version,
and we have not intentionally falsified any in later versions.

## Installing the link

The link requires you to have Python installed with `python3` in the system path.

We strongly recommend installing Lean with the `elan` version manager
and `leanproject` supporting tool,
following [the "regular install" instructions](https://leanprover-community.github.io/get_started.html#regular-install).

The core tool for using Mathematica from Lean is available on
[GitHub](https://github.com/rlewis1988/mathematica). This project can be added as a dependency to
any Lean project using the `leanpkg` package manager.
Note that, if you install the project as a dependency using `leanpkg`,
you do not need to download it separately.
It will be downloaded automatically to the `_target/deps/mathematica` directory of your project.

To use the link in this direction, you must start the Mathematica server. Do this either by

* running `math --noprompt -run '<<"server2.m"`
  in the `_target/deps/mathematica/src` directory of your project, or
* opening the Mathematica frontend and evaluating `<<"/path/to/_target/deps/mathematica/src/server2.m"`
  (with the correct path).



The code for using Lean from Mathematica is also available on
[GitHub](https://github.com/minchaowu/mm_lean). This project uses the above as a dependency.
See directions below for using it.

## Examples of calling Mathematica from Lean

A project containing examples of the Mathematica-from-Lean link in action is available
[here](https://github.com/rlewis1988/mathematica_examples).

The easiest way to try this out is to download the project using `leanproject`:

    leanproject get robertylewis/mathematica_examples
    cd mathematica_examples/_target/deps/mathematica/src
    math --noprompt -run '<<"server2.m"'

This will download the core link, the examples,
Lean's mathematical library mathlib (on which the examples depend),
and precompiled binaries for mathlib.
If you use an alternate installation method, you may have to compile mathlib yourself,
which can take a long time.

You can then see the link in action in any file in `mathematica_examples/src`.
**Note**: if you use the VSCode editor,
you must use the "Open Folder" feature to open the `mathematica_examples` directory.
Opening individual files will not work.
An easy way to do this from the command line,
starting in the same directory you started in above, is

    code mathematica_examples


## Examples of calling Lean from Mathematica

These examples and the code to make them work are on [GitHub](https://github.com/minchaowu/mm_lean).

As above, it is easiest to install using `leanproject`:

    leanproject get minchaowu/mm_lean

The file `LeanProof.nb` in the `mm_lean` directory contains examples of the
Lean-from-Mathematica link.
You will need to evaluate the first few configuration lines
to start a Lean server;
after that, the examples below can be tried in any order.

## Possible issues

The Mathematica-from-Lean link expects a `python3` executable in the path. Create an alias if you do
not have this.

The link communicates over port 10000. If this is taken, change the port numbers in `client2.py` and
`server2.m`.

There are known issues with Mathematica's socket server functionality on certain versions of Linux.
This may cause the server to use excess CPU.

## Additional information
The full, unabbreviated form of the expression `x^2-2*x+1` in Lean is

```
app (app (app (app (const (name.mk_string add (name.anonymous)) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_has_add (name.mk_string distrib (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_distrib (name.mk_string ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_ring (name.mk_string division_ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_division_ring (name.mk_string field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_field (name.mk_string linear_ordered_field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (const (name.mk_string h (name.anonymous)) (level_list.nil)))))))) (app (app (app (app (const (name.mk_string sub (name.anonymous)) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string add_group_has_sub (name.anonymous)) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_add_group (name.mk_string add_comm_group (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_add_comm_group (name.mk_string ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_ring (name.mk_string division_ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_division_ring (name.mk_string field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_field (name.mk_string linear_ordered_field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (const (name.mk_string h (name.anonymous)) (level_list.nil))))))))) (app (app (app (app (const (name.mk_string mul (name.anonymous)) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_has_mul (name.mk_string mul_zero_class (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_mul_zero_class (name.mk_string semiring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_semiring (name.mk_string ordered_semiring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_ordered_semiring (name.mk_string ordered_ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_ordered_ring (name.mk_string linear_ordered_ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_linear_ordered_ring (name.mk_string linear_ordered_field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (const (name.mk_string h (name.anonymous)) (level_list.nil))))))))) (local_const (name.mk_numeral 1 (name.mk_numeral 18 (name.anonymous))) (name.mk_string x (name.anonymous)) (binder_info.default) (const (name.mk_string real (name.anonymous)) (level_list.nil)))) (local_const (name.mk_numeral 1 (name.mk_numeral 18 (name.anonymous))) (name.mk_string x (name.anonymous)) (binder_info.default) (const (name.mk_string real (name.anonymous)) (level_list.nil))))) (app (app (app (app (const (name.mk_string mul (name.anonymous)) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_has_mul (name.mk_string mul_zero_class (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_mul_zero_class (name.mk_string semiring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_semiring (name.mk_string ordered_semiring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_ordered_semiring (name.mk_string ordered_ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_ordered_ring (name.mk_string linear_ordered_ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_linear_ordered_ring (name.mk_string linear_ordered_field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (const (name.mk_string h (name.anonymous)) (level_list.nil))))))))) (app (app (app (const (name.mk_string bit0 (name.anonymous)) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_has_add (name.mk_string distrib (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_distrib (name.mk_string ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_ring (name.mk_string division_ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_division_ring (name.mk_string field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_field (name.mk_string linear_ordered_field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (const (name.mk_string h (name.anonymous)) (level_list.nil)))))))) (app (app (const (name.mk_string one (name.anonymous)) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_has_one (name.mk_string zero_ne_one_class (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_zero_ne_one_class (name.mk_string division_ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_division_ring (name.mk_string field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_field (name.mk_string linear_ordered_field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (const (name.mk_string h (name.anonymous)) (level_list.nil))))))))) (local_const (name.mk_numeral 1 (name.mk_numeral 18 (name.anonymous))) (name.mk_string x (name.anonymous)) (binder_info.default) (const (name.mk_string real (name.anonymous)) (level_list.nil)))))) (app (app (const (name.mk_string one (name.anonymous)) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_has_one (name.mk_string zero_ne_one_class (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_zero_ne_one_class (name.mk_string division_ring (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_division_ring (name.mk_string field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (app (app (const (name.mk_string to_field (name.mk_string linear_ordered_field (name.anonymous))) (level_list.cons (level.zero) (level_list.nil))) (const (name.mk_string real (name.anonymous)) (level_list.nil))) (const (name.mk_string h (name.anonymous)) (level_list.nil)))))))
```

The Mathematica version of this same expression is:

```
"LeanApp[LeanApp[LeanApp[LeanApp[LeanConst[LeanNameMkString["add", LeanNameAnonymous], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_has_add", LeanNameMkString["distrib", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_distrib", LeanNameMkString["ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_ring", LeanNameMkString["division_ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_division_ring", LeanNameMkString["field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_field", LeanNameMkString["linear_ordered_field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanConst[LeanNameMkString["h", LeanNameAnonymous], LeanLevelListNil]]]]]]], LeanApp[LeanApp[LeanApp[LeanApp[LeanConst[LeanNameMkString["sub", LeanNameAnonymous], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["add_group_has_sub", LeanNameAnonymous], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_add_group", LeanNameMkString["add_comm_group", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_add_comm_group", LeanNameMkString["ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_ring", LeanNameMkString["division_ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_division_ring", LeanNameMkString["field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_field", LeanNameMkString["linear_ordered_field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanConst[LeanNameMkString["h", LeanNameAnonymous], LeanLevelListNil]]]]]]]], LeanApp[LeanApp[LeanApp[LeanApp[LeanConst[LeanNameMkString["mul", LeanNameAnonymous], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_has_mul", LeanNameMkString["mul_zero_class", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_mul_zero_class", LeanNameMkString["semiring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_semiring", LeanNameMkString["ordered_semiring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_ordered_semiring", LeanNameMkString["ordered_ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_ordered_ring", LeanNameMkString["linear_ordered_ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_linear_ordered_ring", LeanNameMkString["linear_ordered_field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanConst[LeanNameMkString["h", LeanNameAnonymous], LeanLevelListNil]]]]]]]], LeanLocal[LeanNameMkNum[1843, LeanNameMkNum[17, LeanNameAnonymous]], LeanNameMkString["x", LeanNameAnonymous], BinderInfoDefault, LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]]], LeanLocal[LeanNameMkNum[1843, LeanNameMkNum[17, LeanNameAnonymous]], LeanNameMkString["x", LeanNameAnonymous], BinderInfoDefault, LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]]]], LeanApp[LeanApp[LeanApp[LeanApp[LeanConst[LeanNameMkString["mul", LeanNameAnonymous], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_has_mul", LeanNameMkString["mul_zero_class", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_mul_zero_class", LeanNameMkString["semiring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_semiring", LeanNameMkString["ordered_semiring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_ordered_semiring", LeanNameMkString["ordered_ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_ordered_ring", LeanNameMkString["linear_ordered_ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_linear_ordered_ring", LeanNameMkString["linear_ordered_field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanConst[LeanNameMkString["h", LeanNameAnonymous], LeanLevelListNil]]]]]]]], LeanApp[LeanApp[LeanApp[LeanConst[LeanNameMkString["bit0", LeanNameAnonymous], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_has_add", LeanNameMkString["distrib", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_distrib", LeanNameMkString["ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_ring", LeanNameMkString["division_ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_division_ring", LeanNameMkString["field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_field", LeanNameMkString["linear_ordered_field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanConst[LeanNameMkString["h", LeanNameAnonymous], LeanLevelListNil]]]]]]], LeanApp[LeanApp[LeanConst[LeanNameMkString["one", LeanNameAnonymous], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_has_one", LeanNameMkString["zero_ne_one_class", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_zero_ne_one_class", LeanNameMkString["division_ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_division_ring", LeanNameMkString["field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_field", LeanNameMkString["linear_ordered_field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanConst[LeanNameMkString["h", LeanNameAnonymous], LeanLevelListNil]]]]]]]], LeanLocal[LeanNameMkNum[1843, LeanNameMkNum[17, LeanNameAnonymous]], LeanNameMkString["x", LeanNameAnonymous], BinderInfoDefault, LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]]]]], LeanApp[LeanApp[LeanConst[LeanNameMkString["one", LeanNameAnonymous], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_has_one", LeanNameMkString["zero_ne_one_class", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_zero_ne_one_class", LeanNameMkString["division_ring", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_division_ring", LeanNameMkString["field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanApp[LeanApp[LeanConst[LeanNameMkString["to_field", LeanNameMkString["linear_ordered_field", LeanNameAnonymous]], LeanLevelListCons[LeanZeroLevel, LeanLevelListNil]], LeanConst[LeanNameMkString["real", LeanNameAnonymous], LeanLevelListNil]], LeanConst[LeanNameMkString["h", LeanNameAnonymous], LeanLevelListNil]]]]]]]
```