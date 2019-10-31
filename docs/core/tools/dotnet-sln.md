---
title: dotnet sln – příkaz
description: Příkaz dotnet-sln nabízí pohodlný způsob přidávání, odebírání a vypsání projektů v souboru řešení.
ms.date: 10/29/2019
ms.openlocfilehash: 18702c7638798117bd04d5c6a829d64cc6bf18a8
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191817"
---
# <a name="dotnet-sln"></a>dotnet sln

**Tento článek se týká: ✓** .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet sln` – upraví soubor řešení .NET Core.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet sln` poskytuje pohodlný způsob, jak přidávat, odebírat a vypisovat projekty v souboru řešení.

Chcete-li použít příkaz `dotnet sln`, soubor řešení již musí existovat. Pokud ho potřebujete vytvořit, použijte příkaz [dotnet New](dotnet-new.md) , jako v následujícím příkladu:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Soubor řešení, který se má použít. Pokud není zadán, příkaz vyhledá v aktuálním adresáři. Pokud je v adresáři více souborů řešení, je nutné zadat jeden.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

## <a name="commands"></a>Příkazy

### `add`

Přidá do souboru řešení projekt nebo více projektů.

#### <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Soubor řešení, který se má použít. Pokud není zadán, příkaz vyhledá v aktuálním adresáři. Pokud je v adresáři více souborů řešení, je nutné zadat jeden.

- **`PROJECT_PATH`**

  Cesta k projektu, který se má přidat do řešení Přidejte více projektů přidáním jednoho po druhém oddělené mezery. Rozšíření [vzoru expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) prostředí systému UNIX/Linux jsou zpracována správně pomocí příkazu `dotnet sln`.

#### <a name="options"></a>Možnosti

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--in-root`**

  Umístí projekty do kořenového adresáře řešení namísto vytvoření složky řešení. K dispozici od verze .NET Core 3,0 SDK.

- **`-s|--solution-folder`**

  Cílová cesta ke složce řešení, do které se mají přidat projekty K dispozici od verze .NET Core 3,0 SDK.

### `remove`

Odebere projekt nebo více projektů ze souboru řešení.

#### <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Soubor řešení, který se má použít. Pokud není zadán, příkaz vyhledá v aktuálním adresáři. Pokud je v adresáři více souborů řešení, je nutné zadat jeden.

- **`PROJECT_PATH`**

  Cesta k projektu, který se má odebrat z řešení Odeberte více projektů přidáním jednoho po druhém odděleném mezerami. Rozšíření [vzoru expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) prostředí systému UNIX/Linux jsou zpracována správně pomocí příkazu `dotnet sln`.

#### <a name="options"></a>Možnosti

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

### `list`

Zobrazí seznam všech projektů v souboru řešení.

#### <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet sln list [-h|--help]
```
  
#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Soubor řešení, který se má použít. Pokud není zadán, příkaz vyhledá v aktuálním adresáři. Pokud je v adresáři více souborů řešení, je nutné zadat jeden.

#### <a name="options"></a>Možnosti

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

## <a name="examples"></a>Příklady

Přidání C# projektu do řešení:

```dotnetcli
dotnet sln todo.sln add todo-app/todo-app.csproj
```

Odebrání C# projektu z řešení:

```dotnetcli
dotnet sln todo.sln remove todo-app/todo-app.csproj
```

Přidání více C# projektů do řešení:

```dotnetcli
dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
```

Odebrání více C# projektů z řešení:

```dotnetcli
dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
```

Přidání více C# projektů do řešení pomocí vzoru expanze názvů (jenom UNIX/Linux):

```dotnetcli
dotnet sln todo.sln add **/*.csproj
```

Odebrání více C# projektů z řešení pomocí vzoru expanze (pouze systém UNIX/Linux):

```dotnetcli
dotnet sln todo.sln remove **/*.csproj
```
