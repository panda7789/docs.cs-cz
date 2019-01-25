---
title: Načítání informací uložených v atributech
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d921c13765f5d61ce9822df0b4059b2cf93a6f6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744082"
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="a2e00-102">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="a2e00-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="a2e00-103">Načítání vlastního atributu je jednoduchý proces.</span><span class="sxs-lookup"><span data-stu-id="a2e00-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="a2e00-104">Nejprve deklarujte instanci atributu, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="a2e00-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="a2e00-105">Potom použijte <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metody k inicializaci nového atributu hodnotu atributu, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="a2e00-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="a2e00-106">Po inicializaci nový atribut jednoduše pomocí její vlastnosti k získání hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a2e00-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a2e00-107">Toto téma popisuje, jak načíst atributy pro kód načtený do kontextu spuštění.</span><span class="sxs-lookup"><span data-stu-id="a2e00-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="a2e00-108">Načíst atributy pro kód načtený do kontextu pouze pro reflexi, je nutné použít <xref:System.Reflection.CustomAttributeData> třídy, jak je znázorněno v [jak: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="a2e00-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="a2e00-109">Tato část popisuje načtení atributů následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="a2e00-109">This section describes the following ways to retrieve attributes:</span></span>  
  
-   [<span data-ttu-id="a2e00-110">Načítání jednu instanci atributu</span><span class="sxs-lookup"><span data-stu-id="a2e00-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
-   [<span data-ttu-id="a2e00-111">Načítání více instancí atributu použít ve stejném rozsahu</span><span class="sxs-lookup"><span data-stu-id="a2e00-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [<span data-ttu-id="a2e00-112">Načítání více instancí atributu použitého k různým oborům</span><span class="sxs-lookup"><span data-stu-id="a2e00-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="a2e00-113">Načítání jednu instanci atributu</span><span class="sxs-lookup"><span data-stu-id="a2e00-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="a2e00-114">V následujícím příkladu `DeveloperAttribute` (popsané v předchozí části) platí pro `MainApp` třídy na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="a2e00-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="a2e00-115">`GetAttribute` Používá metoda **GetCustomAttribute** k načtení hodnoty uložené v `DeveloperAttribute` na úrovni třídy před zobrazením do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a2e00-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="a2e00-116">Tento program zobrazí tento text při spuštění.</span><span class="sxs-lookup"><span data-stu-id="a2e00-116">This program displays the following text when executed.</span></span>  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="a2e00-117">Pokud atribut nebyl nalezen, **GetCustomAttribute** metoda inicializuje `MyAttribute` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a2e00-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="a2e00-118">Tento příklad kontroluje `MyAttribute` pro takové situaci a upozorní uživatele, pokud není nalezen žádný atribut.</span><span class="sxs-lookup"><span data-stu-id="a2e00-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="a2e00-119">Pokud `DeveloperAttribute` nebyla nalezena v oboru třídy do konzoly se zobrazí následující zpráva.</span><span class="sxs-lookup"><span data-stu-id="a2e00-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```  
The attribute was not found.   
```  
  
 <span data-ttu-id="a2e00-120">Tento příklad předpokládá, že definice atributu je v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a2e00-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="a2e00-121">Mějte na paměti pro import oboru názvů, ve kterém se nachází definice atributu, pokud není v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a2e00-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="a2e00-122">Načítání více instancí atributu použít ve stejném rozsahu</span><span class="sxs-lookup"><span data-stu-id="a2e00-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="a2e00-123">V předchozím příkladu třída ke kontrole a k nalezení konkrétní atribut jsou předány <xref:System.Attribute.GetCustomAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2e00-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="a2e00-124">Tento kód funguje dobře, pokud pouze jedna instance atributu se použije na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="a2e00-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="a2e00-125">Nicméně, pokud více instancí atributu se použije na stejné úrovni třídy, **GetCustomAttribute** metoda nenačte všechny informace.</span><span class="sxs-lookup"><span data-stu-id="a2e00-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="a2e00-126">V případech použití více instancí stejného atributu ve stejném rozsahu, můžete použít <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> pro umístění všech instancí atributu na pole.</span><span class="sxs-lookup"><span data-stu-id="a2e00-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="a2e00-127">Například, pokud dva výskyty `DeveloperAttribute` se použijí na úrovni třídy stejné třídy, `GetAttribute` metodu je možné upravit pro zobrazení informací v oba atributy.</span><span class="sxs-lookup"><span data-stu-id="a2e00-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="a2e00-128">Mějte na paměti, chcete-li použít několik atributů na stejné úrovni atribut musí být definované s **AllowMultiple** vlastnost nastavena na hodnotu **true** v <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a2e00-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="a2e00-129">Následující příklad kódu ukazuje, jak používat **GetCustomAttributes** metodu pro vytvoření pole, která odkazuje na všechny instance `DeveloperAttribute` v libovolné zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="a2e00-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="a2e00-130">Hodnoty všech atributů je následně zobrazen konzole.</span><span class="sxs-lookup"><span data-stu-id="a2e00-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="a2e00-131">Pokud nejsou nalezeny žádné atributy, tento kód zobrazí uživateli výstrahu.</span><span class="sxs-lookup"><span data-stu-id="a2e00-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="a2e00-132">V opačném případě informace obsažené v obou instancích `DeveloperAttribute` se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a2e00-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="a2e00-133">Načítání více instancí atributu použitého k různým oborům</span><span class="sxs-lookup"><span data-stu-id="a2e00-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="a2e00-134"><xref:System.Attribute.GetCustomAttributes%2A> a <xref:System.Attribute.GetCustomAttribute%2A> metody celou třídu a nevrací všechny instance atributu v dané třídě.</span><span class="sxs-lookup"><span data-stu-id="a2e00-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="a2e00-135">Vyhledat místo toho najednou pouze jednu zadanou metodu nebo člen.</span><span class="sxs-lookup"><span data-stu-id="a2e00-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="a2e00-136">Pokud máte na stejný atribut u každého člena třídy a chcete načíst hodnoty v všechny atributy použité na tyto členy, je nutné zadat každou metodu nebo člen jednotlivě **GetCustomAttributes** a  **GetCustomAttribute**.</span><span class="sxs-lookup"><span data-stu-id="a2e00-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="a2e00-137">Následující příklad kódu používá třídu jako parametr a vyhledá `DeveloperAttribute` (definovaného dříve) na úrovni třídy a v každé jednotlivé metody této třídy.</span><span class="sxs-lookup"><span data-stu-id="a2e00-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="a2e00-138">Pokud žádné instance `DeveloperAttribute` jsou k dispozici na úrovni metody nebo třídy, `GetAttribute` metoda upozorní uživatele, že nebyly nalezeny žádné atributy a zobrazí název metody nebo třídy, která neobsahuje atribut.</span><span class="sxs-lookup"><span data-stu-id="a2e00-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="a2e00-139">Pokud se najde atribut `Name`, `Level`, a `Reviewed` pole se zobrazí v konzole.</span><span class="sxs-lookup"><span data-stu-id="a2e00-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="a2e00-140">Můžete použít jako objekty její členové <xref:System.Type> třídy pro získání jednotlivé metody a členy v předaných třídě.</span><span class="sxs-lookup"><span data-stu-id="a2e00-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="a2e00-141">V tomto příkladu nejdřív dotazuje **typ** můžete získat informace o atributu pro úroveň třídy.</span><span class="sxs-lookup"><span data-stu-id="a2e00-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="a2e00-142">V dalším kroku použije <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> umístit všechny metody instance do pole <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objekty se načíst informace o atributu pro úroveň metody.</span><span class="sxs-lookup"><span data-stu-id="a2e00-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="a2e00-143">Můžete také použít <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> metodu ke kontrole atributů na úrovni vlastnosti nebo <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> pro vyhledání atributů na úrovni konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a2e00-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e00-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2e00-144">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a2e00-145">Atributy</span><span class="sxs-lookup"><span data-stu-id="a2e00-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)
