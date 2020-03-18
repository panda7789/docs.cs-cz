---
title: Přehled
ms.date: 12/13/2019
description: Přehled Microsoft.Data.Sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543596"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="35ee2-103">Microsoft.Data.Sqlite – přehled</span><span class="sxs-lookup"><span data-stu-id="35ee2-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="35ee2-104">Microsoft.Data.Sqlite je lehký [zprostředkovatel ADO.NET](../../../framework/data/adonet/index.md) pro SQLite.</span><span class="sxs-lookup"><span data-stu-id="35ee2-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="35ee2-105">Zprostředkovatel [Entity Framework Core](/ef/core/) pro SQLite je postaven na této knihovně.</span><span class="sxs-lookup"><span data-stu-id="35ee2-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="35ee2-106">Lze jej však také použít samostatně nebo s jinými knihovnami pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="35ee2-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="35ee2-107">Instalace</span><span class="sxs-lookup"><span data-stu-id="35ee2-107">Installation</span></span>

<span data-ttu-id="35ee2-108">Nejnovější stabilní verze je k dispozici na [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span><span class="sxs-lookup"><span data-stu-id="35ee2-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="35ee2-109">Rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="35ee2-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="35ee2-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="35ee2-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="35ee2-111">Využití</span><span class="sxs-lookup"><span data-stu-id="35ee2-111">Usage</span></span>

<span data-ttu-id="35ee2-112">Tato knihovna implementuje běžné ADO.NET abstrakce pro připojení, příkazy, čtečky dat a tak dále.</span><span class="sxs-lookup"><span data-stu-id="35ee2-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="35ee2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="35ee2-113">See also</span></span>

* [<span data-ttu-id="35ee2-114">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="35ee2-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="35ee2-115">Referenční informace k rozhraním API</span><span class="sxs-lookup"><span data-stu-id="35ee2-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0)
* [<span data-ttu-id="35ee2-116">Syntaxe SQL</span><span class="sxs-lookup"><span data-stu-id="35ee2-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
