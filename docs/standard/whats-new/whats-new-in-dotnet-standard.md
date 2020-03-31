---
title: Co je nového ve standardu .NET
description: Tento článek shrnuje nové funkce a vylepšení, které se nacházejí v každé nové verzi standardu .NET.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 28d6a3546e08bbc3a7d4a26f08ba9cc5e16a901b
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438206"
---
# <a name="whats-new-in-net-standard"></a><span data-ttu-id="48c8e-103">Co je nového ve standardu .NET</span><span class="sxs-lookup"><span data-stu-id="48c8e-103">What's new in .NET Standard</span></span>

<span data-ttu-id="48c8e-104">.NET Standard je formální specifikace, která definuje sadu rozhraní API s verzí, která musí být k dispozici v implementacích rozhraní .NET, které jsou v souladu s touto verzí standardu.</span><span class="sxs-lookup"><span data-stu-id="48c8e-104">.NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="48c8e-105">Standard .NET je určen pro vývojáře knihoven.</span><span class="sxs-lookup"><span data-stu-id="48c8e-105">.NET Standard is targeted at library developers.</span></span> <span data-ttu-id="48c8e-106">Knihovnu, která cílí na verzi .NET Standard, lze použít v libovolné implementaci rozhraní .NET Framework, .NET Core nebo Xamarin, která tuto verzi standardu podporuje.</span><span class="sxs-lookup"><span data-stu-id="48c8e-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="48c8e-107">Standard .NET Standard je součástí sady .NET Core SDK a také s visual studio při výběru zatížení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="48c8e-107">.NET Standard is included with the .NET Core SDK, as well as with Visual Studio when you select the .NET Core workload.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="48c8e-108">Podporované implementace rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="48c8e-108">Supported .NET implementations</span></span>

<span data-ttu-id="48c8e-109">.NET Standard 2.0 je podporován následujícími implementacemi rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="48c8e-109">.NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="48c8e-110">.NET Core 2.0 nebo novější</span><span class="sxs-lookup"><span data-stu-id="48c8e-110">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="48c8e-111">Rozhraní .NET Framework 4.6.1 nebo novější</span><span class="sxs-lookup"><span data-stu-id="48c8e-111">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="48c8e-112">Mono 5.4 nebo novější</span><span class="sxs-lookup"><span data-stu-id="48c8e-112">Mono 5.4 or later</span></span>
- <span data-ttu-id="48c8e-113">Xamarin.iOS 10.14 nebo novější</span><span class="sxs-lookup"><span data-stu-id="48c8e-113">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="48c8e-114">Xamarin.Mac 3.8 nebo novější</span><span class="sxs-lookup"><span data-stu-id="48c8e-114">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="48c8e-115">Xamarin.Android 8.0 nebo novější</span><span class="sxs-lookup"><span data-stu-id="48c8e-115">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="48c8e-116">Univerzální platforma Windows 10.0.16299 nebo novější</span><span class="sxs-lookup"><span data-stu-id="48c8e-116">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-net-standard-20"></a><span data-ttu-id="48c8e-117">Co je nového v rozhraní .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="48c8e-117">What's new in .NET Standard 2.0</span></span>

<span data-ttu-id="48c8e-118">.NET Standard 2.0 obsahuje následující nové funkce:</span><span class="sxs-lookup"><span data-stu-id="48c8e-118">.NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="48c8e-119">Výrazně rozšířená sada api</span><span class="sxs-lookup"><span data-stu-id="48c8e-119">A vastly expanded set of APIs</span></span>

<span data-ttu-id="48c8e-120">Prostřednictvím verze 1.6.NET Standard zahrnoval poměrně malou podmnožinu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="48c8e-120">Through version 1.6, .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="48c8e-121">Mezi vyloučenými bylo mnoho rozhraní API, které se běžně používaly v rozhraní .NET Framework nebo Xamarin.</span><span class="sxs-lookup"><span data-stu-id="48c8e-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="48c8e-122">To komplikuje vývoj, protože vyžaduje, aby vývojáři najít vhodné náhrady za známé rozhraní API při vývoji aplikací a knihoven, které se zaměřují na více implementací .NET.</span><span class="sxs-lookup"><span data-stu-id="48c8e-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="48c8e-123">.NET Standard 2.0 řeší toto omezení přidáním více než 20 000 více rozhraní API, než bylo k dispozici v rozhraní .NET Standard 1.6, předchozí verze standardu.</span><span class="sxs-lookup"><span data-stu-id="48c8e-123">.NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="48c8e-124">Seznam rozhraní API, které byly přidány do standardu .NET Standard 2.0, naleznete v tématu [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="48c8e-124">For a list of the APIs that have been added to .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="48c8e-125">Některé dodatky k <xref:System> oboru názvů v rozhraní .NET Standard 2.0 zahrnují:</span><span class="sxs-lookup"><span data-stu-id="48c8e-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="48c8e-126">Podpora pro <xref:System.AppDomain> třídu.</span><span class="sxs-lookup"><span data-stu-id="48c8e-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="48c8e-127">Lepší podpora pro práci s poli <xref:System.Array> z dalších členů ve třídě.</span><span class="sxs-lookup"><span data-stu-id="48c8e-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="48c8e-128">Lepší podpora pro práci s atributy <xref:System.Attribute> z dalších členů ve třídě.</span><span class="sxs-lookup"><span data-stu-id="48c8e-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="48c8e-129">Lepší podpora kalendáře a další <xref:System.DateTime> možnosti formátování hodnot.</span><span class="sxs-lookup"><span data-stu-id="48c8e-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="48c8e-130">Další <xref:System.Decimal> funkce zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="48c8e-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="48c8e-131">Další funkce ve <xref:System.Environment> třídě.</span><span class="sxs-lookup"><span data-stu-id="48c8e-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="48c8e-132">Rozšířená kontrola nad uvolňování <xref:System.GC> prostřednictvím třídy.</span><span class="sxs-lookup"><span data-stu-id="48c8e-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="48c8e-133">Rozšířená podpora pro porovnání řetězců, výčt u <xref:System.String> a normalizaci ve třídě.</span><span class="sxs-lookup"><span data-stu-id="48c8e-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="48c8e-134">Podpora pro úpravy letního času <xref:System.TimeZoneInfo.AdjustmentRule> <xref:System.TimeZoneInfo.TransitionTime> a doby přechodu ve třídách a.</span><span class="sxs-lookup"><span data-stu-id="48c8e-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="48c8e-135">Výrazně vylepšená funkčnost <xref:System.Type> ve třídě.</span><span class="sxs-lookup"><span data-stu-id="48c8e-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="48c8e-136">Lepší podpora pro deserializaci objektů výjimek přidáním konstruktoru výjimky s <xref:System.Runtime.Serialization.SerializationInfo> parametry a <xref:System.Runtime.Serialization.StreamingContext> parametry.</span><span class="sxs-lookup"><span data-stu-id="48c8e-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="48c8e-137">Podpora knihoven rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="48c8e-137">Support for .NET Framework libraries</span></span>

<span data-ttu-id="48c8e-138">Drtivá většina knihoven cílit rozhraní .NET Framework spíše než .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="48c8e-138">The overwhelming majority of libraries target .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="48c8e-139">Většina volání v těchto knihovnách jsou však rozhraní API, které jsou zahrnuty v .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="48c8e-139">However, most of the calls in those libraries are to APIs that are included in .NET Standard 2.0.</span></span> <span data-ttu-id="48c8e-140">Počínaje rozhraním .NET Standard 2.0 můžete přistupovat ke knihovnám rozhraní .NET Framework z knihovny .NET Standard pomocí [překrytí kompatibility](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="48c8e-140">Starting with .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="48c8e-141">Tato vrstva kompatibility je pro vývojáře průhledná. nemusíte dělat nic, abyste mohli využít výhod knihoven rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48c8e-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="48c8e-142">Jediným požadavkem je, že rozhraní API volaná knihovnou tříd rozhraní .NET Framework musí být zahrnuta do standardu .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="48c8e-142">The single requirement is that the APIs called by the .NET Framework class library must be included in .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="48c8e-143">Podpora jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48c8e-143">Support for Visual Basic</span></span>

<span data-ttu-id="48c8e-144">Nyní můžete vyvíjet knihovny .NET Standard v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="48c8e-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="48c8e-145">Visual Studio 2019 a Visual Studio 2017 verze 15.3 nebo novější s nainstalovaným zatížením .NET Core zahrnují šablonu knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="48c8e-145">Visual Studio 2019 and Visual Studio 2017 version 15.3 or later with the .NET Core workload installed include a .NET Standard Class Library template.</span></span> <span data-ttu-id="48c8e-146">Pro vývojáře jazyka, kteří používají jiné vývojové nástroje a prostředí, můžete použít [dotnet new](../../core/tools/dotnet-new.md) příkaz k vytvoření projektu knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="48c8e-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="48c8e-147">Další informace naleznete v [části Podpora nástrojů pro knihovny .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="48c8e-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="48c8e-148">Podpora nástrojů pro knihovny .NET Standard</span><span class="sxs-lookup"><span data-stu-id="48c8e-148">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="48c8e-149">S vydáním .NET Core 2.0 a .NET Standard 2.0, Visual Studio 2017 a [.NET Core CLI](../../core/tools/index.md) zahrnují podporu nástrojů pro vytváření knihoven .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="48c8e-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="48c8e-150">Pokud instalujete Visual Studio s **úlohou vývoje napříč platformami .NET Core,** můžete vytvořit projekt knihovny .NET Standard 2.0 pomocí šablony projektu, jak ukazuje následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="48c8e-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="48c8e-151">C #</span><span class="sxs-lookup"><span data-stu-id="48c8e-151">C#</span></span>](#tab/csharp)

![Přidat nový projekt knihovny .NET Standard](./media/std-project-cs.png)

<span data-ttu-id="48c8e-153">Pokud používáte rozhraní PŘÍKAZOVÉHO PŘÍKAZU Jádra .NET, následující [dotnet new](../../core/tools/dotnet-new.md) příkaz vytvoří projekt knihovny tříd, který cílí na rozhraní .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="48c8e-153">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="48c8e-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48c8e-154">Visual Basic</span></span>](#tab/vb)

![Přidat nový projekt knihovny .NET Standard](./media/std-project-vb.png)

<span data-ttu-id="48c8e-156">Pokud používáte rozhraní PŘÍKAZOVÉHO PŘÍKAZU Jádra .NET, následující [dotnet new](../../core/tools/dotnet-new.md) příkaz vytvoří projekt knihovny tříd, který cílí na rozhraní .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="48c8e-156">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="48c8e-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="48c8e-157">See also</span></span>

- [<span data-ttu-id="48c8e-158">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="48c8e-158">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="48c8e-159">Představujeme standard .NET</span><span class="sxs-lookup"><span data-stu-id="48c8e-159">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
