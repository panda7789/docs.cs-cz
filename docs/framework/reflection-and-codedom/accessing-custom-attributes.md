---
title: Přístup k vlastním atributům
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
ms.openlocfilehash: a5651e9dc8cf40e737dd523ec5d29e876a9c0765
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130303"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="af063-102">Přístup k vlastním atributům</span><span class="sxs-lookup"><span data-stu-id="af063-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="af063-103">Po přiřazení atributů k prvkům programu lze reflexi použít k dotazování jejich existence a hodnot.</span><span class="sxs-lookup"><span data-stu-id="af063-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="af063-104">V .NET Framework verze 1,0 a 1,1 jsou vlastní atributy zkontrolovány v kontextu spuštění.</span><span class="sxs-lookup"><span data-stu-id="af063-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="af063-105">.NET Framework verze 2,0 poskytuje nový kontext zatížení, kontext pouze pro reflexi, který lze použít k prohlédnutí kódu, který nelze načíst ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="af063-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="af063-106">Kontext pouze pro reflexi</span><span class="sxs-lookup"><span data-stu-id="af063-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="af063-107">Kód načtený do kontextu pouze pro reflexi nelze provést.</span><span class="sxs-lookup"><span data-stu-id="af063-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="af063-108">To znamená, že instance vlastních atributů nelze vytvořit, protože by vyžadovaly provádění jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="af063-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="af063-109">Chcete-li načíst a ověřit vlastní atributy v kontextu pouze pro reflexi, použijte třídu <xref:System.Reflection.CustomAttributeData>.</span><span class="sxs-lookup"><span data-stu-id="af063-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="af063-110">Instance této třídy lze získat pomocí vhodného přetížení metody static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af063-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="af063-111">Viz [Postupy: načtení sestavení do kontextu pouze pro reflexi](how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="af063-111">See [How to: Load Assemblies into the Reflection-Only Context](how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="af063-112">Kontext spuštění</span><span class="sxs-lookup"><span data-stu-id="af063-112">The Execution Context</span></span>  
 <span data-ttu-id="af063-113">Hlavní metody reflexe pro dotazování atributů v kontextu spuštění jsou <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> a <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af063-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="af063-114">Přístupnost vlastního atributu je zkontrolována s ohledem na sestavení, ve kterém je připojen.</span><span class="sxs-lookup"><span data-stu-id="af063-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="af063-115">To je ekvivalentní k kontrole, zda metoda na typu v sestavení, ve kterém je vlastní atribut připojen, může volat konstruktor vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="af063-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="af063-116">Metody jako <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> kontrolují viditelnost a přístupnost argumentu typu.</span><span class="sxs-lookup"><span data-stu-id="af063-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="af063-117">Pouze kód v sestavení, které obsahuje uživatelsky definovaný typ, může načíst vlastní atribut tohoto typu pomocí **GetCustomAttributes**.</span><span class="sxs-lookup"><span data-stu-id="af063-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="af063-118">Následující C# příklad je typický vzor návrhu vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="af063-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="af063-119">Znázorňuje model reflexe vlastního atributu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="af063-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
```csharp
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 <span data-ttu-id="af063-120">Pokud se modul runtime pokouší načíst vlastní atributy pro typ vlastního atributu Public <xref:System.ComponentModel.DescriptionAttribute> připojen k metodě **GetLanguage** , provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="af063-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1. <span data-ttu-id="af063-121">Modul runtime kontroluje, zda je argument typu DescriptionAttribute **typu. GetCustomAttributes** *(typ typu) veřejný*, a proto je viditelný a přístupný.</span><span class="sxs-lookup"><span data-stu-id="af063-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2. <span data-ttu-id="af063-122">Modul runtime kontroluje, zda je uživatelem definovaný typ **MyDescriptionAttribute** , který je odvozen z **DescriptionAttribute** , viditelný a přístupný v rámci sestavení **System. Web. dll** , kde je připojen k metodě **GetLanguage** ().</span><span class="sxs-lookup"><span data-stu-id="af063-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3. <span data-ttu-id="af063-123">Modul runtime kontroluje, zda je konstruktor třídy **MyDescriptionAttribute** viditelný a přístupný v rámci sestavení **System. Web. dll** .</span><span class="sxs-lookup"><span data-stu-id="af063-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4. <span data-ttu-id="af063-124">Modul runtime volá konstruktor třídy **MyDescriptionAttribute** s parametry vlastního atributu a vrátí nový objekt volajícímu.</span><span class="sxs-lookup"><span data-stu-id="af063-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="af063-125">Model reflexe vlastního atributu by mohl navrácení instancí uživatelsky definovaných typů mimo sestavení, ve kterém je definován typ.</span><span class="sxs-lookup"><span data-stu-id="af063-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="af063-126">Neliší se od členů v běhové systémové knihovně, které vracejí instance uživatelsky definovaných typů, například <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> vrací pole objektů **RuntimeMethodInfo** .</span><span class="sxs-lookup"><span data-stu-id="af063-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="af063-127">Chcete-li klientovi zabránit v zjišťování informací o typu vlastního atributu definovaného uživatelem, definujte členy typu, které mají být NonPublic.</span><span class="sxs-lookup"><span data-stu-id="af063-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="af063-128">Následující příklad ukazuje základní způsob použití reflexe k získání přístupu k vlastním atributům.</span><span class="sxs-lookup"><span data-stu-id="af063-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="af063-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af063-129">See also</span></span>

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="af063-130">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="af063-130">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="af063-131">Důležité informace o zabezpečení pro reflexi</span><span class="sxs-lookup"><span data-stu-id="af063-131">Security Considerations for Reflection</span></span>](security-considerations-for-reflection.md)
