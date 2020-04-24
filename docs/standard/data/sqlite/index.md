---
title: Přehled
ms.date: 12/13/2019
description: Přehled Microsoft. data. sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543596"
---
# <a name="microsoftdatasqlite-overview"></a>Přehled Microsoft. data. sqlite

Microsoft. data. sqlite je jednoduchý poskytovatel [ADO.NET](../../../framework/data/adonet/index.md) pro sqlite. Poskytovatel [Entity Framework Core](/ef/core/) pro SQLite je postaven nad touto knihovnou. Dá se ale použít taky nezávisle nebo s jinými knihovnami pro přístup k datům.

## <a name="installation"></a>Instalace

Nejnovější stabilní verze je k dispozici v [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).

### <a name="net-core-cli"></a>[Rozhraní příkazového řádku .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Využití

Tato knihovna implementuje společné abstrakce ADO.NET pro připojení, příkazy, čtečky dat a tak dále.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Viz také

* [Připojovací řetězce](connection-strings.md)
* [Referenční informace k rozhraním API](/dotnet/api/?view=msdata-sqlite-3.0)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
