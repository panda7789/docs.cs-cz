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
ms.openlocfilehash: 2028bc8d9f160daef8afcdf881e1dfd514b4c94f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190393"
---
# <a name="viewing-type-information"></a>Zobrazení informací o typu
<xref:System.Type?displayProperty=nameWithType> Třídy je zásadním reflexe. Vytvoří modul common language runtime **typ** pro typ načtený reflexe o to požádá. Můžete použít **typ** metody, pole, vlastnosti a vnořené třídy a zjistěte všechno, co o tomto typu objektu.  
  
 Použití <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> získat **typ** objekty ze sestavení, které nebyly načteny, předejte název typu nebo typy, které chcete. Použití <xref:System.Type.GetType%2A?displayProperty=nameWithType> zobrazíte **typ** objekty ze sestavení, který je již načten. Použití <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> a <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> získat modul **typ** objekty.  
  
> [!NOTE]
>  Pokud chcete k prozkoumání a manipulaci s obecnými typy a metody, naleznete další informace uvedené v [reflexe a obecné typy](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) a [jak: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Následující příklad ukazuje syntaxi nezbytné pro uvedení <xref:System.Reflection.Assembly> objektu a modul pro sestavení.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 Následující příklad ukazuje získání **typ** objekty z načteného sestavení.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Po získání **typ**, existuje mnoho způsobů, můžete zjistit informace o členy tohoto typu. Například můžete zjistit členy všechny typu při volání <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metodu, která získá pole <xref:System.Reflection.MemberInfo> popisem jednotlivých členů aktuální typ objektů.  
  
 Můžete také použít metody na **typ** třídy k načtení informací o jeden nebo více konstruktorů, metod, události, pole nebo vlastnosti, které zadáte podle názvu. Například <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> zapouzdřuje konkrétního konstruktoru aktuální třídy.  
  
 Pokud máte **typ**, můžete použít <xref:System.Type.Module%2A?displayProperty=nameWithType> vlastnost získat objekt, který zapouzdřuje modulu, který obsahuje tohoto typu. Použití <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> vlastnost vyhledat objekt, který zapouzdřuje sestavení obsahující modul. Můžete získat sestavení, který zapouzdřuje typ přímo pomocí <xref:System.Type.Assembly%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="systemtype-and-constructorinfo"></a>System.Type a ConstructorInfo  
 Následující příklad ukazuje, jak zobrazit seznam konstruktory pro třídy, v takovém případě <xref:System.String> třídy.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo, MethodInfo, FieldInfo nebo PropertyInfo  
 Získání informací o typu metody, vlastnosti, události a pole pomocí <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, nebo <xref:System.Reflection.PropertyInfo> objekty.  
  
 Následující příklad používá **MemberInfo** počet členů v seznamu **System.IO.File** třídy a používá <xref:System.Type.IsPublic%2A> a určí, zda se třída.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 Následující příklad prozkoumá typu zadaného člena. Provádí reflexi u člena **MemberInfo** třídy a zobrazení jeho typu.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 V následujícím příkladu všechny reflexe  **\*informace** třídy společně s <xref:System.Reflection.BindingFlags> seznam členů (konstruktorů, pole, vlastnosti, události a metody) ze zadané třídy dělení členy do statické a instanci kategorie.  
  
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
