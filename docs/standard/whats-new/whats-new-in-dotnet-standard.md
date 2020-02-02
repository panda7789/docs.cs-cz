---
title: Novinky v rozhraní .NET Standard
description: Tento článek shrnuje nové funkce a vylepšení, které najdete v každé nové verzi .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: a90df0360211c3b02f4f2d8697890180099c5807
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921062"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="c1328-103">Novinky v rozhraní .NET Standard</span><span class="sxs-lookup"><span data-stu-id="c1328-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="c1328-104">.NET Standard je formální specifikace, která definuje sadu rozhraní API s verzí, která musí být dostupná v implementacích .NET, které vyhovují této verzi standardu.</span><span class="sxs-lookup"><span data-stu-id="c1328-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="c1328-105">.NET Standard je cílena na vývojáře knihovny.</span><span class="sxs-lookup"><span data-stu-id="c1328-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="c1328-106">Knihovna, která cílí na verzi .NET Standard, se dá použít v jakékoli implementaci .NET Framework, .NET Core nebo Xamarin, která podporuje tuto verzi standardu.</span><span class="sxs-lookup"><span data-stu-id="c1328-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="c1328-107">Nejnovější verze .NET Standard je 2,0.</span><span class="sxs-lookup"><span data-stu-id="c1328-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="c1328-108">Je součástí sady .NET Core 2,0 SDK a také se sadou Visual Studio 2017 verze 15,3 s nainstalovanou úlohou .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1328-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="c1328-109">Podporované implementace .NET</span><span class="sxs-lookup"><span data-stu-id="c1328-109">Supported .NET implementations</span></span>

<span data-ttu-id="c1328-110">.NET Standard 2,0 jsou podporovány následujícími implementacemi rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="c1328-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="c1328-111">.NET Core 2,0 nebo novější</span><span class="sxs-lookup"><span data-stu-id="c1328-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="c1328-112">.NET Framework 4.6.1 nebo novější</span><span class="sxs-lookup"><span data-stu-id="c1328-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="c1328-113">Mono 5,4 nebo novější</span><span class="sxs-lookup"><span data-stu-id="c1328-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="c1328-114">Xamarin. iOS 10,14 nebo novější</span><span class="sxs-lookup"><span data-stu-id="c1328-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="c1328-115">Xamarin. Mac 3,8 nebo novější</span><span class="sxs-lookup"><span data-stu-id="c1328-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="c1328-116">Xamarin. Android 8,0 nebo novější</span><span class="sxs-lookup"><span data-stu-id="c1328-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="c1328-117">Univerzální platforma Windows 10.0.16299 nebo novější</span><span class="sxs-lookup"><span data-stu-id="c1328-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="c1328-118">Co je nového v .NET Standard 2,0</span><span class="sxs-lookup"><span data-stu-id="c1328-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="c1328-119">.NET Standard 2,0 obsahuje následující nové funkce:</span><span class="sxs-lookup"><span data-stu-id="c1328-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="c1328-120">Obrovské rozšířené sady rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c1328-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="c1328-121">Až do verze 1,6, .NET Standard zahrnuli relativně malou podmnožinu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c1328-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="c1328-122">Mezi vyloučenými z těchto možností bylo mnoho rozhraní API, které se běžně používalo v .NET Framework nebo Xamarin.</span><span class="sxs-lookup"><span data-stu-id="c1328-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="c1328-123">To ztěžuje vývoj, protože vyžaduje, aby vývojáři našli vhodné náhrady pro známá rozhraní API při vývoji aplikací a knihoven, které cílí na více implementací rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c1328-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="c1328-124">.NET Standard 2,0 řeší toto omezení přidáním více než 20 000 více rozhraní API, než je k dispozici v .NET Standard 1,6, předchozí verze standardu.</span><span class="sxs-lookup"><span data-stu-id="c1328-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="c1328-125">Seznam rozhraní API, která byla přidána do .NET Standard 2,0, najdete v článku [.NET Standard 2,0 vs 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="c1328-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="c1328-126">Mezi doplňky <xref:System> oboru názvů v .NET Standard 2,0 patří:</span><span class="sxs-lookup"><span data-stu-id="c1328-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="c1328-127">Podpora pro třídu <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="c1328-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="c1328-128">Lepší podpora pro práci s poli z dalších členů třídy <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="c1328-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="c1328-129">Lepší podpora pro práci s atributy z dalších členů ve třídě <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="c1328-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="c1328-130">Lepší podpora kalendáře a další možnosti formátování pro <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c1328-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="c1328-131">Další funkce zaokrouhlování <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="c1328-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="c1328-132">Další funkce ve třídě <xref:System.Environment>.</span><span class="sxs-lookup"><span data-stu-id="c1328-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="c1328-133">Vylepšená kontrola uvolňování paměti prostřednictvím <xref:System.GC> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1328-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="c1328-134">Rozšířená podpora pro porovnání řetězců, výčet a normalizaci ve třídě <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c1328-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="c1328-135">Podpora pro letní čas a časy přechodu v <xref:System.TimeZoneInfo.AdjustmentRule> a <xref:System.TimeZoneInfo.TransitionTime>ch třídách.</span><span class="sxs-lookup"><span data-stu-id="c1328-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="c1328-136">Výrazně vylepšené funkce třídy <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="c1328-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="c1328-137">Lepší podpora pro deserializaci objektů výjimek přidáním konstruktoru výjimky s parametry <xref:System.Runtime.Serialization.SerializationInfo> a <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="c1328-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="c1328-138">Podpora pro knihovny .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c1328-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="c1328-139">Většina knihoven cílí na .NET Framework místo .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c1328-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="c1328-140">Většina volání v těchto knihovnách je však rozhraní API, která jsou součástí .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="c1328-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="c1328-141">Počínaje .NET Standard 2,0 můžete k .NET Framework knihoven přistupovat z knihovny .NET Standard pomocí [překrytí kompatibility](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="c1328-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="c1328-142">Tato vrstva kompatibility je pro vývojáře transparentní; nemusíte nic dělat, abyste mohli využívat .NET Framework knihoven.</span><span class="sxs-lookup"><span data-stu-id="c1328-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="c1328-143">Jediným požadavkem je, aby rozhraní API volaná knihovnou tříd .NET Framework měla být zahrnutá do .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="c1328-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="c1328-144">Podpora Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1328-144">Support for Visual Basic</span></span>

<span data-ttu-id="c1328-145">Nyní můžete vyvíjet knihovny .NET Standard v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1328-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="c1328-146">Pro Visual Basic vývojářů, kteří používají Visual Studio 2017 verze 15,3 nebo novější s nainstalovanou úlohou .NET Core, Visual Studio teď obsahuje .NET Standard šablonu knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="c1328-146">For Visual Basic developers using Visual Studio 2017 version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="c1328-147">Pro Visual Basic vývojářů, kteří používají jiné vývojové nástroje a prostředí, můžete pomocí příkazu [dotnet New](../../core/tools/dotnet-new.md) vytvořit projekt knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c1328-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="c1328-148">Další informace najdete v tématu [Podpora nástrojů pro knihovny .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="c1328-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="c1328-149">Podpora nástrojů pro knihovny .NET Standard</span><span class="sxs-lookup"><span data-stu-id="c1328-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="c1328-150">S vydáním .NET Core 2,0 a .NET Standard 2,0 aplikace Visual Studio 2017 i [.NET Core CLI](../../core/tools/index.md) zahrnují podporu nástrojů pro vytváření knihoven .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c1328-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="c1328-151">Pokud nainstalujete Visual Studio s úlohou **vývoje .NET Core pro různé platformy** , můžete vytvořit projekt knihovny .NET Standard 2,0 pomocí šablony projektu, jak ukazuje následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="c1328-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="c1328-152">C#</span><span class="sxs-lookup"><span data-stu-id="c1328-152">C#</span></span>](#tab/csharp)

![Přidat nový projekt knihovny .NET Standard](./media/std-project-cs.png)

<span data-ttu-id="c1328-154">Pokud používáte .NET Core CLI, následující příkaz [dotnet New](../../core/tools/dotnet-new.md) vytvoří projekt knihovny tříd, který cílí na .NET Standard 2,0:</span><span class="sxs-lookup"><span data-stu-id="c1328-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="c1328-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1328-155">Visual Basic</span></span>](#tab/vb)

![Přidat nový projekt knihovny .NET Standard](./media/std-project-vb.png)

<span data-ttu-id="c1328-157">Pokud používáte .NET Core CLI, následující příkaz [dotnet New](../../core/tools/dotnet-new.md) vytvoří projekt knihovny tříd, který cílí na .NET Standard 2,0:</span><span class="sxs-lookup"><span data-stu-id="c1328-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="c1328-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1328-158">See also</span></span>

- [<span data-ttu-id="c1328-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="c1328-159">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="c1328-160">Představujeme .NET Standard</span><span class="sxs-lookup"><span data-stu-id="c1328-160">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
