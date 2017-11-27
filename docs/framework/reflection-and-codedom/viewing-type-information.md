---
title: "Zobrazení informací o typu"
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
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5f6051c3da274c6a8579516e073c0ea91a195d59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="viewing-type-information"></a><span data-ttu-id="611a5-102">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="611a5-102">Viewing Type Information</span></span>
<span data-ttu-id="611a5-103"><xref:System.Type?displayProperty=nameWithType> Třída je důležitá pro reflexe.</span><span class="sxs-lookup"><span data-stu-id="611a5-103">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="611a5-104">Vytvoří modul common language runtime **typ** pro načíst typ v případě reflexe požaduje.</span><span class="sxs-lookup"><span data-stu-id="611a5-104">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="611a5-105">Můžete použít **typ** metody, polí, vlastnosti a vnořené třídy a zjistěte všechny údaje o typu objektu.</span><span class="sxs-lookup"><span data-stu-id="611a5-105">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="611a5-106">Použití <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> získat **typ** objekty ze sestavení, které nebyly načteny, předání názvu typ nebo typy, které chcete.</span><span class="sxs-lookup"><span data-stu-id="611a5-106">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="611a5-107">Použití <xref:System.Type.GetType%2A?displayProperty=nameWithType> získat **typ** objekty z sestavení, které je již načten.</span><span class="sxs-lookup"><span data-stu-id="611a5-107">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="611a5-108">Použití <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> a <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> získat modul **typ** objekty.</span><span class="sxs-lookup"><span data-stu-id="611a5-108">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="611a5-109">Pokud chcete prozkoumat a upravit obecné typy a metody, naleznete další informace v [reflexe a obecné typy](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) a [postup: Zkontrolujte a vytvořit instance obecných typů pomocí reflexe](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="611a5-109">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="611a5-110">Následující příklad ukazuje syntaxi nutné <xref:System.Reflection.Assembly> objekt a modul pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="611a5-110">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="611a5-111">Následující příklad ukazuje získání **typ** objekty z načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="611a5-111">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="611a5-112">Po získání **typu**, existuje mnoho způsobů, můžete zjistit informace o členech daného typu.</span><span class="sxs-lookup"><span data-stu-id="611a5-112">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="611a5-113">Například můžete zjistit členy všechny typu voláním <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metoda, která získává pole <xref:System.Reflection.MemberInfo> objekty, které popisují každou členy aktuální typu.</span><span class="sxs-lookup"><span data-stu-id="611a5-113">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="611a5-114">Můžete také použít metody na **typ** třídy k načtení informací o jeden nebo více konstruktory, metody, události, pole nebo vlastnosti, které určíte podle názvu.</span><span class="sxs-lookup"><span data-stu-id="611a5-114">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="611a5-115">Například <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> zapouzdří konkrétní konstruktor aktuální třídy.</span><span class="sxs-lookup"><span data-stu-id="611a5-115">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="611a5-116">Pokud máte **typ**, můžete použít <xref:System.Type.Module%2A?displayProperty=nameWithType> vlastnost získat objekt, který zapouzdří modul, který obsahuje typu.</span><span class="sxs-lookup"><span data-stu-id="611a5-116">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="611a5-117">Použití <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> vlastnost vyhledat objekt, který zapouzdřuje sestavení obsahující modul.</span><span class="sxs-lookup"><span data-stu-id="611a5-117">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="611a5-118">Můžete získat sestavení, který zapouzdřuje typ přímo pomocí <xref:System.Type.Assembly%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="611a5-118">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="611a5-119">System.Type a ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="611a5-119">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="611a5-120">Následující příklad ukazuje, jak zobrazit konstruktorů třídy v tomto případě <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="611a5-120">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="611a5-121">MemberInfo –, MethodInfo, FieldInfo a PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="611a5-121">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="611a5-122">Získání informací o typu metody, vlastnosti, události a polí pomocí <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, nebo <xref:System.Reflection.PropertyInfo> objekty.</span><span class="sxs-lookup"><span data-stu-id="611a5-122">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="611a5-123">Následující příklad používá **MemberInfo –** seznam počet členů v **System.IO.File** třídy a používá <xref:System.Type.IsPublic%2A> vlastnosti k určení, zda se třída.</span><span class="sxs-lookup"><span data-stu-id="611a5-123">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="611a5-124">Následující příklad prozkoumá typ zadaného člena.</span><span class="sxs-lookup"><span data-stu-id="611a5-124">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="611a5-125">Provede reflexe na členem **MemberInfo –** třídy a vypíše typ.</span><span class="sxs-lookup"><span data-stu-id="611a5-125">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="611a5-126">Následující příklad používá všechny reflexe  **\*informace** tříd spolu s <xref:System.Reflection.BindingFlags> seznam všech členů (konstruktory, pole, vlastnosti, události a metody) pro zadanou třídu dělení členy do statické a instanci kategorie.</span><span class="sxs-lookup"><span data-stu-id="611a5-126">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="611a5-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="611a5-127">See Also</span></span>  
 <xref:System.Reflection.BindingFlags>  
 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetFields%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.MemberInfo>  
 <xref:System.Reflection.ConstructorInfo>  
 <xref:System.Reflection.MethodInfo>  
 <xref:System.Reflection.FieldInfo>  
 <xref:System.Reflection.EventInfo>  
 <xref:System.Reflection.ParameterInfo>  
 [<span data-ttu-id="611a5-128">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="611a5-128">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
