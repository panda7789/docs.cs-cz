---
title: Vlastní verze SQLite
ms.date: 05/14/2020
description: Naučte se používat vlastní verzi nativní knihovny SQLite.
ms.openlocfilehash: 15db10db26bc7c5017313ca020a0e1e528ba207a
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83440834"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="9d83e-103">Vlastní verze SQLite</span><span class="sxs-lookup"><span data-stu-id="9d83e-103">Custom SQLite versions</span></span>

<span data-ttu-id="9d83e-104">`Microsoft.Data.Sqlite`je postaven na začátku `SQLitePCLRaw` .</span><span class="sxs-lookup"><span data-stu-id="9d83e-104">`Microsoft.Data.Sqlite` is built on top of `SQLitePCLRaw`.</span></span> <span data-ttu-id="9d83e-105">Můžete použít vlastní verze nativní knihovny SQLite pomocí sady prostředků nebo konfigurací `SQLitePCLRaw` poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="9d83e-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a `SQLitePCLRaw` provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="9d83e-106">Sady</span><span class="sxs-lookup"><span data-stu-id="9d83e-106">Bundles</span></span>

<span data-ttu-id="9d83e-107">`SQLitePCLRaw`poskytuje balíčky na bázi pohodlí, které usnadňují přenesení správných závislostí napříč různými platformami.</span><span class="sxs-lookup"><span data-stu-id="9d83e-107">`SQLitePCLRaw` provides convenience-based bundle packages, that make it easy to bring in the right dependencies across different platforms.</span></span> <span data-ttu-id="9d83e-108">Hlavní `Microsoft.Data.Sqlite` balíček ve `SQLitePCLRaw.bundle_e_sqlite3` výchozím nastavení přinese.</span><span class="sxs-lookup"><span data-stu-id="9d83e-108">The main `Microsoft.Data.Sqlite` package brings in `SQLitePCLRaw.bundle_e_sqlite3` by default.</span></span> <span data-ttu-id="9d83e-109">Pokud chcete použít jinou sadu prostředků, nainstalujte `Microsoft.Data.Sqlite.Core` balíček místo toho společně s balíčkem sady, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="9d83e-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="9d83e-110">Sady jsou automaticky inicializovány nástrojem `Microsoft.Data.Sqlite` .</span><span class="sxs-lookup"><span data-stu-id="9d83e-110">Bundles are automatically initialized by `Microsoft.Data.Sqlite`.</span></span>

| <span data-ttu-id="9d83e-111">Nabídky</span><span class="sxs-lookup"><span data-stu-id="9d83e-111">Bundle</span></span> | <span data-ttu-id="9d83e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9d83e-112">Description</span></span> |
|--|--|
| [<span data-ttu-id="9d83e-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="9d83e-113">SQLitePCLRaw.bundle_e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | <span data-ttu-id="9d83e-114">Poskytuje konzistentní verzi SQLite na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="9d83e-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="9d83e-115">Zahrnuje rozšíření stromu FTS4, FTS5, JSON1 a R \*.</span><span class="sxs-lookup"><span data-stu-id="9d83e-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="9d83e-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="9d83e-116">This is the default.</span></span> |
| [<span data-ttu-id="9d83e-117">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="9d83e-117">SQLitePCLRaw.bundle_e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | <span data-ttu-id="9d83e-118">Poskytuje neoficiální sestavení open source `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="9d83e-118">Provides an unofficial, open-source build of `SQLCipher`.</span></span> |
| [<span data-ttu-id="9d83e-119">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="9d83e-119">SQLitePCLRaw.bundle_green</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | <span data-ttu-id="9d83e-120">Stejné jako `bundle_e_sqlite3` , s výjimkou iOS, kde používá systémovou knihovnu sqlite.</span><span class="sxs-lookup"><span data-stu-id="9d83e-120">Same as `bundle_e_sqlite3`, except on iOS where it uses the system SQLite library.</span></span> |
| [<span data-ttu-id="9d83e-121">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="9d83e-121">SQLitePCLRaw.bundle_winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | <span data-ttu-id="9d83e-122">Používá `winsqlite3.dll` , systémová knihovna SQLite ve Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9d83e-122">Uses `winsqlite3.dll`, the system SQLite library on Windows 10.</span></span> |
| [<span data-ttu-id="9d83e-123">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="9d83e-123">SQLitePCLRaw.bundle_zetetic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | <span data-ttu-id="9d83e-124">Používá oficiální `SQLCipher` buildy z Zetetic (Nezahrnuto).</span><span class="sxs-lookup"><span data-stu-id="9d83e-124">Uses the official `SQLCipher` builds from Zetetic (not included).</span></span> |

<span data-ttu-id="9d83e-125">Například pro použití neoficiálního Open Source sestavení `SQLCipher` použijte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="9d83e-125">For example, to use the unofficial, open-source build of `SQLCipher` use the following commands.</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="9d83e-126">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="9d83e-126">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="9d83e-127">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9d83e-127">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a><span data-ttu-id="9d83e-128">SQLitePCLRaw poskytovatelé k dispozici</span><span class="sxs-lookup"><span data-stu-id="9d83e-128">SQLitePCLRaw available providers</span></span>

<span data-ttu-id="9d83e-129">Pokud se nespoléháte na sadu prostředků, můžete použít dostupné poskytovatele SQLite se základním sestavením.</span><span class="sxs-lookup"><span data-stu-id="9d83e-129">When not relying on a bundle, you can use the available providers of SQLite with the core assembly.</span></span>

| <span data-ttu-id="9d83e-130">Poskytovatel</span><span class="sxs-lookup"><span data-stu-id="9d83e-130">Provider</span></span> | <span data-ttu-id="9d83e-131">Popis</span><span class="sxs-lookup"><span data-stu-id="9d83e-131">Description</span></span> |
|--|--|
| [<span data-ttu-id="9d83e-132">SQLitePCLRaw. Provider. Dynamic</span><span class="sxs-lookup"><span data-stu-id="9d83e-132">SQLitePCLRaw.provider.dynamic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | <span data-ttu-id="9d83e-133">`dynamic`Zprostředkovatel načte nativní knihovnu namísto použití <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> atributů.</span><span class="sxs-lookup"><span data-stu-id="9d83e-133">The `dynamic` provider loads the native library instead of using <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributes.</span></span> <span data-ttu-id="9d83e-134">Další informace o použití tohoto poskytovatele najdete v tématu [použití dynamického poskytovatele](#use-the-dynamic-provider).</span><span class="sxs-lookup"><span data-stu-id="9d83e-134">For more information on using this provider, see [use the dynamic provider](#use-the-dynamic-provider).</span></span> |
| [<span data-ttu-id="9d83e-135">SQLitePCLRaw. Provider. e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="9d83e-135">SQLitePCLRaw.provider.e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | <span data-ttu-id="9d83e-136">`e_sqlite3`Je výchozím zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="9d83e-136">The `e_sqlite3` is the default provider.</span></span> |
| [<span data-ttu-id="9d83e-137">SQLitePCLRaw. Provider. e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="9d83e-137">SQLitePCLRaw.provider.e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | <span data-ttu-id="9d83e-138">`e_sqlcipher`Poskytovatel je neoficiální a nepodporovaný `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="9d83e-138">The `e_sqlcipher` provider is the unofficial and unsupported `SQLCipher`.</span></span> |
| [<span data-ttu-id="9d83e-139">SQLitePCLRaw. Provider. sqlite3</span><span class="sxs-lookup"><span data-stu-id="9d83e-139">SQLitePCLRaw.provider.sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | <span data-ttu-id="9d83e-140">`sqlite3`Poskytovatel se poskytuje systémem `SQLite` pro iOS, MacOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="9d83e-140">The `sqlite3` provider is a system-provided `SQLite` for iOS, macOS, and Linux.</span></span> |
| [<span data-ttu-id="9d83e-141">SQLitePCLRaw. Provider. SQLCIPHER</span><span class="sxs-lookup"><span data-stu-id="9d83e-141">SQLitePCLRaw.provider.sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | <span data-ttu-id="9d83e-142">`sqlcipher`Poskytovatel je pro oficiální `SQLCipher` sestavení z `Zetetic` .</span><span class="sxs-lookup"><span data-stu-id="9d83e-142">The `sqlcipher` provider is for official `SQLCipher` builds from `Zetetic`.</span></span> |
| [<span data-ttu-id="9d83e-143">SQLitePCLRaw. Provider. winsqlite3</span><span class="sxs-lookup"><span data-stu-id="9d83e-143">SQLitePCLRaw.provider.winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | <span data-ttu-id="9d83e-144">`winsqlite3`Zprostředkovatel je pro prostředí Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9d83e-144">The `winsqlite3` provider is for Windows 10 environments.</span></span> |

<span data-ttu-id="9d83e-145">Chcete-li použít `sqlite3` zprostředkovatele, použijte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="9d83e-145">To use the `sqlite3` provider use the following commands:</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="9d83e-146">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="9d83e-146">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[<span data-ttu-id="9d83e-147">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9d83e-147">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

<span data-ttu-id="9d83e-148">S nainstalovanými balíčky pak nastavte poskytovatele na `sqlite3` instanci.</span><span class="sxs-lookup"><span data-stu-id="9d83e-148">With the packages installed, you then set the provider to the `sqlite3` instance.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a><span data-ttu-id="9d83e-149">Použití dynamického poskytovatele</span><span class="sxs-lookup"><span data-stu-id="9d83e-149">Use the dynamic provider</span></span>

<span data-ttu-id="9d83e-150">Můžete použít vlastní sestavení SQLite využitím `SQLitePCLRaw.provider.dynamic_cdecl` balíčku.</span><span class="sxs-lookup"><span data-stu-id="9d83e-150">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="9d83e-151">V tomto případě zodpovídáte za nasazení nativní knihovny s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="9d83e-151">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="9d83e-152">Všimněte si, že podrobnosti o nasazení nativních knihoven s vaší aplikací se výrazně liší v závislosti na tom, kterou platformu .NET a modul runtime používáte.</span><span class="sxs-lookup"><span data-stu-id="9d83e-152">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="9d83e-153">Nejdřív budete muset implementovat `IGetFunctionPointer` .</span><span class="sxs-lookup"><span data-stu-id="9d83e-153">First, you'll need to implement `IGetFunctionPointer`.</span></span> <span data-ttu-id="9d83e-154">Implementace rozhraní .NET Core je následující:</span><span class="sxs-lookup"><span data-stu-id="9d83e-154">The implementation on .NET Core is as follows:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="9d83e-155">Dále nakonfigurujte `SQLitePCLRaw` poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="9d83e-155">Next, configure the `SQLitePCLRaw` provider.</span></span> <span data-ttu-id="9d83e-156">Zajistěte, aby se to dokončilo předtím, než `Microsoft.Data.Sqlite` se ve vaší aplikaci použije.</span><span class="sxs-lookup"><span data-stu-id="9d83e-156">Ensure this is done before `Microsoft.Data.Sqlite` is used in your app.</span></span> <span data-ttu-id="9d83e-157">Nepoužívejte také `SQLitePCLRaw` balíček sady prostředků, který by mohl přepsat vašeho poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="9d83e-157">Also, avoid using a `SQLitePCLRaw` bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
