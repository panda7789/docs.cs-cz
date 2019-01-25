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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb537950ce240d77282551f847b637a77792a264
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645233"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="60e89-102">Přístup k vlastním atributům</span><span class="sxs-lookup"><span data-stu-id="60e89-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="60e89-103">Po atributy byly spojeny s prvky programu, reflexe je možné zadávat dotazy na jejich existence a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="60e89-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="60e89-104">V rozhraní .NET Framework verze 1.0 a 1.1 uživatelských atributů, které jsou zkoumány podle kontextu spuštění.</span><span class="sxs-lookup"><span data-stu-id="60e89-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="60e89-105">Rozhraní .NET Framework verze 2.0 obsahuje nový kontext načtení kontextu pouze pro reflexi, který slouží ke kontrole kódu, který nelze načíst pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="60e89-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="60e89-106">Kontextu pouze pro reflexi</span><span class="sxs-lookup"><span data-stu-id="60e89-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="60e89-107">Nelze spustit kód načtený do kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="60e89-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="60e89-108">To znamená, že nelze vytvořit instance vlastních atributů, protože, které by vyžadovaly provádění jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="60e89-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="60e89-109">Chcete-li načíst a zkontrolovat vlastních atributů v kontextu pouze pro reflexi, použijte <xref:System.Reflection.CustomAttributeData> třídy.</span><span class="sxs-lookup"><span data-stu-id="60e89-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="60e89-110">Instance této třídy lze získat pomocí odpovídající přetížení statické <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="60e89-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="60e89-111">Zobrazit [jak: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="60e89-111">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="60e89-112">Kontext spuštění</span><span class="sxs-lookup"><span data-stu-id="60e89-112">The Execution Context</span></span>  
 <span data-ttu-id="60e89-113">Metody reflexe hlavní atributy dotazu v kontextu spuštění jsou <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> a <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="60e89-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="60e89-114">Usnadnění vlastního atributu je zaškrtnuté políčko s ohledem na sestavení, ve které je připojené.</span><span class="sxs-lookup"><span data-stu-id="60e89-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="60e89-115">Jde o ekvivalent kontroluje, zda můžete volat metody pro typ v sestavení, ve kterém je vlastní atribut připojen konstruktoru vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="60e89-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="60e89-116">Metody jako <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> zkontrolujte viditelnost a přístupnost typu argumentu.</span><span class="sxs-lookup"><span data-stu-id="60e89-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="60e89-117">Pouze pro kód v sestavení, který obsahuje uživatelem definovaný typ může načíst vlastní atribut pomocí tohoto typu **GetCustomAttributes**.</span><span class="sxs-lookup"><span data-stu-id="60e89-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="60e89-118">Následující C# příklad je vzor návrh typický vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="60e89-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="60e89-119">Ilustruje modelu reflexe runtime vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="60e89-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
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
  
 <span data-ttu-id="60e89-120">Pokud při pokusu o načtení vlastních atributů pro veřejné vlastní typ atributu je v modulu runtime <xref:System.ComponentModel.DescriptionAttribute> připojené k **getlanguage –** metoda, provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="60e89-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1.  <span data-ttu-id="60e89-121">Modul runtime kontroluje, že argument typu **DescriptionAttribute** k **Type.GetCustomAttributes**(typ *typ*) je veřejná a proto je viditelný a přístupný.</span><span class="sxs-lookup"><span data-stu-id="60e89-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2.  <span data-ttu-id="60e89-122">Modul runtime kontroluje, zda uživatelský typ **MyDescriptionAttribute** , která je odvozena od **DescriptionAttribute** je viditelný a přístupný v rámci **System.Web.DLL**sestavení, ve kterém je připojen k metodě **getlanguage –**().</span><span class="sxs-lookup"><span data-stu-id="60e89-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3.  <span data-ttu-id="60e89-123">Modul runtime kontroluje, že konstruktor třídy **MyDescriptionAttribute** je viditelný a přístupný v rámci **System.Web.DLL** sestavení.</span><span class="sxs-lookup"><span data-stu-id="60e89-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4.  <span data-ttu-id="60e89-124">Modul runtime volá konstruktor třídy **MyDescriptionAttribute** s parametry, které vlastní atribut a vrátí nový objekt volajícímu.</span><span class="sxs-lookup"><span data-stu-id="60e89-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="60e89-125">Model reflexe vlastních atributů může způsobit únik těchto instance uživatelsky definované typy mimo sestavení, ve kterém je typ definován.</span><span class="sxs-lookup"><span data-stu-id="60e89-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="60e89-126">To se nijak neliší od členů v knihovně modulu runtime systému, které vracejí výskyty uživatelem definované typy, jako například <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> vrací pole **RuntimeMethodInfo** objekty.</span><span class="sxs-lookup"><span data-stu-id="60e89-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="60e89-127">Aby klient zjišťování informací o typu uživatelem definované vlastní atribut definujte členy tohoto typu bude neveřejné.</span><span class="sxs-lookup"><span data-stu-id="60e89-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="60e89-128">Následující příklad ukazuje základní způsob, jak získat přístup k vlastní atributy pomocí operace reflection.</span><span class="sxs-lookup"><span data-stu-id="60e89-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="60e89-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60e89-129">See also</span></span>
- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="60e89-130">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="60e89-130">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="60e89-131">Důležité informace o zabezpečení pro reflexi</span><span class="sxs-lookup"><span data-stu-id="60e89-131">Security Considerations for Reflection</span></span>](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
