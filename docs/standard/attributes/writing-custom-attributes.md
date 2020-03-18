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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140583"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="510f8-102">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="510f8-102">Writing Custom Attributes</span></span>
<span data-ttu-id="510f8-103">Chcete-li navrhnout vlastní atributy, není nutné zvládnout mnoho nových konceptů.</span><span class="sxs-lookup"><span data-stu-id="510f8-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="510f8-104">Pokud jste obeznámeni s objektově orientované programování a víte, jak navrhnout třídy, již máte většinu znalostí potřebných.</span><span class="sxs-lookup"><span data-stu-id="510f8-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="510f8-105">Vlastní atributy jsou v podstatě tradiční <xref:System.Attribute?displayProperty=nameWithType>třídy, které jsou odvozeny přímo nebo nepřímo z .</span><span class="sxs-lookup"><span data-stu-id="510f8-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="510f8-106">Stejně jako tradiční třídy, vlastní atributy obsahují metody, které ukládají a načítají data.</span><span class="sxs-lookup"><span data-stu-id="510f8-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="510f8-107">Primární kroky správně navrhnout vlastní atribut třídy jsou následující:</span><span class="sxs-lookup"><span data-stu-id="510f8-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="510f8-108">Použití atributu AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="510f8-108">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="510f8-109">Deklarování třídy atributu</span><span class="sxs-lookup"><span data-stu-id="510f8-109">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="510f8-110">Deklarování konstruktorů</span><span class="sxs-lookup"><span data-stu-id="510f8-110">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="510f8-111">Deklarování vlastností</span><span class="sxs-lookup"><span data-stu-id="510f8-111">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="510f8-112">Tato část popisuje každý z těchto kroků a končí [s příkladem vlastní atribut](#custom-attribute-example).</span><span class="sxs-lookup"><span data-stu-id="510f8-112">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="510f8-113">Použití atributu AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="510f8-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="510f8-114">Deklarace vlastního atributu <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>začíná na , který definuje některé klíčové charakteristiky třídy atributů.</span><span class="sxs-lookup"><span data-stu-id="510f8-114">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="510f8-115">Můžete například určit, zda může být váš atribut zděděn jinými třídami, nebo určit, na které prvky lze atribut použít.</span><span class="sxs-lookup"><span data-stu-id="510f8-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="510f8-116">Následující fragment kódu ukazuje, jak <xref:System.AttributeUsageAttribute>používat .</span><span class="sxs-lookup"><span data-stu-id="510f8-116">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="510f8-117">Má <xref:System.AttributeUsageAttribute> tři členy, které jsou důležité pro vytvoření vlastníatributy: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), a [AllowMultiple](#allowmultiple-property).</span><span class="sxs-lookup"><span data-stu-id="510f8-117">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="510f8-118">Člen attributetargets</span><span class="sxs-lookup"><span data-stu-id="510f8-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="510f8-119">V předchozím příkladu <xref:System.AttributeTargets.All?displayProperty=nameWithType> je zadán, označující, že tento atribut lze použít na všechny prvky programu.</span><span class="sxs-lookup"><span data-stu-id="510f8-119">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="510f8-120">Případně můžete zadat <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, označující, že váš atribut lze použít <xref:System.AttributeTargets.Method?displayProperty=nameWithType>pouze pro třídu, nebo , označující, že atribut lze použít pouze pro metodu.</span><span class="sxs-lookup"><span data-stu-id="510f8-120">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="510f8-121">Všechny prvky programu mohou být označeny pro popis vlastním atributem tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="510f8-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="510f8-122">Můžete také předat <xref:System.AttributeTargets> více hodnot.</span><span class="sxs-lookup"><span data-stu-id="510f8-122">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="510f8-123">Následující fragment kódu určuje, že vlastní atribut lze použít pro libovolnou třídu nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="510f8-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="510f8-124">Zděděná vlastnost</span><span class="sxs-lookup"><span data-stu-id="510f8-124">Inherited Property</span></span>  
 <span data-ttu-id="510f8-125">Vlastnost <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> označuje, zda váš atribut může být zděděn třídy, které jsou odvozeny z tříd, na které je atribut použit.</span><span class="sxs-lookup"><span data-stu-id="510f8-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="510f8-126">Tato vlastnost trvá `true` buď (výchozí) nebo `false` příznak.</span><span class="sxs-lookup"><span data-stu-id="510f8-126">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="510f8-127">V následujícím `MyAttribute` příkladu má <xref:System.AttributeUsageAttribute.Inherited%2A> výchozí `true`hodnotu , zatímco `YourAttribute` má hodnotu <xref:System.AttributeUsageAttribute.Inherited%2A> `false`.</span><span class="sxs-lookup"><span data-stu-id="510f8-127">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="510f8-128">Tyto dva atributy jsou pak použity `MyClass`na metodu v základní třídě .</span><span class="sxs-lookup"><span data-stu-id="510f8-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="510f8-129">Nakonec je `YourClass` třída zděděna `MyClass`ze základní třídy .</span><span class="sxs-lookup"><span data-stu-id="510f8-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="510f8-130">Metoda `MyMethod` ukazuje `MyAttribute`, `YourAttribute`ale ne .</span><span class="sxs-lookup"><span data-stu-id="510f8-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="510f8-131">Vlastnost Povolit více</span><span class="sxs-lookup"><span data-stu-id="510f8-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="510f8-132">Vlastnost <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> označuje, zda může existovat více instancí atributu na elementu.</span><span class="sxs-lookup"><span data-stu-id="510f8-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="510f8-133">Pokud je `true`nastavena na , jsou povoleny více instancí; pokud je `false` nastavena na (výchozí), je povolena pouze jedna instance.</span><span class="sxs-lookup"><span data-stu-id="510f8-133">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="510f8-134">V `MyAttribute` následujícím příkladu má <xref:System.AttributeUsageAttribute.AllowMultiple%2A> výchozí `false`hodnotu , zatímco `YourAttribute` má hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="510f8-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="510f8-135">Při použití více instancí těchto `MyAttribute` atributů, vytvoří chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="510f8-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="510f8-136">Následující příklad kódu ukazuje platné `YourAttribute` použití a `MyAttribute`neplatné použití .</span><span class="sxs-lookup"><span data-stu-id="510f8-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="510f8-137">Pokud jsou <xref:System.AttributeUsageAttribute.AllowMultiple%2A> vlastnost <xref:System.AttributeUsageAttribute.Inherited%2A> i vlastnost `true`nastaveny na , třída, která je zděděna z jiné třídy, může zdědit atribut a mít jinou instanci stejného atributu použitou ve stejné podřízené třídě.</span><span class="sxs-lookup"><span data-stu-id="510f8-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="510f8-138">Pokud <xref:System.AttributeUsageAttribute.AllowMultiple%2A> je `false`nastavena na , hodnoty všechny atributy v nadřazené třídě budou přepsány nové instance stejného atributu v podřízené třídě.</span><span class="sxs-lookup"><span data-stu-id="510f8-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="510f8-139">Deklarování třídy atributů</span><span class="sxs-lookup"><span data-stu-id="510f8-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="510f8-140">Po použití <xref:System.AttributeUsageAttribute>aplikace můžete začít definovat specifika atributu.</span><span class="sxs-lookup"><span data-stu-id="510f8-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="510f8-141">Deklarace třídy atributů vypadá podobně jako deklarace tradiční třídy, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="510f8-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="510f8-142">Tato definice atributu ukazuje následující body:</span><span class="sxs-lookup"><span data-stu-id="510f8-142">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="510f8-143">Třídy atributů musí být deklarovány jako veřejné třídy.</span><span class="sxs-lookup"><span data-stu-id="510f8-143">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="510f8-144">Podle konvence název třídy atributu končí slovem **Atribut**.</span><span class="sxs-lookup"><span data-stu-id="510f8-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="510f8-145">I když není vyžadováno, tato konvence se doporučuje pro čitelnost.</span><span class="sxs-lookup"><span data-stu-id="510f8-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="510f8-146">Při použití atributu je zahrnutí slova Atribut volitelné.</span><span class="sxs-lookup"><span data-stu-id="510f8-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="510f8-147">Všechny třídy atributů musí <xref:System.Attribute?displayProperty=nameWithType>dědit přímo nebo nepřímo z .</span><span class="sxs-lookup"><span data-stu-id="510f8-147">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="510f8-148">V jazyce Microsoft Visual Basic musí <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> mít atribut všechny třídy vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="510f8-148">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="510f8-149">Deklarování konstruktorů</span><span class="sxs-lookup"><span data-stu-id="510f8-149">Declaring Constructors</span></span>  
 <span data-ttu-id="510f8-150">Atributy jsou inicializovány s konstruktory stejným způsobem jako tradiční třídy.</span><span class="sxs-lookup"><span data-stu-id="510f8-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="510f8-151">Následující fragment kódu ilustruje konstruktor typického atributu.</span><span class="sxs-lookup"><span data-stu-id="510f8-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="510f8-152">Tento veřejný konstruktor převezme parametr a nastaví člennou proměnnou rovnou jeho hodnotě.</span><span class="sxs-lookup"><span data-stu-id="510f8-152">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="510f8-153">Můžete přetížení konstruktoru tak, aby vyhovovaly různé kombinace hodnot.</span><span class="sxs-lookup"><span data-stu-id="510f8-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="510f8-154">Pokud také definujete [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) pro vlastní třídu atributů, můžete při inicializaci atributu použít kombinaci pojmenovaných a pozičních parametrů.</span><span class="sxs-lookup"><span data-stu-id="510f8-154">If you also define a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="510f8-155">Obvykle definujete všechny požadované parametry jako poziční a všechny volitelné parametry, jak je pojmenováno.</span><span class="sxs-lookup"><span data-stu-id="510f8-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="510f8-156">V tomto případě nelze atribut inicializovat bez požadovaného parametru.</span><span class="sxs-lookup"><span data-stu-id="510f8-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="510f8-157">Všechny ostatní parametry jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="510f8-157">All other parameters are optional.</span></span> <span data-ttu-id="510f8-158">Všimněte si, že v jazyce Visual Basic by konstruktory pro třídu atributů neměly používat argument ParamArray.</span><span class="sxs-lookup"><span data-stu-id="510f8-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="510f8-159">Následující příklad kódu ukazuje, jak lze použít atribut, který používá předchozí konstruktor pomocí volitelných a požadovaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="510f8-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="510f8-160">Předpokládá, že atribut má jednu požadovanou logickou hodnotu a jednu volitelnou vlastnost řetězce.</span><span class="sxs-lookup"><span data-stu-id="510f8-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="510f8-161">Deklarování vlastností</span><span class="sxs-lookup"><span data-stu-id="510f8-161">Declaring Properties</span></span>  
 <span data-ttu-id="510f8-162">Pokud chcete definovat pojmenovaný parametr nebo poskytnout snadný způsob, jak vrátit hodnoty uložené atributem, deklarujte [vlastnost](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="510f8-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="510f8-163">Vlastnosti atributu by měly být deklarovány jako veřejné entity s popisem datového typu, který bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="510f8-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="510f8-164">Definujte proměnnou, která bude obsahovat hodnotu vaší vlastnosti, a přidružte ji k metodám **get** a **set.**</span><span class="sxs-lookup"><span data-stu-id="510f8-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="510f8-165">Následující příklad kódu ukazuje, jak implementovat jednoduchou vlastnost ve vašem atributu.</span><span class="sxs-lookup"><span data-stu-id="510f8-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="510f8-166">Příklad vlastního atributu</span><span class="sxs-lookup"><span data-stu-id="510f8-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="510f8-167">Tato část obsahuje předchozí informace a ukazuje, jak navrhnout jednoduchý atribut, který dokumentuje informace o autorovi části kódu.</span><span class="sxs-lookup"><span data-stu-id="510f8-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="510f8-168">Atribut v tomto příkladu ukládá název a úroveň programátora a zda byl kód zkontrolován.</span><span class="sxs-lookup"><span data-stu-id="510f8-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="510f8-169">Používá tři soukromé proměnné pro uložení skutečné hodnoty uložit.</span><span class="sxs-lookup"><span data-stu-id="510f8-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="510f8-170">Každá proměnná je reprezentována veřejnou vlastností, která získá a nastaví hodnoty.</span><span class="sxs-lookup"><span data-stu-id="510f8-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="510f8-171">Nakonec je konstruktor definován dvěma požadovanými parametry.</span><span class="sxs-lookup"><span data-stu-id="510f8-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="510f8-172">Tento atribut můžete použít pomocí `DeveloperAttribute`celého názvu , nebo pomocí `Developer`zkráceného názvu , jedním z následujících způsobů.</span><span class="sxs-lookup"><span data-stu-id="510f8-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="510f8-173">První příklad ukazuje atribut použitý pouze s požadovanými pojmenovanými parametry, zatímco druhý příklad ukazuje atribut použitý s požadovanými i volitelnými parametry.</span><span class="sxs-lookup"><span data-stu-id="510f8-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510f8-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="510f8-174">See also</span></span>

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="510f8-175">Atributy</span><span class="sxs-lookup"><span data-stu-id="510f8-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
