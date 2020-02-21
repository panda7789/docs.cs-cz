---
title: Přehled
ms.date: 12/13/2019
description: Přehled Microsoft. data. sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543596"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="4a389-103">Přehled Microsoft. data. sqlite</span><span class="sxs-lookup"><span data-stu-id="4a389-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="4a389-104">Microsoft. data. sqlite je jednoduchý poskytovatel [ADO.NET](../../../framework/data/adonet/index.md) pro sqlite.</span><span class="sxs-lookup"><span data-stu-id="4a389-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="4a389-105">Poskytovatel [Entity Framework Core](/ef/core/) pro SQLite je postaven nad touto knihovnou.</span><span class="sxs-lookup"><span data-stu-id="4a389-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="4a389-106">Dá se ale použít taky nezávisle nebo s jinými knihovnami pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="4a389-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="4a389-107">Instalace</span><span class="sxs-lookup"><span data-stu-id="4a389-107">Installation</span></span>

<span data-ttu-id="4a389-108">Nejnovější stabilní verze je k dispozici v [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span><span class="sxs-lookup"><span data-stu-id="4a389-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="4a389-109">Rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="4a389-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="4a389-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4a389-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="4a389-111">Využití</span><span class="sxs-lookup"><span data-stu-id="4a389-111">Usage</span></span>

<span data-ttu-id="4a389-112">Tato knihovna implementuje společné abstrakce ADO.NET pro připojení, příkazy, čtečky dat a tak dále.</span><span class="sxs-lookup"><span data-stu-id="4a389-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="4a389-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a389-113">See also</span></span>

* [<span data-ttu-id="4a389-114">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="4a389-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="4a389-115">Referenční dokumentace ke knihovně API</span><span class="sxs-lookup"><span data-stu-id="4a389-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0)
* [<span data-ttu-id="4a389-116">Syntaxe SQL</span><span class="sxs-lookup"><span data-stu-id="4a389-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
