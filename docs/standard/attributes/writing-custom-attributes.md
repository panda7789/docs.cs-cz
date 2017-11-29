---
title: "Zápis vlastních atributů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0205edba221b833625becbe6a1f2fdda2f9409a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="f9133-102">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="f9133-102">Writing Custom Attributes</span></span>
<span data-ttu-id="f9133-103">K návrhu vlastní atributy, není potřeba hlavní mnoho nových konceptů.</span><span class="sxs-lookup"><span data-stu-id="f9133-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="f9133-104">Pokud jste obeznámeni s objektově orientované programování a vědět, jak navrhnout třídy, že máte většinu potřebných znalostí.</span><span class="sxs-lookup"><span data-stu-id="f9133-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="f9133-105">Vlastní atributy jsou v podstatě tradiční třídy, které jsou odvozeny od přímo nebo nepřímo <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9133-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f9133-106">Stejně jako tradiční třídy vlastní atributy obsahují metody, které ukládají a načítají data.</span><span class="sxs-lookup"><span data-stu-id="f9133-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="f9133-107">Hlavní kroky správně návrhu vlastní atribut třídy jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f9133-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
-   [<span data-ttu-id="f9133-108">Použití AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="f9133-108">Applying the AttributeUsageAttribute</span></span>](#cpconapplyingattributeusageattribute)  
  
-   [<span data-ttu-id="f9133-109">Deklarování třídy atributů</span><span class="sxs-lookup"><span data-stu-id="f9133-109">Declaring the attribute class</span></span>](#cpcondeclaringattributeclass)  
  
-   [<span data-ttu-id="f9133-110">Deklarování konstruktorů</span><span class="sxs-lookup"><span data-stu-id="f9133-110">Declaring constructors</span></span>](#cpcondeclaringconstructors)  
  
-   [<span data-ttu-id="f9133-111">Deklarování vlastností</span><span class="sxs-lookup"><span data-stu-id="f9133-111">Declaring properties</span></span>](#cpcondeclaringproperties)  
  
 <span data-ttu-id="f9133-112">Tato část popisuje každý z těchto kroků a končí [příklad vlastní atribut](#cpconcustomattributeexample).</span><span class="sxs-lookup"><span data-stu-id="f9133-112">This section describes each of these steps and concludes with a [custom attribute example](#cpconcustomattributeexample).</span></span>  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="f9133-113">Použití AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="f9133-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="f9133-114">Vlastní atribut deklarace začíná **AttributeUsageAttribute**, která definuje některé klíčové charakteristiky vaší třídy atributů.</span><span class="sxs-lookup"><span data-stu-id="f9133-114">A custom attribute declaration begins with the **AttributeUsageAttribute**, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="f9133-115">Můžete například určit, zda vaše atribut možné zdědit jiné třídy, nebo zadejte prvky, které atribut lze použít k.</span><span class="sxs-lookup"><span data-stu-id="f9133-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="f9133-116">Následující fragment kódu ukazuje, jak používat **AttributeUsageAttribute**.</span><span class="sxs-lookup"><span data-stu-id="f9133-116">The following code fragment demonstrates how to use the **AttributeUsageAttribute**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="f9133-117"><xref:System.AttributeUsageAttribute?displayProperty=nameWithType> Má tři členy, které jsou důležité pro vytváření vlastních atributů: [AttributeTargets](#cpconwritingcustomattributesanchor1), [zděděné](#cpconwritingcustomattributesanchor2), a [AllowMultiple](#cpconwritingcustomattributesanchor3).</span><span class="sxs-lookup"><span data-stu-id="f9133-117">The <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> has three members that are important for the creation of custom attributes: [AttributeTargets](#cpconwritingcustomattributesanchor1), [Inherited](#cpconwritingcustomattributesanchor2), and [AllowMultiple](#cpconwritingcustomattributesanchor3).</span></span>  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### <a name="attributetargets-member"></a><span data-ttu-id="f9133-118">Člen AttributeTargets</span><span class="sxs-lookup"><span data-stu-id="f9133-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="f9133-119">V předchozím příkladu **AttributeTargets.All** není zadaný, označující, že tento atribut lze použít pro všechny prvky programu.</span><span class="sxs-lookup"><span data-stu-id="f9133-119">In the previous example, **AttributeTargets.All** is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="f9133-120">Alternativně můžete zadat **AttributeTargets.Class**, označující, že váš atribut lze použít pouze na třídu, nebo **AttributeTargets.Method**, označující, že můžete použít atribut pouze pro metodu.</span><span class="sxs-lookup"><span data-stu-id="f9133-120">Alternatively, you can specify **AttributeTargets.Class**, indicating that your attribute can be applied only to a class, or **AttributeTargets.Method**, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="f9133-121">Všechny elementy program může být označen pro popis vlastní atribut tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="f9133-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="f9133-122">Můžete také předat více instancí <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="f9133-122">You can also pass multiple instances of <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="f9133-123">Následující fragment kódu určuje, že vlastních atributů může být použitá pro všechny třída nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="f9133-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### <a name="inherited-property"></a><span data-ttu-id="f9133-124">Zděděná vlastnost</span><span class="sxs-lookup"><span data-stu-id="f9133-124">Inherited Property</span></span>  
 <span data-ttu-id="f9133-125"><xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Vlastnost určuje, zda požadovaný atribut může být zděděn třídy, které jsou odvozeny od třídy, na které je použit požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f9133-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="f9133-126">Tato vlastnost má buď **true** (výchozí) nebo **false** příznak.</span><span class="sxs-lookup"><span data-stu-id="f9133-126">This property takes either a **true** (the default) or **false** flag.</span></span> <span data-ttu-id="f9133-127">Například v následujícím příkladu `MyAttribute` má výchozí <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu **true**, zatímco `YourAttribute` má <xref:System.AttributeUsageAttribute.Inherited%2A> hodnotu **false**.</span><span class="sxs-lookup"><span data-stu-id="f9133-127">For example, in the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of **true**, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of **false**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="f9133-128">Dva atributy jsou poté použity na metodu v základní třídě `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="f9133-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="f9133-129">Nakonec je třída `YourClass` je zděděn ze základní třídy `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="f9133-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="f9133-130">Metoda `MyMethod` ukazuje `MyAttribute`, ale ne `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="f9133-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### <a name="allowmultiple-property"></a><span data-ttu-id="f9133-131">AllowMultiple – vlastnost</span><span class="sxs-lookup"><span data-stu-id="f9133-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="f9133-132"><xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Vlastnost určuje, zda může existovat více instancí atributu v elementu.</span><span class="sxs-lookup"><span data-stu-id="f9133-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="f9133-133">Pokud nastavena na **true**, více instance jsou povoleny; Pokud nastavena na **false** (výchozí), je povolena pouze jedna instance.</span><span class="sxs-lookup"><span data-stu-id="f9133-133">If set to **true**, multiple instances are allowed; if set to **false** (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="f9133-134">V následujícím příkladu `MyAttribute` má výchozí <xref:System.AttributeUsageAttribute.AllowMultiple%2A> hodnotu **false**, zatímco `YourAttribute` má hodnotu **true**.</span><span class="sxs-lookup"><span data-stu-id="f9133-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of **false**, while `YourAttribute` has a value of **true**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="f9133-135">Pokud jsou použity více instancí těchto atributů, `MyAttribute` dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f9133-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="f9133-136">Následující příklad kódu ukazuje platné použití `YourAttribute` a neplatné použití `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="f9133-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="f9133-137">Pokud <xref:System.AttributeUsageAttribute.AllowMultiple%2A> vlastnost a <xref:System.AttributeUsageAttribute.Inherited%2A> nastavena na **true**, třídu, která dědí z jiné třídy lze dědit atribut a mít jiná instance stejného atributu použité ve stejné třídě podřízené.</span><span class="sxs-lookup"><span data-stu-id="f9133-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to **true**, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="f9133-138">Pokud <xref:System.AttributeUsageAttribute.AllowMultiple%2A> je nastaven na **false**, hodnoty atributů v nadřazené třídě budou přepsány nové instance třídy stejný atribut ve třídě podřízené.</span><span class="sxs-lookup"><span data-stu-id="f9133-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to **false**, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
<a name="cpcondeclaringattributeclass"></a>   
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="f9133-139">Deklarování třídy atributů</span><span class="sxs-lookup"><span data-stu-id="f9133-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="f9133-140">Po použití <xref:System.AttributeUsageAttribute>, můžete začít definovat specifické požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f9133-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="f9133-141">Deklarace třídy atributu bude vypadat podobně jako deklarace tradiční třídy, jak je ukázáno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f9133-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="f9133-142">Tato definice atributu ukazuje následující body:</span><span class="sxs-lookup"><span data-stu-id="f9133-142">This attribute definition demonstrates the following points:</span></span>  
  
-   <span data-ttu-id="f9133-143">Jako veřejné třídy musí být deklarován atribut třídy.</span><span class="sxs-lookup"><span data-stu-id="f9133-143">Attribute classes must be declared as public classes.</span></span>  
  
-   <span data-ttu-id="f9133-144">Podle konvence, název třídy atributů končí slovem **atribut**.</span><span class="sxs-lookup"><span data-stu-id="f9133-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="f9133-145">Není požadováno touto konvencí se doporučuje čitelnější.</span><span class="sxs-lookup"><span data-stu-id="f9133-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="f9133-146">Při použití atribut zahrnutí aplikace word atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="f9133-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
-   <span data-ttu-id="f9133-147">Všechny třídy atributu musí dědit přímo nebo nepřímo z **System.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="f9133-147">All attribute classes must inherit directly or indirectly from **System.Attribute**.</span></span>  
  
-   <span data-ttu-id="f9133-148">V jazyce Microsoft Visual Basic, musí mít všechny vlastní atribut třídy **AttributeUsageAttribute** atribut.</span><span class="sxs-lookup"><span data-stu-id="f9133-148">In Microsoft Visual Basic, all custom attribute classes must have the **AttributeUsageAttribute** attribute.</span></span>  
  
<a name="cpcondeclaringconstructors"></a>   
## <a name="declaring-constructors"></a><span data-ttu-id="f9133-149">Deklarování konstruktorů</span><span class="sxs-lookup"><span data-stu-id="f9133-149">Declaring Constructors</span></span>  
 <span data-ttu-id="f9133-150">Atributy jsou inicializovány konstruktory stejným způsobem jako tradiční třídy.</span><span class="sxs-lookup"><span data-stu-id="f9133-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="f9133-151">Následující fragment kódu ukazuje typický konstruktor atributu.</span><span class="sxs-lookup"><span data-stu-id="f9133-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="f9133-152">Tento konstruktor public, který přebírá parametr a nastaví její hodnota rovna členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="f9133-152">This public constructor takes a parameter and sets its value equal to a member variable.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="f9133-153">Můžete použít přetížení konstruktoru pro různé kombinace hodnot.</span><span class="sxs-lookup"><span data-stu-id="f9133-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="f9133-154">Pokud je také definovat [vlastnost](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) pro vaše vlastní atribut třídu, můžete použít kombinaci s názvem a pojmenovaných parametrů při inicializaci atributu.</span><span class="sxs-lookup"><span data-stu-id="f9133-154">If you also define a [property](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="f9133-155">Obvykle můžete definovat všechny požadované parametry jako poziční a všechny volitelné parametry jako s názvem.</span><span class="sxs-lookup"><span data-stu-id="f9133-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="f9133-156">V takovém případě atribut nelze inicializovat bez povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f9133-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="f9133-157">Všechny ostatní parametry jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="f9133-157">All other parameters are optional.</span></span> <span data-ttu-id="f9133-158">Upozorňujeme, že v jazyce Visual Basic konstruktory pro třídu atributu nesmí použít ParamArray argument.</span><span class="sxs-lookup"><span data-stu-id="f9133-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="f9133-159">Následující příklad kódu ukazuje, jak atribut, který používá předchozí konstruktor lze aplikovat pomocí volitelné a požadované parametry.</span><span class="sxs-lookup"><span data-stu-id="f9133-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="f9133-160">Přitom se předpokládá, že má atribut vyžaduje jednu logickou hodnotu a vlastnost jeden volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="f9133-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## <a name="declaring-properties"></a><span data-ttu-id="f9133-161">Deklarování vlastností</span><span class="sxs-lookup"><span data-stu-id="f9133-161">Declaring Properties</span></span>  
 <span data-ttu-id="f9133-162">Pokud chcete definovat pojmenovaný parametr nebo poskytují snadný způsob, jak vrátit hodnoty uložených ve vašem atributu, deklarovat [vlastnost](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="f9133-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="f9133-163">Vlastnosti atributu by měla deklarovat jako veřejné entity s popisem datového typu, který bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="f9133-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="f9133-164">Definujte proměnnou, která bude obsahovat hodnotu vaší vlastnosti a přidružit ho s **získat** a **nastavit** metody.</span><span class="sxs-lookup"><span data-stu-id="f9133-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="f9133-165">Následující příklad kódu ukazuje, jak implementovat jednoduché vlastnosti ve vašem atributu.</span><span class="sxs-lookup"><span data-stu-id="f9133-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## <a name="custom-attribute-example"></a><span data-ttu-id="f9133-166">Příklad vlastní atribut</span><span class="sxs-lookup"><span data-stu-id="f9133-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="f9133-167">Tato část zahrnuje předchozí informace a ukazuje, jak navrhnout jednoduché atributy, které dokumentů informace o autorovi oddílu kódu.</span><span class="sxs-lookup"><span data-stu-id="f9133-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="f9133-168">Atribut v tomto příkladu obsahuje název a úrovně programátory, a jestli byl revidován kód.</span><span class="sxs-lookup"><span data-stu-id="f9133-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="f9133-169">Tři soukromé proměnné používá k ukládání skutečnými hodnotami pro uložení.</span><span class="sxs-lookup"><span data-stu-id="f9133-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="f9133-170">Každá proměnná je reprezentována veřejné vlastnosti, který získá a nastaví hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f9133-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="f9133-171">Nakonec konstruktoru je definována pomocí dvou požadované parametry.</span><span class="sxs-lookup"><span data-stu-id="f9133-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="f9133-172">Můžete použít tento atribut pomocí úplný název, `DeveloperAttribute`, nebo pomocí zkrácený název `Developer`, v jednom z následujících způsobů.</span><span class="sxs-lookup"><span data-stu-id="f9133-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="f9133-173">V prvním příkladu ukazuje atribut obsahuje jenom požadované pojmenované parametry, zatímco druhý příklad ukazuje atribut s povinných a volitelných parametrů.</span><span class="sxs-lookup"><span data-stu-id="f9133-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9133-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9133-174">See Also</span></span>  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="f9133-175">Atributy</span><span class="sxs-lookup"><span data-stu-id="f9133-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
