---
title: Zobrazení informací o typu
description: Zobrazení informací o typu pomocí System. Type, což je centrální odraz v .NET. Zkontrolujte ConstructorInfo, MemberInfo, MethodInfo, FieldInfo a PropertyInfo.
ms.date: 03/30/2017
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
ms.openlocfilehash: cd74021e1f1a79626e171db13def98e546cd51df
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865200"
---
# <a name="viewing-type-information"></a><span data-ttu-id="ca426-104">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="ca426-104">Viewing Type Information</span></span>
<span data-ttu-id="ca426-105"><xref:System.Type?displayProperty=nameWithType>Třída je od střední k reflexi.</span><span class="sxs-lookup"><span data-stu-id="ca426-105">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="ca426-106">Modul CLR (Common Language Runtime) vytvoří **typ** načteného typu, když ho požádá o reflexi.</span><span class="sxs-lookup"><span data-stu-id="ca426-106">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="ca426-107">Můžete použít metody, pole, vlastnosti a vnořené třídy **typu** objektu, abyste zjistili vše o tomto typu.</span><span class="sxs-lookup"><span data-stu-id="ca426-107">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="ca426-108">Použijte <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> k získání objektů **typu** ze sestavení, která nebyla načtena, předejte název typu nebo typy, které chcete.</span><span class="sxs-lookup"><span data-stu-id="ca426-108">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="ca426-109">Slouží <xref:System.Type.GetType%2A?displayProperty=nameWithType> k získání **typu** objektů ze sestavení, které je již načteno.</span><span class="sxs-lookup"><span data-stu-id="ca426-109">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="ca426-110">Použijte <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> a <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> k získání objektů **typu** modulu.</span><span class="sxs-lookup"><span data-stu-id="ca426-110">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca426-111">Pokud chcete prošetřit a manipulovat s obecnými typy a metodami, přečtěte si další informace, které jsou k dispozici v [reflexi a obecných typech](reflection-and-generic-types.md) a [Postupy: prostudování a vytváření instancí obecných typů pomocí reflexe](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="ca426-111">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="ca426-112">Následující příklad ukazuje syntaxi nutnou k získání <xref:System.Reflection.Assembly> objektu a modulu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca426-112">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="ca426-113">Následující příklad ukazuje, jak načíst objekty **typu** z načteného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca426-113">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="ca426-114">Jakmile získáte **typ**, existuje mnoho způsobů, jak můžete zjistit informace o členech tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="ca426-114">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="ca426-115">Můžete například získat informace o všech členech typu voláním <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metody, která získá pole <xref:System.Reflection.MemberInfo> objektů popisujících každého z členů aktuálního typu.</span><span class="sxs-lookup"><span data-stu-id="ca426-115">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="ca426-116">Můžete také použít metody třídy **Type** pro načtení informací o jednom nebo více konstruktorech, metodách, událostech, polích nebo vlastnostech, které určíte podle názvu.</span><span class="sxs-lookup"><span data-stu-id="ca426-116">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="ca426-117">Například <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> zapouzdřuje konkrétní konstruktor aktuální třídy.</span><span class="sxs-lookup"><span data-stu-id="ca426-117">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="ca426-118">Pokud máte **typ**, můžete použít <xref:System.Type.Module%2A?displayProperty=nameWithType> vlastnost k získání objektu, který zapouzdřuje modul obsahující tento typ.</span><span class="sxs-lookup"><span data-stu-id="ca426-118">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="ca426-119">Pomocí <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> Vlastnosti vyhledejte objekt, který zapouzdřuje sestavení obsahující modul.</span><span class="sxs-lookup"><span data-stu-id="ca426-119">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="ca426-120">Sestavení, které zapouzdřuje typ, lze získat přímo pomocí <xref:System.Type.Assembly%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ca426-120">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="ca426-121">System. Type a ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="ca426-121">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="ca426-122">Následující příklad ukazuje, jak vytvořit seznam konstruktorů pro třídu, v tomto případě <xref:System.String> Třída.</span><span class="sxs-lookup"><span data-stu-id="ca426-122">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="ca426-123">MemberInfo, MethodInfo, FieldInfo a PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="ca426-123">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="ca426-124">Získejte informace o metodách, vlastnostech, událostech a polích typu pomocí <xref:System.Reflection.MemberInfo> objektů, <xref:System.Reflection.MethodInfo> , <xref:System.Reflection.FieldInfo> nebo <xref:System.Reflection.PropertyInfo> .</span><span class="sxs-lookup"><span data-stu-id="ca426-124">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="ca426-125">Následující příklad používá **MemberInfo** pro výpis počtu členů ve třídě **System. IO. File** a používá <xref:System.Type.IsPublic%2A> vlastnost k určení viditelnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="ca426-125">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="ca426-126">Následující příklad prozkoumá typ zadaného člena.</span><span class="sxs-lookup"><span data-stu-id="ca426-126">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="ca426-127">Provádí reflexi člena třídy **MemberInfo** a seznam jeho typu.</span><span class="sxs-lookup"><span data-stu-id="ca426-127">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="ca426-128">Následující příklad používá všechny třídy \*\* \* informací o\*\* reflexi společně s <xref:System.Reflection.BindingFlags> pro výpis všech členů (konstruktory, pole, vlastnosti, události a metody) zadané třídy a rozdělení členů na kategorie static a instance.</span><span class="sxs-lookup"><span data-stu-id="ca426-128">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ca426-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca426-129">See also</span></span>

- <xref:System.Reflection.BindingFlags>
- <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>
- <xref:System.Type.GetFields%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Reflection.MemberInfo>
- <xref:System.Reflection.ConstructorInfo>
- <xref:System.Reflection.MethodInfo>
- <xref:System.Reflection.FieldInfo>
- <xref:System.Reflection.EventInfo>
- <xref:System.Reflection.ParameterInfo>
- [<span data-ttu-id="ca426-130">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="ca426-130">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
