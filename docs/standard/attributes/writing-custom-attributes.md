---
title: Zápis vlastních atributů
description: Navrhněte vlastní atributy v rozhraní .NET. Vlastní atributy jsou v podstatě třídy odvozené přímo nebo nepřímo z atributu System. Attribute.
ms.date: 07/17/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
ms.openlocfilehash: 3cae8de9b76aa9953b21ad2e23ad003e97555aa9
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768479"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="29a93-104">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="29a93-104">Writing Custom Attributes</span></span>
<span data-ttu-id="29a93-105">Chcete-li navrhnout vlastní atributy, nemusíte vytvářet hlavní spoustu nových konceptů.</span><span class="sxs-lookup"><span data-stu-id="29a93-105">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="29a93-106">Pokud jste obeznámeni s objektově orientovaným programováním a víte, jak navrhovat třídy, již máte většinu potřebných znalostí.</span><span class="sxs-lookup"><span data-stu-id="29a93-106">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="29a93-107">Vlastní atributy jsou v podstatě tradiční třídy, které jsou odvozeny přímo nebo nepřímo z <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="29a93-107">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="29a93-108">Stejně jako tradiční třídy obsahují vlastní atributy metody, které ukládají a načítají data.</span><span class="sxs-lookup"><span data-stu-id="29a93-108">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="29a93-109">Hlavní kroky pro správné navrhování vlastních tříd atributů jsou následující:</span><span class="sxs-lookup"><span data-stu-id="29a93-109">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="29a93-110">Použití AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="29a93-110">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="29a93-111">Deklarace třídy atributů</span><span class="sxs-lookup"><span data-stu-id="29a93-111">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="29a93-112">Deklarace konstruktorů</span><span class="sxs-lookup"><span data-stu-id="29a93-112">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="29a93-113">Deklarace vlastností</span><span class="sxs-lookup"><span data-stu-id="29a93-113">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="29a93-114">Tato část popisuje každý z těchto kroků a končí [příkladem vlastního atributu](#custom-attribute-example).</span><span class="sxs-lookup"><span data-stu-id="29a93-114">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="29a93-115">Použití AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="29a93-115">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="29a93-116">Deklarace vlastního atributu začíná na <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> , který definuje některé klíčové charakteristiky vaší třídy atributů.</span><span class="sxs-lookup"><span data-stu-id="29a93-116">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="29a93-117">Můžete například určit, zda může být atribut děděn jinými třídami nebo určit, na které prvky lze atribut použít.</span><span class="sxs-lookup"><span data-stu-id="29a93-117">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="29a93-118">Následující fragment kódu ukazuje, jak použít <xref:System.AttributeUsageAttribute> .</span><span class="sxs-lookup"><span data-stu-id="29a93-118">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="29a93-119"><xref:System.AttributeUsageAttribute>Má tři členy, které jsou důležité pro vytváření vlastních atributů: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property)a [AllowMultiple](#allowmultiple-property).</span><span class="sxs-lookup"><span data-stu-id="29a93-119">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="29a93-120">Člen AttributeTargets</span><span class="sxs-lookup"><span data-stu-id="29a93-120">AttributeTargets Member</span></span>  
 <span data-ttu-id="29a93-121">V předchozím příkladu <xref:System.AttributeTargets.All?displayProperty=nameWithType> je určena, což značí, že tento atribut lze použít pro všechny prvky programu.</span><span class="sxs-lookup"><span data-stu-id="29a93-121">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="29a93-122">Alternativně můžete určit <xref:System.AttributeTargets.Class?displayProperty=nameWithType> , že váš atribut lze použít pouze pro třídu, nebo <xref:System.AttributeTargets.Method?displayProperty=nameWithType> , což značí, že váš atribut lze použít pouze pro metodu.</span><span class="sxs-lookup"><span data-stu-id="29a93-122">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="29a93-123">V tomto způsobu lze pomocí vlastního atributu označit všechny prvky programu jako popis.</span><span class="sxs-lookup"><span data-stu-id="29a93-123">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="29a93-124">Můžete také předat více <xref:System.AttributeTargets> hodnot.</span><span class="sxs-lookup"><span data-stu-id="29a93-124">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="29a93-125">Následující fragment kódu určuje, že vlastní atribut lze použít pro libovolnou třídu nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="29a93-125">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="29a93-126">Zděděná vlastnost</span><span class="sxs-lookup"><span data-stu-id="29a93-126">Inherited Property</span></span>  
 <span data-ttu-id="29a93-127"><xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType>Vlastnost označuje, zda lze atribut dědit pomocí tříd, které jsou odvozeny z tříd, pro které je použit atribut.</span><span class="sxs-lookup"><span data-stu-id="29a93-127">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="29a93-128">Tato vlastnost používá buď `true` (výchozí), nebo `false` příznak.</span><span class="sxs-lookup"><span data-stu-id="29a93-128">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="29a93-129">V následujícím příkladu `MyAttribute` má výchozí <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu `true` , zatímco `YourAttribute` má <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu `false` .</span><span class="sxs-lookup"><span data-stu-id="29a93-129">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="29a93-130">Tyto dva atributy jsou následně aplikovány na metodu v základní třídě `MyClass` .</span><span class="sxs-lookup"><span data-stu-id="29a93-130">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="29a93-131">Nakonec `YourClass` je třída zděděna ze základní třídy `MyClass` .</span><span class="sxs-lookup"><span data-stu-id="29a93-131">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="29a93-132">Metoda `MyMethod` ukazuje `MyAttribute` , ale ne `YourAttribute` .</span><span class="sxs-lookup"><span data-stu-id="29a93-132">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="29a93-133">AllowMultiple – vlastnost</span><span class="sxs-lookup"><span data-stu-id="29a93-133">AllowMultiple Property</span></span>  
 <span data-ttu-id="29a93-134"><xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType>Vlastnost určuje, zda více instancí atributu může existovat na elementu.</span><span class="sxs-lookup"><span data-stu-id="29a93-134">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="29a93-135">Je-li nastavena na hodnotu `true` , je povolena více instancí. je-li nastavena na hodnotu `false` (výchozí možnost), je povolena pouze jedna instance.</span><span class="sxs-lookup"><span data-stu-id="29a93-135">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="29a93-136">V následujícím příkladu `MyAttribute` má výchozí <xref:System.AttributeUsageAttribute.AllowMultiple%2A> hodnotu `false` , zatímco `YourAttribute` má hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="29a93-136">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="29a93-137">Při použití více instancí těchto atributů `MyAttribute` vytvoří kompilátor chybu.</span><span class="sxs-lookup"><span data-stu-id="29a93-137">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="29a93-138">Následující příklad kódu ukazuje platné použití `YourAttribute` a neplatné použití `MyAttribute` .</span><span class="sxs-lookup"><span data-stu-id="29a93-138">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="29a93-139">Pokud je <xref:System.AttributeUsageAttribute.AllowMultiple%2A> vlastnost i <xref:System.AttributeUsageAttribute.Inherited%2A> vlastnost nastavena na hodnotu `true` , třída, která je zděděna z jiné třídy, může dědit atribut a mít v rámci stejné podřízené třídy použitu jinou instanci stejného atributu.</span><span class="sxs-lookup"><span data-stu-id="29a93-139">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="29a93-140">Pokud <xref:System.AttributeUsageAttribute.AllowMultiple%2A> je parametr nastaven na hodnotu `false` , hodnoty všech atributů v nadřazené třídě budou přepsány novými instancemi stejného atributu v podřízené třídě.</span><span class="sxs-lookup"><span data-stu-id="29a93-140">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="29a93-141">Deklarace třídy atributů</span><span class="sxs-lookup"><span data-stu-id="29a93-141">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="29a93-142">Po použití <xref:System.AttributeUsageAttribute> můžete začít definovat specifiky vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="29a93-142">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="29a93-143">Deklarace třídy atributu vypadá podobně jako deklarace tradiční třídy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="29a93-143">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="29a93-144">Tato definice atributu demonstruje následující body:</span><span class="sxs-lookup"><span data-stu-id="29a93-144">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="29a93-145">Třídy atributů musí být deklarovány jako veřejné třídy.</span><span class="sxs-lookup"><span data-stu-id="29a93-145">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="29a93-146">Podle konvence název třídy atributu končí **atributem**Word.</span><span class="sxs-lookup"><span data-stu-id="29a93-146">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="29a93-147">I když se to nevyžaduje, doporučuje se tato konvence číst.</span><span class="sxs-lookup"><span data-stu-id="29a93-147">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="29a93-148">Při použití atributu je zahrnutí atributu Word volitelné.</span><span class="sxs-lookup"><span data-stu-id="29a93-148">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="29a93-149">Všechny třídy atributů musí dědit přímo nebo nepřímo z <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="29a93-149">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="29a93-150">V Microsoft Visual Basic musí mít všechny třídy vlastního atributu <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> atribut.</span><span class="sxs-lookup"><span data-stu-id="29a93-150">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="29a93-151">Deklarace konstruktorů</span><span class="sxs-lookup"><span data-stu-id="29a93-151">Declaring Constructors</span></span>  
 <span data-ttu-id="29a93-152">Atributy jsou inicializovány s konstruktory stejným způsobem jako tradiční třídy.</span><span class="sxs-lookup"><span data-stu-id="29a93-152">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="29a93-153">Následující fragment kódu ilustruje typický konstruktor atributu.</span><span class="sxs-lookup"><span data-stu-id="29a93-153">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="29a93-154">Tento veřejný konstruktor přijímá parametr a nastavuje členskou proměnnou rovnající se její hodnotě.</span><span class="sxs-lookup"><span data-stu-id="29a93-154">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="29a93-155">Můžete přetížit konstruktor pro přizpůsobení různých kombinací hodnot.</span><span class="sxs-lookup"><span data-stu-id="29a93-155">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="29a93-156">Pokud definujete také [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) pro vlastní třídu atributu, můžete při inicializaci atributu použít kombinaci pojmenovaných a pozičních parametrů.</span><span class="sxs-lookup"><span data-stu-id="29a93-156">If you also define a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="29a93-157">Obvykle definujete všechny požadované parametry jako poziční a všechny volitelné parametry jako pojmenované.</span><span class="sxs-lookup"><span data-stu-id="29a93-157">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="29a93-158">V takovém případě nelze atribut inicializovat bez požadovaného parametru.</span><span class="sxs-lookup"><span data-stu-id="29a93-158">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="29a93-159">Všechny ostatní parametry jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="29a93-159">All other parameters are optional.</span></span> <span data-ttu-id="29a93-160">Všimněte si, že v Visual Basic konstruktory pro třídu atributu by neměly používat argument ParamArray.</span><span class="sxs-lookup"><span data-stu-id="29a93-160">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="29a93-161">Následující příklad kódu ukazuje, jak atribut, který používá předchozí konstruktor, lze použít pomocí volitelných a vyžadovaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="29a93-161">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="29a93-162">Předpokládá, že atribut má jednu požadovanou logickou hodnotu a jednu volitelnou vlastnost řetězce.</span><span class="sxs-lookup"><span data-stu-id="29a93-162">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="29a93-163">Deklarace vlastností</span><span class="sxs-lookup"><span data-stu-id="29a93-163">Declaring Properties</span></span>  
 <span data-ttu-id="29a93-164">Pokud chcete definovat pojmenovaný parametr nebo poskytnout snadný způsob, jak vrátit hodnoty uložené v atributu, deklarujte [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="29a93-164">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="29a93-165">Vlastnosti atributu by měly být deklarovány jako veřejné entity s popisem datového typu, který bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="29a93-165">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="29a93-166">Definujte proměnnou, která bude obsahovat hodnotu vlastnosti a přidružte ji k metodám **Get** a **set** .</span><span class="sxs-lookup"><span data-stu-id="29a93-166">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="29a93-167">Následující příklad kódu ukazuje, jak implementovat jednoduchou vlastnost v atributu.</span><span class="sxs-lookup"><span data-stu-id="29a93-167">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="29a93-168">Příklad vlastního atributu</span><span class="sxs-lookup"><span data-stu-id="29a93-168">Custom Attribute Example</span></span>  
 <span data-ttu-id="29a93-169">Tato část obsahuje předchozí informace a ukazuje, jak navrhnout jednoduchý atribut, který dokumentuje informace o autorovi oddílu kódu.</span><span class="sxs-lookup"><span data-stu-id="29a93-169">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="29a93-170">Atribut v tomto příkladu ukládá název a úroveň programátora a informaci o tom, zda byl kód zkontrolován.</span><span class="sxs-lookup"><span data-stu-id="29a93-170">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="29a93-171">Používá tři soukromé proměnné pro uložení skutečných hodnot k uložení.</span><span class="sxs-lookup"><span data-stu-id="29a93-171">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="29a93-172">Každá proměnná je reprezentovaná veřejnou vlastností, která získává a nastavuje hodnoty.</span><span class="sxs-lookup"><span data-stu-id="29a93-172">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="29a93-173">Nakonec je definován konstruktor se dvěma požadovanými parametry.</span><span class="sxs-lookup"><span data-stu-id="29a93-173">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="29a93-174">Tento atribut lze použít pomocí úplného názvu, `DeveloperAttribute` nebo pomocí zkráceného názvu, `Developer` v jednom z následujících způsobů.</span><span class="sxs-lookup"><span data-stu-id="29a93-174">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="29a93-175">První příklad ukazuje atribut použit pouze s požadovanými pojmenovanými parametry, zatímco druhý příklad ukazuje atribut použit s požadovaným i nepovinnými parametry.</span><span class="sxs-lookup"><span data-stu-id="29a93-175">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a93-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="29a93-176">See also</span></span>

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="29a93-177">Atributy</span><span class="sxs-lookup"><span data-stu-id="29a93-177">Attributes</span></span>](index.md)
