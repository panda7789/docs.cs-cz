---
title: "Načítání informací uložených v atributech"
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
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 146572fb060d1bd37d6eee5b5dce3c255b28f8b2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="f548e-102">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="f548e-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="f548e-103">Načítání vlastní atribut je jednoduchý proces.</span><span class="sxs-lookup"><span data-stu-id="f548e-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="f548e-104">Nejprve deklarujte instanci atribut, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="f548e-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="f548e-105">Potom použít <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metoda pro inicializaci nového atributu na hodnotu atributu, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="f548e-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="f548e-106">Jakmile nový atribut inicializován, jednoduše použijte jeho vlastnosti a získat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f548e-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f548e-107">Toto téma popisuje, jak načíst atributy pro kód načtený do kontextu spuštění.</span><span class="sxs-lookup"><span data-stu-id="f548e-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="f548e-108">Chcete-li načíst atributy pro kód načtený do kontextu pouze pro reflexi, musíte použít <xref:System.Reflection.CustomAttributeData> třídy, jak je znázorněno v [postupy: načtení sestavení do kontextu Reflection](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="f548e-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="f548e-109">Tato část popisuje tyto způsoby načíst atributy:</span><span class="sxs-lookup"><span data-stu-id="f548e-109">This section describes the following ways to retrieve attributes:</span></span>  
  
-   [<span data-ttu-id="f548e-110">Načítání jednu instanci atributu</span><span class="sxs-lookup"><span data-stu-id="f548e-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
-   [<span data-ttu-id="f548e-111">Načítání více instancí atributu použitého pro stejný obor</span><span class="sxs-lookup"><span data-stu-id="f548e-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [<span data-ttu-id="f548e-112">Načítání více instancí atributu použitého pro různé obory</span><span class="sxs-lookup"><span data-stu-id="f548e-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="f548e-113">Načítání jednu instanci atributu</span><span class="sxs-lookup"><span data-stu-id="f548e-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="f548e-114">V následujícím příkladu `DeveloperAttribute` (popsané v předchozí části) se použijí na `MainApp` třídy na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="f548e-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="f548e-115">`GetAttribute` Používá metoda **GetCustomAttribute** načíst hodnotami uloženými v `DeveloperAttribute` na úrovni třídy před jejich zobrazením ke konzole.</span><span class="sxs-lookup"><span data-stu-id="f548e-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="f548e-116">Tento program zobrazí následující text při spuštění.</span><span class="sxs-lookup"><span data-stu-id="f548e-116">This program displays the following text when executed.</span></span>  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="f548e-117">Pokud není nalezen atribut, **GetCustomAttribute** metoda inicializuje `MyAttribute` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f548e-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="f548e-118">Tento příklad zkontroluje `MyAttribute` takovýchto instancí a upozorní uživatele, pokud není nalezen žádný atribut.</span><span class="sxs-lookup"><span data-stu-id="f548e-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="f548e-119">Pokud `DeveloperAttribute` nebyla nalezena v oboru třída konzoli se zobrazí následující zprávu.</span><span class="sxs-lookup"><span data-stu-id="f548e-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```  
The attribute was not found.   
```  
  
 <span data-ttu-id="f548e-120">Tento příklad předpokládá, že definice atributu je v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f548e-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="f548e-121">Nezapomeňte importovat obor názvů, ve kterém se nachází definice atributu, pokud není v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f548e-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="f548e-122">Načítání více instancí atributu použitého pro stejný obor</span><span class="sxs-lookup"><span data-stu-id="f548e-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="f548e-123">V předchozím příkladu třída ke kontrole a konkrétní atribut se předávají do <xref:System.Attribute.GetCustomAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="f548e-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="f548e-124">Tento kód funguje dobře, pokud pouze jedna instance atributu se použije na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="f548e-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="f548e-125">Ale v případě, že jsou na stejné úrovni třídy, použito více instancí atributu **GetCustomAttribute** metoda nenačte všechny informace.</span><span class="sxs-lookup"><span data-stu-id="f548e-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="f548e-126">V případech, kdy se více instancí stejného atributu používá ve stejném rozsahu, můžete použít <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> umístit všechny instance atributu do pole.</span><span class="sxs-lookup"><span data-stu-id="f548e-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="f548e-127">Například, pokud dvě instance `DeveloperAttribute` jsou použity na úrovni třídy stejné třídy, `GetAttribute` metoda můžete upravit tak, aby zobrazení informací v oba atributy nalezen.</span><span class="sxs-lookup"><span data-stu-id="f548e-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="f548e-128">Nezapomeňte, chcete-li použít více atributů na stejné úrovni, musí být definován atribut s **AllowMultiple** vlastnost nastavena na hodnotu **true** v <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f548e-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="f548e-129">Následující příklad kódu ukazuje, jak používat **GetCustomAttributes** metodu pro vytvoření pole, které odkazuje na všechny instance `DeveloperAttribute` v žádném zadána třída.</span><span class="sxs-lookup"><span data-stu-id="f548e-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="f548e-130">Hodnoty všechny atributy se zobrazí konzole.</span><span class="sxs-lookup"><span data-stu-id="f548e-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="f548e-131">Pokud nejsou nalezeny žádné atributy, tento kód upozorní uživatele.</span><span class="sxs-lookup"><span data-stu-id="f548e-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="f548e-132">Jinak, informace obsažené v obou instancí `DeveloperAttribute` se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="f548e-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="f548e-133">Načítání více instancí atributu použitého pro různé obory</span><span class="sxs-lookup"><span data-stu-id="f548e-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="f548e-134"><xref:System.Attribute.GetCustomAttributes%2A> a <xref:System.Attribute.GetCustomAttribute%2A> metody celou třídu a nevrací všechny instance atributu v této třídě.</span><span class="sxs-lookup"><span data-stu-id="f548e-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="f548e-135">Hledání místo toho najednou pouze jednu zadanou metodu nebo člen.</span><span class="sxs-lookup"><span data-stu-id="f548e-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="f548e-136">Pokud máte s stejný atribut použitým na každého člena třídy a chcete načíst hodnoty v všechny atributy použité u členů, musíte zadat každou metodu nebo člen jednotlivě na **GetCustomAttributes** a  **GetCustomAttribute**.</span><span class="sxs-lookup"><span data-stu-id="f548e-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="f548e-137">Následující příklad kódu třída jako parametr a hledá `DeveloperAttribute` (definované dříve) na úrovni třídy a každé jednotlivé metody této třídy.</span><span class="sxs-lookup"><span data-stu-id="f548e-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="f548e-138">Pokud žádné instance `DeveloperAttribute` se nacházejí na úrovni metody nebo úrovni třídy `GetAttribute` metoda upozorní uživatele, že nebyly nalezeny žádné atributy a zobrazí název metody nebo třídu, která neobsahuje atribut.</span><span class="sxs-lookup"><span data-stu-id="f548e-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="f548e-139">Pokud je atribut nalezen, `Name`, `Level`, a `Reviewed` jsou zobrazeny na konzole.</span><span class="sxs-lookup"><span data-stu-id="f548e-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="f548e-140">Můžete použít členů <xref:System.Type> třídy pro získání jednotlivých metod a členů v předané třídě.</span><span class="sxs-lookup"><span data-stu-id="f548e-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="f548e-141">Tento příklad nejprve dotazuje **typ** objekt, který chcete získat informace o atributu pro úrovni tříd.</span><span class="sxs-lookup"><span data-stu-id="f548e-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="f548e-142">Dále je použita <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> pro umístění instancí všech metod do pole <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objekty, které chcete načíst informace o atributu pro úroveň metody.</span><span class="sxs-lookup"><span data-stu-id="f548e-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="f548e-143">Můžete také <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> metoda pro vyhledání atributů na úrovni vlastnosti nebo <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> pro vyhledání atributů na úrovni konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f548e-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f548e-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="f548e-144">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f548e-145">Atributy</span><span class="sxs-lookup"><span data-stu-id="f548e-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)
