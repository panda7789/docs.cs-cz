---
title: Vlastní verze SQLite
ms.date: 12/13/2019
description: Naučte se používat vlastní verzi nativní knihovny SQLite.
ms.openlocfilehash: dd27278c1dbe17b12e5067d04d19043bf259b1e8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746988"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="b0b89-103">Vlastní verze SQLite</span><span class="sxs-lookup"><span data-stu-id="b0b89-103">Custom SQLite versions</span></span>

<span data-ttu-id="b0b89-104">Microsoft. data. sqlite je postaven nad SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="b0b89-104">Microsoft.Data.Sqlite is built on top of SQLitePCLRaw.</span></span> <span data-ttu-id="b0b89-105">Můžete použít vlastní verze nativní knihovny SQLite pomocí sady prostředků nebo konfigurací poskytovatele SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="b0b89-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a SQLitePCLRaw provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="b0b89-106">Sady</span><span class="sxs-lookup"><span data-stu-id="b0b89-106">Bundles</span></span>

<span data-ttu-id="b0b89-107">SQLitePCLRaw poskytuje balíčky sady prostředků, které usnadňují přenesení správných závislostí napříč různými platformami.</span><span class="sxs-lookup"><span data-stu-id="b0b89-107">SQLitePCLRaw provides bundle packages that make it easy to bring in the right dependencies across different platforms.</span></span>

<span data-ttu-id="b0b89-108">Hlavní balíček Microsoft. data. sqlite ve výchozím nastavení přináší SQLitePCLRaw. bundle_e_sqlite3.</span><span class="sxs-lookup"><span data-stu-id="b0b89-108">The main Microsoft.Data.Sqlite package brings in SQLitePCLRaw.bundle_e_sqlite3 by default.</span></span>

<span data-ttu-id="b0b89-109">Pokud chcete použít jinou sadu prostředků, nainstalujte místo toho balíček `Microsoft.Data.Sqlite.Core` společně s balíčkem sady, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="b0b89-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="b0b89-110">Sady se automaticky inicializují pomocí Microsoft. data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="b0b89-110">Bundles are automatically initialized by Microsoft.Data.Sqlite.</span></span>

| <span data-ttu-id="b0b89-111">Nabídky</span><span class="sxs-lookup"><span data-stu-id="b0b89-111">Bundle</span></span> | <span data-ttu-id="b0b89-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b0b89-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b0b89-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="b0b89-113">SQLitePCLRaw.bundle_e_sqlite3</span></span> | <span data-ttu-id="b0b89-114">Poskytuje konzistentní verzi SQLite na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="b0b89-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="b0b89-115">Zahrnuje rozšíření stromu FTS4, FTS5, JSON1 a R \*.</span><span class="sxs-lookup"><span data-stu-id="b0b89-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="b0b89-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="b0b89-116">This is the default.</span></span> |
| <span data-ttu-id="b0b89-117">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="b0b89-117">SQLitePCLRaw.bundle_green</span></span> | <span data-ttu-id="b0b89-118">Stejné jako bundle_e_sqlite3, s výjimkou iOS, kde používá systémovou knihovnu SQLite.</span><span class="sxs-lookup"><span data-stu-id="b0b89-118">Same as bundle_e_sqlite3, except on iOS where it uses the system SQLite library.</span></span> |
| <span data-ttu-id="b0b89-119">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="b0b89-119">SQLitePCLRaw.bundle_zetetic</span></span> | <span data-ttu-id="b0b89-120">Používá oficiální SQLCipher buildy z Zetetic (Nezahrnuto).</span><span class="sxs-lookup"><span data-stu-id="b0b89-120">Uses the official SQLCipher builds from Zetetic (not included).</span></span> |
| <span data-ttu-id="b0b89-121">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="b0b89-121">SQLitePCLRaw.bundle_winsqlite3</span></span> | <span data-ttu-id="b0b89-122">Používá winsqlite3. dll, systémovou knihovnu SQLite ve Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b0b89-122">Uses winsqlite3.dll, the system SQLite library on Windows 10.</span></span> |
| <span data-ttu-id="b0b89-123">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="b0b89-123">SQLitePCLRaw.bundle_e_sqlcipher</span></span> | <span data-ttu-id="b0b89-124">Poskytuje neoficiální a open source sestavení SQLCipher.</span><span class="sxs-lookup"><span data-stu-id="b0b89-124">Provides an unofficial, open-source build of SQLCipher.</span></span> |

<span data-ttu-id="b0b89-125">Například pro použití neoficiálního Open Source sestavení SQLCipher použijte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="b0b89-125">For example, to use the unofficial, open-source build of SQLCipher use the following commands.</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="b0b89-126">Rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="b0b89-126">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="b0b89-127">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b0b89-127">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a><span data-ttu-id="b0b89-128">SQLitePCLRaw poskytovatelé</span><span class="sxs-lookup"><span data-stu-id="b0b89-128">SQLitePCLRaw providers</span></span>

<span data-ttu-id="b0b89-129">Pomocí `SQLitePCLRaw.provider.dynamic_cdecl` balíčku můžete použít vlastní sestavení SQLite.</span><span class="sxs-lookup"><span data-stu-id="b0b89-129">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="b0b89-130">V tomto případě zodpovídáte za nasazení nativní knihovny s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="b0b89-130">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="b0b89-131">Všimněte si, že podrobnosti o nasazení nativních knihoven s vaší aplikací se výrazně liší v závislosti na tom, kterou platformu .NET a modul runtime používáte.</span><span class="sxs-lookup"><span data-stu-id="b0b89-131">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="b0b89-132">Nejdřív budete muset implementovat IGetFunctionPointer.</span><span class="sxs-lookup"><span data-stu-id="b0b89-132">First, you'll need to implement IGetFunctionPointer.</span></span> <span data-ttu-id="b0b89-133">Implementace je poměrně triviální v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b0b89-133">The implementation is fairly trivial on .NET Core.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="b0b89-134">Dále nakonfigurujte poskytovatele SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="b0b89-134">Next, configure the SQLitePCLRaw provider.</span></span> <span data-ttu-id="b0b89-135">Ujistěte se, že je to hotové předtím, než se v aplikaci použije Microsoft. data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="b0b89-135">Ensure this is done before Microsoft.Data.Sqlite is used in your app.</span></span> <span data-ttu-id="b0b89-136">Nepoužívejte také balíček SQLitePCLRaw sady, který by mohl přepsat vašeho poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="b0b89-136">Also, avoid using a SQLitePCLRaw bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
