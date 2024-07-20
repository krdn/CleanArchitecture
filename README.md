# Clean Architecture Solution Template

[![Build](https://github.com/jasontaylordev/CleanArchitecture/actions/workflows/build.yml/badge.svg)](https://github.com/jasontaylordev/CleanArchitecture/actions/workflows/build.yml)
[![CodeQL](https://github.com/jasontaylordev/CleanArchitecture/actions/workflows/codeql.yml/badge.svg)](https://github.com/jasontaylordev/CleanArchitecture/actions/workflows/codeql.yml)
[![Nuget](https://img.shields.io/nuget/v/Clean.Architecture.Solution.Template?label=NuGet)](https://www.nuget.org/packages/Clean.Architecture.Solution.Template)
[![Nuget](https://img.shields.io/nuget/dt/Clean.Architecture.Solution.Template?label=Downloads)](https://www.nuget.org/packages/Clean.Architecture.Solution.Template)
![Twitter Follow](https://img.shields.io/twitter/follow/jasontaylordev?label=Follow&style=social)

이 템플릿의 목표는 Clean Architecture 및 ASP.NET Core의 기능을 활용하여 엔터프라이즈 애플리케이션 개발에 대한 간단하고 효율적인 접근 방식을 제공하는 것입니다. 이 템플릿을 사용하면 Clean Architecture의 원칙을 준수하면서 ASP.NET Core 및 Angular 또는 React를 사용하여 SPA(단일 페이지 앱)를 쉽게 만들 수 있습니다. 시작하는 것은 쉽습니다. .NET 템플릿을 설치하기만 하면 됩니다(자세한 내용은 아래 참조).

이 프로젝트가 유용하다고 생각되면 별점을 주세요. 감사해요! ⭐

## Getting Started

솔루션을 빌드하고 실행하려면 다음 필수 구성 요소가 필요합니다:

- [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) (latest version)
- [Node.js](https://nodejs.org/) (latest LTS, only required if you are using Angular or React)

The easiest way to get started is to install the [.NET template](https://www.nuget.org/packages/Clean.Architecture.Solution.Template):
```
dotnet new install Clean.Architecture.Solution.Template::8.0.5
```

Once installed, create a new solution using the template. You can choose to use Angular, React, or create a Web API-only solution. Specify the client framework using the `-cf` or `--client-framework` option, and provide the output directory where your project will be created. Here are some examples:

To create a Single-Page Application (SPA) with Angular and ASP.NET Core:
```bash
dotnet new ca-sln --client-framework Angular --output YourProjectName
```

To create a SPA with React and ASP.NET Core:
```bash
dotnet new ca-sln -cf React -o YourProjectName
```

To create a ASP.NET Core Web API-only solution:
```bash
dotnet new ca-sln -cf None -o YourProjectName
```

Launch the app:
```bash
cd src/Web
dotnet run
```

To learn more, run the following command:
```bash
dotnet new ca-sln --help
```

You can create use cases (commands or queries) by navigating to `./src/Application` and running `dotnet new ca-usecase`. Here are some examples:

To create a new command:
```bash
dotnet new ca-usecase --name CreateTodoList --feature-name TodoLists --usecase-type command --return-type int
```

To create a query:
```bash
dotnet new ca-usecase -n GetTodos -fn TodoLists -ut query -rt TodosVm
```

To learn more, run the following command:
```bash
dotnet new ca-usecase --help
```

## Database

The template is configured to use SQL Server by default. If you would prefer to use SQLite, create your solution using the following command:

```bash
dotnet new ca-sln --use-sqlite
```

When you run the application the database will be automatically created (if necessary) and the latest migrations will be applied.

Running database migrations is easy. Ensure you add the following flags to your command (values assume you are executing from repository root)

* `--project src/Infrastructure` (optional if in this folder)
* `--startup-project src/Web`
* `--output-dir Data/Migrations`

For example, to add a new migration from the root folder:

 `dotnet ef migrations add "SampleMigration" --project src\Infrastructure --startup-project src\Web --output-dir Data\Migrations`

## Deploy

The template includes a full CI/CD pipeline. The pipeline is responsible for building, testing, publishing and deploying the solution to Azure. If you would like to learn more, read the [deployment instructions](https://github.com/jasontaylordev/CleanArchitecture/wiki/Deployment).

## Technologies

* [ASP.NET Core 8](https://docs.microsoft.com/en-us/aspnet/core/introduction-to-aspnet-core)
* [Entity Framework Core 8](https://docs.microsoft.com/en-us/ef/core/)
* [Angular 15](https://angular.io/) or [React 18](https://react.dev/)
* [MediatR](https://github.com/jbogard/MediatR)
* [AutoMapper](https://automapper.org/)
* [FluentValidation](https://fluentvalidation.net/)
* [NUnit](https://nunit.org/), [FluentAssertions](https://fluentassertions.com/), [Moq](https://github.com/moq) & [Respawn](https://github.com/jbogard/Respawn)

## Versions
The main branch is now on .NET 8.0. The following previous versions are available:

* [7.0](https://github.com/jasontaylordev/CleanArchitecture/tree/net7.0)
* [6.0](https://github.com/jasontaylordev/CleanArchitecture/tree/net6.0)
* [5.0](https://github.com/jasontaylordev/CleanArchitecture/tree/net5.0)
* [3.1](https://github.com/jasontaylordev/CleanArchitecture/tree/netcore3.1)

## Learn More

* [Clean Architecture with ASP.NET Core 3.0 (GOTO 2019)](https://youtu.be/dK4Yb6-LxAk)
* [Clean Architecture with .NET Core: Getting Started](https://jasontaylor.dev/clean-architecture-getting-started/)

## Support

If you are having problems, please let me know by [raising a new issue](https://github.com/jasontaylordev/CleanArchitecture/issues/new/choose).

## License

This project is licensed with the [MIT license](LICENSE).
