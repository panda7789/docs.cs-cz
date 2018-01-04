---
title: "Přístup k vlastním atributům"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0980488f3093bfcaedc730bac126b1b5b6505187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="47af0-102">Přístup k vlastním atributům</span><span class="sxs-lookup"><span data-stu-id="47af0-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="47af0-103">Po atributy nejsou spojené s prvky programu, reflexe můžete použít k dotazování jejich existence a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="47af0-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="47af0-104">V rozhraní .NET Framework verze 1.0 a 1.1 vlastní atributy jsou zkoumány v kontextu spuštění.</span><span class="sxs-lookup"><span data-stu-id="47af0-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="47af0-105">Poskytuje rozhraní .NET Framework verze 2.0 nový kontext načítání pouze pro reflexi kontext, který můžete použít k prozkoumání kód, který nelze načíst pro provedení.</span><span class="sxs-lookup"><span data-stu-id="47af0-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="47af0-106">Kontext pouze pro reflexi</span><span class="sxs-lookup"><span data-stu-id="47af0-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="47af0-107">Kód načtený do kontextu pouze pro reflexi nelze provést.</span><span class="sxs-lookup"><span data-stu-id="47af0-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="47af0-108">To znamená, že nelze vytvořit instance vlastních atributů, protože, které by vyžadovaly provedením jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="47af0-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="47af0-109">Pokud chcete načíst a zkontrolujte vlastní atributy v kontextu pouze pro reflexi, použijte <xref:System.Reflection.CustomAttributeData> třídy.</span><span class="sxs-lookup"><span data-stu-id="47af0-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="47af0-110">Instance této třídy lze získat pomocí statické předáte příslušnému přetížení <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="47af0-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="47af0-111">V tématu [postupy: načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="47af0-111">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="47af0-112">Kontext spuštění</span><span class="sxs-lookup"><span data-stu-id="47af0-112">The Execution Context</span></span>  
 <span data-ttu-id="47af0-113">Metody reflexe hlavní atributů dotazu v kontextu spuštění <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> a <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47af0-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="47af0-114">Usnadnění vlastního atributu se kontroluje s ohledem na sestavení, ve které je připojen.</span><span class="sxs-lookup"><span data-stu-id="47af0-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="47af0-115">Jde o ekvivalent kontrola, zda metoda typu v sestavení, ve které je připojen vlastních atributů může volat konstruktor vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="47af0-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="47af0-116">Metody, jako <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> zkontrolujte viditelnost a usnadnění argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="47af0-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="47af0-117">Pouze kód v sestavení, které obsahuje uživatelsky definovaný typ. můžete načíst vlastní atribut tento typ použití **GetCustomAttributes**.</span><span class="sxs-lookup"><span data-stu-id="47af0-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="47af0-118">Následující příklad jazyka C# je návrhový vzor typické vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="47af0-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="47af0-119">Ilustruje modelu reflexe runtime vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="47af0-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
```  
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
  
 <span data-ttu-id="47af0-120">Pokud při pokusu o načtení vlastní atributy pro veřejné vlastní typ atributu je v modulu runtime <xref:System.ComponentModel.DescriptionAttribute> připojené k **GetLanguage** metoda, provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="47af0-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1.  <span data-ttu-id="47af0-121">Modul runtime kontroluje, zda argument typu **DescriptionAttribute** k **Type.GetCustomAttributes**(typ *typu*) je veřejný a proto je viditelná a přístupné.</span><span class="sxs-lookup"><span data-stu-id="47af0-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2.  <span data-ttu-id="47af0-122">Modul runtime kontroluje, zda uživatelem definovaný typ **MyDescriptionAttribute** je odvozena z **DescriptionAttribute** viditelné a zda je dostupný v rámci **System.Web.DLL**sestavení, kde je připojen k metodě **GetLanguage**().</span><span class="sxs-lookup"><span data-stu-id="47af0-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3.  <span data-ttu-id="47af0-123">Modul runtime kontroluje, zda konstruktoru **MyDescriptionAttribute** viditelné a zda je dostupný v rámci **System.Web.DLL** sestavení.</span><span class="sxs-lookup"><span data-stu-id="47af0-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4.  <span data-ttu-id="47af0-124">Modul runtime volání konstruktoru **MyDescriptionAttribute** s parametry vlastních atributů a vrací nový objekt volajícímu.</span><span class="sxs-lookup"><span data-stu-id="47af0-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="47af0-125">Model reflexe vlastních atributů může úniku instancí uživatelem definované typy mimo sestavení, ve kterém je definovaný typ.</span><span class="sxs-lookup"><span data-stu-id="47af0-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="47af0-126">Nijak se to neliší od členů v knihovně system runtime, které vracejí instancí uživatelem definované typy, jako například <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> vrací pole **RuntimeMethodInfo** objekty.</span><span class="sxs-lookup"><span data-stu-id="47af0-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="47af0-127">Členy typu být neveřejní definujte v případě, že aby klienta z zjišťování informací o uživateli definované vlastního typu atributu.</span><span class="sxs-lookup"><span data-stu-id="47af0-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="47af0-128">Následující příklad ukazuje základní způsob použití reflexe získat přístup k vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="47af0-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="47af0-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="47af0-129">See Also</span></span>  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="47af0-130">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="47af0-130">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [<span data-ttu-id="47af0-131">Důležité informace o zabezpečení pro reflexi</span><span class="sxs-lookup"><span data-stu-id="47af0-131">Security Considerations for Reflection</span></span>](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
