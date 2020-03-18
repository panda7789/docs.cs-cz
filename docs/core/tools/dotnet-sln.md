---
title: dotnet sln, příkaz
description: Příkaz dotnet-sln poskytuje vhodnou možnost přidání, odebrání a seznamu projektů v souboru řešení.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543479"
---
# <a name="dotnet-sln"></a>dotnet sln

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet sln`- Uvádí nebo upravuje projekty v souboru řešení .NET Core.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet sln` poskytuje pohodlný způsob, jak vypsat a upravit projekty v souboru řešení.

Chcete-li `dotnet sln` použít příkaz, musí již existovat soubor řešení. Pokud ho potřebujete vytvořit, použijte nový příkaz [dotnet,](dotnet-new.md) jako v následujícím příkladu:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Soubor řešení, který chcete použít. Pokud je tento argument vynechán, příkaz prohledá aktuální adresář. Pokud nenalezne žádný soubor řešení nebo více souborů řešení, příkaz se nezdaří.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne popis použití příkazu.

## <a name="commands"></a>Příkazy

### `list`

Zobrazí seznam všech projektů v souboru řešení.

#### <a name="synopsis"></a>Synopse

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Soubor řešení, který chcete použít. Pokud je tento argument vynechán, příkaz prohledá aktuální adresář. Pokud nenalezne žádný soubor řešení nebo více souborů řešení, příkaz se nezdaří.

#### <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne popis použití příkazu.
  
### `add`

Přidá jeden nebo více projektů do souboru řešení.

#### <a name="synopsis"></a>Synopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Soubor řešení, který chcete použít. Pokud není zadán, příkaz vyhledá aktuální adresář pro jeden a selže, pokud existuje více souborů řešení.

- **`PROJECT_PATH`**

  Cesta k projektu nebo projekty přidat do řešení. Unix/Linux shell [globbing vzor](https://en.wikipedia.org/wiki/Glob_(programming)) expanze jsou `dotnet sln` zpracovány správně příkazem.

#### <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne popis použití příkazu.

- **`--in-root`**

  Umístí projekty do kořenového adresáře řešení, nikoli do vytvoření složky řešení. K dispozici od .NET Core 3.0 SDK.

- **`-s|--solution-folder`**

  Cílová cesta ke složce řešení, do které chcete přidat projekty. K dispozici od .NET Core 3.0 SDK.

### `remove`

Odebere projekt nebo více projektů ze souboru řešení.

#### <a name="synopsis"></a>Synopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Argumenty

- **`SOLUTION_FILE`**

  Soubor řešení, který chcete použít. Pokud je ponecháno neurčeno, příkaz hledá aktuální adresář pro jeden a selže, pokud existuje více souborů řešení.

- **`PROJECT_PATH`**

  Cesta k projektu nebo projekty přidat do řešení. Unix/Linux shell [globbing vzor](https://en.wikipedia.org/wiki/Glob_(programming)) expanze jsou `dotnet sln` zpracovány správně příkazem.

#### <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne popis použití příkazu.

## <a name="examples"></a>Příklady

- Seznam projektů v řešení:

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- Přidejte projekt Jazyka C# do řešení:

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- Odeberte projekt Jazyka C# z řešení:

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- Přidejte více projektů jazyka C# do kořenového adresáře řešení:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- Přidejte do řešení více projektů jazyka C#:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Odeberte z řešení více projektů jazyka C#:

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Přidejte do řešení více projektů Jazyka C# pomocí globbingového vzoru (pouze Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Odebrání více projektů Jazyka C# z řešení pomocí globbing ového vzoru (pouze Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
