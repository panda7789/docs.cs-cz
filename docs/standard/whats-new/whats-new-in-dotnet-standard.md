---
title: "Co je nového ve standardní rozhraní .NET"
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
ms.##devlang: dotnet
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e938c009b79af3b2f36094bbb74f4d38baeeac0b
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2017
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="3aa5b-102">Co je nového ve standardní rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="3aa5b-102">What's new in the .NET Standard</span></span>

<span data-ttu-id="3aa5b-103">.NET Standard je formální specifikaci, která definuje sadu rozhraní API, které musí být k dispozici na implementace rozhraní .NET, které jsou v souladu s touto verzí standardní verzí.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-103">The .NET Standard is a formal specification that defines a versioned set of APIs which must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="3aa5b-104">.NET Standard je cílena na vývojáře knihovny.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-104">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="3aa5b-105">Knihovna, která cílí na .NET Standard verzi lze použít v rozhraní .NET Framework, .NET Core nebo Xamarin implementace, která podporuje tuto verzi standard.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-105">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="3aa5b-106">Nejnovější verze .NET Standard je 2.0.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-106">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="3aa5b-107">Je zahrnut pomocí .NET SDK 2.0 jádra, a také s Visual Studio 2017 verze 15.3 se zatížením .NET Core nainstalována.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-107">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="3aa5b-108">Podporované implementace rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="3aa5b-108">Supported .NET implementations</span></span>

<span data-ttu-id="3aa5b-109">Rozhraní .NET 2.0 standardní podporuje následující implementace rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="3aa5b-109">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="3aa5b-110">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="3aa5b-110">.NET Core 2.0</span></span>
- <span data-ttu-id="3aa5b-111">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="3aa5b-111">.NET Framework 4.6.1</span></span>
- <span data-ttu-id="3aa5b-112">Mono 5.4</span><span class="sxs-lookup"><span data-stu-id="3aa5b-112">Mono 5.4</span></span>
- <span data-ttu-id="3aa5b-113">Xamarin.iOS 10.14</span><span class="sxs-lookup"><span data-stu-id="3aa5b-113">Xamarin.iOS 10.14</span></span>
- <span data-ttu-id="3aa5b-114">Xamarin.Mac 3.8</span><span class="sxs-lookup"><span data-stu-id="3aa5b-114">Xamarin.Mac 3.8</span></span>
- <span data-ttu-id="3aa5b-115">Xamarin.Android 8.0</span><span class="sxs-lookup"><span data-stu-id="3aa5b-115">Xamarin.Android 8.0</span></span>
- <span data-ttu-id="3aa5b-116">Univerzální platformu Windows 10.0.16299</span><span class="sxs-lookup"><span data-stu-id="3aa5b-116">Universal Windows Platform 10.0.16299</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="3aa5b-117">Co je nového v rozhraní .NET 2.0 Standard</span><span class="sxs-lookup"><span data-stu-id="3aa5b-117">What's new in the .NET Standard 2.0</span></span>
 
<span data-ttu-id="3aa5b-118">Rozhraní .NET 2.0 standardní obsahuje následující nové funkce:</span><span class="sxs-lookup"><span data-stu-id="3aa5b-118">The .NET Standard 2.0 includes the following new features:</span></span>

<span data-ttu-id="3aa5b-119">**Významně rozšířená sada rozhraní API**</span><span class="sxs-lookup"><span data-stu-id="3aa5b-119">**A vastly expanded set of APIs**</span></span>

<span data-ttu-id="3aa5b-120">Prostřednictvím verzi 1.6 zahrnuty .NET Standard poměrně malou podmnožinu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-120">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="3aa5b-121">Mezi ty vyloučené byly mnoho rozhraní API, které byly často používány v rozhraní .NET Framework nebo Xamarin.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="3aa5b-122">To komplikuje vývoj, protože vyžaduje, že vývojáři najít vhodný nahrazení pro známé rozhraní API při vývoji aplikací a knihovny, které cílí více implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="3aa5b-123">Rozhraní .NET 2.0 standardní řeší toto omezení přidáním přes 20 000 další rozhraní API, než byly k dispozici v rozhraní .NET standardní 1.6, předchozí verzi standard.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-123">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="3aa5b-124">Seznam rozhraní API, které jsou přidané do standardní rozhraní .NET 2.0, naleznete v části [standardní rozhraní .NET 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="3aa5b-124">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span> 

<span data-ttu-id="3aa5b-125">Některé doplňky k <xref:System> oboru názvů v rozhraní .NET 2.0 standardní patří:</span><span class="sxs-lookup"><span data-stu-id="3aa5b-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="3aa5b-126">Podpora pro <xref:System.AppDomain> třídy.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="3aa5b-127">Lepší podpory pro práci s poli od další členové <xref:System.Array> třídy.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="3aa5b-128">Lepší podpory pro práci s atributy z další členové <xref:System.Attribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="3aa5b-129">Lépe kalendář podpory a další možnosti formátování <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="3aa5b-130">Další <xref:System.Decimal> zaokrouhlení funkce.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="3aa5b-131">Další funkce v <xref:System.Environment> třídy.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="3aa5b-132">Rozšířené kontrolu nad uvolňování prostřednictvím <xref:System.GC> třídy.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="3aa5b-133">Rozšířenou podporu pro porovnání řetězců, výčet a normalizaci v <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="3aa5b-134">Podpora pro letní čas úpravy a doby přechodu v <xref:System.TimeZoneInfo.AdjustmentRule> a <xref:System.TimeZoneInfo.TransitionTime> třídy.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="3aa5b-135">Výrazně rozšířené funkce v <xref:System.Type> třídy.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="3aa5b-136">Lepší podpory pro deserializaci objektů výjimek přidáním k výjimce konstruktor s <xref:System.Runtime.Serialization.SerializationInfo> a <xref:System.Runtime.Serialization.StreamingContext> parametry.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

<span data-ttu-id="3aa5b-137">**Podporu pro knihovny rozhraní .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="3aa5b-137">**Support for .NET Framework libraries**</span></span>

<span data-ttu-id="3aa5b-138">Naprostou většinu knihovny cílí rozhraní .NET Framework místo .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-138">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="3aa5b-139">Většina volání v tyto knihovny jsou však k rozhraním API, které jsou obsažené v rozhraní .NET 2.0 standardní.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-139">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="3aa5b-140">Od verze rozhraní .NET 2.0 standardní, dostanete knihovny rozhraní .NET Framework z knihovny .NET Standard pomocí [kompatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="3aa5b-140">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="3aa5b-141">Tuto vrstvu kompatibility je transparentní pro vývojáře; nemusíte dělat nic využívat výhod knihovnách rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="3aa5b-142">Jeden požadavek je, že rozhraní API volat knihovna tříd rozhraní .NET Framework musí být součástí standardní rozhraní .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-142">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

<span data-ttu-id="3aa5b-143">**Podpora jazyka Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="3aa5b-143">**Support for Visual Basic**</span></span>

<span data-ttu-id="3aa5b-144">Nyní můžete vyvíjet .NET standardní knihovny v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="3aa5b-145">Pro vývojáře jazyka Visual Basic, Visual Studio 2017 verze 15.3 pomocí nebo novější s .NET Core zatížení nainstalované Visual Studio teď obsahuje šablonu standardní knihovna tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-145">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="3aa5b-146">Pro vývojáře jazyka Visual Basic, kteří používají jiné nástroje pro vývoj a prostředí, můžete použít [dotnet nové](../../core/tools/dotnet-new.md) příkaz k vytvoření standardní knihovny .NET projektu.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="3aa5b-147">Další informace najdete v tématu [Podpora nástrojů pro rozhraní .NET standardní knihovny](#tooling).</span><span class="sxs-lookup"><span data-stu-id="3aa5b-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling).</span></span>

<span data-ttu-id="3aa5b-148"><a name="tooling" />**Podpora nástrojů pro rozhraní .NET standardní knihovny**</span><span class="sxs-lookup"><span data-stu-id="3aa5b-148"><a name="tooling" />**Tooling support for .NET Standard libraries**</span></span>

<span data-ttu-id="3aa5b-149">Verze rozhraní .NET Core 2.0 a .NET standardní 2.0, jak Visual Studio 2017 a [.NET Core rozhraní příkazového řádku (CLI)](../../core/tools/index.md) patří podpora nástrojů pro vytváření .NET standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span> 

<span data-ttu-id="3aa5b-150">Pokud nainstalujete Visual Studio s **vývoj pro různé platformy .NET Core** zatížení, můžete vytvořit projekt knihovny .NET standardní 2.0 pomocí šablony projektu, jak ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows.</span></span> 

# <a name="ctabcsharp"></a>[<span data-ttu-id="3aa5b-151">C#</span><span class="sxs-lookup"><span data-stu-id="3aa5b-151">C#</span></span>](#tab/csharp)
![Přidat nové standardní rozhraní .NET projektu knihovny](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="3aa5b-153">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3aa5b-153">Visual Basic</span></span>](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![Přidat nové standardní rozhraní .NET projektu knihovny](./media/std-project-vb.png)
---

<span data-ttu-id="3aa5b-155">Pokud používáte rozhraní .NET Core příkazového řádku, následující [dotnet nové](../../core/tools/dotnet-new.md) příkaz vytvoří projektu knihovny tříd zacílený standardní rozhraní .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="3aa5b-155">If you are using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0.</span></span>

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a><span data-ttu-id="3aa5b-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="3aa5b-156">See Also</span></span>
<span data-ttu-id="3aa5b-157">[Standardní .NET](../net-standard.md)
[představení Standard rozhraní .NET](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span><span class="sxs-lookup"><span data-stu-id="3aa5b-157">[.NET Standard](../net-standard.md)
[Introducing .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span></span>
