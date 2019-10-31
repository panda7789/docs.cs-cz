---
title: Zápis vlastních atributů
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
ms.openlocfilehash: 6570c6994c0f2e6571361c3eadc73b02a55f1584
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140583"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="4a147-102">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="4a147-102">Writing Custom Attributes</span></span>
<span data-ttu-id="4a147-103">Chcete-li navrhnout vlastní atributy, nemusíte vytvářet hlavní spoustu nových konceptů.</span><span class="sxs-lookup"><span data-stu-id="4a147-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="4a147-104">Pokud jste obeznámeni s objektově orientovaným programováním a víte, jak navrhovat třídy, již máte většinu potřebných znalostí.</span><span class="sxs-lookup"><span data-stu-id="4a147-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="4a147-105">Vlastní atributy jsou v podstatě tradiční třídy, které jsou odvozeny přímo nebo nepřímo z <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a147-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4a147-106">Stejně jako tradiční třídy obsahují vlastní atributy metody, které ukládají a načítají data.</span><span class="sxs-lookup"><span data-stu-id="4a147-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="4a147-107">Hlavní kroky pro správné navrhování vlastních tříd atributů jsou následující:</span><span class="sxs-lookup"><span data-stu-id="4a147-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="4a147-108">Použití AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="4a147-108">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="4a147-109">Deklarace třídy atributů</span><span class="sxs-lookup"><span data-stu-id="4a147-109">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="4a147-110">Deklarace konstruktorů</span><span class="sxs-lookup"><span data-stu-id="4a147-110">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="4a147-111">Deklarace vlastností</span><span class="sxs-lookup"><span data-stu-id="4a147-111">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="4a147-112">Tato část popisuje každý z těchto kroků a končí [příkladem vlastního atributu](#custom-attribute-example).</span><span class="sxs-lookup"><span data-stu-id="4a147-112">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="4a147-113">Použití AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="4a147-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="4a147-114">Deklarace vlastního atributu začíná na <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, která definuje některé klíčové charakteristiky vaší třídy atributů.</span><span class="sxs-lookup"><span data-stu-id="4a147-114">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="4a147-115">Můžete například určit, zda může být atribut děděn jinými třídami nebo určit, na které prvky lze atribut použít.</span><span class="sxs-lookup"><span data-stu-id="4a147-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="4a147-116">Následující fragment kódu ukazuje, jak použít <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4a147-116">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="4a147-117"><xref:System.AttributeUsageAttribute> má tři členy, které jsou důležité pro vytváření vlastních atributů: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property)a [AllowMultiple](#allowmultiple-property).</span><span class="sxs-lookup"><span data-stu-id="4a147-117">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="4a147-118">Člen AttributeTargets</span><span class="sxs-lookup"><span data-stu-id="4a147-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="4a147-119">V předchozím příkladu je zadána <xref:System.AttributeTargets.All?displayProperty=nameWithType>, což značí, že tento atribut lze použít pro všechny prvky programu.</span><span class="sxs-lookup"><span data-stu-id="4a147-119">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="4a147-120">Alternativně lze zadat <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, což znamená, že váš atribut lze použít pouze pro třídu nebo <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, což značí, že atribut lze použít pouze pro metodu.</span><span class="sxs-lookup"><span data-stu-id="4a147-120">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="4a147-121">V tomto způsobu lze pomocí vlastního atributu označit všechny prvky programu jako popis.</span><span class="sxs-lookup"><span data-stu-id="4a147-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="4a147-122">Můžete také předat více <xref:System.AttributeTargets> hodnot.</span><span class="sxs-lookup"><span data-stu-id="4a147-122">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="4a147-123">Následující fragment kódu určuje, že vlastní atribut lze použít pro libovolnou třídu nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="4a147-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="4a147-124">Zděděná vlastnost</span><span class="sxs-lookup"><span data-stu-id="4a147-124">Inherited Property</span></span>  
 <span data-ttu-id="4a147-125">Vlastnost <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> označuje, zda lze atribut dědit pomocí tříd, které jsou odvozeny z tříd, pro které je použit atribut.</span><span class="sxs-lookup"><span data-stu-id="4a147-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="4a147-126">Tato vlastnost přebírá buď `true` (výchozí), nebo příznak `false`.</span><span class="sxs-lookup"><span data-stu-id="4a147-126">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="4a147-127">V následujícím příkladu má `MyAttribute` výchozí <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu `true`, zatímco `YourAttribute` má <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="4a147-127">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="4a147-128">Tyto dva atributy jsou následně aplikovány na metodu v základní třídě `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="4a147-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="4a147-129">Nakonec `YourClass` třídy dědí ze `MyClass`základní třídy.</span><span class="sxs-lookup"><span data-stu-id="4a147-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="4a147-130">Metoda `MyMethod` zobrazuje `MyAttribute`, ale ne `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="4a147-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="4a147-131">AllowMultiple – vlastnost</span><span class="sxs-lookup"><span data-stu-id="4a147-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="4a147-132">Vlastnost <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> určuje, zda více instancí atributu může existovat na elementu.</span><span class="sxs-lookup"><span data-stu-id="4a147-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="4a147-133">Pokud je nastaveno na `true`, je povoleno více instancí; Pokud je nastavená na `false` (výchozí), je povolená jenom jedna instance.</span><span class="sxs-lookup"><span data-stu-id="4a147-133">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="4a147-134">V následujícím příkladu má `MyAttribute` výchozí hodnotu <xref:System.AttributeUsageAttribute.AllowMultiple%2A> `false`, zatímco `YourAttribute` má hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="4a147-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="4a147-135">Při použití více instancí těchto atributů `MyAttribute` vytvoří chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4a147-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="4a147-136">Následující příklad kódu ukazuje platné použití `YourAttribute` a neplatné použití `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="4a147-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="4a147-137">Je-li vlastnost <xref:System.AttributeUsageAttribute.AllowMultiple%2A> a vlastnost <xref:System.AttributeUsageAttribute.Inherited%2A> nastavena na `true`, třída, která je zděděna z jiné třídy, může dědit atribut a mít v rámci stejné podřízené třídy použitu jinou instanci stejného atributu.</span><span class="sxs-lookup"><span data-stu-id="4a147-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="4a147-138">Pokud je <xref:System.AttributeUsageAttribute.AllowMultiple%2A> nastaveno na `false`, hodnoty všech atributů v nadřazené třídě budou přepsány novými instancemi stejného atributu v podřízené třídě.</span><span class="sxs-lookup"><span data-stu-id="4a147-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="4a147-139">Deklarace třídy atributů</span><span class="sxs-lookup"><span data-stu-id="4a147-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="4a147-140">Po použití <xref:System.AttributeUsageAttribute>můžete začít definovat specifiky vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="4a147-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="4a147-141">Deklarace třídy atributu vypadá podobně jako deklarace tradiční třídy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4a147-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="4a147-142">Tato definice atributu demonstruje následující body:</span><span class="sxs-lookup"><span data-stu-id="4a147-142">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="4a147-143">Třídy atributů musí být deklarovány jako veřejné třídy.</span><span class="sxs-lookup"><span data-stu-id="4a147-143">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="4a147-144">Podle konvence název třídy atributu končí **atributem**Word.</span><span class="sxs-lookup"><span data-stu-id="4a147-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="4a147-145">I když se to nevyžaduje, doporučuje se tato konvence číst.</span><span class="sxs-lookup"><span data-stu-id="4a147-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="4a147-146">Při použití atributu je zahrnutí atributu Word volitelné.</span><span class="sxs-lookup"><span data-stu-id="4a147-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="4a147-147">Všechny třídy atributů musí dědit přímo nebo nepřímo z <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a147-147">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="4a147-148">V Microsoft Visual Basic musí mít všechny třídy vlastního atributu atribut <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a147-148">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="4a147-149">Deklarace konstruktorů</span><span class="sxs-lookup"><span data-stu-id="4a147-149">Declaring Constructors</span></span>  
 <span data-ttu-id="4a147-150">Atributy jsou inicializovány s konstruktory stejným způsobem jako tradiční třídy.</span><span class="sxs-lookup"><span data-stu-id="4a147-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="4a147-151">Následující fragment kódu ilustruje typický konstruktor atributu.</span><span class="sxs-lookup"><span data-stu-id="4a147-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="4a147-152">Tento veřejný konstruktor přijímá parametr a nastavuje členskou proměnnou rovnající se její hodnotě.</span><span class="sxs-lookup"><span data-stu-id="4a147-152">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="4a147-153">Můžete přetížit konstruktor pro přizpůsobení různých kombinací hodnot.</span><span class="sxs-lookup"><span data-stu-id="4a147-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="4a147-154">Pokud definujete také [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) pro vlastní třídu atributu, můžete při inicializaci atributu použít kombinaci pojmenovaných a pozičních parametrů.</span><span class="sxs-lookup"><span data-stu-id="4a147-154">If you also define a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="4a147-155">Obvykle definujete všechny požadované parametry jako poziční a všechny volitelné parametry jako pojmenované.</span><span class="sxs-lookup"><span data-stu-id="4a147-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="4a147-156">V takovém případě nelze atribut inicializovat bez požadovaného parametru.</span><span class="sxs-lookup"><span data-stu-id="4a147-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="4a147-157">Všechny ostatní parametry jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="4a147-157">All other parameters are optional.</span></span> <span data-ttu-id="4a147-158">Všimněte si, že v Visual Basic konstruktory pro třídu atributu by neměly používat argument ParamArray.</span><span class="sxs-lookup"><span data-stu-id="4a147-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="4a147-159">Následující příklad kódu ukazuje, jak atribut, který používá předchozí konstruktor, lze použít pomocí volitelných a vyžadovaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="4a147-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="4a147-160">Předpokládá, že atribut má jednu požadovanou logickou hodnotu a jednu volitelnou vlastnost řetězce.</span><span class="sxs-lookup"><span data-stu-id="4a147-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="4a147-161">Deklarace vlastností</span><span class="sxs-lookup"><span data-stu-id="4a147-161">Declaring Properties</span></span>  
 <span data-ttu-id="4a147-162">Pokud chcete definovat pojmenovaný parametr nebo poskytnout snadný způsob, jak vrátit hodnoty uložené v atributu, deklarujte [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="4a147-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="4a147-163">Vlastnosti atributu by měly být deklarovány jako veřejné entity s popisem datového typu, který bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="4a147-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="4a147-164">Definujte proměnnou, která bude obsahovat hodnotu vlastnosti a přidružte ji k metodám **Get** a **set** .</span><span class="sxs-lookup"><span data-stu-id="4a147-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="4a147-165">Následující příklad kódu ukazuje, jak implementovat jednoduchou vlastnost v atributu.</span><span class="sxs-lookup"><span data-stu-id="4a147-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="4a147-166">Příklad vlastního atributu</span><span class="sxs-lookup"><span data-stu-id="4a147-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="4a147-167">Tato část obsahuje předchozí informace a ukazuje, jak navrhnout jednoduchý atribut, který dokumentuje informace o autorovi oddílu kódu.</span><span class="sxs-lookup"><span data-stu-id="4a147-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="4a147-168">Atribut v tomto příkladu ukládá název a úroveň programátora a informaci o tom, zda byl kód zkontrolován.</span><span class="sxs-lookup"><span data-stu-id="4a147-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="4a147-169">Používá tři soukromé proměnné pro uložení skutečných hodnot k uložení.</span><span class="sxs-lookup"><span data-stu-id="4a147-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="4a147-170">Každá proměnná je reprezentovaná veřejnou vlastností, která získává a nastavuje hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4a147-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="4a147-171">Nakonec je definován konstruktor se dvěma požadovanými parametry.</span><span class="sxs-lookup"><span data-stu-id="4a147-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="4a147-172">Tento atribut lze použít pomocí úplného názvu, `DeveloperAttribute`nebo pomocí zkráceného názvu `Developer`, jedním z následujících způsobů.</span><span class="sxs-lookup"><span data-stu-id="4a147-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="4a147-173">První příklad ukazuje atribut použit pouze s požadovanými pojmenovanými parametry, zatímco druhý příklad ukazuje atribut použit s požadovaným i nepovinnými parametry.</span><span class="sxs-lookup"><span data-stu-id="4a147-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a147-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a147-174">See also</span></span>

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="4a147-175">Atributy</span><span class="sxs-lookup"><span data-stu-id="4a147-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
