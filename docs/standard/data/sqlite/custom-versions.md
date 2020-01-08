---
title: Vlastní verze SQLite
ms.date: 12/13/2019
description: Naučte se používat vlastní verzi nativní knihovny SQLite.
ms.openlocfilehash: 8a2646138ea9dbecf412a2e8e0e347e2d71a5b0b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447144"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="a00a8-103">Vlastní verze SQLite</span><span class="sxs-lookup"><span data-stu-id="a00a8-103">Custom SQLite versions</span></span>

<span data-ttu-id="a00a8-104">Microsoft. data. sqlite je postaven nad SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="a00a8-104">Microsoft.Data.Sqlite is built on top of SQLitePCLRaw.</span></span> <span data-ttu-id="a00a8-105">Můžete použít vlastní verze nativní knihovny SQLite pomocí sady prostředků nebo konfigurací poskytovatele SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="a00a8-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a SQLitePCLRaw provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="a00a8-106">Sady</span><span class="sxs-lookup"><span data-stu-id="a00a8-106">Bundles</span></span>

<span data-ttu-id="a00a8-107">SQLitePCLRaw poskytuje balíčky sady prostředků, které usnadňují přenesení správných závislostí napříč různými platformami.</span><span class="sxs-lookup"><span data-stu-id="a00a8-107">SQLitePCLRaw provides bundle packages that make it easy to bring in the right dependencies across different platforms.</span></span>

<span data-ttu-id="a00a8-108">Hlavní balíček Microsoft. data. sqlite ve výchozím nastavení přináší SQLitePCLRaw. bundle_e_sqlite3.</span><span class="sxs-lookup"><span data-stu-id="a00a8-108">The main Microsoft.Data.Sqlite package brings in SQLitePCLRaw.bundle_e_sqlite3 by default.</span></span>

<span data-ttu-id="a00a8-109">Pokud chcete použít jinou sadu prostředků, nainstalujte místo toho balíček `Microsoft.Data.Sqlite.Core` společně s balíčkem sady, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="a00a8-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="a00a8-110">Sady se automaticky inicializují pomocí Microsoft. data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="a00a8-110">Bundles are automatically initialized by Microsoft.Data.Sqlite.</span></span>

| <span data-ttu-id="a00a8-111">Nabídky</span><span class="sxs-lookup"><span data-stu-id="a00a8-111">Bundle</span></span> | <span data-ttu-id="a00a8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a00a8-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="a00a8-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="a00a8-113">SQLitePCLRaw.bundle_e_sqlite3</span></span> | <span data-ttu-id="a00a8-114">Poskytuje konzistentní verzi SQLite na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="a00a8-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="a00a8-115">Zahrnuje FTS4, FTS5, JSON1 a</span><span class="sxs-lookup"><span data-stu-id="a00a8-115">Includes the FTS4, FTS5, JSON1, and</span></span> | <span data-ttu-id="a00a8-116">Stromová rozšíření R \*.</span><span class="sxs-lookup"><span data-stu-id="a00a8-116">R\*Tree extensions.</span></span> <span data-ttu-id="a00a8-117">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a00a8-117">This is the default.</span></span> |
| <span data-ttu-id="a00a8-118">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="a00a8-118">SQLitePCLRaw.bundle_green</span></span> | <span data-ttu-id="a00a8-119">Stejné jako bundle_e_sqlite3, s výjimkou iOS, kde používá systémovou knihovnu SQLite.</span><span class="sxs-lookup"><span data-stu-id="a00a8-119">Same as bundle_e_sqlite3, except on iOS where it uses the system SQLite library.</span></span> |
| <span data-ttu-id="a00a8-120">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="a00a8-120">SQLitePCLRaw.bundle_zetetic</span></span> | <span data-ttu-id="a00a8-121">Používá oficiální SQLCipher buildy z Zetetic (Nezahrnuto).</span><span class="sxs-lookup"><span data-stu-id="a00a8-121">Uses the official SQLCipher builds from Zetetic (not included).</span></span> |
| <span data-ttu-id="a00a8-122">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="a00a8-122">SQLitePCLRaw.bundle_winsqlite3</span></span> | <span data-ttu-id="a00a8-123">Používá winsqlite3. dll, systémovou knihovnu SQLite ve Windows 10.</span><span class="sxs-lookup"><span data-stu-id="a00a8-123">Uses winsqlite3.dll, the system SQLite library on Windows 10.</span></span> |
| <span data-ttu-id="a00a8-124">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="a00a8-124">SQLitePCLRaw.bundle_e_sqlcipher</span></span> | <span data-ttu-id="a00a8-125">Poskytuje neoficiální a open source sestavení SQLCipher.</span><span class="sxs-lookup"><span data-stu-id="a00a8-125">Provides an unofficial, open-source build of SQLCipher.</span></span> |

<span data-ttu-id="a00a8-126">Například pro použití neoficiálního Open Source sestavení SQLCipher použijte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="a00a8-126">For example, to use the unofficial, open-source build of SQLCipher use the following commands.</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="a00a8-127">Rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="a00a8-127">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="a00a8-128">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a00a8-128">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a><span data-ttu-id="a00a8-129">SQLitePCLRaw poskytovatelé</span><span class="sxs-lookup"><span data-stu-id="a00a8-129">SQLitePCLRaw providers</span></span>

<span data-ttu-id="a00a8-130">Pomocí `SQLitePCLRaw.provider.dynamic_cdecl` balíčku můžete použít vlastní sestavení SQLite.</span><span class="sxs-lookup"><span data-stu-id="a00a8-130">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="a00a8-131">V tomto případě zodpovídáte za nasazení nativní knihovny s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="a00a8-131">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="a00a8-132">Všimněte si, že podrobnosti o nasazení nativních knihoven s vaší aplikací se výrazně liší v závislosti na tom, kterou platformu .NET a modul runtime používáte.</span><span class="sxs-lookup"><span data-stu-id="a00a8-132">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="a00a8-133">Nejdřív budete muset implementovat IGetFunctionPointer.</span><span class="sxs-lookup"><span data-stu-id="a00a8-133">First, you'll need to implement IGetFunctionPointer.</span></span> <span data-ttu-id="a00a8-134">Implementace je poměrně triviální v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a00a8-134">The implementation is fairly trivial on .NET Core.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="a00a8-135">Dále nakonfigurujte poskytovatele SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="a00a8-135">Next, configure the SQLitePCLRaw provider.</span></span> <span data-ttu-id="a00a8-136">Ujistěte se, že je to hotové předtím, než se v aplikaci použije Microsoft. data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="a00a8-136">Ensure this is done before Microsoft.Data.Sqlite is used in your app.</span></span> <span data-ttu-id="a00a8-137">Nepoužívejte také balíček SQLitePCLRaw sady, který by mohl přepsat vašeho poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="a00a8-137">Also, avoid using a SQLitePCLRaw bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
