---
title: Co je nového ve standardní rozhraní .NET
description: Tento článek shrnuje nové funkce a vylepšení v každé nové verze .NET Standard nalezen.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e422e6ff65439d105020a6305b66a8192586a8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591486"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="99131-103">Co je nového ve standardní rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="99131-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="99131-104">.NET Standard je formální specifikaci, která definuje sadu rozhraní API, která musí být k dispozici na implementace rozhraní .NET, které jsou v souladu s touto verzí standardní verzí.</span><span class="sxs-lookup"><span data-stu-id="99131-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="99131-105">.NET Standard je cílena na vývojáře knihovny.</span><span class="sxs-lookup"><span data-stu-id="99131-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="99131-106">Knihovna, která cílí na .NET Standard verzi lze použít v rozhraní .NET Framework, .NET Core nebo Xamarin implementace, která podporuje tuto verzi standard.</span><span class="sxs-lookup"><span data-stu-id="99131-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="99131-107">Nejnovější verze .NET Standard je 2.0.</span><span class="sxs-lookup"><span data-stu-id="99131-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="99131-108">Je zahrnut pomocí .NET SDK 2.0 jádra, a také s Visual Studio 2017 verze 15.3 se zatížením .NET Core nainstalována.</span><span class="sxs-lookup"><span data-stu-id="99131-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="99131-109">Podporované implementace rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="99131-109">Supported .NET implementations</span></span>

<span data-ttu-id="99131-110">Rozhraní .NET 2.0 standardní podporuje následující implementace rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="99131-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="99131-111">.NET core 2.0 nebo novější</span><span class="sxs-lookup"><span data-stu-id="99131-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="99131-112">Rozhraní .NET framework 4.6.1 nebo novější</span><span class="sxs-lookup"><span data-stu-id="99131-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="99131-113">Mono 5.4 nebo novější</span><span class="sxs-lookup"><span data-stu-id="99131-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="99131-114">Xamarin.iOS 10.14 nebo novější</span><span class="sxs-lookup"><span data-stu-id="99131-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="99131-115">Xamarin.Mac 3.8 nebo novější</span><span class="sxs-lookup"><span data-stu-id="99131-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="99131-116">Xamarin.Android 8.0 nebo novější</span><span class="sxs-lookup"><span data-stu-id="99131-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="99131-117">Univerzální platformu Windows 10.0.16299 nebo novější</span><span class="sxs-lookup"><span data-stu-id="99131-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="99131-118">Co je nového v rozhraní .NET 2.0 Standard</span><span class="sxs-lookup"><span data-stu-id="99131-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="99131-119">Rozhraní .NET 2.0 standardní obsahuje následující nové funkce:</span><span class="sxs-lookup"><span data-stu-id="99131-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="99131-120">Významně rozšířená sada rozhraní API</span><span class="sxs-lookup"><span data-stu-id="99131-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="99131-121">Prostřednictvím verzi 1.6 zahrnuty .NET Standard poměrně malou podmnožinu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="99131-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="99131-122">Mezi ty vyloučené byly mnoho rozhraní API, které byly často používány v rozhraní .NET Framework nebo Xamarin.</span><span class="sxs-lookup"><span data-stu-id="99131-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="99131-123">To komplikuje vývoj, protože vyžaduje, že vývojáři najít vhodný nahrazení pro známé rozhraní API při vývoji aplikací a knihovny, které cílí více implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="99131-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="99131-124">Rozhraní .NET 2.0 standardní řeší toto omezení přidáním přes 20 000 další rozhraní API, než byly k dispozici v rozhraní .NET standardní 1.6, předchozí verzi standard.</span><span class="sxs-lookup"><span data-stu-id="99131-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="99131-125">Seznam rozhraní API, které jsou přidané do standardní rozhraní .NET 2.0, naleznete v části [standardní rozhraní .NET 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="99131-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="99131-126">Některé doplňky k <xref:System> oboru názvů v rozhraní .NET 2.0 standardní patří:</span><span class="sxs-lookup"><span data-stu-id="99131-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="99131-127">Podpora pro <xref:System.AppDomain> třídy.</span><span class="sxs-lookup"><span data-stu-id="99131-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="99131-128">Lepší podpory pro práci s poli od další členové <xref:System.Array> třídy.</span><span class="sxs-lookup"><span data-stu-id="99131-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="99131-129">Lepší podpory pro práci s atributy z další členové <xref:System.Attribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="99131-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="99131-130">Lépe kalendář podpory a další možnosti formátování <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="99131-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="99131-131">Další <xref:System.Decimal> zaokrouhlení funkce.</span><span class="sxs-lookup"><span data-stu-id="99131-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="99131-132">Další funkce v <xref:System.Environment> třídy.</span><span class="sxs-lookup"><span data-stu-id="99131-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="99131-133">Rozšířené kontrolu nad uvolňování prostřednictvím <xref:System.GC> třídy.</span><span class="sxs-lookup"><span data-stu-id="99131-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="99131-134">Rozšířenou podporu pro porovnání řetězců, výčet a normalizaci v <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="99131-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="99131-135">Podpora pro letní čas úpravy a doby přechodu v <xref:System.TimeZoneInfo.AdjustmentRule> a <xref:System.TimeZoneInfo.TransitionTime> třídy.</span><span class="sxs-lookup"><span data-stu-id="99131-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="99131-136">Výrazně rozšířené funkce v <xref:System.Type> třídy.</span><span class="sxs-lookup"><span data-stu-id="99131-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="99131-137">Lepší podpory pro deserializaci objektů výjimek přidáním k výjimce konstruktor s <xref:System.Runtime.Serialization.SerializationInfo> a <xref:System.Runtime.Serialization.StreamingContext> parametry.</span><span class="sxs-lookup"><span data-stu-id="99131-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="99131-138">Podporu pro knihovny rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="99131-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="99131-139">Naprostou většinu knihovny cílí rozhraní .NET Framework místo .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="99131-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="99131-140">Většina volání v tyto knihovny jsou však k rozhraním API, které jsou obsažené v rozhraní .NET 2.0 standardní.</span><span class="sxs-lookup"><span data-stu-id="99131-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="99131-141">Od verze rozhraní .NET 2.0 standardní, dostanete knihovny rozhraní .NET Framework z knihovny .NET Standard pomocí [kompatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="99131-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="99131-142">Tuto vrstvu kompatibility je transparentní pro vývojáře; nemusíte dělat nic využívat výhod knihovnách rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99131-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="99131-143">Jeden požadavek je, že rozhraní API volat knihovna tříd rozhraní .NET Framework musí být součástí standardní rozhraní .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="99131-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="99131-144">Podpora jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99131-144">Support for Visual Basic</span></span>

<span data-ttu-id="99131-145">Nyní můžete vyvíjet .NET standardní knihovny v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="99131-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="99131-146">Pro vývojáře jazyka Visual Basic, Visual Studio 2017 verze 15.3 pomocí nebo novější s .NET Core zatížení nainstalované Visual Studio teď obsahuje šablonu standardní knihovna tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="99131-146">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="99131-147">Pro vývojáře jazyka Visual Basic, kteří používají jiné nástroje pro vývoj a prostředí, můžete použít [dotnet nové](../../core/tools/dotnet-new.md) příkaz k vytvoření standardní knihovny .NET projektu.</span><span class="sxs-lookup"><span data-stu-id="99131-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="99131-148">Další informace najdete v tématu [Podpora nástrojů pro rozhraní .NET standardní knihovny](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="99131-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="99131-149">Podpora nástrojů pro rozhraní .NET standardní knihovny</span><span class="sxs-lookup"><span data-stu-id="99131-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="99131-150">Verze rozhraní .NET Core 2.0 a .NET standardní 2.0, jak Visual Studio 2017 a [.NET Core rozhraní příkazového řádku (CLI)](../../core/tools/index.md) patří podpora nástrojů pro vytváření .NET standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="99131-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="99131-151">Pokud nainstalujete Visual Studio s **vývoj pro různé platformy .NET Core** zatížení, můžete vytvořit projekt knihovny .NET standardní 2.0 pomocí šablony projektu, jak ukazuje následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="99131-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="99131-152">C#</span><span class="sxs-lookup"><span data-stu-id="99131-152">C#</span></span>](#tab/csharp)

![Přidat nové standardní rozhraní .NET projektu knihovny](./media/std-project-cs.png)

<span data-ttu-id="99131-154">Pokud používáte rozhraní .NET Core příkazového řádku, následující [dotnet nové](../../core/tools/dotnet-new.md) příkaz vytvoří projektu knihovny tříd, která cílí rozhraní .NET 2.0 standardní:</span><span class="sxs-lookup"><span data-stu-id="99131-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="99131-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99131-155">Visual Basic</span></span>](#tab/vb)

![Přidat nové standardní rozhraní .NET projektu knihovny](./media/std-project-vb.png)

<span data-ttu-id="99131-157">Pokud používáte rozhraní .NET Core příkazového řádku, následující [dotnet nové](../../core/tools/dotnet-new.md) příkaz vytvoří projektu knihovny tříd, která cílí rozhraní .NET 2.0 standardní:</span><span class="sxs-lookup"><span data-stu-id="99131-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="99131-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="99131-158">See also</span></span>

[<span data-ttu-id="99131-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="99131-159">.NET Standard</span></span>](../net-standard.md)  
[<span data-ttu-id="99131-160">Představení Standard rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="99131-160">Introducing .NET Standard</span></span>](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
