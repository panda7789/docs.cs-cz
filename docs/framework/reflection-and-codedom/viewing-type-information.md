---
title: Zobrazení informací o typu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e658b2c86eecdbc45a9adde8d28cfb890dd591b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956664"
---
# <a name="viewing-type-information"></a>Zobrazení informací o typu
Třída <xref:System.Type?displayProperty=nameWithType> je od střední k reflexi. Modul CLR (Common Language Runtime) vytvoří **typ** načteného typu, když ho požádá o reflexi. Můžete použít metody, pole, vlastnosti a vnořené třídy **typu** objektu, abyste zjistili vše o tomto typu.  
  
 Použijte <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> nebo<xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> k získání objektů **typu** ze sestavení, která nebyla načtena, předejte název typu nebo typy, které chcete. Slouží <xref:System.Type.GetType%2A?displayProperty=nameWithType> k získání **typu** objektů ze sestavení, které je již načteno. Použijte <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> a<xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> k získání objektů **typu** modulu.  
  
> [!NOTE]
> Pokud chcete prošetřit a manipulovat s obecnými typy a metodami, přečtěte si další informace, které jsou k dispozici [v reflexi [a obecných typech](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) a postupy: Prověřte a vytvořte instanci obecných typů pomocí](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)reflexe.  
  
 Následující příklad ukazuje syntaxi nutnou k získání <xref:System.Reflection.Assembly> objektu a modulu pro sestavení.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 Následující příklad ukazuje, jak načíst objekty **typu** z načteného sestavení.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Jakmile získáte **typ**, existuje mnoho způsobů, jak můžete zjistit informace o členech tohoto typu. Můžete například získat informace o všech členech typu voláním <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metody, která získá <xref:System.Reflection.MemberInfo> pole objektů popisujících každého z členů aktuálního typu.  
  
 Můžete také použít metody třídy **Type** pro načtení informací o jednom nebo více konstruktorech, metodách, událostech, polích nebo vlastnostech, které určíte podle názvu. Například <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> zapouzdřuje konkrétní konstruktor aktuální třídy.  
  
 Pokud máte **typ**, můžete použít <xref:System.Type.Module%2A?displayProperty=nameWithType> vlastnost k získání objektu, který zapouzdřuje modul obsahující tento typ. <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> Pomocí vlastnosti vyhledejte objekt, který zapouzdřuje sestavení obsahující modul. Sestavení, které zapouzdřuje typ, lze získat přímo pomocí <xref:System.Type.Assembly%2A?displayProperty=nameWithType> vlastnosti.  
  
## <a name="systemtype-and-constructorinfo"></a>System. Type a ConstructorInfo  
 Následující příklad ukazuje, jak vytvořit seznam konstruktorů pro třídu, v tomto případě <xref:System.String> třída.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo, MethodInfo, FieldInfo a PropertyInfo  
 Získejte informace <xref:System.Reflection.MemberInfo>o metodách, vlastnostech, událostech a polích typu pomocí objektů, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>nebo. <xref:System.Reflection.PropertyInfo>  
  
 Následující příklad používá **MemberInfo** pro výpis počtu členů ve třídě **System. IO. File** <xref:System.Type.IsPublic%2A> a používá vlastnost k určení viditelnosti třídy.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 Následující příklad prozkoumá typ zadaného člena. Provádí reflexi člena třídy **MemberInfo** a seznam jeho typu.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 Následující příklad používá všechny třídy  **\*informací o** reflexi společně <xref:System.Reflection.BindingFlags> s pro výpis všech členů (konstruktory, pole, vlastnosti, události a metody) zadané třídy a rozdělení členů na statické a instance. kategorie.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Viz také:

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
- [Reflexe a obecné typy](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
