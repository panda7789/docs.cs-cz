---
title: Novinky v rozhraní .NET Standard
description: Tento článek shrnuje nové funkce a vylepšení, které se nacházejí v každé nové verzi standardu .NET.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: a90df0360211c3b02f4f2d8697890180099c5807
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921062"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="1dbd2-103">Novinky v rozhraní .NET Standard</span><span class="sxs-lookup"><span data-stu-id="1dbd2-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="1dbd2-104">Standard .NET Je formální specifikace, která definuje sadu rozhraní API s verzí, která musí být k dispozici na implementacích .NET, které jsou v souladu s touto verzí standardu.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="1dbd2-105">Standard .NET je určen pro vývojáře knihoven.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="1dbd2-106">Knihovnu, která cílí na verzi .NET Standard, lze použít v libovolné implementaci rozhraní .NET Framework, .NET Core nebo Xamarin, která tuto verzi standardu podporuje.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="1dbd2-107">Nejnovější verze standardu .NET je 2.0.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="1dbd2-108">Je součástí sady .NET Core 2.0 SDK a také s visual studio 2017 verze 15.3 s nainstalovanou úlohou .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="1dbd2-109">Podporované implementace rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="1dbd2-109">Supported .NET implementations</span></span>

<span data-ttu-id="1dbd2-110">Standard .NET 2.0 je podporován následujícími implementacemi rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="1dbd2-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="1dbd2-111">.NET Core 2.0 nebo novější</span><span class="sxs-lookup"><span data-stu-id="1dbd2-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="1dbd2-112">Rozhraní .NET Framework 4.6.1 nebo novější</span><span class="sxs-lookup"><span data-stu-id="1dbd2-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="1dbd2-113">Mono 5.4 nebo novější</span><span class="sxs-lookup"><span data-stu-id="1dbd2-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="1dbd2-114">Xamarin.iOS 10.14 nebo novější</span><span class="sxs-lookup"><span data-stu-id="1dbd2-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="1dbd2-115">Xamarin.Mac 3.8 nebo novější</span><span class="sxs-lookup"><span data-stu-id="1dbd2-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="1dbd2-116">Xamarin.Android 8.0 nebo novější</span><span class="sxs-lookup"><span data-stu-id="1dbd2-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="1dbd2-117">Univerzální platforma Windows 10.0.16299 nebo novější</span><span class="sxs-lookup"><span data-stu-id="1dbd2-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="1dbd2-118">Co je nového ve standardu .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="1dbd2-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="1dbd2-119">Standard .NET 2.0 obsahuje následující nové funkce:</span><span class="sxs-lookup"><span data-stu-id="1dbd2-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="1dbd2-120">Výrazně rozšířená sada api</span><span class="sxs-lookup"><span data-stu-id="1dbd2-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="1dbd2-121">Prostřednictvím verze 1.6 standard .NET zahrnoval poměrně malou podmnožinu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="1dbd2-122">Mezi vyloučenými bylo mnoho rozhraní API, které se běžně používaly v rozhraní .NET Framework nebo Xamarin.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="1dbd2-123">To komplikuje vývoj, protože vyžaduje, aby vývojáři najít vhodné náhrady za známé rozhraní API při vývoji aplikací a knihoven, které se zaměřují na více implementací .NET.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="1dbd2-124">Standard .NET 2.0 řeší toto omezení přidáním více než 20 000 více rozhraní API, než bylo k dispozici v rozhraní .NET Standard 1.6, předchozí verze standardu.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="1dbd2-125">Seznam rozhraní API, které byly přidány do standardu .NET Standard 2.0, naleznete v tématu [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="1dbd2-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="1dbd2-126">Některé dodatky k <xref:System> oboru názvů v rozhraní .NET Standard 2.0 zahrnují:</span><span class="sxs-lookup"><span data-stu-id="1dbd2-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="1dbd2-127">Podpora pro <xref:System.AppDomain> třídu.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="1dbd2-128">Lepší podpora pro práci s poli <xref:System.Array> z dalších členů ve třídě.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="1dbd2-129">Lepší podpora pro práci s atributy <xref:System.Attribute> z dalších členů ve třídě.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="1dbd2-130">Lepší podpora kalendáře a další <xref:System.DateTime> možnosti formátování hodnot.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="1dbd2-131">Další <xref:System.Decimal> funkce zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="1dbd2-132">Další funkce ve <xref:System.Environment> třídě.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="1dbd2-133">Rozšířená kontrola nad uvolňování <xref:System.GC> prostřednictvím třídy.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="1dbd2-134">Rozšířená podpora pro porovnání řetězců, výčt u <xref:System.String> a normalizaci ve třídě.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="1dbd2-135">Podpora pro úpravy letního času <xref:System.TimeZoneInfo.AdjustmentRule> <xref:System.TimeZoneInfo.TransitionTime> a doby přechodu ve třídách a.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="1dbd2-136">Výrazně vylepšená funkčnost <xref:System.Type> ve třídě.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="1dbd2-137">Lepší podpora pro deserializaci objektů výjimek přidáním konstruktoru výjimky s <xref:System.Runtime.Serialization.SerializationInfo> parametry a <xref:System.Runtime.Serialization.StreamingContext> parametry.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="1dbd2-138">Podpora knihoven rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1dbd2-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="1dbd2-139">Drtivá většina knihoven cílí na rozhraní .NET Framework místo na standard .NET.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="1dbd2-140">Většina volání v těchto knihovnách jsou však rozhraní API, které jsou zahrnuty v .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="1dbd2-141">Počínaje rozhraním .NET Standard 2.0 můžete přistupovat ke knihovnám rozhraní .NET Framework z knihovny .NET Standard pomocí [překrytí kompatibility](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="1dbd2-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="1dbd2-142">Tato vrstva kompatibility je pro vývojáře průhledná. nemusíte dělat nic, abyste mohli využít výhod knihoven rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="1dbd2-143">Jediným požadavkem je, že rozhraní API volaná knihovnou tříd rozhraní .NET Framework musí být zahrnuta do standardu .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="1dbd2-144">Podpora jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dbd2-144">Support for Visual Basic</span></span>

<span data-ttu-id="1dbd2-145">Nyní můžete vyvíjet knihovny .NET Standard v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="1dbd2-146">Pro vývojáře jazyka Visual Basic, kteří používají Visual Studio 2017 verze 15.3 nebo novější s nainstalovaným zatížením jádra .NET, visual studio nyní obsahuje šablonu knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-146">For Visual Basic developers using Visual Studio 2017 version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="1dbd2-147">Pro vývojáře jazyka, kteří používají jiné vývojové nástroje a prostředí, můžete použít [dotnet new](../../core/tools/dotnet-new.md) příkaz k vytvoření projektu knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="1dbd2-148">Další informace naleznete v [části Podpora nástrojů pro knihovny .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="1dbd2-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="1dbd2-149">Podpora nástrojů pro knihovny .NET Standard</span><span class="sxs-lookup"><span data-stu-id="1dbd2-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="1dbd2-150">S vydáním .NET Core 2.0 a .NET Standard 2.0, Visual Studio 2017 a [.NET Core CLI](../../core/tools/index.md) zahrnují podporu nástrojů pro vytváření knihoven .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="1dbd2-151">Pokud instalujete Visual Studio s **úlohou vývoje napříč platformami .NET Core,** můžete vytvořit projekt knihovny .NET Standard 2.0 pomocí šablony projektu, jak ukazuje následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="1dbd2-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="1dbd2-152">C #</span><span class="sxs-lookup"><span data-stu-id="1dbd2-152">C#</span></span>](#tab/csharp)

![Přidat nový projekt knihovny .NET Standard](./media/std-project-cs.png)

<span data-ttu-id="1dbd2-154">Pokud používáte rozhraní PŘÍKAZOVÉHO PŘÍKAZU Jádra .NET, následující [dotnet new](../../core/tools/dotnet-new.md) příkaz vytvoří projekt knihovny tříd, který cílí na rozhraní .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="1dbd2-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="1dbd2-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dbd2-155">Visual Basic</span></span>](#tab/vb)

![Přidat nový projekt knihovny .NET Standard](./media/std-project-vb.png)

<span data-ttu-id="1dbd2-157">Pokud používáte rozhraní PŘÍKAZOVÉHO PŘÍKAZU Jádra .NET, následující [dotnet new](../../core/tools/dotnet-new.md) příkaz vytvoří projekt knihovny tříd, který cílí na rozhraní .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="1dbd2-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="1dbd2-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dbd2-158">See also</span></span>

- [<span data-ttu-id="1dbd2-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="1dbd2-159">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="1dbd2-160">Představujeme standard .NET</span><span class="sxs-lookup"><span data-stu-id="1dbd2-160">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
