---
title: Managed Extensibility Framework (MEF)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0994303cb758439dda08ee7df206f0a3bcecd854
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="8ebfa-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="8ebfa-102">Managed Extensibility Framework (MEF)</span></span>
<span data-ttu-id="8ebfa-103">Toto téma obsahuje přehled spravované rozhraní rozšiřitelnosti byla zavedená v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-103">This topic provides an overview of the Managed Extensibility Framework introduced in the .NET Framework 4.</span></span>  
  
<a name="what_is_mef"></a>   
## <a name="what-is-mef"></a><span data-ttu-id="8ebfa-104">Co je MEF?</span><span class="sxs-lookup"><span data-stu-id="8ebfa-104">What is MEF?</span></span>  
 <span data-ttu-id="8ebfa-105">Spravovaná rozhraní rozšiřitelnosti nebo MEF je knihovna pro vytváření aplikací pro jednoduché a rozšiřitelné.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="8ebfa-106">To umožňuje vývojáři aplikace k zjišťovat a používat rozšíření s nutná žádná konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="8ebfa-107">Také umožňuje rozšíření vývojáři snadno zapouzdření kódu a vyhnout se křehké pevný závislosti.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="8ebfa-108">MEF nejen umožňuje rozšíření znovu použije v rámci aplikace, ale napříč i aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>  
  
<a name="the_problem_of_extensibility"></a>   
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="8ebfa-109">Problém rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="8ebfa-109">The Problem of Extensibility</span></span>  
 <span data-ttu-id="8ebfa-110">Představte si, že jste architekt velké aplikace, které musí poskytovat podporu pro rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="8ebfa-111">Aplikace musí obsahovat potenciálně velkého počtu menší součásti a je odpovědná za vytváření a spustil je.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>  
  
 <span data-ttu-id="8ebfa-112">Nejjednodušším přístupem při problém je zahrnout komponenty jako zdrojového kódu v aplikaci, a je volat přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span>  <span data-ttu-id="8ebfa-113">To má počet zřejmé nevýhody.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-113">This has a number of obvious drawbacks.</span></span>  <span data-ttu-id="8ebfa-114">Co je nejdůležitější – nelze přidat nové komponenty beze změny zdrojový kód, který může být přijatelné in, například webovou aplikaci, ale je v aplikaci klienta nefunkčním omezení.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span>  <span data-ttu-id="8ebfa-115">Stejně problematické, nemáte přístup ke zdrojovému kódu pro součásti, protože může být vyvinutá třetích stran a ze stejného důvodu, že nelze povolit, aby váš přístup.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>  
  
 <span data-ttu-id="8ebfa-116">Mírně propracovanější postup by poskytnout rozšíření bodu nebo rozhraní, tak, aby povolovala oddělení mezi aplikací a jeho komponenty.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span>  <span data-ttu-id="8ebfa-117">V tomto modelu můžete zadat rozhraní, které můžete implementovat součásti a rozhraní API pro interakci s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span>  <span data-ttu-id="8ebfa-118">To řeší problém vyžadující přístup ke zdrojovému kódu, ale stále má svou vlastní problémy.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>  
  
 <span data-ttu-id="8ebfa-119">Protože aplikace nemá žádné kapacity pro zjišťování součásti sama o sobě, se musí stále explicitně říct, součástí, které jsou k dispozici a mělo by být načíst.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span>  <span data-ttu-id="8ebfa-120">Obvykle to provádí explicitně registrace dostupné součásti v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="8ebfa-121">To znamená, že zabezpečit, aby komponenty jsou správné stane údržby problém, zvlášť pokud je koncové uživatele a není vývojář, který se očekává proveďte aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>  
  
 <span data-ttu-id="8ebfa-122">Kromě toho jsou komponenty nepodporující komunikaci mezi sebou, s výjimkou prostřednictvím pevně definovaných kanálů samotné aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span>  <span data-ttu-id="8ebfa-123">Pokud architekt aplikace nebyla očekává nutné pro konkrétní komunikaci, je obvykle možné.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>  
  
 <span data-ttu-id="8ebfa-124">Nakonec vývojáři komponent musí přijmout pevný závislost na jaké sestavení obsahuje rozhraní, která implementují.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span>  <span data-ttu-id="8ebfa-125">To ztěžuje součást použije ve více než jednu aplikaci a může také způsobit problémy při vytváření test framework pro součásti.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>  
  
<a name="what_mef_provides"></a>   
## <a name="what-mef-provides"></a><span data-ttu-id="8ebfa-126">Co nabízí MEF</span><span class="sxs-lookup"><span data-stu-id="8ebfa-126">What MEF Provides</span></span>  
 <span data-ttu-id="8ebfa-127">Místo tato explicitní registrace k dispozici součástí MEF poskytuje způsob, jak je implicitně, zjišťovat prostřednictvím *složení*.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span>  <span data-ttu-id="8ebfa-128">Komponenty MEF, s názvem *část*, deklarativně určuje jeho závislé součásti (označované jako *importuje*) a funkcích (označované jako *exportuje*) jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="8ebfa-129">Když je vytvořen součástí, modul složení MEF splňuje jeho importy s co je dostupné z dalších částí.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>  
  
 <span data-ttu-id="8ebfa-130">Tento přístup řeší problémy, které jsou popsané v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-130">This approach solves the problems discussed in the previous section.</span></span>  <span data-ttu-id="8ebfa-131">Protože částí rozhraní MEF deklarativně zadat jejich schopnosti, jsou zjistitelný za běhu, což znamená, že aplikace provádět použít částí bez pevně odkazy nebo křehké konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span>  <span data-ttu-id="8ebfa-132">MEF umožňuje aplikacím pro zjišťování a kontrolu částí podle jejich metadat bez vytváření instancí je nebo i načtení jejich sestavení.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="8ebfa-133">V důsledku toho není třeba pečlivě určit, kdy a jak se mají načíst rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>  
  
 <span data-ttu-id="8ebfa-134">Kromě jeho zadaný exportuje můžete zadat část jeho importy, které budou plnit podle dalších částí.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span>  <span data-ttu-id="8ebfa-135">Tato díky komunikace mezi částí není pouze možná, ale snadno a umožňuje dobré řešení kódu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="8ebfa-136">Například služby, které jsou společné pro celou řadu součástí můžete být promítnou do samostatné části a snadno upravit nebo nahradit.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>  
  
 <span data-ttu-id="8ebfa-137">Protože MEF modelu vyžaduje žádné pevné závislost na konkrétní aplikaci sestavení, umožňuje rozšíření znovu použije z aplikace do aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span>  <span data-ttu-id="8ebfa-138">To také umožňuje snadno vyvíjet test harness, nezávisle na aplikaci, otestovat rozšíření součásti.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>  
  
 <span data-ttu-id="8ebfa-139">Rozšiřitelné aplikace napsané pomocí MEF deklaruje, že importu, který může být vyplněna součástmi rozšíření a může také deklarovat exportuje tak, aby získal aplikačních služeb pro rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span>  <span data-ttu-id="8ebfa-140">Jednotlivé komponenty rozšíření deklaruje exportu a může také deklarovat importy.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-140">Each extension component declares an export, and may also declare imports.</span></span>  <span data-ttu-id="8ebfa-141">Tímto způsobem jsou automaticky extensible rozšíření komponenty, sami.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-141">In this way, extension components themselves are automatically extensible.</span></span>  
  
<a name="where_is_mef_available"></a>   
## <a name="where-is-mef-available"></a><span data-ttu-id="8ebfa-142">Kde je k dispozici MEF?</span><span class="sxs-lookup"><span data-stu-id="8ebfa-142">Where Is MEF Available?</span></span>  
 <span data-ttu-id="8ebfa-143">MEF je nedílnou součástí [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]a je k dispozici, kdekoli se používá rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-143">MEF is an integral part of the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], and is available wherever the .NET Framework is used.</span></span>  <span data-ttu-id="8ebfa-144">Můžete vytvořit MEF v klientských aplikacích, ať už používají Windows Forms, WPF nebo jiné technologie, nebo v serverových aplikací, které pomocí technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>  
  
<a name="mef_and_maf"></a>   
## <a name="mef-and-maf"></a><span data-ttu-id="8ebfa-145">MEF a MAF</span><span class="sxs-lookup"><span data-stu-id="8ebfa-145">MEF and MAF</span></span>  
 <span data-ttu-id="8ebfa-146">Předchozí verze rozhraní .NET Framework zavedl spravované Add-in Framework (MAF), navržená tak, aby aplikacím umožňují izolovat a správě rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span>  <span data-ttu-id="8ebfa-147">Cílem tohoto MAF je něco vyšší úrovni než MEF, který je zaměřený na rozšíření izolace a sestavení načítání a uvolňování, pokud je fokus na MEF na možnosti rozpoznání, rozšíření a přenositelnost.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span>  <span data-ttu-id="8ebfa-148">Dvě rozhraní spolupracovat plynule a jedné aplikace můžete využít i.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>  
  
<a name="simplecalculator_an_example_application"></a>   
## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="8ebfa-149">SimpleCalculator: Ukázková aplikace</span><span class="sxs-lookup"><span data-stu-id="8ebfa-149">SimpleCalculator: An Example Application</span></span>  
 <span data-ttu-id="8ebfa-150">Nejjednodušší způsob, jak zobrazit, co můžete dělat MEF je vytvořit jednoduchou aplikaci MEF.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="8ebfa-151">V tomto příkladu vytvoříte velmi jednoduché kalkulačky s názvem SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="8ebfa-152">Cílem SimpleCalculator je k vytvoření konzolové aplikace, který přijímá základní aritmetické příkazy ve tvaru "5 + 3" nebo "6-2" a vrátí správné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="8ebfa-153">Pomocí rozhraní MEF, nebudete moct přidat nové operátory beze změny kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-153">Using MEF, you will be able to add new operators without changing the application code.</span></span>  
  
 <span data-ttu-id="8ebfa-154">Si můžete stáhnout kompletní kód v tomto příkladu [SimpleCalculator ukázka](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="8ebfa-154">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ebfa-155">Účelem SimpleCalculator je k předvedení konceptů a syntaxe MEF, nikoli nutně zajistit realistické scénář pro jeho použití.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="8ebfa-156">Mnoho aplikací, které by měla mít prospěch většinu od výkonu MEF je mnohem složitější než SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="8ebfa-157">Rozsáhlejší příklady najdete v tématu [spravované rozhraní rozšiřitelnosti](https://github.com/MicrosoftArchive/mef) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>
  
 <span data-ttu-id="8ebfa-158">Chcete-li spustit v [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], vytvořte nový projekt konzolové aplikace s názvem `SimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-158">To start, in [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], create a new Console Application project named `SimpleCalculator`.</span></span> <span data-ttu-id="8ebfa-159">Přidáte odkaz na sestavení System.ComponentModel.Composition, kde se nachází MEF.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span> <span data-ttu-id="8ebfa-160">Otevřete Module1.vb nebo Program.cs a přidejte `Imports` nebo `using` příkazy pro System.ComponentModel.Composition a System.ComponentModel.Composition.Hosting.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="8ebfa-161">Tyto dva obory názvů obsahovat typy MEF budete muset vyvíjet rozšiřitelné aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span> <span data-ttu-id="8ebfa-162">V jazyce Visual Basic, přidejte `Public` – klíčové slovo na řádek, který deklaruje `Module1` modulu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-162">In Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>  
  
<a name="composition_container_and_catalogs"></a>   
## <a name="composition-container-and-catalogs"></a><span data-ttu-id="8ebfa-163">Složení kontejneru a katalogy</span><span class="sxs-lookup"><span data-stu-id="8ebfa-163">Composition Container and Catalogs</span></span>  
 <span data-ttu-id="8ebfa-164">Je základní modelu složení MEF *složení kontejneru*, který obsahuje všechny části k dispozici a provede složení.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span>  <span data-ttu-id="8ebfa-165">(To znamená, shody s importy pro export.)  Nejběžnějším typem složení kontejneru je <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, a to bude používat pro SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-165">(That is, the matching up of imports to exports.)  The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you will use this for SimpleCalculator.</span></span>  
  
 <span data-ttu-id="8ebfa-166">V jazyce Visual Basic v Module1.vb přidejte veřejnou třídu s názvem `Program`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-166">In Visual Basic, in Module1.vb, add a public class named `Program`.</span></span> <span data-ttu-id="8ebfa-167">Pak přidejte následující řádek na `Program` třídy v Module1.vb nebo Program.cs:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-167">Then add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>  
  
```vb  
Dim _container As CompositionContainer  
```  
  
```csharp  
private CompositionContainer _container;  
```  
  
 <span data-ttu-id="8ebfa-168">Chcete-li vyhledat dostupné, kontejnery složení částí využívá *katalogu*.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-168">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="8ebfa-169">Katalog je objekt, který je k dispozici částí zjištěných z některé zdroje.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-169">A catalog is an object that makes available parts discovered from some source.</span></span>  <span data-ttu-id="8ebfa-170">MEF poskytuje katalogy pro zjišťování částí ze zadaného typu, sestavení nebo v adresáři.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-170">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="8ebfa-171">Vývojáři aplikací můžete snadno vytvořit nový katalogy pro zjišťování částí z jiných zdrojů, například webovou službu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-171">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>  
  
 <span data-ttu-id="8ebfa-172">Přidejte následující konstruktor `Program` třídy:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-172">Add the following constructor to the `Program` class:</span></span>  
  
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
  
 <span data-ttu-id="8ebfa-173">Volání <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> informuje kontejner složení, aby tvoří konkrétní sadu části v tomto případě aktuální instancí třídy `Program`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-173">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="8ebfa-174">V tuto chvíli však není provedena žádná akce, protože `Program` nemá žádné importy k vyplnění.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-174">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>  
  
<a name="imports_and_exports_with_attributes"></a>   
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="8ebfa-175">Import a export s atributy</span><span class="sxs-lookup"><span data-stu-id="8ebfa-175">Imports and Exports with Attributes</span></span>  
 <span data-ttu-id="8ebfa-176">Nejdřív musíte `Program` importovat kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-176">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="8ebfa-177">To umožňuje oddělení uživatelské rozhraní otázky, jako je například konzola vstup a výstup, který bude odeslán do `Program`, z logiky kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-177">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>  
  
 <span data-ttu-id="8ebfa-178">Přidejte následující kód, který `Program` třídy:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-178">Add the following code to the `Program` class:</span></span>  
  
```vb  
<Import(GetType(ICalculator))>  
Public Property calculator As ICalculator  
```  
  
```csharp  
[Import(typeof(ICalculator))]  
public ICalculator calculator;  
```  
  
 <span data-ttu-id="8ebfa-179">Všimněte si, že deklaraci `calculator` objekt není, ale je upravena pomocí <xref:System.ComponentModel.Composition.ImportAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-179">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span>  <span data-ttu-id="8ebfa-180">Tento atribut deklaruje něco jako importu; To znamená, že ho bude vyplněno modul složení při objekt se skládá.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-180">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>  
  
 <span data-ttu-id="8ebfa-181">Má každý importu *kontrakt*, která určuje, jaké exporty budou přiřazeny.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-181">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="8ebfa-182">Kontrakt může být explicitně zadaný řetězec, nebo ji automaticky generuje služba MEF z daného typu, v tomto případě rozhraní `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-182">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span>  <span data-ttu-id="8ebfa-183">Každý export deklarovat s kontraktu odpovídající bude splnění tohoto importu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-183">Any export declared with a matching contract will fulfill this import.</span></span>  <span data-ttu-id="8ebfa-184">Všimněte si, že se při typ `calculator` objekt je ve skutečnosti `ICalculator`, není to povinné.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-184">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="8ebfa-185">Kontrakt je nezávislé na typ objektu import.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-185">The contract is independent from the type of the importing object.</span></span>  <span data-ttu-id="8ebfa-186">(V takovém případě může nechat `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-186">(In this case, you could leave out the `typeof(ICalculator)`.</span></span>  <span data-ttu-id="8ebfa-187">MEF automaticky převezme kontrakt byl založen na typ importu, pokud ji zadáte explicitně.)</span><span class="sxs-lookup"><span data-stu-id="8ebfa-187">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>  
  
 <span data-ttu-id="8ebfa-188">Přidejte tento velmi jednoduché rozhraní, modul nebo `SimpleCalculator` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-188">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="8ebfa-189">Teď, když jste definovali `ICalculator`, musíte třídu, která implementuje ho.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-189">Now that you have defined `ICalculator`, you need a class that implements it.</span></span>  <span data-ttu-id="8ebfa-190">Přidejte následující třídy modulu nebo `SimpleCalculator` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-190">Add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="8ebfa-191">Tady je export, který se bude shodovat s import do `Program`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-191">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="8ebfa-192">V pořadí pro export tak, aby odpovídaly import export musí mít stejné smlouvy.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-192">In order for the export to match the import, the export must have the same contract.</span></span>  <span data-ttu-id="8ebfa-193">Export v rámci smlouvy na základě `typeof(MySimpleCalculator)` byste mohli vytvořit neshody a import by být vyplněna; kontrakt musí přesně shodovat.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-193">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>  
  
 <span data-ttu-id="8ebfa-194">Vzhledem k tomu, že kontejner složení vyplní se všechny součásti, které jsou k dispozici v tomto sestavení `MySimpleCalculator` část bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-194">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span>  <span data-ttu-id="8ebfa-195">Když v konstruktoru pro `Program` složení provádí `Program` objektu, bude vyplněn jeho import `MySimpleCalculator` objekt, který se vytvoří pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-195">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>  
  
 <span data-ttu-id="8ebfa-196">Uživatelské rozhraní vrstvě (`Program`) nemusí vědět nic jiného.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-196">The user interface layer (`Program`) does not need to know anything else.</span></span>  <span data-ttu-id="8ebfa-197">Proto můžete vyplnit ve zbývající části logiku uživatelského rozhraní v `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-197">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>  
  
 <span data-ttu-id="8ebfa-198">Přidejte následující kód, který `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-198">Add the following code to the `Main` method:</span></span>  
  
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
  
 <span data-ttu-id="8ebfa-199">Tento kód jednoduše přečte řádek vstupu a volání `Calculate` funkce `ICalculator` na výsledek, který zapíše zpět do konzoly.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-199">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="8ebfa-200">To znamená všechny kód, který potřebujete v `Program`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-200">That is all the code you need in `Program`.</span></span>  <span data-ttu-id="8ebfa-201">Všechny zbývající práce proběhne v části.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-201">All the rest of the work will happen in the parts.</span></span>  
  
<a name="further_imports_and_importmany"></a>   
## <a name="further-imports-and-importmany"></a><span data-ttu-id="8ebfa-202">Další importy a ImportMany</span><span class="sxs-lookup"><span data-stu-id="8ebfa-202">Further Imports and ImportMany</span></span>  
 <span data-ttu-id="8ebfa-203">Aby SimpleCalculator na rozšiřitelnost je nutné importovat seznam operací.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-203">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="8ebfa-204">Běžný <xref:System.ComponentModel.Composition.ImportAttribute> atribut vyplní pouze jeden <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-204">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span>  <span data-ttu-id="8ebfa-205">Pokud je více než jeden dostupný, modul složení vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-205">If more than one is available, the composition engine produces an error.</span></span>  <span data-ttu-id="8ebfa-206">Pokud chcete vytvořit tak může být vyplněna podle libovolný počet exportuje importu, můžete použít <xref:System.ComponentModel.Composition.ImportManyAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-206">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>  
  
 <span data-ttu-id="8ebfa-207">Přidejte následující vlastnosti operací `MySimpleCalculator` třídy:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-207">Add the following operations property to the `MySimpleCalculator` class:</span></span>  
  
```vb  
<ImportMany()>  
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))  
```  
  
```csharp  
[ImportMany]  
IEnumerable<Lazy<IOperation, IOperationData>> operations;  
```  
  
 <span data-ttu-id="8ebfa-208"><xref:System.Lazy%602>Typ poskytovaný MEF pro uložení nepřímé odkazy na export.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-208"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span>  <span data-ttu-id="8ebfa-209">Zde, kromě exportovaný samotného objektu získáte *export metadat*, nebo informace, které popisují exportovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-209">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="8ebfa-210">Každý <xref:System.Lazy%602> obsahuje `IOperation` objekt, představující aktuální operace a `IOperationData` objekt, představující jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-210">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>  
  
 <span data-ttu-id="8ebfa-211">Přidejte následující jednoduché rozhraní modulu nebo `SimpleCalculator` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-211">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="8ebfa-212">V takovém případě metadata pro každou operaci je symbol, který představuje tuto operaci, jako například +, -, *, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-212">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, *, and so on.</span></span> <span data-ttu-id="8ebfa-213">Operace přidání zpřístupnit, přidejte následující třídy modulu nebo `SimpleCalculator` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-213">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="8ebfa-214"><xref:System.ComponentModel.Composition.ExportAttribute> Atribut funkce jako předtím.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-214">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span>  <span data-ttu-id="8ebfa-215"><xref:System.ComponentModel.Composition.ExportMetadataAttribute> Atribut připojí metadata, a to ve formě pár název hodnota pro tento export.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-215">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span>  <span data-ttu-id="8ebfa-216">Když `Add` třída implementuje `IOperation`, třídu, která implementuje `IOperationData` nejsou výslovně definované.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-216">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="8ebfa-217">Místo toho třída je implicitně vytvořen MEF s na základě názvů metadata zadané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-217">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span>  <span data-ttu-id="8ebfa-218">(To je jedním z několika způsoby, jak získat přístup k metadatům v MEF.)</span><span class="sxs-lookup"><span data-stu-id="8ebfa-218">(This is one of several ways to access metadata in MEF.)</span></span>  
  
 <span data-ttu-id="8ebfa-219">Složení v MEF je *rekurzivní*.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-219">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="8ebfa-220">Můžete explicitně skládá `Program` objekt, který importován `ICalculator` , je typu `MySimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-220">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span>  <span data-ttu-id="8ebfa-221">`MySimpleCalculator`, pak importuje kolekce `IOperation` objekty a že import bude vyplněno při `MySimpleCalculator` se vytvoří ve stejnou dobu jako importy z `Program`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-221">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="8ebfa-222">Pokud `Add` třída deklarována další import, který příliš musel být vyplněna a tak dále.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-222">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="8ebfa-223">Importovat všechny levé nevyplněný výsledkem chyba složení.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-223">Any import left unfilled results in a composition error.</span></span>  <span data-ttu-id="8ebfa-224">(Je možné, ale deklarovat importy jako volitelnou nebo jim ho přiřadit výchozí hodnoty.)</span><span class="sxs-lookup"><span data-stu-id="8ebfa-224">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>  
  
<a name="calculator_logic"></a>   
## <a name="calculator-logic"></a><span data-ttu-id="8ebfa-225">Kalkulačky logiky</span><span class="sxs-lookup"><span data-stu-id="8ebfa-225">Calculator Logic</span></span>  
 <span data-ttu-id="8ebfa-226">Pomocí těchto částí v místě zbývá vlastní logiky kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-226">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="8ebfa-227">Přidejte následující kód v `MySimpleCalculator` třídu pro implementaci `Calculate` metoda:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-227">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>  
  
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
  
 <span data-ttu-id="8ebfa-228">Počáteční kroky analyzovat vstupní řetězec do levé a pravé operandy a znakem operátor.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-228">The initial steps parse the input string into left and right operands and an operator character.</span></span>  <span data-ttu-id="8ebfa-229">V `foreach` cykly, každý člen `operations` je zkontrolován kolekce.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-229">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="8ebfa-230">Tyto objekty jsou typu <xref:System.Lazy%602>, a jejich hodnoty metadat a exportovaný objekt lze přistupovat pomocí <xref:System.Lazy%602.Metadata%2A> vlastnost a <xref:System.Lazy%601.Value%2A> vlastnost v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-230">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="8ebfa-231">V takovém případě pokud `Symbol` vlastnost `IOperationData` objektu byla vyhodnocena jako odpovídající, volání kalkulačky `Operate` metodu `IOperation` objektu a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-231">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>  
  
 <span data-ttu-id="8ebfa-232">K dokončení kalkulačky, musíte taky Pomocná metoda, která vrátí pozici prvního nečíselným znaku v řetězci.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-232">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span>  <span data-ttu-id="8ebfa-233">Přidejte následující metodu helper do `MySimpleCalculator` třídy:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-233">Add the following helper method to the `MySimpleCalculator` class:</span></span>  
  
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
  
 <span data-ttu-id="8ebfa-234">Teď by měla být moct zkompilování a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-234">You should now be able to compile and run the project.</span></span> <span data-ttu-id="8ebfa-235">V jazyce Visual Basic, ujistěte se, zda jste přidali `Public` – klíčové slovo k `Module1`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-235">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="8ebfa-236">V okně konzoly zadejte operace přidání, například "5 + 3", a kalkulačky vrátí výsledky.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-236">In the console window, type an addition operation, such as "5+3", and the calculator will return the results.</span></span>  <span data-ttu-id="8ebfa-237">Další operátor bude výsledkem "operaci nebyl nalezen!"</span><span class="sxs-lookup"><span data-stu-id="8ebfa-237">Any other operator will result in the "Operation Not Found!"</span></span> <span data-ttu-id="8ebfa-238">Zpráva.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-238">message.</span></span>  
  
<a name="extending_simplecalculator_using_a_new_class"></a>   
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="8ebfa-239">Rozšíření SimpleCalculator pomocí nové třídy</span><span class="sxs-lookup"><span data-stu-id="8ebfa-239">Extending SimpleCalculator Using A New Class</span></span>  
 <span data-ttu-id="8ebfa-240">Teď, když kalkulačky funguje, přidání nové operaci je snadné.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-240">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="8ebfa-241">Přidejte následující třídy modulu nebo `SimpleCalculator` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-241">Add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="8ebfa-242">Zkompilování a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-242">Compile and run the project.</span></span> <span data-ttu-id="8ebfa-243">Zadejte odčítání operace, jako je například "5-3".</span><span class="sxs-lookup"><span data-stu-id="8ebfa-243">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="8ebfa-244">Rozhraní kalkulačky teď podporuje odčítání a také přidání.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-244">The calculator now supports subtraction as well as addition.</span></span>  
  
<a name="extending_simplecalculator_using_a_new_assembly"></a>   
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="8ebfa-245">Rozšíření SimpleCalculator pomocí nové sestavení</span><span class="sxs-lookup"><span data-stu-id="8ebfa-245">Extending SimpleCalculator Using A New Assembly</span></span>  
 <span data-ttu-id="8ebfa-246">Přidávání tříd ke zdroji kód je dostatečně jednoduchá, ale MEF umožňuje hledat částí mimo na aplikace vlastní zdroj.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-246">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="8ebfa-247">Ukazuje to, budete muset upravit SimpleCalculator k vyhledání adresáře, jakož i vlastní sestavení pro části přidáním <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-247">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>  
  
 <span data-ttu-id="8ebfa-248">Přidat nový adresář s názvem `Extensions` do projektu SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-248">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span>  <span data-ttu-id="8ebfa-249">Ujistěte se, že ho přidat na úrovni projektu a nikoli na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-249">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="8ebfa-250">Pak přidejte nový projekt knihovny tříd do řešení, s názvem `ExtendedOperations`.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-250">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="8ebfa-251">Nový projekt zkompiluje do samostatné sestavení.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-251">The new project will compile into a separate assembly.</span></span>  
  
 <span data-ttu-id="8ebfa-252">Otevřete vlastnosti Návrhář projektu ExtendedOperations projektu a klikněte **zkompilovat** nebo **sestavení** kartě. Změna **sestavení výstupní cesta** nebo **výstupní cesta** tak, aby odkazoval na adresář rozšíření v adresáři projektu SimpleCalculator (.. \SimpleCalculator\Extensions\\).</span><span class="sxs-lookup"><span data-stu-id="8ebfa-252">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>  
  
 <span data-ttu-id="8ebfa-253">V Module1.vb nebo Program.cs přidejte následující řádek na `Program` konstruktor:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-253">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>  
  
```vb  
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))  
```  
  
```csharp  
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));  
```  
  
 <span data-ttu-id="8ebfa-254">Příklad cesty nahraďte cestu k adresáři rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-254">Replace the example path with the path to your Extensions directory.</span></span>  <span data-ttu-id="8ebfa-255">(Tato absolutní cesta je pouze pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-255">(This absolute path is for debugging purposes only.</span></span>  <span data-ttu-id="8ebfa-256">V případě produkční aplikace použijete relativní cesta.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Teď přidá všechny části v jakékoli sestavení v adresáři rozšíření ke kontejneru složení nalezen.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-256">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>  
  
 <span data-ttu-id="8ebfa-257">V projektu ExtendedOperations přidáte odkazy na SimpleCalculator a System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-257">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="8ebfa-258">V souboru ExtendedOperations třídy, přidejte `Imports` nebo `using` příkaz pro System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-258">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="8ebfa-259">V jazyce Visual Basic také přidat `Imports` příkaz pro SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-259">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="8ebfa-260">Do souboru třídy ExtendedOperations přidáte následující třídy:</span><span class="sxs-lookup"><span data-stu-id="8ebfa-260">Then add the following class to the ExtendedOperations class file:</span></span>  
  
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
  
 <span data-ttu-id="8ebfa-261">Všimněte si, že v pořadí pro daný kontrakt tak, aby odpovídaly, <xref:System.ComponentModel.Composition.ExportAttribute> atributu musí mít stejný typ jako <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-261">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>  
  
 <span data-ttu-id="8ebfa-262">Zkompilování a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-262">Compile and run the project.</span></span> <span data-ttu-id="8ebfa-263">Otestujte novou operátor Mod (%).</span><span class="sxs-lookup"><span data-stu-id="8ebfa-263">Test the new Mod (%) operator.</span></span>  
  
<a name="conclusion"></a>   
## <a name="conclusion"></a><span data-ttu-id="8ebfa-264">Závěr</span><span class="sxs-lookup"><span data-stu-id="8ebfa-264">Conclusion</span></span>  
 <span data-ttu-id="8ebfa-265">Toto téma je zahrnuté se základními koncepty MEF.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-265">This topic covered the basic concepts of MEF.</span></span>  
  
-   <span data-ttu-id="8ebfa-266">Části, katalogů a kontejneru složení</span><span class="sxs-lookup"><span data-stu-id="8ebfa-266">Parts, catalogs, and the composition container</span></span>  
  
     <span data-ttu-id="8ebfa-267">Části a kontejneru složení jsou základní stavební bloky MEF aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-267">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="8ebfa-268">Součástí je libovolný objekt, který importuje nebo exportuje hodnotu, do a včetně sám sebe.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-268">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="8ebfa-269">Katalog poskytuje kolekci částí z určitého zdroje.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-269">A catalog provides a collection of parts from a particular source.</span></span>  <span data-ttu-id="8ebfa-270">Kontejneru složení částí poskytované katalog používá k sestavení, vazba importy pro export.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-270">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>  
  
-   <span data-ttu-id="8ebfa-271">Import a export</span><span class="sxs-lookup"><span data-stu-id="8ebfa-271">Imports and exports</span></span>  
  
     <span data-ttu-id="8ebfa-272">Import a export představují způsob, kterým součásti komunikovat.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-272">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="8ebfa-273">Importu komponentu určuje potřebu konkrétní hodnota nebo objekt a s exportu určuje dostupnost hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-273">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="8ebfa-274">Každý import je nalezena shoda se seznamem exportuje prostřednictvím její smlouvy.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-274">Each import is matched with a list of exports by way of its contract.</span></span>  
  
<a name="where_do_i_go_now"></a>   
## <a name="where-do-i-go-now"></a><span data-ttu-id="8ebfa-275">Kde přejít teď?</span><span class="sxs-lookup"><span data-stu-id="8ebfa-275">Where Do I Go Now?</span></span>  
 <span data-ttu-id="8ebfa-276">Si můžete stáhnout kompletní kód v tomto příkladu [SimpleCalculator ukázka](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="8ebfa-276">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>  
  
 <span data-ttu-id="8ebfa-277">Další informace a příklady kódu najdete v tématu [spravované rozhraní rozšiřitelnosti](http://go.microsoft.com/fwlink/?LinkId=144282).</span><span class="sxs-lookup"><span data-stu-id="8ebfa-277">For more information and code examples, see [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282).</span></span> <span data-ttu-id="8ebfa-278">Seznam typů MEF, najdete v článku <xref:System.ComponentModel.Composition?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8ebfa-278">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
