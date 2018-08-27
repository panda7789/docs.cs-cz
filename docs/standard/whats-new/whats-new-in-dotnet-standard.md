---
title: Co je nového v .NET Standard
description: Tento článek shrnuje nové funkce a vylepšení v každé nové verze .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8810508bc61f6fd625b1485f199249a96b2686e6
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931505"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="cdb5b-103">Co je nového v .NET Standard</span><span class="sxs-lookup"><span data-stu-id="cdb5b-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="cdb5b-104">.NET Standard je formální specifikaci, který definuje sadu označené verzí rozhraní API, která musí být k dispozici na implementace .NET, které jsou v souladu s touto verzí standardu.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="cdb5b-105">.NET Standard je cílena na vývojáře knihovny.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="cdb5b-106">Knihovnu, která cílí na .NET Standard verze lze použít v rozhraní .NET Framework a .NET Core, Xamarin implementaci, která podporuje verzi standard.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="cdb5b-107">Překopírujte nejnovější verzi .NET Standard je 2.0.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="cdb5b-108">To je součástí s .NET Core 2.0 SDK, stejně jako s Visual Studio 2017 verze 15.3 nainstalovaná úloha .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="cdb5b-109">Podporovaná implementace .NET</span><span class="sxs-lookup"><span data-stu-id="cdb5b-109">Supported .NET implementations</span></span>

<span data-ttu-id="cdb5b-110">Rozhraní .NET Standard 2.0 podporuje následující implementace .NET:</span><span class="sxs-lookup"><span data-stu-id="cdb5b-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="cdb5b-111">.NET core 2.0 nebo novější</span><span class="sxs-lookup"><span data-stu-id="cdb5b-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="cdb5b-112">Rozhraní .NET framework 4.6.1 nebo novější</span><span class="sxs-lookup"><span data-stu-id="cdb5b-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="cdb5b-113">Mono 5.4 nebo novější</span><span class="sxs-lookup"><span data-stu-id="cdb5b-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="cdb5b-114">Xamarin.iOS 10.14 nebo novější</span><span class="sxs-lookup"><span data-stu-id="cdb5b-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="cdb5b-115">Rozhraní Xamarin.Mac 3,8 nebo novější</span><span class="sxs-lookup"><span data-stu-id="cdb5b-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="cdb5b-116">Xamarin.Android 8.0 nebo novější</span><span class="sxs-lookup"><span data-stu-id="cdb5b-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="cdb5b-117">Univerzální platforma Windows 10.0.16299 nebo novější</span><span class="sxs-lookup"><span data-stu-id="cdb5b-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="cdb5b-118">Co je nového v .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="cdb5b-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="cdb5b-119">Rozhraní .NET Standard 2.0 obsahuje následující nové funkce:</span><span class="sxs-lookup"><span data-stu-id="cdb5b-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="cdb5b-120">Výrazně rozšířené sady rozhraní API</span><span class="sxs-lookup"><span data-stu-id="cdb5b-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="cdb5b-121">Prostřednictvím verze 1.6 zahrnuté relativně malou podmnožinu rozhraní API .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="cdb5b-122">Mezi ty vyloučené byly mnoho rozhraní API, které se běžně používá v rozhraní .NET Framework nebo Xamarin.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="cdb5b-123">To komplikuje vývoje, protože vyžaduje, že vývojáři najít vhodné při nahrazování známá rozhraní API při vývoji aplikací a knihoven, které se zaměřují víc implementací rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="cdb5b-124">Rozhraní .NET Standard 2.0 řeší toto omezení přidáním více než 20 000 další rozhraní API, než byly k dispozici v rozhraní .NET Standard 1.6, předchozí verze standard.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="cdb5b-125">Seznam rozhraní API, která byla přidána do .NET Standard 2.0 najdete v tématu [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="cdb5b-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="cdb5b-126">Některé nové funkce do <xref:System> obor názvů v rozhraní .NET Standard 2.0 patří:</span><span class="sxs-lookup"><span data-stu-id="cdb5b-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="cdb5b-127">Podpora <xref:System.AppDomain> třídy.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="cdb5b-128">Lepší podporu pro práci s poli z další členy v <xref:System.Array> třídy.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="cdb5b-129">Lepší podporu pro práci s atributy z další členy v <xref:System.Attribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="cdb5b-130">Kalendář lepší podporu a další možnosti formátování pro <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="cdb5b-131">Další <xref:System.Decimal> zaokrouhlení funkce.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="cdb5b-132">Další funkce v <xref:System.Environment> třídy.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="cdb5b-133">Vylepšené kontroly nad systému uvolňování paměti prostřednictvím <xref:System.GC> třídy.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="cdb5b-134">Vylepšená podpora pro porovnání řetězců, výčet a normalizace v <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="cdb5b-135">Podpora pro letní čas úpravy a časů přechodů v <xref:System.TimeZoneInfo.AdjustmentRule> a <xref:System.TimeZoneInfo.TransitionTime> třídy.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="cdb5b-136">K výraznému rozšíření funkčnosti v <xref:System.Type> třídy.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="cdb5b-137">Lepší podpora pro deserializaci objektů výjimek tak, že přidáte k výjimce konstruktor s <xref:System.Runtime.Serialization.SerializationInfo> a <xref:System.Runtime.Serialization.StreamingContext> parametry.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="cdb5b-138">Podporu pro knihovny rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cdb5b-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="cdb5b-139">Drtivou většinu knihoven cílit .NET Framework, nikoli .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="cdb5b-140">Většina výzev v těchto knihoven jsou však k rozhraním API, které jsou součástí rozhraní .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="cdb5b-141">Počínaje rozhraním .NET Standard 2.0, dostanete knihovny rozhraní .NET Framework z knihovny .NET Standard s využitím [kompatibility](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="cdb5b-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="cdb5b-142">Tato vrstva kompatibility je transparentní pro vývojáře; nemusíte dělat nic výhod knihovny rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="cdb5b-143">Jeden požadavkem je, že rozhraní API volané knihovny tříd rozhraní .NET Framework musí být součástí rozhraní .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="cdb5b-144">Podpora jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cdb5b-144">Support for Visual Basic</span></span>

<span data-ttu-id="cdb5b-145">Teď můžete vyvíjet knihovny .NET Standard v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="cdb5b-146">Pro vývojáře v jazyce Visual Basic pomocí Visual Studio 2017 verze 15.3 nebo novější s .NET Core zatížení nainstalované Visual Studio teď obsahuje šablony knihovna tříd rozhraní .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-146">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="cdb5b-147">Pro vývojáře jazyka Visual Basic, kteří používají další nástroje pro vývoj a prostředí, můžete použít [dotnet nové](../../core/tools/dotnet-new.md) příkaz pro vytvoření projektu knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="cdb5b-148">Další informace najdete v tématu [Podpora nástrojů pro knihovny .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="cdb5b-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="cdb5b-149">Podpora nástrojů pro knihovny .NET Standard</span><span class="sxs-lookup"><span data-stu-id="cdb5b-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="cdb5b-150">Ve verzi 2.0 rozhraní .NET Core a .NET Standard 2.0, obě sady Visual Studio 2017 a [.NET Core rozhraní příkazového řádku (CLI)](../../core/tools/index.md) patří podpora nástrojů pro vytváření knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cdb5b-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="cdb5b-151">Při instalaci sady Visual Studio s **vývoj pro různé platformy .NET Core** úlohy, můžete vytvořit projekt knihovny .NET Standard 2.0 pomocí šablony projektu, jak ukazuje následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="cdb5b-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="cdb5b-152">C#</span><span class="sxs-lookup"><span data-stu-id="cdb5b-152">C#</span></span>](#tab/csharp)

![Přidejte novou .NET Standard projekt knihovny](./media/std-project-cs.png)

<span data-ttu-id="cdb5b-154">Pokud používáte .NET Core CLI, následující [dotnet nové](../../core/tools/dotnet-new.md) příkaz vytvoří projekt knihovny tříd, který cílí na .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="cdb5b-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="cdb5b-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cdb5b-155">Visual Basic</span></span>](#tab/vb)

![Přidejte novou .NET Standard projekt knihovny](./media/std-project-vb.png)

<span data-ttu-id="cdb5b-157">Pokud používáte .NET Core CLI, následující [dotnet nové](../../core/tools/dotnet-new.md) příkaz vytvoří projekt knihovny tříd, který cílí na .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="cdb5b-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="cdb5b-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdb5b-158">See also</span></span>

[<span data-ttu-id="cdb5b-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="cdb5b-159">.NET Standard</span></span>](../net-standard.md)  
[<span data-ttu-id="cdb5b-160">Představujeme .NET Standard</span><span class="sxs-lookup"><span data-stu-id="cdb5b-160">Introducing .NET Standard</span></span>](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
