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
ms.openlocfilehash: 9a601ac860ac3bf81dd01980b020470d3323772f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181290"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="1de2c-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="1de2c-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="1de2c-103">Toto téma obsahuje přehled spravovaného rozhraní rozšiřitelnosti, který byl zaveden v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1de2c-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

## <a name="what-is-mef"></a><span data-ttu-id="1de2c-104">Co je MEF?</span><span class="sxs-lookup"><span data-stu-id="1de2c-104">What is MEF?</span></span>

<span data-ttu-id="1de2c-105">Spravované rozhraní rozšiřitelnosti nebo MEF je knihovna pro vytváření lehkých a rozšiřitelných aplikací.</span><span class="sxs-lookup"><span data-stu-id="1de2c-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, and extensible applications.</span></span> <span data-ttu-id="1de2c-106">Umožňuje vývojářům aplikací zjišťovat a používat rozšíření bez nutnosti konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1de2c-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="1de2c-107">Umožňuje také vývojářům rozšíření snadno zapouzdřit kód a vyhnout se křehkým pevným závislostem.</span><span class="sxs-lookup"><span data-stu-id="1de2c-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="1de2c-108">MEF umožňuje nejen rozšíření, které mají být znovu použity v rámci aplikací, ale napříč aplikacemi stejně.</span><span class="sxs-lookup"><span data-stu-id="1de2c-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

## <a name="the-problem-of-extensibility"></a><span data-ttu-id="1de2c-109">Problém rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="1de2c-109">The problem of extensibility</span></span>

<span data-ttu-id="1de2c-110">Představte si, že jste architekt emitované velké aplikace, která musí poskytovat podporu pro rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="1de2c-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="1de2c-111">Aplikace musí obsahovat potenciálně velký počet menších součástí a je zodpovědný za jejich vytváření a spouštění.</span><span class="sxs-lookup"><span data-stu-id="1de2c-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

<span data-ttu-id="1de2c-112">Nejjednodušší přístup k problému je zahrnout součásti jako zdrojový kód ve vaší aplikaci a volat je přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="1de2c-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="1de2c-113">To má řadu zjevných nevýhod.</span><span class="sxs-lookup"><span data-stu-id="1de2c-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="1de2c-114">A co je nejdůležitější, nelze přidat nové součásti bez úpravy zdrojového kódu, omezení, které může být přijatelné, například webové aplikace, ale je nefunkční v klientské aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1de2c-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="1de2c-115">Stejně problematické je, že pravděpodobně nemáte přístup ke zdrojovému kódu komponent, protože mohou být vyvinuty třetími stranami a ze stejného důvodu jim nemůžete povolit přístup k vašim.</span><span class="sxs-lookup"><span data-stu-id="1de2c-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

<span data-ttu-id="1de2c-116">O něco sofistikovanější přístup by bylo poskytnout rozšíření bodu nebo rozhraní, aby oddělení mezi aplikací a jeho součástí.</span><span class="sxs-lookup"><span data-stu-id="1de2c-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="1de2c-117">V rámci tohoto modelu můžete poskytnout rozhraní, které může implementovat součást a rozhraní API, které jí umožní interakci s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="1de2c-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="1de2c-118">To řeší problém vyžadující přístup ke zdrojovému kódu, ale stále má své vlastní potíže.</span><span class="sxs-lookup"><span data-stu-id="1de2c-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

<span data-ttu-id="1de2c-119">Vzhledem k tomu, že aplikace postrádá žádnou kapacitu pro zjišťování součástí samostatně, musí být stále explicitně sděleny, které součásti jsou k dispozici a měly by být načteny.</span><span class="sxs-lookup"><span data-stu-id="1de2c-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="1de2c-120">To se obvykle provádí explicitní registrací dostupných součástí v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="1de2c-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="1de2c-121">To znamená, že zajištění správné součásti se stane problém údržby, zejména v případě, že je koncový uživatel a nikoli vývojář, který se očekává, že aktualizace.</span><span class="sxs-lookup"><span data-stu-id="1de2c-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

<span data-ttu-id="1de2c-122">Kromě toho součásti nejsou schopny komunikovat mezi sebou, s výjimkou prostřednictvím pevně definovaných kanálů samotné aplikace.</span><span class="sxs-lookup"><span data-stu-id="1de2c-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="1de2c-123">Pokud architekt aplikace nepředpokládá potřebu konkrétní komunikace, je to obvykle nemožné.</span><span class="sxs-lookup"><span data-stu-id="1de2c-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

<span data-ttu-id="1de2c-124">Nakonec vývojáři komponent musí přijmout tvrdou závislost na tom, jaké sestavení obsahuje rozhraní, které implementují.</span><span class="sxs-lookup"><span data-stu-id="1de2c-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="1de2c-125">To ztěžuje součást, která má být použita ve více než jedné aplikaci a může také způsobit problémy při vytváření testovacího rámce pro součásti.</span><span class="sxs-lookup"><span data-stu-id="1de2c-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

## <a name="what-mef-provides"></a><span data-ttu-id="1de2c-126">Co MEF poskytuje</span><span class="sxs-lookup"><span data-stu-id="1de2c-126">What MEF provides</span></span>

<span data-ttu-id="1de2c-127">Namísto této explicitní registrace dostupných komponent, MEF poskytuje způsob, jak objevit implicitně, prostřednictvím *složení*.</span><span class="sxs-lookup"><span data-stu-id="1de2c-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="1de2c-128">Komponenta MEF, nazývaná *část*, deklarativně určuje jak své závislosti (označované jako *importy),* tak jaké možnosti (označované jako *exporty)* zpřístupňuje.</span><span class="sxs-lookup"><span data-stu-id="1de2c-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="1de2c-129">Při vytvoření součásti kompoziční motor MEF splňuje své importy s tím, co je k dispozici z jiných částí.</span><span class="sxs-lookup"><span data-stu-id="1de2c-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

<span data-ttu-id="1de2c-130">Tento přístup řeší problémy popsané v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1de2c-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="1de2c-131">Vzhledem k tomu, že součásti MEF deklarativně určují své možnosti, jsou zjistitelné za běhu, což znamená, že aplikace může využívat součásti bez pevně zakódovaných odkazů nebo křehkých konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="1de2c-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="1de2c-132">MEF umožňuje aplikacím zjišťovat a zkoumat součásti podle jejich metadat, aniž by byly konkretizovat nebo dokonce načítat jejich sestavení.</span><span class="sxs-lookup"><span data-stu-id="1de2c-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="1de2c-133">V důsledku toho není nutné pečlivě určit, kdy a jak by měla být načtena rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1de2c-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

<span data-ttu-id="1de2c-134">Kromě poskytnutých vývozů může část specifikovat své dovozy, které budou vyplněny jinými částmi.</span><span class="sxs-lookup"><span data-stu-id="1de2c-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="1de2c-135">Díky komunikaci mezi částmi je nejen možná, ale i snadná a umožňuje dobré faktoring kódu.</span><span class="sxs-lookup"><span data-stu-id="1de2c-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="1de2c-136">Například služby společné pro mnoho součástí mohou být započítány do samostatného dílu a snadno upraveny nebo nahrazeny.</span><span class="sxs-lookup"><span data-stu-id="1de2c-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

<span data-ttu-id="1de2c-137">Vzhledem k tomu, že model MEF nevyžaduje žádnou tvrdou závislost na konkrétním sestavení aplikace, umožňuje rozšíření opakovaně z aplikace do aplikace.</span><span class="sxs-lookup"><span data-stu-id="1de2c-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="1de2c-138">To také usnadňuje vývoj testovacího svazku, nezávisle na aplikaci, na testování rozšiřujících komponent.</span><span class="sxs-lookup"><span data-stu-id="1de2c-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

<span data-ttu-id="1de2c-139">Rozšiřitelná aplikace napsaná pomocí MEF deklaruje import, který lze vyplnit komponenty rozšíření a může také deklarovat exporty za účelem vystavení aplikačních služeb rozšířením.</span><span class="sxs-lookup"><span data-stu-id="1de2c-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="1de2c-140">Každá komponenta rozšíření deklaruje export a může také deklarovat importy.</span><span class="sxs-lookup"><span data-stu-id="1de2c-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="1de2c-141">Tímto způsobem jsou komponenty rozšíření automaticky rozšiřitelné.</span><span class="sxs-lookup"><span data-stu-id="1de2c-141">In this way, extension components themselves are automatically extensible.</span></span>

## <a name="where-mef-is-available"></a><span data-ttu-id="1de2c-142">Kde je MEF k dispozici</span><span class="sxs-lookup"><span data-stu-id="1de2c-142">Where MEF is available</span></span>

<span data-ttu-id="1de2c-143">MEF je nedílnou součástí rozhraní .NET Framework 4 a je k dispozici všude, kde se používá rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1de2c-143">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="1de2c-144">Mef můžete použít v klientských aplikacích, ať už používají Windows Forms, WPF nebo jakoukoli jinou technologii nebo v serverových aplikacích, které používají ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1de2c-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

## <a name="mef-and-maf"></a><span data-ttu-id="1de2c-145">MEF a MAF</span><span class="sxs-lookup"><span data-stu-id="1de2c-145">MEF and MAF</span></span>

<span data-ttu-id="1de2c-146">Předchozí verze rozhraní .NET Framework zavedly rozhraní Managed Add-in Framework (MAF), které umožňuje aplikacím izolovat a spravovat rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1de2c-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="1de2c-147">Zaměření MAF je o něco vyšší úroveň než MEF, se zaměřením na rozšíření izolace a montáž zatížení a vykládky, zatímco MEF se zaměřuje na zjistitelnost, rozšiřitelnost a přenositelnost.</span><span class="sxs-lookup"><span data-stu-id="1de2c-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="1de2c-148">Tyto dva rámce hladce spolupracují a jedna aplikace může využít obojí.</span><span class="sxs-lookup"><span data-stu-id="1de2c-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="1de2c-149">SimpleCalculator: Ukázková aplikace</span><span class="sxs-lookup"><span data-stu-id="1de2c-149">SimpleCalculator: An example application</span></span>

<span data-ttu-id="1de2c-150">Nejjednodušší způsob, jak zjistit, co MEF může udělat, je vytvořit jednoduchou aplikaci MEF.</span><span class="sxs-lookup"><span data-stu-id="1de2c-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="1de2c-151">V tomto příkladu vytvoříte velmi jednoduchou kalkulačku s názvem SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="1de2c-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="1de2c-152">Cílem SimpleCalculator je vytvořit konzolovou aplikaci, která přijímá základní aritmetické příkazy ve tvaru "5+3" nebo "6-2" a vrací správné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1de2c-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="1de2c-153">Pomocí MEF budete moci přidat nové operátory beze změny kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="1de2c-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="1de2c-154">Chcete-li stáhnout úplný kód pro tento příklad, naleznete [simplecalculator ukázka (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span><span class="sxs-lookup"><span data-stu-id="1de2c-154">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

> [!NOTE]
> <span data-ttu-id="1de2c-155">Účelem SimpleCalculator je demonstrovat koncepty a syntaxe MEF, spíše než nutně poskytnout realistický scénář pro jeho použití.</span><span class="sxs-lookup"><span data-stu-id="1de2c-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="1de2c-156">Mnoho aplikací, které by nejvíce těžit z výkonu MEF jsou složitější než SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="1de2c-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="1de2c-157">Podrobnější příklady najdete v tématu [spravované rozšiřitelnost i framework](https://github.com/MicrosoftArchive/mef) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="1de2c-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="1de2c-158">Chcete-li začít, vytvořte v sadě Visual `SimpleCalculator`Studio nový projekt konzolové aplikace a pojmenujte jej .</span><span class="sxs-lookup"><span data-stu-id="1de2c-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="1de2c-159">Přidejte odkaz `System.ComponentModel.Composition` na sestavení, kde mef sídlí.</span><span class="sxs-lookup"><span data-stu-id="1de2c-159">Add a reference to the `System.ComponentModel.Composition` assembly, where MEF resides.</span></span>

- <span data-ttu-id="1de2c-160">Otevřete *modul1.vb* nebo `Imports` `using` *Program.cs* `System.ComponentModel.Composition` a `System.ComponentModel.Composition.Hosting`přidejte nebo příkazy pro a .</span><span class="sxs-lookup"><span data-stu-id="1de2c-160">Open *Module1.vb* or *Program.cs* and add `Imports` or `using` statements for `System.ComponentModel.Composition` and `System.ComponentModel.Composition.Hosting`.</span></span> <span data-ttu-id="1de2c-161">Tyto dva obory názvů obsahují typy MEF, které budete potřebovat k vývoji rozšiřitelné aplikace.</span><span class="sxs-lookup"><span data-stu-id="1de2c-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="1de2c-162">Pokud používáte Visual Basic, `Public` přidejte klíčové slovo na `Module1` řádek, který deklaruje modul.</span><span class="sxs-lookup"><span data-stu-id="1de2c-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="1de2c-163">Kontejner složení a katalogy</span><span class="sxs-lookup"><span data-stu-id="1de2c-163">Composition container and catalogs</span></span>

<span data-ttu-id="1de2c-164">Jádrem modelu složení MEF je *kompozice kontejneru*, který obsahuje všechny díly k dispozici a provádí složení.</span><span class="sxs-lookup"><span data-stu-id="1de2c-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="1de2c-165">Složení je sladění dovozu s vývozem.</span><span class="sxs-lookup"><span data-stu-id="1de2c-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="1de2c-166">Nejběžnější typ kontejneru složení <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>je a budete používat pro SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="1de2c-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="1de2c-167">Pokud používáte Visual Basic, přidejte `Program` veřejnou třídu s názvem v *Module1.vb*.</span><span class="sxs-lookup"><span data-stu-id="1de2c-167">If you're using Visual Basic, add a public class named `Program` in *Module1.vb*.</span></span>

<span data-ttu-id="1de2c-168">Přidejte následující řádek `Program` do třídy v *Module1.vb* nebo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="1de2c-168">Add the following line to the `Program` class in *Module1.vb* or *Program.cs*:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="1de2c-169">Aby bylo možné zjistit části, které má k dispozici, kontejnery složení využívá *katalogu*.</span><span class="sxs-lookup"><span data-stu-id="1de2c-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="1de2c-170">Katalog je objekt, který zpřístupňuje součásti zjištěné z některého zdroje.</span><span class="sxs-lookup"><span data-stu-id="1de2c-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="1de2c-171">MEF poskytuje katalogy ke zjišťování částí z poskytnutého typu, sestavení nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="1de2c-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="1de2c-172">Vývojáři aplikací mohou snadno vytvářet nové katalogy a zjišťovat součásti z jiných zdrojů, například z webové služby.</span><span class="sxs-lookup"><span data-stu-id="1de2c-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="1de2c-173">Přidejte do třídy `Program` následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="1de2c-173">Add the following constructor to the `Program` class:</span></span>

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

<span data-ttu-id="1de2c-174">Volání říká <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> kompozice kontejneru sestavit určitou sadu částí, v tomto `Program`případě aktuální instance .</span><span class="sxs-lookup"><span data-stu-id="1de2c-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="1de2c-175">V tomto okamžiku se však `Program` nic nestane, protože nemá žádný dovoz k vyplnění.</span><span class="sxs-lookup"><span data-stu-id="1de2c-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="1de2c-176">Importy a exporty s atributy</span><span class="sxs-lookup"><span data-stu-id="1de2c-176">Imports and Exports with attributes</span></span>

<span data-ttu-id="1de2c-177">Nejprve máte `Program` import kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="1de2c-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="1de2c-178">To umožňuje oddělení uživatelského rozhraní obavy, jako je například vstup konzoly a výstup, který bude přecházet do `Program`, z logiky kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="1de2c-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

<span data-ttu-id="1de2c-179">Do `Program` třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="1de2c-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

<span data-ttu-id="1de2c-180">Všimněte si, `calculator` že deklarace objektu není neobvyklé, <xref:System.ComponentModel.Composition.ImportAttribute> ale že je zdoben atributem.</span><span class="sxs-lookup"><span data-stu-id="1de2c-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="1de2c-181">Tento atribut deklaruje něco jako import; to znamená, že bude vyplněna modul složení při skládání objektu.</span><span class="sxs-lookup"><span data-stu-id="1de2c-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

<span data-ttu-id="1de2c-182">Každý import má *smlouvu*, která určuje, s jakým exportem bude spárován.</span><span class="sxs-lookup"><span data-stu-id="1de2c-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="1de2c-183">Kontrakt může být explicitně zadaný řetězec, nebo může být automaticky generován MEF z `ICalculator`daného typu, v tomto případě rozhraní .</span><span class="sxs-lookup"><span data-stu-id="1de2c-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="1de2c-184">Každý export deklarovaný s odpovídající smlouvou splní tento import.</span><span class="sxs-lookup"><span data-stu-id="1de2c-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="1de2c-185">Všimněte si, že `calculator` zatímco typ `ICalculator`objektu je ve skutečnosti , to není nutné.</span><span class="sxs-lookup"><span data-stu-id="1de2c-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="1de2c-186">Smlouva je nezávislá na typu importujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="1de2c-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="1de2c-187">(V tomto případě můžete vynechat `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="1de2c-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="1de2c-188">MEF automaticky předpokládá, že smlouva bude založena na typu importu, pokud ji výslovně nezadáte.)</span><span class="sxs-lookup"><span data-stu-id="1de2c-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

<span data-ttu-id="1de2c-189">Přidejte toto velmi jednoduché `SimpleCalculator` rozhraní do modulu nebo oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="1de2c-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

<span data-ttu-id="1de2c-190">Nyní, když `ICalculator`jste definovali , budete potřebovat třídu, která ji implementuje.</span><span class="sxs-lookup"><span data-stu-id="1de2c-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="1de2c-191">Do modulu nebo `SimpleCalculator` oboru názvů přidejte následující třídu:</span><span class="sxs-lookup"><span data-stu-id="1de2c-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

<span data-ttu-id="1de2c-192">Zde je export, který bude `Program`odpovídat importu v .</span><span class="sxs-lookup"><span data-stu-id="1de2c-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="1de2c-193">Aby export odpovídal importu, musí mít export stejnou smlouvu.</span><span class="sxs-lookup"><span data-stu-id="1de2c-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="1de2c-194">Vývoz na základě smlouvy `typeof(MySimpleCalculator)` založené na by vytvořil nesoulad a dovoz by nebyl vyplněn; smlouva musí přesně odpovídat.</span><span class="sxs-lookup"><span data-stu-id="1de2c-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

<span data-ttu-id="1de2c-195">Vzhledem k tomu, že kontejner složení bude naplněn `MySimpleCalculator` všemi díly dostupnými v této sestavě, bude díl k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1de2c-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="1de2c-196">Když konstruktor `Program` pro provádí `Program` složení na objekt, jeho `MySimpleCalculator` import bude vyplněn objektem, který bude vytvořen pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="1de2c-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

<span data-ttu-id="1de2c-197">Vrstva uživatelského`Program`rozhraní ( ) nemusí vědět nic jiného.</span><span class="sxs-lookup"><span data-stu-id="1de2c-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="1de2c-198">Proto můžete vyplnit zbytek logiky uživatelského `Main` rozhraní v metodě.</span><span class="sxs-lookup"><span data-stu-id="1de2c-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

<span data-ttu-id="1de2c-199">Do metody `Main` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="1de2c-199">Add the following code to the `Main` method:</span></span>

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
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="1de2c-200">Tento kód jednoduše přečte řádek `Calculate` vstupu `ICalculator` a volá funkci na výsledek, který zapíše zpět do konzoly.</span><span class="sxs-lookup"><span data-stu-id="1de2c-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="1de2c-201">To je veškerý kód, `Program`který potřebujete v .</span><span class="sxs-lookup"><span data-stu-id="1de2c-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="1de2c-202">Všechny ostatní práce se budou odehrávat v částech.</span><span class="sxs-lookup"><span data-stu-id="1de2c-202">All the rest of the work will happen in the parts.</span></span>

## <a name="further-imports-and-importmany"></a><span data-ttu-id="1de2c-203">Další dovozy a importMnoho</span><span class="sxs-lookup"><span data-stu-id="1de2c-203">Further Imports and ImportMany</span></span>

<span data-ttu-id="1de2c-204">Aby SimpleCalculator být rozšiřitelný, je třeba importovat seznam operací.</span><span class="sxs-lookup"><span data-stu-id="1de2c-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="1de2c-205">Běžný <xref:System.ComponentModel.Composition.ImportAttribute> atribut je vyplněn jedním <xref:System.ComponentModel.Composition.ExportAttribute>a pouze jedním .</span><span class="sxs-lookup"><span data-stu-id="1de2c-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="1de2c-206">Pokud je k dispozici více než jeden, modul složení vytvoří chybu.</span><span class="sxs-lookup"><span data-stu-id="1de2c-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="1de2c-207">Chcete-li vytvořit import, který lze vyplnit libovolným <xref:System.ComponentModel.Composition.ImportManyAttribute> počtem exportů, můžete použít atribut.</span><span class="sxs-lookup"><span data-stu-id="1de2c-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

<span data-ttu-id="1de2c-208">Přidejte do `MySimpleCalculator` třídy následující vlastnost operations:</span><span class="sxs-lookup"><span data-stu-id="1de2c-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<span data-ttu-id="1de2c-209"><xref:System.Lazy%602>je druh poskytnutý MEF pro uložení nepřímých odkazů na vývoz.</span><span class="sxs-lookup"><span data-stu-id="1de2c-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="1de2c-210">Zde kromě samotného exportovaného objektu získáte také *metadata exportu*nebo informace popisující exportovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="1de2c-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="1de2c-211">Každý <xref:System.Lazy%602> obsahuje `IOperation` objekt představující skutečnou operaci `IOperationData` a objekt představující jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="1de2c-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

<span data-ttu-id="1de2c-212">Do modulu nebo `SimpleCalculator` oboru názvů přidejte následující jednoduchá rozhraní:</span><span class="sxs-lookup"><span data-stu-id="1de2c-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
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

 <span data-ttu-id="1de2c-213">V tomto případě metadata pro každou operaci je symbol, který představuje \*tuto operaci, například +, -, , a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1de2c-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="1de2c-214">Chcete-li zpřístupnit operaci sčítání, přidejte do `SimpleCalculator` modulu nebo oboru názvů následující třídu:</span><span class="sxs-lookup"><span data-stu-id="1de2c-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

<span data-ttu-id="1de2c-215">Atribut <xref:System.ComponentModel.Composition.ExportAttribute> funguje stejně jako dříve.</span><span class="sxs-lookup"><span data-stu-id="1de2c-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="1de2c-216">Atribut <xref:System.ComponentModel.Composition.ExportMetadataAttribute> připojí metadata ve formě dvojice název-hodnota k tomuto exportu.</span><span class="sxs-lookup"><span data-stu-id="1de2c-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="1de2c-217">Zatímco `Add` třída implementuje `IOperation`, třída, která implementuje `IOperationData` není explicitně definována.</span><span class="sxs-lookup"><span data-stu-id="1de2c-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="1de2c-218">Místo toho je třída implicitně vytvořena MEF s vlastnostmi založenými na názvech poskytnutých metadat.</span><span class="sxs-lookup"><span data-stu-id="1de2c-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="1de2c-219">(Toto je jeden z několika způsobů, jak získat přístup k metadatům v MEF.)</span><span class="sxs-lookup"><span data-stu-id="1de2c-219">(This is one of several ways to access metadata in MEF.)</span></span>

<span data-ttu-id="1de2c-220">Složení v MEF je *rekurzivní*.</span><span class="sxs-lookup"><span data-stu-id="1de2c-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="1de2c-221">Explicitně jste `Program` složili objekt, `ICalculator` který importoval, `MySimpleCalculator`který se ukázal jako typ .</span><span class="sxs-lookup"><span data-stu-id="1de2c-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="1de2c-222">`MySimpleCalculator`, na druhé straně importuje kolekci `IOperation` objektů a `MySimpleCalculator` tento import bude vyplněn při vytvoření, ve stejnou dobu jako importy . `Program`</span><span class="sxs-lookup"><span data-stu-id="1de2c-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="1de2c-223">Pokud `Add` třída deklarovala další import, muselo by být také vyplněno a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1de2c-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="1de2c-224">Jakýkoli import, který zůstal nevyplněný, má za následek chybu složení.</span><span class="sxs-lookup"><span data-stu-id="1de2c-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="1de2c-225">(Je však možné deklarovat importy jako volitelné nebo jim přiřadit výchozí hodnoty.)</span><span class="sxs-lookup"><span data-stu-id="1de2c-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

## <a name="calculator-logic"></a><span data-ttu-id="1de2c-226">Kalkulačka Logika</span><span class="sxs-lookup"><span data-stu-id="1de2c-226">Calculator Logic</span></span>

<span data-ttu-id="1de2c-227">S těmito částmi na místě, vše, co zbývá, je kalkulačka logiku sám.</span><span class="sxs-lookup"><span data-stu-id="1de2c-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="1de2c-228">Přidejte následující kód `MySimpleCalculator` do třídy k implementaci `Calculate` metody:</span><span class="sxs-lookup"><span data-stu-id="1de2c-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
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
public String Calculate(string input)
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

<span data-ttu-id="1de2c-229">Počáteční kroky analyzovat vstupní řetězec do levé a pravé operandy a znak operátoru.</span><span class="sxs-lookup"><span data-stu-id="1de2c-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="1de2c-230">Ve `foreach` smyčce je zkoumán každý člen `operations` kolekce.</span><span class="sxs-lookup"><span data-stu-id="1de2c-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="1de2c-231">Tyto objekty <xref:System.Lazy%602>jsou typu a jejich hodnoty metadat a exportovaný <xref:System.Lazy%602.Metadata%2A> objekt <xref:System.Lazy%601.Value%2A> lze přistupovat s vlastností a vlastností.</span><span class="sxs-lookup"><span data-stu-id="1de2c-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="1de2c-232">V tomto případě `Symbol` pokud je `IOperationData` vlastnost objektu zjištěno, že se `Operate` shoduje, `IOperation` kalkulačka volá metodu objektu a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="1de2c-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

<span data-ttu-id="1de2c-233">K dokončení kalkulačky potřebujete také pomocnou metodu, která vrátí pozici prvního nečíselného znaku v řetězci.</span><span class="sxs-lookup"><span data-stu-id="1de2c-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="1de2c-234">Do třídy přidejte `MySimpleCalculator` následující pomocnou metodu:</span><span class="sxs-lookup"><span data-stu-id="1de2c-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

<span data-ttu-id="1de2c-235">Nyní byste měli být schopni zkompilovat a spustit projekt.</span><span class="sxs-lookup"><span data-stu-id="1de2c-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="1de2c-236">V jazyce Visual Basic zkontrolujte, zda jste přidali `Public` klíčové slovo do aplikace `Module1`.</span><span class="sxs-lookup"><span data-stu-id="1de2c-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="1de2c-237">V okně konzoly zadejte operaci sčítání, například "5+3", a kalkulačka vrátí výsledky.</span><span class="sxs-lookup"><span data-stu-id="1de2c-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="1de2c-238">Jakýkoli jiný operátor má za následek "Operace nebyla nalezena!"</span><span class="sxs-lookup"><span data-stu-id="1de2c-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="1de2c-239">zpráva.</span><span class="sxs-lookup"><span data-stu-id="1de2c-239">message.</span></span>

## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="1de2c-240">Rozšíření SimpleCalculator pomocí nové třídy</span><span class="sxs-lookup"><span data-stu-id="1de2c-240">Extending SimpleCalculator using a new class</span></span>

<span data-ttu-id="1de2c-241">Nyní, když kalkulačka funguje, přidání nové operace je snadné.</span><span class="sxs-lookup"><span data-stu-id="1de2c-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="1de2c-242">Do modulu nebo `SimpleCalculator` oboru názvů přidejte následující třídu:</span><span class="sxs-lookup"><span data-stu-id="1de2c-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

<span data-ttu-id="1de2c-243">Zkompilujte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="1de2c-243">Compile and run the project.</span></span> <span data-ttu-id="1de2c-244">Zadejte operaci odčítání, například "5-3".</span><span class="sxs-lookup"><span data-stu-id="1de2c-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="1de2c-245">Kalkulačka nyní podporuje odčítání, stejně jako sčítání.</span><span class="sxs-lookup"><span data-stu-id="1de2c-245">The calculator now supports subtraction as well as addition.</span></span>

## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="1de2c-246">Rozšíření SimpleCalculator pomocí nového sestavení</span><span class="sxs-lookup"><span data-stu-id="1de2c-246">Extending SimpleCalculator using a new assembly</span></span>

<span data-ttu-id="1de2c-247">Přidání tříd do zdrojového kódu je dost jednoduché, ale MEF poskytuje možnost podívat se mimo vlastní zdroj aplikace pro součásti.</span><span class="sxs-lookup"><span data-stu-id="1de2c-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="1de2c-248">Chcete-li to demonstrovat, budete muset upravit SimpleCalculator pro vyhledávání v adresáři, <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>stejně jako jeho vlastní sestavení, pro díly, přidáním .</span><span class="sxs-lookup"><span data-stu-id="1de2c-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

<span data-ttu-id="1de2c-249">Přidejte nový `Extensions` adresář s názvem SimpleCalculator projektu.</span><span class="sxs-lookup"><span data-stu-id="1de2c-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="1de2c-250">Nezapomeňte jej přidat na úrovni projektu a ne na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="1de2c-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="1de2c-251">Potom přidejte do řešení nový projekt `ExtendedOperations`knihovny tříd s názvem .</span><span class="sxs-lookup"><span data-stu-id="1de2c-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="1de2c-252">Nový projekt se zkompiluje do samostatného sestavení.</span><span class="sxs-lookup"><span data-stu-id="1de2c-252">The new project will compile into a separate assembly.</span></span>

<span data-ttu-id="1de2c-253">Otevřete Návrhář vlastností projektu pro projekt ExtendedOperations a klepněte na **Output path** kartu **Kompilace** nebo **Sestavení.** **Build output path** \* \SimpleCalculator\Extensions\\*).</span><span class="sxs-lookup"><span data-stu-id="1de2c-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (*..\SimpleCalculator\Extensions\\*).</span></span>

 <span data-ttu-id="1de2c-254">V *modulu 1.vb* nebo *Program.cs*přidejte do konstruktoru `Program` následující řádek:</span><span class="sxs-lookup"><span data-stu-id="1de2c-254">In *Module1.vb* or *Program.cs*, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

<span data-ttu-id="1de2c-255">Nahraďte ukázkovou cestu cestou do adresáře Rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1de2c-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="1de2c-256">(Tato absolutní cesta je pouze pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="1de2c-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="1de2c-257">V produkční aplikaci byste použili relativní cestu.) Nyní <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> přidá všechny součásti nalezené v všech sestaveních v adresáři Rozšíření do kontejneru kompozice.</span><span class="sxs-lookup"><span data-stu-id="1de2c-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

<span data-ttu-id="1de2c-258">V projektu ExtendedOperations přidejte odkazy na SimpleCalculator a System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="1de2c-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="1de2c-259">V souboru třídy ExtendedOperations přidejte příkaz nebo `Imports` `using` příkaz pro System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="1de2c-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="1de2c-260">V jazyce Visual `Imports` Basic také přidejte příkaz pro SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="1de2c-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="1de2c-261">Potom přidejte do souboru třídy ExtendedOperations následující třídu:</span><span class="sxs-lookup"><span data-stu-id="1de2c-261">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

<span data-ttu-id="1de2c-262">Všimněte si, že aby se <xref:System.ComponentModel.Composition.ExportAttribute> smlouva shodovala, musí <xref:System.ComponentModel.Composition.ImportAttribute>mít atribut stejný typ jako .</span><span class="sxs-lookup"><span data-stu-id="1de2c-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

<span data-ttu-id="1de2c-263">Zkompilujte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="1de2c-263">Compile and run the project.</span></span> <span data-ttu-id="1de2c-264">Otestujte nový mod (%) Operátor.</span><span class="sxs-lookup"><span data-stu-id="1de2c-264">Test the new Mod (%) operator.</span></span>

## <a name="conclusion"></a><span data-ttu-id="1de2c-265">Závěr</span><span class="sxs-lookup"><span data-stu-id="1de2c-265">Conclusion</span></span>

<span data-ttu-id="1de2c-266">Toto téma se týkalo základních pojmů MEF.</span><span class="sxs-lookup"><span data-stu-id="1de2c-266">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="1de2c-267">Části, katalogy a kontejner složení</span><span class="sxs-lookup"><span data-stu-id="1de2c-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="1de2c-268">Díly a kontejner složení jsou základními stavebními kameny aplikace MEF.</span><span class="sxs-lookup"><span data-stu-id="1de2c-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="1de2c-269">Součást je libovolný objekt, který importuje nebo exportuje hodnotu až do sebe sama včetně.</span><span class="sxs-lookup"><span data-stu-id="1de2c-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="1de2c-270">Katalog poskytuje kolekci částí z určitého zdroje.</span><span class="sxs-lookup"><span data-stu-id="1de2c-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="1de2c-271">Kontejner složení používá části poskytované katalogu k provedení složení, vazba importu k vývozu.</span><span class="sxs-lookup"><span data-stu-id="1de2c-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="1de2c-272">Dovoz a vývoz</span><span class="sxs-lookup"><span data-stu-id="1de2c-272">Imports and exports</span></span>

     <span data-ttu-id="1de2c-273">Importy a exporty jsou způsob, jakým komponenty komunikují.</span><span class="sxs-lookup"><span data-stu-id="1de2c-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="1de2c-274">Při importu komponenta určuje potřebu určité hodnoty nebo objektu a při exportu určuje dostupnost hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1de2c-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="1de2c-275">Každý import je spárován se seznamem exportů prostřednictvím své smlouvy.</span><span class="sxs-lookup"><span data-stu-id="1de2c-275">Each import is matched with a list of exports by way of its contract.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1de2c-276">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1de2c-276">Next steps</span></span>

<span data-ttu-id="1de2c-277">Chcete-li stáhnout úplný kód pro tento příklad, naleznete [simplecalculator ukázka (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span><span class="sxs-lookup"><span data-stu-id="1de2c-277">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

 <span data-ttu-id="1de2c-278">Další informace a příklady kódu naleznete [v tématu Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span><span class="sxs-lookup"><span data-stu-id="1de2c-278">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="1de2c-279">Seznam typů MEF naleznete v <xref:System.ComponentModel.Composition?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1de2c-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
