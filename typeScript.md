### 1.npm全局安装typescript包 
npm install -g typescript

并在工程根目录运行tsc --init，自动产生tsconfig.json文件
### 2.初始化得到的tsconfig.json无需修改，增加"allowJs": true选项。
### 3.安装 @types/react @types/react-dom tslint tslint-config-prettier tslint-react, 如果用了 css-modules，需要安装 @types/css-modules
### 4.编写 tslint.json
```
{
  "extends": ["tslint:latest", "tslint-react", "tslint-config-prettier"],
  "rules": {
    "no-var-requires": false,
    "no-submodule-imports": false,
    "object-literal-sort-keys": false,
    "jsx-no-lambda": false,
    "no-implicit-dependencies": false,
    "no-console": false
  }
}
```
### 5.配置webpack配置，增加ts的loader，如awesome-typescript-loader。(如果是基于atool-build来构建的项目，则它内置了ts编译，这步省略)
```
loaders: [
  // All files with a '.ts' or '.tsx' extension will be handled by 'awesome-typescript-loader'.
  { test: /\.tsx?$/, loader: "awesome-typescript-loader" }
]
```

###此时可以写ts和tsx（React）后缀的文件，它们可以和现有的ES6代码共存，VSCode会自动校验这部分代码，webpack打包也没问题

#### tsconfig.json配置demo
```
{
  "compilerOptions": {
    "outDir": "build/dist",
    "module": "esnext",
    "target": "es2016",
    "lib": ["es6", "dom"],
    "sourceMap": true,
    "jsx": "react",
    "allowSyntheticDefaultImports": true,
    "moduleResolution": "node",
    "rootDir": "src",
    "forceConsistentCasingInFileNames": true,
    "noImplicitReturns": true,
    "suppressImplicitAnyIndexErrors": true,
    "noUnusedLocals": true,
    "experimentalDecorators": true
  },
  "exclude": [
    "node_modules",
    "build",
    "scripts",
    "acceptance-tests",
    "webpack",
    "jest",
    "src/setupTests.ts",
    "tslint:latest",
    "tslint-config-prettier"
  ]
}
```
