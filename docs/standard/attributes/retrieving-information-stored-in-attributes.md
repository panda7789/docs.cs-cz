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
ms.openlocfilehash: 298ac8eae0a8b125ddf5f1ff35658f426f6b10aa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968586"
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="bb600-102">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="bb600-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="bb600-103">Načítání vlastního atributu je jednoduchý proces.</span><span class="sxs-lookup"><span data-stu-id="bb600-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="bb600-104">Nejprve deklarujte instanci atributu, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="bb600-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="bb600-105">Pak použijte <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metodu pro inicializaci nového atributu na hodnotu atributu, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="bb600-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="bb600-106">Po inicializaci nového atributu jednoduše použijete jeho vlastnosti k získání hodnot.</span><span class="sxs-lookup"><span data-stu-id="bb600-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bb600-107">Toto téma popisuje, jak načíst atributy pro kód načtený do kontextu spuštění.</span><span class="sxs-lookup"><span data-stu-id="bb600-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="bb600-108">Chcete-li načíst atributy pro kód načtený do kontextu pouze pro reflexi, <xref:System.Reflection.CustomAttributeData> je nutné použít třídu, [jak je znázorněno v tématu How to: Načíst sestavení do kontextu](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="bb600-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="bb600-109">Tato část popisuje následující způsoby načtení atributů:</span><span class="sxs-lookup"><span data-stu-id="bb600-109">This section describes the following ways to retrieve attributes:</span></span>  
  
- [<span data-ttu-id="bb600-110">Načtení jedné instance atributu</span><span class="sxs-lookup"><span data-stu-id="bb600-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
- [<span data-ttu-id="bb600-111">Načítání více instancí atributu použitých pro stejný obor</span><span class="sxs-lookup"><span data-stu-id="bb600-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [<span data-ttu-id="bb600-112">Načítání více instancí atributu použitých pro různé obory</span><span class="sxs-lookup"><span data-stu-id="bb600-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="bb600-113">Načtení jedné instance atributu</span><span class="sxs-lookup"><span data-stu-id="bb600-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="bb600-114">V následujícím příkladu `DeveloperAttribute` je (popsané v předchozí části) použito `MainApp` pro třídu na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="bb600-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="bb600-115">Metoda používá **GetCustomAttribute** k načtení hodnot uložených v `DeveloperAttribute` na úrovni třídy před jejich zobrazením do konzoly. `GetAttribute`</span><span class="sxs-lookup"><span data-stu-id="bb600-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="bb600-116">Tento program zobrazí při spuštění následující text.</span><span class="sxs-lookup"><span data-stu-id="bb600-116">This program displays the following text when executed.</span></span>  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="bb600-117">Pokud atribut není nalezen, metoda **GetCustomAttribute** inicializuje `MyAttribute` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="bb600-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="bb600-118">Tento příklad zkontroluje `MyAttribute` takovou instanci a upozorní uživatele, pokud není nalezen žádný atribut.</span><span class="sxs-lookup"><span data-stu-id="bb600-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="bb600-119">`DeveloperAttribute` Pokud se v oboru třídy nenajde, zobrazí se v konzole následující zpráva.</span><span class="sxs-lookup"><span data-stu-id="bb600-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```  
The attribute was not found.   
```  
  
 <span data-ttu-id="bb600-120">V tomto příkladu se předpokládá, že definice atributu je v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bb600-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="bb600-121">Nezapomeňte importovat obor názvů, ve kterém se definice atributu nachází, pokud není v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bb600-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="bb600-122">Načítání více instancí atributu použitých pro stejný obor</span><span class="sxs-lookup"><span data-stu-id="bb600-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="bb600-123">V předchozím příkladu třída, která se má zkontrolovat, a konkrétní atribut, který se má najít <xref:System.Attribute.GetCustomAttribute%2A>, se předávají.</span><span class="sxs-lookup"><span data-stu-id="bb600-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="bb600-124">Tento kód funguje dobře, pokud na úrovni třídy je použita pouze jedna instance atributu.</span><span class="sxs-lookup"><span data-stu-id="bb600-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="bb600-125">Nicméně pokud je více instancí atributu použito na stejné úrovni třídy, metoda **GetCustomAttribute** nenačte všechny informace.</span><span class="sxs-lookup"><span data-stu-id="bb600-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="bb600-126">V případech, kdy je v rámci stejného oboru použito více instancí stejného atributu, lze použít <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> k umístění všech instancí atributu do pole Array.</span><span class="sxs-lookup"><span data-stu-id="bb600-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="bb600-127">Například pokud `DeveloperAttribute` jsou na úrovni třídy stejné třídy použity dvě instance `GetAttribute` , lze metodu upravit tak, aby zobrazovala informace nalezené v obou atributech.</span><span class="sxs-lookup"><span data-stu-id="bb600-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="bb600-128">Nezapomeňte, že chcete-li použít více atributů na stejné úrovni, atribut musí být definován s vlastností **AllowMultiple** nastavenou na **hodnotu true** v <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bb600-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="bb600-129">Následující příklad kódu ukazuje, jak použít metodu **GetCustomAttributes** k vytvoření pole, které odkazuje na všechny instance `DeveloperAttribute` v jakékoli dané třídě.</span><span class="sxs-lookup"><span data-stu-id="bb600-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="bb600-130">Hodnoty všech atributů se pak zobrazí v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="bb600-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="bb600-131">Pokud nejsou nalezeny žádné atributy, tento kód upozorní uživatele.</span><span class="sxs-lookup"><span data-stu-id="bb600-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="bb600-132">V opačném případě se zobrazí informace obsažené v `DeveloperAttribute` obou instancích.</span><span class="sxs-lookup"><span data-stu-id="bb600-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="bb600-133">Načítání více instancí atributu použitých pro různé obory</span><span class="sxs-lookup"><span data-stu-id="bb600-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="bb600-134">Metody <xref:System.Attribute.GetCustomAttributes%2A> a<xref:System.Attribute.GetCustomAttribute%2A> nehledají celou třídu a vracejí všechny instance atributu v této třídě.</span><span class="sxs-lookup"><span data-stu-id="bb600-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="bb600-135">Místo toho hledají pouze jednu zadanou metodu nebo člen v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="bb600-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="bb600-136">Pokud máte třídu se stejným atributem použitým pro každého člena a chcete načíst hodnoty ve všech atributech použitých u těchto členů, je nutné každou metodu nebo člen zadat jednotlivě do **GetCustomAttributes** a **GetCustomAttribute.** .</span><span class="sxs-lookup"><span data-stu-id="bb600-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="bb600-137">Následující příklad kódu přebírá třídu jako parametr a hledá `DeveloperAttribute` (dříve definovaný) na úrovni třídy a pro každou jednotlivou metodu této třídy.</span><span class="sxs-lookup"><span data-stu-id="bb600-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="bb600-138">Pokud nejsou nalezeny žádné instance `DeveloperAttribute` rozhraní na úrovni metody nebo třídy `GetAttribute` , metoda upozorní uživatele, že nebyly nalezeny žádné atributy, a zobrazí název metody nebo třídy, která atribut neobsahuje.</span><span class="sxs-lookup"><span data-stu-id="bb600-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="bb600-139">Pokud je nalezen atribut, `Name`pole, `Level`a `Reviewed` se zobrazí v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="bb600-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="bb600-140">Pomocí členů <xref:System.Type> třídy lze získat jednotlivé metody a členy v předané třídě.</span><span class="sxs-lookup"><span data-stu-id="bb600-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="bb600-141">Tento příklad nejprve vyhledá objekt **typu** , aby získal informace o atributu pro úroveň třídy.</span><span class="sxs-lookup"><span data-stu-id="bb600-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="bb600-142">Dále používá <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> k umístění instancí všech metod do <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> pole objektů pro načtení informací o atributu pro úroveň metody.</span><span class="sxs-lookup"><span data-stu-id="bb600-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="bb600-143">Můžete také použít <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> metodu pro kontrolu atributů na úrovni vlastnosti nebo <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> pro kontrolu atributů na úrovni konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="bb600-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb600-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb600-144">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bb600-145">Atributy</span><span class="sxs-lookup"><span data-stu-id="bb600-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)
