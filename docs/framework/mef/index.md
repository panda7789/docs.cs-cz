---
title: Managed Extensibility Framework (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8738e8d0f6a74e1b8ba963e487d4c153a0a6a872
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47086486"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="5d5ff-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="5d5ff-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="5d5ff-103">Toto téma obsahuje přehled služby Managed Extensibility Framework, která byla zavedena v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a><span data-ttu-id="5d5ff-104">Co je MEF?</span><span class="sxs-lookup"><span data-stu-id="5d5ff-104">What is MEF?</span></span>

<span data-ttu-id="5d5ff-105">Managed Extensibility Framework nebo MEF je knihovna pro vytváření jednoduchých, rozšiřitelných aplikací.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="5d5ff-106">Umožňuje aplikaci vývojářům poznávání a používání rozšíření bez nezbytné konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="5d5ff-107">Také umožňuje rozšíření vývojáři snadno zapouzdření kód a vyhnout se křehké pevné závislosti.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="5d5ff-108">MEF nejen umožňuje rozšíření opětovné použití v aplikacích, ale napříč aplikacemi stejně.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="5d5ff-109">Problém rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="5d5ff-109">The Problem of Extensibility</span></span>
 <span data-ttu-id="5d5ff-110">Představte si, že jste architekt velké aplikace, které musíte poskytovat podporu pro rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="5d5ff-111">Vaše aplikace musí obsahovat potenciálně velký počet menších komponent a je zodpovědný za vytváření a spouštění je.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

 <span data-ttu-id="5d5ff-112">Nejjednodušším přístupem k problému se zahrnout součásti jako zdrojový kód ve vaší aplikaci, a je volat přímo z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="5d5ff-113">Tato akce nemá počet viditelných nevýhody.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="5d5ff-114">Co je nejdůležitější nelze přidat nové komponenty bez změny zdrojového kódu, omezení, které může být přijatelný, například webové aplikace, ale je v nefunkčním v klientské aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="5d5ff-115">Rovnoměrně problematické, nemáte přístup ke zdrojovému kódu pro součásti, protože může být vyvinuté třetími stranami a ze stejného důvodu, že nemůže povolit jejich přístupu k té vaší.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

 <span data-ttu-id="5d5ff-116">Zadejte rozšiřovacího bodu nebo rozhraní, tak, aby povolovala oddělení mezi aplikací a jeho součástí je o něco sofistikovanější přístup.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="5d5ff-117">V rámci tohoto modelu můžete zadat rozhraní, které můžete implementovat součásti a rozhraní API, který umožňuje interakci s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="5d5ff-118">To řeší problém vyžadující přístup ke zdrojovému kódu, ale stále má svůj vlastní potíže.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

 <span data-ttu-id="5d5ff-119">Protože aplikace nemá žádné kapacity pro zjišťování součásti sama o sobě, se musí stále explicitně až k tomu dojde komponenty, které jsou k dispozici a musí být načten.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="5d5ff-120">To je obvykle provedeno explicitně registrací dostupné součásti v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="5d5ff-121">To znamená, že součásti je ujištěním, která jsou správné stane problém údržby, zejména v případě, že je koncový uživatel a ne vývojář, který se má provést aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

 <span data-ttu-id="5d5ff-122">Kromě toho jsou součástí nepodporuje komunikaci mezi sebou, s výjimkou prostřednictvím pevně definovaných kanálů samotná aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="5d5ff-123">Pokud architekt aplikací nebyl očekávané potřebu konkrétního komunikace je obvykle možné.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

 <span data-ttu-id="5d5ff-124">A konečně vývojáři komponent musí přijmout pevné závislost na sestavení, které obsahuje rozhraní, které implementují.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="5d5ff-125">Je těžké pro komponentu, který se má použít ve více než jednu aplikaci a můžete také vytvářet problémy při vytváření testů pro komponenty.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a><span data-ttu-id="5d5ff-126">Co obsahuje rozhraní MEF</span><span class="sxs-lookup"><span data-stu-id="5d5ff-126">What MEF Provides</span></span>
 <span data-ttu-id="5d5ff-127">Místo této explicitní registraci dostupné součásti MEF poskytuje způsob, jak je implicitně, zjišťování prostřednictvím *složení*.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="5d5ff-128">Komponenta MEF, volá se *část*, deklarativně určuje i jeho závislosti (označované jako *importuje*) a jaké možnosti (označované jako *exportuje*) jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="5d5ff-129">Když se části, Kompoziční modul rozhraní MEF splňuje jeho importů s tím, co je k dispozici z jiných částí.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

 <span data-ttu-id="5d5ff-130">Tento přístup řeší problémy popsané v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="5d5ff-131">Protože částí MEF deklarativně specifikovat jejími funkcemi, jsou zjistitelné za běhu, což znamená, že aplikace může být použít částí bez pevně zakódované odkazy nebo křehké konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="5d5ff-132">MEF umožňuje aplikacím zjistit a prozkoumejte části podle metadat, bez vytvoření instance je nebo dokonce načítání jejich sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="5d5ff-133">V důsledku toho není nutné pečlivě určit, kdy a jak se mají načíst rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

 <span data-ttu-id="5d5ff-134">Kromě jeho zadaná exporty můžete zadat část jeho importů, které se sestavil jiné části.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="5d5ff-135">Toto usnadňuje komunikaci mezi části není pouze je to možné, ale snadno a umožňuje dobré řešení kódu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="5d5ff-136">Například služby, které jsou společné pro mnoho součástí můžete být promítnout do samostatných částí a snadno upravit nebo nahradit.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

 <span data-ttu-id="5d5ff-137">Protože MEF model vyžaduje žádné pevné závislost na sestavení konkrétní aplikace, umožňuje rozšíření znovu použít z aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="5d5ff-138">To také usnadňuje vývoj testovací prostředí, nezávisle na aplikaci k testování rozšíření komponenty.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

 <span data-ttu-id="5d5ff-139">Rozšiřitelné aplikace vytvořené pomocí MEF deklaruje, že import, který může být naplněno komponent rozšíření a může také deklarovat exportuje, aby bylo možné zveřejnit aplikačními službami, abyste rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="5d5ff-140">Jednotlivé komponenty rozšíření deklaruje export a může také deklarovat importy.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="5d5ff-141">Tímto způsobem jsou automaticky rozšiřitelné komponent rozšíření sami.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-141">In this way, extension components themselves are automatically extensible.</span></span>

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a><span data-ttu-id="5d5ff-142">Pokud je k dispozici rozhraní MEF</span><span class="sxs-lookup"><span data-stu-id="5d5ff-142">Where Is MEF Available?</span></span>
 <span data-ttu-id="5d5ff-143">MEF je nedílnou součástí toho, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]a je k dispozici všude, kde se používá rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-143">MEF is an integral part of the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="5d5ff-144">MEF můžete použít v klientských aplikacích používají Windows Forms, WPF nebo jiné technologie, nebo v serverové aplikace, které pomocí technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a><span data-ttu-id="5d5ff-145">MEF a MAF</span><span class="sxs-lookup"><span data-stu-id="5d5ff-145">MEF and MAF</span></span>
 <span data-ttu-id="5d5ff-146">Předchozí verze rozhraní .NET Framework zavedené spravované Add-in Framework (MAF), navržená tak, aby umožňovala izolaci a správu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="5d5ff-147">Fokus MAF je mírně vyšší úrovni než MEF soustředíte na rozšíření izolace a sestavení, načítání a uvolňování, zatímco na MEF, zaměřuje se na možnosti rozpoznání, rozšíření a přenositelnost.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="5d5ff-148">Dvě architektury hladce spolupracují, a jednu aplikaci můžete využít výhod obou.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="5d5ff-149">SimpleCalculator: Ukázková aplikace</span><span class="sxs-lookup"><span data-stu-id="5d5ff-149">SimpleCalculator: An Example Application</span></span>

<span data-ttu-id="5d5ff-150">Nejjednodušší způsob, jak zobrazit, co můžete dělat MEF je vytvořit jednoduchou aplikaci MEF.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="5d5ff-151">V tomto příkladu vytvoříte s názvem SimpleCalculator velmi jednoduchou kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="5d5ff-152">Cílem SimpleCalculator je Vytvořte konzolovou aplikaci, která přijímá základní aritmetické příkazy ve tvaru "5 + 3" nebo "6-2" a vrátí správné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="5d5ff-153">Pomocí rozhraní MEF, budete moct přidat nové operátory beze změny kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="5d5ff-154">Stáhnout kompletní kód v tomto příkladu, najdete v článku [SimpleCalculator ukázka](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="5d5ff-154">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

> [!NOTE]
> <span data-ttu-id="5d5ff-155">Účelem SimpleCalculator je k předvedení konceptů a syntaxe MEF, nikoli nutně poskytnout realistické scénáře jeho použití.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="5d5ff-156">Mnoho aplikací, které by měla mít prospěch maximálně využít sílu MEF jsou složitější než SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="5d5ff-157">Rozsáhlejší příklady najdete v článku [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="5d5ff-158">Pokud chcete začít, v sadě Visual Studio vytvořte nový projekt konzolové aplikace a pojmenujte ho `SimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="5d5ff-159">Přidáte odkaz na sestavení System.ComponentModel.Composition, ve které se nachází MEF.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span>

- <span data-ttu-id="5d5ff-160">Otevřete Module1.vb nebo soubor Program.cs a přidejte `Imports` nebo `using` příkazy pro System.ComponentModel.Composition a System.ComponentModel.Composition.Hosting.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="5d5ff-161">Tyto dva obory názvů obsahují typy MEF, které potřebujete pro vývoj rozšiřitelných aplikací.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="5d5ff-162">Pokud používáte jazyk Visual Basic, přidejte `Public` – klíčové slovo na řádek, který deklaruje `Module1` modulu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="5d5ff-163">Kontejner kompozic rozhraní MEF a katalogů</span><span class="sxs-lookup"><span data-stu-id="5d5ff-163">Composition Container and Catalogs</span></span>

<span data-ttu-id="5d5ff-164">Základní model složení MEF je *kontejner kompozic rozhraní MEF*, který obsahuje všechny součásti, které jsou k dispozici a provede sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="5d5ff-165">Složení je odpovídající z importů pro export.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="5d5ff-166">Nejběžnějším typem kontejner kompozic rozhraní MEF je <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, a to pro SimpleCalculator použijete.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="5d5ff-167">Pokud používáte Visual Basic v Module1.vb, přidejte veřejnou třídu s názvem `Program`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-167">If you're using Visual Basic, in Module1.vb, add a public class named `Program`.</span></span>

<span data-ttu-id="5d5ff-168">Přidejte následující řádek, který `Program` třídy v Module1.vb nebo Program.cs:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-168">Add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="5d5ff-169">Chcete-li vyhledat částí, které jsou k dispozici, kompozice kontejnery využívá *katalogu*.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="5d5ff-170">Katalog je objekt, který je k dispozici částí zjištěných z nějakého zdroje.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="5d5ff-171">MEF poskytuje katalogů a zjistit částí z poskytnutého typu, sestavení nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="5d5ff-172">Vývojáři aplikací můžete snadno vytvořit nové katalogů a Objevte částí z jiných zdrojů, jako jsou webové služby.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="5d5ff-173">Přidejte následující konstruktor k `Program` třídy:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-173">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    'An aggregate catalog that combines multiple catalogs
     Dim catalog = New AggregateCatalog()

    'Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    'Create the CompositionContainer with the parts in the catalog
    _container = New CompositionContainer(catalog)

    'Fill the imports of this object
    Try
        _container.ComposeParts(Me)
    Catch ex As Exception
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    //An aggregate catalog that combines multiple catalogs
    var catalog = new AggregateCatalog();
    //Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    //Create the CompositionContainer with the parts in the catalog
    _container = new CompositionContainer(catalog);

    //Fill the imports of this object
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

<span data-ttu-id="5d5ff-174">Volání <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> říká kontejner kompozic sestavit konkrétní sadu části v tomto případě aktuální instancí třídy `Program`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="5d5ff-175">V tomto okamžiku však není provedena žádná akce, protože `Program` nemá žádné importy tak, aby vyplnil.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="5d5ff-176">Importy a exporty s atributy</span><span class="sxs-lookup"><span data-stu-id="5d5ff-176">Imports and Exports with Attributes</span></span>
 <span data-ttu-id="5d5ff-177">Nejdřív musíte `Program` importovat kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="5d5ff-178">To umožňuje oddělení uživatelského rozhraní aspekty, jako je konzola vstup a výstup, který přejde do `Program`, od logiky kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

 <span data-ttu-id="5d5ff-179">Přidejte následující kód, který `Program` třídy:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 <span data-ttu-id="5d5ff-180">Všimněte si, že deklarace `calculator` objekt není, ale je doplněn <xref:System.ComponentModel.Composition.ImportAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="5d5ff-181">Tento atribut deklaruje byste měli importu; To znamená ho bude vyplněno modul složení při objektu se skládá.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

 <span data-ttu-id="5d5ff-182">Má každý import *kontraktu*, který určuje, jaké exporty bude možné porovnat s.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="5d5ff-183">Kontrakt musí být řetězec s explicitně zadanými nebo ho automaticky generuje služba MEF ze zadaného typu, v tomto případě rozhraní `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="5d5ff-184">Každý export deklarována s odpovídající smlouvy bude splnění tohoto importu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="5d5ff-185">Všimněte si, že při typu `calculator` objekt je ve skutečnosti `ICalculator`, tento krok není povinný.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="5d5ff-186">Smlouva je nezávislý na typ importu objektu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="5d5ff-187">(V takovém případě může vynecháte `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="5d5ff-188">MEF automaticky zaujme smlouvy založený na typ importu, pokud ho explicitně neurčíte.)</span><span class="sxs-lookup"><span data-stu-id="5d5ff-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

 <span data-ttu-id="5d5ff-189">Přidat toto velmi jednoduché rozhraní modulu nebo `SimpleCalculator` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(ByVal input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

 <span data-ttu-id="5d5ff-190">Teď, když jste definovali `ICalculator`, je třeba třídu, která jej implementuje.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="5d5ff-191">Přidejte následující třídu modulu nebo `SimpleCalculator` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

 <span data-ttu-id="5d5ff-192">Tady je export, která bude odpovídat import v `Program`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="5d5ff-193">Pro export tak, aby odpovídaly importu, exportu musí mít stejný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="5d5ff-194">Export v rámci smlouvy na základě `typeof(MySimpleCalculator)` vyprodukuje neshodu a import by vyplněné; kontrakt musí přesně shodovat.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

 <span data-ttu-id="5d5ff-195">Vzhledem k tomu, že vyplní kontejner kompozic se všemi částmi, které jsou k dispozici v tomto sestavení `MySimpleCalculator` část bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="5d5ff-196">Při konstruktor pro `Program` provádí složení `Program` objektu, bude vyplněn jeho import `MySimpleCalculator` objekt, který se vytvoří pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

 <span data-ttu-id="5d5ff-197">Uživatelské rozhraní vrstvě (`Program`) nemusí vědět vše ostatní.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="5d5ff-198">Můžete tedy přejít k vyplnění zbývající logiku uživatelského rozhraní v `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

 <span data-ttu-id="5d5ff-199">Přidejte následující kód, který `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-199">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    Program p = new Program(); //Composition is performed in the constructor
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="5d5ff-200">Tento kód jednoduše načte řádek vstupu a volání `Calculate` funkce `ICalculator` na výsledek, který zapíše zpět do konzoly.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="5d5ff-201">Tedy kód potřebujete v `Program`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="5d5ff-202">Všechny zbývající práce proběhne v částech.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-202">All the rest of the work will happen in the parts.</span></span>

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a><span data-ttu-id="5d5ff-203">Další importy a ImportMany</span><span class="sxs-lookup"><span data-stu-id="5d5ff-203">Further Imports and ImportMany</span></span>
 <span data-ttu-id="5d5ff-204">Aby SimpleCalculator mít rozšiřitelný je potřeba importovat seznam operací.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="5d5ff-205">Běžný <xref:System.ComponentModel.Composition.ImportAttribute> atribut vyplní pouze jeden <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="5d5ff-206">Pokud je více než jeden dostupný, Kompoziční modul dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="5d5ff-207">K vytvoření, import, který můžete zadat libovolný počet exportů, můžete použít <xref:System.ComponentModel.Composition.ImportManyAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

 <span data-ttu-id="5d5ff-208">Přidejte následující vlastnosti operace, která má `MySimpleCalculator` třídy:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <span data-ttu-id="5d5ff-209"><xref:System.Lazy%602> typem poskytované rozhraní MEF pro uložení nepřímé odkazy na exporty.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="5d5ff-210">Tady, kromě samotného exportované objektu, budete mít také *export metadat*, nebo informace, které popisují exportované objektu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="5d5ff-211">Každý <xref:System.Lazy%602> obsahuje `IOperation` objekt představující aktuální operace a `IOperationData` objekt představující jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

 <span data-ttu-id="5d5ff-212">Přidejte následující jednoduché rozhraní modulu nebo `SimpleCalculator` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 <span data-ttu-id="5d5ff-213">V tomto případě metadata pro každou operaci je symbol, který představuje tuto operaci, jako například +, -, \*, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="5d5ff-214">Pokud chcete zpřístupnit operaci sčítání, přidejte následující třídu modulu nebo `SimpleCalculator` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

 <span data-ttu-id="5d5ff-215"><xref:System.ComponentModel.Composition.ExportAttribute> Atribut funkce stejně jako dříve.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="5d5ff-216"><xref:System.ComponentModel.Composition.ExportMetadataAttribute> Atribut připojí k této exportu metadat ve formě dvojice název hodnota.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="5d5ff-217">Zatímco `Add` implementuje třída `IOperation`, třídu, která implementuje `IOperationData` nejsou výslovně definované.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="5d5ff-218">Místo toho třídy implicitně vytvoří MEF s vlastnostmi na základě názvů metadata k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="5d5ff-219">(To je jedním z několika způsoby, jak získat přístup k metadatům v MEF.)</span><span class="sxs-lookup"><span data-stu-id="5d5ff-219">(This is one of several ways to access metadata in MEF.)</span></span>

 <span data-ttu-id="5d5ff-220">Složení v MEF *rekurzivní*.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="5d5ff-221">Můžete explicitně složený `Program` objekt, který importován `ICalculator` , ukázalo se typ `MySimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="5d5ff-222">`MySimpleCalculator`, pak importuje kolekci `IOperation` objekty a, import se naplní při `MySimpleCalculator` se vytvoří ve stejnou dobu jako importů `Program`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="5d5ff-223">Pokud `Add` třídy deklarované další importu, který by příliš měla být vyplněny a tak dále.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="5d5ff-224">Žádný import levé nevyplněným výsledků v chybě složení.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="5d5ff-225">(To je ale možné, chcete-li deklarovat importy být volitelný nebo přiřadit výchozí hodnoty.)</span><span class="sxs-lookup"><span data-stu-id="5d5ff-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a><span data-ttu-id="5d5ff-226">Kalkulačka logiky</span><span class="sxs-lookup"><span data-stu-id="5d5ff-226">Calculator Logic</span></span>
 <span data-ttu-id="5d5ff-227">Pomocí těchto částí v místě už jen zbývá vlastní logiky kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="5d5ff-228">Přidejte následující kód `MySimpleCalculator` třídu pro implementaci `Calculate` metody:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    Dim fn = FindFirstNonDigit(input) 'Finds the operator
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(String input)
{
    int left;
    int right;
    Char operation;
    int fn = FindFirstNonDigit(input); //finds the operator
    if (fn < 0) return "Could not parse command.";

    try
    {
        //separate out the operands
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

 <span data-ttu-id="5d5ff-229">Počáteční kroky parsovat vstupní řetězec do levé a pravé operandy a znak operátoru.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="5d5ff-230">V `foreach` smyčky, každý člen `operations` kolekce je zkontrolován.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="5d5ff-231">Tyto objekty jsou typu <xref:System.Lazy%602>, a jejich hodnoty metadat a exportovaný objekt lze přistupovat pomocí <xref:System.Lazy%602.Metadata%2A> vlastnost a <xref:System.Lazy%601.Value%2A> vlastnost v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="5d5ff-232">V takovém případě pokud `Symbol` vlastnost `IOperationData` objekt zjištěn být shoda, volání Kalkulačka `Operate` metodu `IOperation` objekt a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

 <span data-ttu-id="5d5ff-233">K dokončení kalkulačky, potřebujete také Pomocná metoda, která vrátí pozici první nečíslicovému znaku v řetězci.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="5d5ff-234">Přidejte následující pomocnou metodu k `MySimpleCalculator` třídy:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(String s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 <span data-ttu-id="5d5ff-235">Teď by měl být schopen kompilace a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="5d5ff-236">V jazyce Visual Basic, ujistěte se, že jste přidali `Public` – klíčové slovo do `Module1`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="5d5ff-237">V okně konzoly typ operace sčítání, jako je například "5 + 3" a kalkulačky vrátí výsledky.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="5d5ff-238">Výsledkem "operaci nebyl nalezen!" jiných – operátor</span><span class="sxs-lookup"><span data-stu-id="5d5ff-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="5d5ff-239">zpráva.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-239">message.</span></span>

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="5d5ff-240">Rozšíření SimpleCalculator pomocí nové třídy</span><span class="sxs-lookup"><span data-stu-id="5d5ff-240">Extending SimpleCalculator Using A New Class</span></span>
 <span data-ttu-id="5d5ff-241">Teď, když funguje kalkulačky, přidání nové operace je snadné.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="5d5ff-242">Přidejte následující třídu modulu nebo `SimpleCalculator` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

 <span data-ttu-id="5d5ff-243">Kompilace a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-243">Compile and run the project.</span></span> <span data-ttu-id="5d5ff-244">Typ operace odčítání, jako je například "5-3".</span><span class="sxs-lookup"><span data-stu-id="5d5ff-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="5d5ff-245">Kalkulačce teď podporuje odčítání, stejně jako další.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-245">The calculator now supports subtraction as well as addition.</span></span>

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="5d5ff-246">Rozšíření SimpleCalculator pomocí nové sestavení</span><span class="sxs-lookup"><span data-stu-id="5d5ff-246">Extending SimpleCalculator Using A New Assembly</span></span>
 <span data-ttu-id="5d5ff-247">Přidávání tříd ke zdroji je kód dostatečně jednoduchá, ale poskytuje možnost Hledat mimo zdroj aplikace vlastní části MEF.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="5d5ff-248">Abychom si předvedli to, budete muset upravit SimpleCalculator vyhledat adresář, stejně jako vlastní sestavení částí, tak, že přidáte <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

 <span data-ttu-id="5d5ff-249">Přidat nový adresář s názvem `Extensions` SimpleCalculator projektu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="5d5ff-250">Ujistěte se, že ho přidáte na úrovni projektu a ne na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="5d5ff-251">Pak přidejte nový projekt knihovny tříd k řešení s názvem `ExtendedOperations`.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="5d5ff-252">Nový projekt zkompiluje do samostatného sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-252">The new project will compile into a separate assembly.</span></span>

 <span data-ttu-id="5d5ff-253">Otevřete Návrhář vlastnosti projektu pro projekt ExtendedOperations a klikněte na tlačítko **kompilaci** nebo **sestavení** kartu. Změnit **výstupní cesta sestavení** nebo **výstupní cesta** tak, aby odkazoval do adresáře rozšíření v adresáři projektu SimpleCalculator (.. \SimpleCalculator\Extensions\\).</span><span class="sxs-lookup"><span data-stu-id="5d5ff-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>

 <span data-ttu-id="5d5ff-254">V souboru Program.cs nebo Module1.vb, přidejte následující řádek, který `Program` konstruktor:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-254">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 <span data-ttu-id="5d5ff-255">Příklad cesty nahraďte cestou k adresáři rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="5d5ff-256">(Tato absolutní cesta je pouze pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="5d5ff-257">V produkční aplikace použijete relativní cestu.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Teď přidá všechny části v všechna sestavení v adresáři rozšíření pro kontejner složení.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

 <span data-ttu-id="5d5ff-258">V projektu ExtendedOperations přidejte odkazy na SimpleCalculator a System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="5d5ff-259">V souboru ExtendedOperations třídy, přidejte `Imports` nebo `using` příkaz pro System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="5d5ff-260">V jazyce Visual Basic, také přidat `Imports` příkaz pro SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="5d5ff-261">Soubor třídy ExtendedOperations pak přidejte následující třídu:</span><span class="sxs-lookup"><span data-stu-id="5d5ff-261">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

 <span data-ttu-id="5d5ff-262">Všimněte si, že v pořadí pro kontrakt tak, aby odpovídaly, <xref:System.ComponentModel.Composition.ExportAttribute> atribut musí být stejného typu jako <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

 <span data-ttu-id="5d5ff-263">Kompilace a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-263">Compile and run the project.</span></span> <span data-ttu-id="5d5ff-264">Vyzkoušejte nový operátor Mod (%).</span><span class="sxs-lookup"><span data-stu-id="5d5ff-264">Test the new Mod (%) operator.</span></span>

<a name="conclusion"></a>
## <a name="conclusion"></a><span data-ttu-id="5d5ff-265">Závěr</span><span class="sxs-lookup"><span data-stu-id="5d5ff-265">Conclusion</span></span>
 <span data-ttu-id="5d5ff-266">V tomto tématu se vztahují o základních konceptech služby MEF.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-266">This topic covered the basic concepts of MEF.</span></span>

-   <span data-ttu-id="5d5ff-267">Částí, katalogy a kontejner kompozic</span><span class="sxs-lookup"><span data-stu-id="5d5ff-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="5d5ff-268">Části a kontejner kompozic jsou základní stavební bloky aplikací rozhraní MEF.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="5d5ff-269">Součástí je libovolný objekt, který importuje nebo exportuje hodnotu, až po a včetně samotného.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="5d5ff-270">Katalog poskytuje kolekci částí z určitého zdroje.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="5d5ff-271">Kontejner kompozic používá části poskytované katalog k sestavení, vazba importy pro export.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

-   <span data-ttu-id="5d5ff-272">Importy a exporty</span><span class="sxs-lookup"><span data-stu-id="5d5ff-272">Imports and exports</span></span>

     <span data-ttu-id="5d5ff-273">Importy a exporty představují způsob, kterým součásti mohou komunikovat.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="5d5ff-274">Importu komponentu určuje potřebu konkrétní hodnotu nebo objekt a s export určuje dostupnosti hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="5d5ff-275">Každý import je nalezena shoda se seznamem exporty prostřednictvím jejich smlouvy.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-275">Each import is matched with a list of exports by way of its contract.</span></span>

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a><span data-ttu-id="5d5ff-276">Kam se mám obrátit nyní?</span><span class="sxs-lookup"><span data-stu-id="5d5ff-276">Where Do I Go Now?</span></span>
 <span data-ttu-id="5d5ff-277">Stáhnout kompletní kód v tomto příkladu, najdete v článku [SimpleCalculator ukázka](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="5d5ff-277">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

 <span data-ttu-id="5d5ff-278">Další informace a příklady kódu naleznete v tématu [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282).</span><span class="sxs-lookup"><span data-stu-id="5d5ff-278">For more information and code examples, see [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282).</span></span> <span data-ttu-id="5d5ff-279">Seznam typů rozhraní MEF, najdete v článku <xref:System.ComponentModel.Composition?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5d5ff-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
