---
title: dotnet sln – příkaz
description: Příkaz dotnet-sln nabízí pohodlný způsob přidávání, odebírání a vypsání projektů v souboru řešení.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543479"
---
# <a name="dotnet-sln"></a>dotnet sln

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Název

`dotnet sln` – zobrazí nebo upraví projekty v souboru řešení .NET Core.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet sln` poskytuje pohodlný způsob, jak zobrazit a upravit projekty v souboru řešení.

Chcete-li použít příkaz `dotnet sln`, soubor řešení již musí existovat. Pokud ho potřebujete vytvořit, použijte příkaz [dotnet New](dotnet-new.md) , jako v následujícím příkladu:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Soubor řešení, který se má použít. Pokud je tento argument vynechán, příkaz vyhledá v aktuálním adresáři jeden z nich. Pokud nenajde žádný soubor řešení nebo více souborů řešení, příkaz se nezdařil.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne popis způsobu použití příkazu.

## <a name="commands"></a>Příkazy

### `list`

Zobrazí seznam všech projektů v souboru řešení.

#### <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Soubor řešení, který se má použít. Pokud je tento argument vynechán, příkaz vyhledá v aktuálním adresáři jeden z nich. Pokud nenajde žádný soubor řešení nebo více souborů řešení, příkaz se nezdařil.

#### <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne popis způsobu použití příkazu.
  
### `add`

Přidá do souboru řešení jeden nebo více projektů.

#### <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Soubor řešení, který se má použít. Pokud tento parametr není zadán, příkaz vyhledá v aktuálním adresáři jeden a v případě, že existuje více souborů řešení, bude neúspěšný.

- **`PROJECT_PATH`**

  Cesta k projektu nebo projektům, které se mají přidat do řešení Rozšíření [vzoru expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) prostředí systému UNIX/Linux jsou zpracována správně pomocí příkazu `dotnet sln`.

#### <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne popis způsobu použití příkazu.

- **`--in-root`**

  Umístí projekty do kořenového adresáře řešení namísto vytvoření složky řešení. K dispozici od verze .NET Core 3,0 SDK.

- **`-s|--solution-folder`**

  Cílová cesta ke složce řešení, do které se mají přidat projekty K dispozici od verze .NET Core 3,0 SDK.

### `remove`

Odebere projekt nebo více projektů ze souboru řešení.

#### <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Soubor řešení, který se má použít. Pokud parametr není zadán, příkaz vyhledá soubor v aktuálním adresáři a dojde k chybě, pokud existuje více souborů řešení.

- **`PROJECT_PATH`**

  Cesta k projektu nebo projektům, které se mají přidat do řešení Rozšíření [vzoru expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) prostředí systému UNIX/Linux jsou zpracována správně pomocí příkazu `dotnet sln`.

#### <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne popis způsobu použití příkazu.

## <a name="examples"></a>Příklady

- Seznam projektů v řešení:

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- Přidání C# projektu do řešení:

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- Odebrání C# projektu z řešení:

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- Přidání více C# projektů do kořenového adresáře řešení:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- Přidání více C# projektů do řešení:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Odebrání více C# projektů z řešení:

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Přidání více C# projektů do řešení pomocí vzoru expanze názvů (jenom UNIX/Linux):

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Odebrání více C# projektů z řešení pomocí vzoru expanze (pouze systém UNIX/Linux):

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
