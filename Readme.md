# pklTsConfig

A [Pkl](https://pkl-lang.org) module for Typescript's *tsconfig.json* based on Totally Typescript's TsConfig Cheatsheet (https://www.totaltypescript.com/tsconfig-cheat-sheet) configuration.

## Usage

You can amend this package's provided module to configure your Typescript tsconfig.json file. Simply add the following line to a Pkl file 
```pkl
amends "package://pkg.pkl-lang.org/github.com/PaulJPhilp/pklTsConfig/pklTsConfig@0.3.0#/TsConfigDefault.pkl"
```

and then specify your configuration below. With the VSCode Pkl extension, you'll get autocomplete for all the available options.

```
config {
    useDom: true
    useTranspiling: false
}

root {
    files { 
        "main.ts"
        "index.ts"
        }
    exclude { 
        "tests.ts"
        }
}
```

## Config Element

The config element is transformed into the **"compilerOptions"** section of your tsconfig.json file.  Based on the sections
provided in TotalTypescript's TsConfig Cheat Sheet, the following flags are available:

- **useBase**: use all the entries definded in the *Base Options* section in the Cheat Sheet.
- **useStrict**: use all the entries definded in the *Strict Options* section in the Cheat Sheet.
- **useStrictest**: use all the strict entries which are **not recommended** in the Cheat Sheet.
- **useDom**: use all the entries definded in the *Dom Options* section in the Cheat Sheet.
- **useMonorepo**: use all the entries definded in the *Monorepo Options* section in the Cheat Sheet.
- **useLibrary**: use all the entries definded in the *Library Options* section in the Cheat Sheet.
- **useTranspiling**: use all the entries definded in the *Transpiling Options* section in the Cheat Sheet.

### Default Values

```
config {
  useBase = true
  useStrict = true
  useStrictest = false
  useDom = true
  useMonorepo = false
  useLibrary = false
  useTranspiling = true
}
```

### Root Element

The root element is transformed into the root level elements allowed in a *tsconfig.json* file which
are not defined in the Cheat Sheet *["extends", "files", "includes", "excludes"]*.  The *reference* field
will be add in a future release.

By default, the root elements are not included in the tsconfig.json file unless an
element is explicitly specified.

For example:

`
root {
    extends: "project_tsconfig.json"
    files { 
        "main.ts"
        "index.ts"
        }
    exclude { 
        "exlude.ts"
        }
    include {
        "include.ts"
    }
}
`

To build, run `pkl eval tsconfig.pkl -m .`, and it will create a `tsconfig.json` in the same directory.