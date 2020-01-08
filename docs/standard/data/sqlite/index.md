---
title: Přehled
ms.date: 12/13/2019
description: Přehled Microsoft. data. sqlite
ms.openlocfilehash: a5dc1366cc0ddfcd5501e26bf2a994456bcd5d98
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447228"
---
# <a name="microsoftdatasqlite-overview"></a>Přehled Microsoft. data. sqlite

Microsoft. data. sqlite je jednoduchý poskytovatel [ADO.NET](../../../framework/data/adonet/index.md) pro sqlite. Poskytovatel [Entity Framework Core](/ef/core/) pro SQLite je postaven nad touto knihovnou. Dá se ale použít taky nezávisle nebo s jinými knihovnami pro přístup k datům.

## <a name="installation"></a>Instalace služby

Nejnovější stabilní verze je k dispozici v [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).

### <a name="net-core-clitabnetcore-cli"></a>[Rozhraní příkazového řádku .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Použití

Tato knihovna implementuje společné abstrakce ADO.NET pro připojení, příkazy, čtečky dat a tak dále.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Viz také:

* [Připojovací řetězce](connection-strings.md)
* [Referenční dokumentace ke knihovně API](/dotnet/api/?view=msdata-sqlite-3.0.0)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
