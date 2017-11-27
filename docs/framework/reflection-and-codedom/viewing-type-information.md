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
# <a name="viewing-type-information"></a>Zobrazení informací o typu
<xref:System.Type?displayProperty=nameWithType> Třída je důležitá pro reflexe. Vytvoří modul common language runtime **typ** pro načíst typ v případě reflexe požaduje. Můžete použít **typ** metody, polí, vlastnosti a vnořené třídy a zjistěte všechny údaje o typu objektu.  
  
 Použití <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> získat **typ** objekty ze sestavení, které nebyly načteny, předání názvu typ nebo typy, které chcete. Použití <xref:System.Type.GetType%2A?displayProperty=nameWithType> získat **typ** objekty z sestavení, které je již načten. Použití <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> a <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> získat modul **typ** objekty.  
  
> [!NOTE]
>  Pokud chcete prozkoumat a upravit obecné typy a metody, naleznete další informace v [reflexe a obecné typy](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) a [postup: Zkontrolujte a vytvořit instance obecných typů pomocí reflexe](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Následující příklad ukazuje syntaxi nutné <xref:System.Reflection.Assembly> objekt a modul pro sestavení.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 Následující příklad ukazuje získání **typ** objekty z načíst sestavení.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Po získání **typu**, existuje mnoho způsobů, můžete zjistit informace o členech daného typu. Například můžete zjistit členy všechny typu voláním <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metoda, která získává pole <xref:System.Reflection.MemberInfo> objekty, které popisují každou členy aktuální typu.  
  
 Můžete také použít metody na **typ** třídy k načtení informací o jeden nebo více konstruktory, metody, události, pole nebo vlastnosti, které určíte podle názvu. Například <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> zapouzdří konkrétní konstruktor aktuální třídy.  
  
 Pokud máte **typ**, můžete použít <xref:System.Type.Module%2A?displayProperty=nameWithType> vlastnost získat objekt, který zapouzdří modul, který obsahuje typu. Použití <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> vlastnost vyhledat objekt, který zapouzdřuje sestavení obsahující modul. Můžete získat sestavení, který zapouzdřuje typ přímo pomocí <xref:System.Type.Assembly%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="systemtype-and-constructorinfo"></a>System.Type a ConstructorInfo  
 Následující příklad ukazuje, jak zobrazit konstruktorů třídy v tomto případě <xref:System.String> třídy.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo –, MethodInfo, FieldInfo a PropertyInfo  
 Získání informací o typu metody, vlastnosti, události a polí pomocí <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, nebo <xref:System.Reflection.PropertyInfo> objekty.  
  
 Následující příklad používá **MemberInfo –** seznam počet členů v **System.IO.File** třídy a používá <xref:System.Type.IsPublic%2A> vlastnosti k určení, zda se třída.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 Následující příklad prozkoumá typ zadaného člena. Provede reflexe na členem **MemberInfo –** třídy a vypíše typ.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 Následující příklad používá všechny reflexe  **\*informace** tříd spolu s <xref:System.Reflection.BindingFlags> seznam všech členů (konstruktory, pole, vlastnosti, události a metody) pro zadanou třídu dělení členy do statické a instanci kategorie.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Viz také  
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
 [Reflexe a obecné typy](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
