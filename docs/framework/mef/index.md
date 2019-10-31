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
ms.openlocfilehash: da73200513d451ee391fb6dd9c214a5b8ca771c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126338"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="10417-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="10417-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="10417-103">V tomto tématu najdete přehled Managed Extensibility Framework představených v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="10417-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a><span data-ttu-id="10417-104">Co je MEF?</span><span class="sxs-lookup"><span data-stu-id="10417-104">What is MEF?</span></span>

<span data-ttu-id="10417-105">Managed Extensibility Framework nebo MEF je knihovna pro vytváření odlehčených a rozšiřitelných aplikací.</span><span class="sxs-lookup"><span data-stu-id="10417-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="10417-106">Umožňuje vývojářům aplikací zjišťovat a používat rozšíření bez nutnosti konfigurace.</span><span class="sxs-lookup"><span data-stu-id="10417-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="10417-107">Také umožňuje vývojářům rozšíření snadno zapouzdřit kód a vyhnout se nekřehkým pevným závislostem.</span><span class="sxs-lookup"><span data-stu-id="10417-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="10417-108">MEF neumožňuje znovu použít rozšíření v aplikacích, ale i napříč aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="10417-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="10417-109">Problém rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="10417-109">The Problem of Extensibility</span></span>
 <span data-ttu-id="10417-110">Představte si, že jste architekt velké aplikace, která musí poskytovat podporu pro rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="10417-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="10417-111">Vaše aplikace musí zahrnovat potenciálně velký počet menších součástí a zodpovídá za jejich vytvoření a spuštění.</span><span class="sxs-lookup"><span data-stu-id="10417-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

 <span data-ttu-id="10417-112">Nejjednodušším přístupem k problému je zahrnout komponenty jako zdrojový kód do vaší aplikace a volat je přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="10417-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="10417-113">To má řadu zjevných nevýhod.</span><span class="sxs-lookup"><span data-stu-id="10417-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="10417-114">Nejdůležitější je, že nemůžete přidávat nové komponenty bez změny zdrojového kódu, což je omezení, které může být přijatelné například pro webovou aplikaci, ale nefunguje v klientské aplikaci.</span><span class="sxs-lookup"><span data-stu-id="10417-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="10417-115">Stejně problematický, možná nebudete mít přístup ke zdrojovému kódu pro součásti, protože můžou být vyvinuty třetími stranami a ze stejného důvodu je nemůžete jim dovolit přístup.</span><span class="sxs-lookup"><span data-stu-id="10417-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

 <span data-ttu-id="10417-116">Mírně propracovanější přístup by byl poskytnutím rozšiřujícího bodu nebo rozhraní, aby bylo možné odsouhlasení mezi aplikací a jejími součástmi.</span><span class="sxs-lookup"><span data-stu-id="10417-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="10417-117">V rámci tohoto modelu můžete zadat rozhraní, které může komponenta implementovat, a rozhraní API, které bude umožňovat interakci s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="10417-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="10417-118">Tím se vyřeší problém vyžadující přístup ke zdrojovému kódu, ale stále se jedná o vlastní problémy.</span><span class="sxs-lookup"><span data-stu-id="10417-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

 <span data-ttu-id="10417-119">Vzhledem k tomu, že aplikace nemá žádnou kapacitu pro zjišťování komponent na vlastní, musí být stále výslovně jasné, které součásti jsou k dispozici a měly by být načteny.</span><span class="sxs-lookup"><span data-stu-id="10417-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="10417-120">To se obvykle provádí explicitním registrací dostupných komponent do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="10417-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="10417-121">To znamená, že ujištění, že tyto součásti jsou správné a že se jedná o problém s údržbou, zejména pokud se jedná o koncového uživatele, nikoli vývojáře, který by se měl aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="10417-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

 <span data-ttu-id="10417-122">Kromě toho součásti nejsou schopny vzájemně komunikovat, s výjimkou pevně definovaných kanálů samotné aplikace.</span><span class="sxs-lookup"><span data-stu-id="10417-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="10417-123">Pokud architekt aplikace nepředpokládal nutnost konkrétní komunikace, je obvykle nemožné.</span><span class="sxs-lookup"><span data-stu-id="10417-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

 <span data-ttu-id="10417-124">Nakonec musí vývojáři komponent přijmout pevně závislou závislost na tom, jaké sestavení obsahuje rozhraní, které implementuje.</span><span class="sxs-lookup"><span data-stu-id="10417-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="10417-125">Proto je obtížné použít komponentu ve více než jedné aplikaci a může také vytvořit problémy při vytváření testovacího rozhraní pro komponenty.</span><span class="sxs-lookup"><span data-stu-id="10417-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a><span data-ttu-id="10417-126">Jaké rozhraní MEF poskytuje</span><span class="sxs-lookup"><span data-stu-id="10417-126">What MEF Provides</span></span>
 <span data-ttu-id="10417-127">Namísto této explicitní registrace dostupných komponent poskytuje rozhraní MEF způsob, jak je zjistit implicitně, prostřednictvím *složení*.</span><span class="sxs-lookup"><span data-stu-id="10417-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="10417-128">Komponenta MEF, která se označuje jako *součást*, deklarativně určuje jejich závislosti (známé jako *importy*) a jaké funkce (označované jako *Export*) zpřístupňují.</span><span class="sxs-lookup"><span data-stu-id="10417-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="10417-129">Když je vytvořena část, modul kompozice MEF splní svůj import s tím, co je k dispozici z jiných částí.</span><span class="sxs-lookup"><span data-stu-id="10417-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

 <span data-ttu-id="10417-130">Tento přístup řeší problémy popsané v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="10417-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="10417-131">Vzhledem k tomu, že součásti MEF deklarativně specifikují své možnosti, jsou zjistitelné za běhu, což znamená, že aplikace může využít části bez pevně zakódovaných odkazů nebo křehkých konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="10417-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="10417-132">MEF umožňuje aplikacím vyhledat a prozkoumat části podle jejich metadat, aniž by bylo nutné je vytvořit nebo dokonce načíst jejich sestavení.</span><span class="sxs-lookup"><span data-stu-id="10417-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="10417-133">V důsledku toho není nutné pečlivě určovat, kdy a jak se mají rozšíření načíst.</span><span class="sxs-lookup"><span data-stu-id="10417-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

 <span data-ttu-id="10417-134">Kromě poskytnutých exportů může součást určit její importy, které budou vyplněny jinými částmi.</span><span class="sxs-lookup"><span data-stu-id="10417-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="10417-135">To umožňuje komunikaci mezi součástmi, které nejsou pouze možné, ale jednoduché, a umožňuje dobrý faktoring kódu.</span><span class="sxs-lookup"><span data-stu-id="10417-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="10417-136">Například služby společné na mnoho komponent lze rozdělit do samostatné části a snadno upravit nebo nahradit.</span><span class="sxs-lookup"><span data-stu-id="10417-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

 <span data-ttu-id="10417-137">Vzhledem k tomu, že model MEF nepožaduje žádné pevné závislosti na konkrétním sestavení aplikace, umožňuje rozšíření znovu použít z aplikace do aplikace.</span><span class="sxs-lookup"><span data-stu-id="10417-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="10417-138">To také usnadňuje vývoj testovacího vodiče nezávisle na aplikaci pro testování komponent rozšíření.</span><span class="sxs-lookup"><span data-stu-id="10417-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

 <span data-ttu-id="10417-139">Rozšiřitelná aplikace napsaná pomocí rozhraní MEF deklaruje import, který může být vyplněn součástmi rozšíření, a může také deklarovat exporty, aby bylo možné vystavit aplikační služby pro rozšíření.</span><span class="sxs-lookup"><span data-stu-id="10417-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="10417-140">Každá součást rozšíření deklaruje export a může také deklarovat import.</span><span class="sxs-lookup"><span data-stu-id="10417-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="10417-141">Tímto způsobem jsou samotné součásti rozšíření automaticky rozšiřitelné.</span><span class="sxs-lookup"><span data-stu-id="10417-141">In this way, extension components themselves are automatically extensible.</span></span>

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a><span data-ttu-id="10417-142">Kde je k dispozici MEF?</span><span class="sxs-lookup"><span data-stu-id="10417-142">Where Is MEF Available?</span></span>
 <span data-ttu-id="10417-143">MEF je nedílnou součástí .NET Framework 4 a je k dispozici všude, kde se používá .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10417-143">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="10417-144">V klientských aplikacích můžete použít MEF, ať už používají model Windows Forms, WPF nebo jakoukoli jinou technologii, nebo v serverových aplikacích, které používají ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="10417-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a><span data-ttu-id="10417-145">MEF a MAF</span><span class="sxs-lookup"><span data-stu-id="10417-145">MEF and MAF</span></span>
 <span data-ttu-id="10417-146">Předchozí verze .NET Framework představily spravované rozhraní doplňku (MAF), navržené tak, aby aplikacím umožnily izolaci a správu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="10417-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="10417-147">Zaměření na MAF je mírně vyšší než MEF, zaměřuje se na izolaci rozšíření a načítání a uvolňování sestavení, zatímco se rozhraní MEF zaměřuje na zjistitelnost, rozšiřitelnost a přenositelnost.</span><span class="sxs-lookup"><span data-stu-id="10417-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="10417-148">Obě architektury fungují hladce a jedna aplikace může využít obojí.</span><span class="sxs-lookup"><span data-stu-id="10417-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="10417-149">SimpleCalculator: Ukázková aplikace</span><span class="sxs-lookup"><span data-stu-id="10417-149">SimpleCalculator: An Example Application</span></span>

<span data-ttu-id="10417-150">Nejjednodušší způsob, jak zjistit, co může MEF udělat, je sestavení jednoduché aplikace MEF.</span><span class="sxs-lookup"><span data-stu-id="10417-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="10417-151">V tomto příkladu vytvoříte velmi jednoduchou kalkulačku s názvem SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="10417-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="10417-152">Cílem SimpleCalculator je vytvořit konzolovou aplikaci, která přijímá základní aritmetické příkazy ve formátu "5 + 3" nebo "6-2" a vrací správné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="10417-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="10417-153">Pomocí MEF budete moci přidat nové operátory beze změny kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="10417-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="10417-154">Úplný kód pro tento příklad si můžete stáhnout v [ukázce SimpleCalculator](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="10417-154">To download the complete code for this example, see the [SimpleCalculator sample](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

> [!NOTE]
> <span data-ttu-id="10417-155">Účelem SimpleCalculator je předvedení konceptů a syntaxe MEF, místo aby nutně poskytovala reálný scénář pro použití.</span><span class="sxs-lookup"><span data-stu-id="10417-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="10417-156">Mnohé z aplikací, které by mohly těžit z mocniny MEF, jsou složitější než SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="10417-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="10417-157">Další podrobné příklady najdete v [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="10417-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="10417-158">Chcete-li začít, v aplikaci Visual Studio vytvořte nový projekt konzolové aplikace a pojmenujte jej `SimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="10417-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="10417-159">Přidejte odkaz na sestavení System. ComponentModel. složení, kde se nachází rozhraní MEF.</span><span class="sxs-lookup"><span data-stu-id="10417-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span>

- <span data-ttu-id="10417-160">Otevřete Module1. vb nebo Program.cs a přidejte `Imports` nebo `using` příkazy pro System. ComponentModel. kompozici a System. ComponentModel. kompozice. Hosting.</span><span class="sxs-lookup"><span data-stu-id="10417-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="10417-161">Tyto dva obory názvů obsahují typy MEF, které budete potřebovat pro vývoj rozšiřitelné aplikace.</span><span class="sxs-lookup"><span data-stu-id="10417-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="10417-162">Pokud používáte Visual Basic, přidejte klíčové slovo `Public` na řádek, který deklaruje modul `Module1`.</span><span class="sxs-lookup"><span data-stu-id="10417-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="10417-163">Kontejner a katalog kompozic</span><span class="sxs-lookup"><span data-stu-id="10417-163">Composition Container and Catalogs</span></span>

<span data-ttu-id="10417-164">Základem modelu složení MEF je *kontejner kompozice*, který obsahuje všechny dostupné součásti a provádí složení.</span><span class="sxs-lookup"><span data-stu-id="10417-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="10417-165">Složení je porovnáním s importy a exporty.</span><span class="sxs-lookup"><span data-stu-id="10417-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="10417-166">Nejběžnější typ kontejneru kompozice je <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>a použijete ho pro SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="10417-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="10417-167">Pokud používáte Visual Basic, v Module1. vb přidejte veřejnou třídu s názvem `Program`.</span><span class="sxs-lookup"><span data-stu-id="10417-167">If you're using Visual Basic, in Module1.vb, add a public class named `Program`.</span></span>

<span data-ttu-id="10417-168">Přidejte následující řádek do třídy `Program` v Module1. vb nebo Program.cs:</span><span class="sxs-lookup"><span data-stu-id="10417-168">Add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="10417-169">Aby bylo možné zjistit, jaké součásti jsou k dispozici, kontejnery kompozice využívají *katalog*.</span><span class="sxs-lookup"><span data-stu-id="10417-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="10417-170">Catalog je objekt, který zpřístupňuje dostupné části z nějakého zdroje.</span><span class="sxs-lookup"><span data-stu-id="10417-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="10417-171">MEF poskytuje katalogy pro zjišťování částí ze zadaného typu, sestavení nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="10417-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="10417-172">Vývojáři aplikací můžou snadno vytvářet nové katalogy a zjišťovat části z jiných zdrojů, například webové služby.</span><span class="sxs-lookup"><span data-stu-id="10417-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="10417-173">Přidejte následující konstruktor do třídy `Program`:</span><span class="sxs-lookup"><span data-stu-id="10417-173">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
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

<span data-ttu-id="10417-174">Volání <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> říká kontejneru kompozice, aby vytvářeal určitou sadu částí, v tomto případě aktuální instance `Program`.</span><span class="sxs-lookup"><span data-stu-id="10417-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="10417-175">V tuto chvíli se ale nic nestane, protože `Program` nemá žádné importy k vyplnění.</span><span class="sxs-lookup"><span data-stu-id="10417-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="10417-176">Import a export s atributy</span><span class="sxs-lookup"><span data-stu-id="10417-176">Imports and Exports with Attributes</span></span>
 <span data-ttu-id="10417-177">Nejdřív máte `Program` importovat kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="10417-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="10417-178">To umožňuje oddělení jednotlivých uživatelských rozhraní, jako je například vstup z konzoly a výstup, který se bude přecházet do `Program`z logiky kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="10417-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

 <span data-ttu-id="10417-179">Do `Program` třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="10417-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 <span data-ttu-id="10417-180">Všimněte si, že deklarace objektu `calculator` není neobvyklé, ale je upravena atributem <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="10417-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="10417-181">Tento atribut deklaruje něco pro import; To znamená, že bude modul sestavování vyplněn modulem složení, pokud je objekt sestaven.</span><span class="sxs-lookup"><span data-stu-id="10417-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

 <span data-ttu-id="10417-182">Každý import má *kontrakt*, který určuje, s jakými exporty bude odpovídat.</span><span class="sxs-lookup"><span data-stu-id="10417-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="10417-183">Kontraktem může být explicitně zadaný řetězec nebo může být automaticky vygenerován pomocí MEF z daného typu, v tomto případě `ICalculator`rozhraní.</span><span class="sxs-lookup"><span data-stu-id="10417-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="10417-184">Tento import bude plnit jakýkoli export deklarovaný s vyhovující smlouvou.</span><span class="sxs-lookup"><span data-stu-id="10417-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="10417-185">Všimněte si, že pokud je typ objektu `calculator` ve skutečnosti `ICalculator`, není to nutné.</span><span class="sxs-lookup"><span data-stu-id="10417-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="10417-186">Kontrakt je nezávislý na typu importovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="10417-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="10417-187">(V tomto případě můžete `typeof(ICalculator)`opustit.</span><span class="sxs-lookup"><span data-stu-id="10417-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="10417-188">MEF bude automaticky předpokládat, že kontrakt bude založen na typu importu, pokud ho explicitně neurčíte.)</span><span class="sxs-lookup"><span data-stu-id="10417-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

 <span data-ttu-id="10417-189">Přidejte toto velmi jednoduché rozhraní do modulu nebo `SimpleCalculator` oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="10417-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="10417-190">Nyní, když jste definovali `ICalculator`, potřebujete třídu, která ji implementuje.</span><span class="sxs-lookup"><span data-stu-id="10417-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="10417-191">Do modulu nebo `SimpleCalculator` oboru názvů přidejte následující třídu:</span><span class="sxs-lookup"><span data-stu-id="10417-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="10417-192">Tady je export, který bude odpovídat importu v `Program`.</span><span class="sxs-lookup"><span data-stu-id="10417-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="10417-193">Aby export odpovídal importu, musí mít export stejný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="10417-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="10417-194">Export v rámci smlouvy na základě `typeof(MySimpleCalculator)` by způsobil neshodu a import nebude vyplněn. kontrakt musí přesně odpovídat.</span><span class="sxs-lookup"><span data-stu-id="10417-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

 <span data-ttu-id="10417-195">Vzhledem k tomu, že kontejner skládání bude naplněn všemi částmi, které jsou k dispozici v tomto sestavení, bude k dispozici `MySimpleCalculator`á součást.</span><span class="sxs-lookup"><span data-stu-id="10417-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="10417-196">Když konstruktor pro `Program` provádí kompozici objektu `Program`, jeho import bude vyplněn objektem `MySimpleCalculator`, který bude vytvořen pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="10417-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

 <span data-ttu-id="10417-197">Vrstva uživatelského rozhraní (`Program`) nepotřebuje žádné další informace.</span><span class="sxs-lookup"><span data-stu-id="10417-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="10417-198">Z tohoto důvodu můžete v metodě `Main` vyplnit zbývající část logiky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="10417-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

 <span data-ttu-id="10417-199">Do `Main` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="10417-199">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
    ' Composition is performed in the constructor.
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
    // Composition is performed in the constructor.
    var p = new Program();
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="10417-200">Tento kód jednoduše přečte řádek vstupu a zavolá funkci `Calculate` `ICalculator` ve výsledku, kterou zapisuje zpět do konzoly.</span><span class="sxs-lookup"><span data-stu-id="10417-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="10417-201">To je veškerý kód, který potřebujete v `Program`.</span><span class="sxs-lookup"><span data-stu-id="10417-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="10417-202">Veškerá zbývající část práce nastane v částech.</span><span class="sxs-lookup"><span data-stu-id="10417-202">All the rest of the work will happen in the parts.</span></span>

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a><span data-ttu-id="10417-203">Další import a ImportMany</span><span class="sxs-lookup"><span data-stu-id="10417-203">Further Imports and ImportMany</span></span>
 <span data-ttu-id="10417-204">Aby SimpleCalculator bylo rozšiřitelné, musí importovat seznam operací.</span><span class="sxs-lookup"><span data-stu-id="10417-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="10417-205">Obyčejný <xref:System.ComponentModel.Composition.ImportAttribute> atribut je vyplněn jedním a pouze jedním <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="10417-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="10417-206">Pokud je k dispozici více než jeden, modul kompozice vytvoří chybu.</span><span class="sxs-lookup"><span data-stu-id="10417-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="10417-207">Chcete-li vytvořit import, který může být vyplněn libovolným počtem exportů, můžete použít atribut <xref:System.ComponentModel.Composition.ImportManyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="10417-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

 <span data-ttu-id="10417-208">Do `MySimpleCalculator` třídy přidejte následující vlastnost Operations:</span><span class="sxs-lookup"><span data-stu-id="10417-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <span data-ttu-id="10417-209"><xref:System.Lazy%602> je typ poskytnutý rozhraním MEF pro uchování nepřímých odkazů na export.</span><span class="sxs-lookup"><span data-stu-id="10417-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="10417-210">Zde, kromě exportovaných objektů, také získáte *metadata exportu*nebo informace, které popisují exportovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="10417-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="10417-211">Každý <xref:System.Lazy%602> obsahuje objekt `IOperation`, který představuje skutečnou operaci, a objekt `IOperationData`, který představuje jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="10417-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

 <span data-ttu-id="10417-212">Do modulu nebo `SimpleCalculator` oboru názvů přidejte následující jednoduchá rozhraní:</span><span class="sxs-lookup"><span data-stu-id="10417-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="10417-213">V tomto případě je metadata pro každou operaci symbol, který představuje tuto operaci, například +,-, \* a tak dále.</span><span class="sxs-lookup"><span data-stu-id="10417-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="10417-214">K zpřístupnění operace sčítání přidejte následující třídu do modulu nebo `SimpleCalculator` oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="10417-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="10417-215">Atribut <xref:System.ComponentModel.Composition.ExportAttribute> funguje jako dříve.</span><span class="sxs-lookup"><span data-stu-id="10417-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="10417-216">Atribut <xref:System.ComponentModel.Composition.ExportMetadataAttribute> připojí k tomuto exportu metadata ve formě páru název-hodnota.</span><span class="sxs-lookup"><span data-stu-id="10417-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="10417-217">I když třída `Add` implementuje `IOperation`, třída, která implementuje `IOperationData`, není explicitně definována.</span><span class="sxs-lookup"><span data-stu-id="10417-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="10417-218">Místo toho je třída implicitně vytvořena pomocí MEF s vlastnostmi na základě názvů poskytnutých metadat.</span><span class="sxs-lookup"><span data-stu-id="10417-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="10417-219">(Toto je jeden z několika způsobů, jak získat přístup k metadatům v MEF.)</span><span class="sxs-lookup"><span data-stu-id="10417-219">(This is one of several ways to access metadata in MEF.)</span></span>

 <span data-ttu-id="10417-220">Složení v rozhraní MEF je *rekurzivní*.</span><span class="sxs-lookup"><span data-stu-id="10417-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="10417-221">Objekt `Program`, který importoval `ICalculator`, který se vypnul jako typ `MySimpleCalculator`, se explicitně skládá.</span><span class="sxs-lookup"><span data-stu-id="10417-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="10417-222">`MySimpleCalculator`pak naimportuje kolekci objektů `IOperation` a tento import bude vyplněn při vytváření `MySimpleCalculator`, a to ve stejnou dobu jako při importu `Program`.</span><span class="sxs-lookup"><span data-stu-id="10417-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="10417-223">Pokud třída `Add` deklarovala další import, je nutné ji vyplnit a tak dále.</span><span class="sxs-lookup"><span data-stu-id="10417-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="10417-224">Všechny naimportované nevyplnit výsledky v důsledku chyby složení.</span><span class="sxs-lookup"><span data-stu-id="10417-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="10417-225">(Je však možné deklarovat importy jako volitelné nebo přiřadit výchozí hodnoty.)</span><span class="sxs-lookup"><span data-stu-id="10417-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a><span data-ttu-id="10417-226">Logika kalkulačky</span><span class="sxs-lookup"><span data-stu-id="10417-226">Calculator Logic</span></span>
 <span data-ttu-id="10417-227">Spolu s těmito částmi jsou všechny tyto součásti stále logikou kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="10417-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="10417-228">Přidejte následující kód do třídy `MySimpleCalculator` pro implementaci metody `Calculate`:</span><span class="sxs-lookup"><span data-stu-id="10417-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
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
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input); 
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
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

 <span data-ttu-id="10417-229">Počáteční kroky analyzují vstupní řetězec na levý a pravý operand a znak operátoru.</span><span class="sxs-lookup"><span data-stu-id="10417-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="10417-230">Ve smyčce `foreach` je zkontrolován každý člen kolekce `operations`.</span><span class="sxs-lookup"><span data-stu-id="10417-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="10417-231">Tyto objekty jsou typu <xref:System.Lazy%602>a jejich hodnoty metadat a exportovaných objektů jsou k dispozici s vlastností <xref:System.Lazy%602.Metadata%2A> a vlastností <xref:System.Lazy%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="10417-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="10417-232">V tomto případě, pokud je vlastnost `Symbol` objektu `IOperationData` zjištěna jako shoda, vyvolá Kalkulačka metodu `Operate` objektu `IOperation` a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="10417-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

 <span data-ttu-id="10417-233">K dokončení kalkulačky je také potřeba pomocná metoda, která vrací pozici prvního nenumerického znaku v řetězci.</span><span class="sxs-lookup"><span data-stu-id="10417-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="10417-234">Do `MySimpleCalculator` třídy přidejte následující pomocnou metodu:</span><span class="sxs-lookup"><span data-stu-id="10417-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length - 1
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 <span data-ttu-id="10417-235">Nyní byste měli být schopni zkompilovat a spustit projekt.</span><span class="sxs-lookup"><span data-stu-id="10417-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="10417-236">V Visual Basic Ujistěte se, že jste přidali klíčové slovo `Public` do `Module1`.</span><span class="sxs-lookup"><span data-stu-id="10417-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="10417-237">V okně konzoly zadejte operaci sčítání, například "5 + 3", a kalkulačka vrátí výsledky.</span><span class="sxs-lookup"><span data-stu-id="10417-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="10417-238">Jakýkoli jiný operátor má za následek, že operace nebyla nalezena!</span><span class="sxs-lookup"><span data-stu-id="10417-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="10417-239">Zpráva.</span><span class="sxs-lookup"><span data-stu-id="10417-239">message.</span></span>

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="10417-240">Rozšíření SimpleCalculator pomocí nové třídy</span><span class="sxs-lookup"><span data-stu-id="10417-240">Extending SimpleCalculator Using A New Class</span></span>
 <span data-ttu-id="10417-241">Teď, když Kalkulačka funguje, je přidání nové operace snadné.</span><span class="sxs-lookup"><span data-stu-id="10417-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="10417-242">Do modulu nebo `SimpleCalculator` oboru názvů přidejte následující třídu:</span><span class="sxs-lookup"><span data-stu-id="10417-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="10417-243">Zkompilujte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="10417-243">Compile and run the project.</span></span> <span data-ttu-id="10417-244">Zadejte operaci odčítání, například "5-3".</span><span class="sxs-lookup"><span data-stu-id="10417-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="10417-245">Kalkulačka teď podporuje odčítání a navíc.</span><span class="sxs-lookup"><span data-stu-id="10417-245">The calculator now supports subtraction as well as addition.</span></span>

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="10417-246">Rozšíření SimpleCalculator pomocí nového sestavení</span><span class="sxs-lookup"><span data-stu-id="10417-246">Extending SimpleCalculator Using A New Assembly</span></span>
 <span data-ttu-id="10417-247">Přidávání tříd do zdrojového kódu je dostatečně snadné, ale rozhraní MEF poskytuje možnost podívat se mimo vlastní zdroj aplikace pro části.</span><span class="sxs-lookup"><span data-stu-id="10417-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="10417-248">K tomu je nutné upravit SimpleCalculator pro hledání v adresáři, stejně jako jeho vlastní sestavení, pro části přidáním <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="10417-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

 <span data-ttu-id="10417-249">Přidejte do projektu SimpleCalculator nový adresář s názvem `Extensions`.</span><span class="sxs-lookup"><span data-stu-id="10417-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="10417-250">Nezapomeňte ho přidat na úrovni projektu, a ne na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="10417-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="10417-251">Pak přidejte nový projekt knihovny tříd do řešení s názvem `ExtendedOperations`.</span><span class="sxs-lookup"><span data-stu-id="10417-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="10417-252">Nový projekt se zkompiluje do samostatného sestavení.</span><span class="sxs-lookup"><span data-stu-id="10417-252">The new project will compile into a separate assembly.</span></span>

 <span data-ttu-id="10417-253">Otevřete Návrhář vlastností projektu pro projekt ExtendedOperations a klikněte na kartu **kompilovat** nebo **sestavit** . Změňte **výstupní cestu sestavení** nebo **výstupní cestu** tak, aby odkazovaly na adresář rozšíření v projektu SimpleCalculator. Adresář (.. \SimpleCalculator\Extensions\\).</span><span class="sxs-lookup"><span data-stu-id="10417-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>

 <span data-ttu-id="10417-254">V Module1. vb nebo Program.cs přidejte následující řádek do konstruktoru `Program`:</span><span class="sxs-lookup"><span data-stu-id="10417-254">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 <span data-ttu-id="10417-255">Nahraďte příklad cesty cestou k adresáři rozšíření.</span><span class="sxs-lookup"><span data-stu-id="10417-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="10417-256">(Tato absolutní cesta je určena pouze pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="10417-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="10417-257">V produkční aplikaci byste použili relativní cestu.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> nyní přidá jakékoli části, které se nacházejí v jakýchkoli sestaveních v adresáři rozšíření, do kontejneru kompozice.</span><span class="sxs-lookup"><span data-stu-id="10417-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

 <span data-ttu-id="10417-258">V projektu ExtendedOperations přidejte odkazy na SimpleCalculator a System. ComponentModel. kompozici.</span><span class="sxs-lookup"><span data-stu-id="10417-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="10417-259">V souboru třídy ExtendedOperations přidejte `Imports` nebo příkaz `using` pro System. ComponentModel. kompozici.</span><span class="sxs-lookup"><span data-stu-id="10417-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="10417-260">V Visual Basic také přidejte příkaz `Imports` pro SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="10417-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="10417-261">Pak přidejte následující třídu do souboru třídy ExtendedOperations:</span><span class="sxs-lookup"><span data-stu-id="10417-261">Then add the following class to the ExtendedOperations class file:</span></span>

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

 <span data-ttu-id="10417-262">Všimněte si, že aby se kontrakt shodoval, musí mít atribut <xref:System.ComponentModel.Composition.ExportAttribute> stejný typ jako <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="10417-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

 <span data-ttu-id="10417-263">Zkompilujte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="10417-263">Compile and run the project.</span></span> <span data-ttu-id="10417-264">Otestujte nové rozhraní mod (%) podnikatel.</span><span class="sxs-lookup"><span data-stu-id="10417-264">Test the new Mod (%) operator.</span></span>

<a name="conclusion"></a>
## <a name="conclusion"></a><span data-ttu-id="10417-265">Závěr</span><span class="sxs-lookup"><span data-stu-id="10417-265">Conclusion</span></span>
 <span data-ttu-id="10417-266">Toto téma se zabývá základními koncepty rozhraní MEF.</span><span class="sxs-lookup"><span data-stu-id="10417-266">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="10417-267">Části, katalogy a kontejner kompozice</span><span class="sxs-lookup"><span data-stu-id="10417-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="10417-268">Části a kontejner skládání jsou základní stavební kameny aplikace MEF.</span><span class="sxs-lookup"><span data-stu-id="10417-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="10417-269">Součást je libovolný objekt, který importuje nebo exportuje hodnotu, a to až do a včetně samotného.</span><span class="sxs-lookup"><span data-stu-id="10417-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="10417-270">Katalog poskytuje kolekci částí z konkrétního zdroje.</span><span class="sxs-lookup"><span data-stu-id="10417-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="10417-271">Kontejner kompozice používá části poskytované katalogem k provedení složení, vazby importů do exportů.</span><span class="sxs-lookup"><span data-stu-id="10417-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="10417-272">Importy a exporty</span><span class="sxs-lookup"><span data-stu-id="10417-272">Imports and exports</span></span>

     <span data-ttu-id="10417-273">Importy a exporty představují způsob, jakým komponenty komunikují.</span><span class="sxs-lookup"><span data-stu-id="10417-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="10417-274">V případě importu Tato součást Určuje potřebu konkrétní hodnoty nebo objektu a s exportem určuje dostupnost hodnoty.</span><span class="sxs-lookup"><span data-stu-id="10417-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="10417-275">Každý import se shoduje se seznamem exportů podle jejich smlouvy.</span><span class="sxs-lookup"><span data-stu-id="10417-275">Each import is matched with a list of exports by way of its contract.</span></span>

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a><span data-ttu-id="10417-276">Kde se mám hned vrátit?</span><span class="sxs-lookup"><span data-stu-id="10417-276">Where Do I Go Now?</span></span>
 <span data-ttu-id="10417-277">Úplný kód pro tento příklad si můžete stáhnout v [ukázce SimpleCalculator](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="10417-277">To download the complete code for this example, see the [SimpleCalculator sample](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

 <span data-ttu-id="10417-278">Další informace a příklady kódu naleznete v tématu [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span><span class="sxs-lookup"><span data-stu-id="10417-278">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="10417-279">Seznam typů MEF naleznete v oboru názvů <xref:System.ComponentModel.Composition?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10417-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
