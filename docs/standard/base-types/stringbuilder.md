---
title: "Používání třídy StringBuilder v rozhraní .NET"
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
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cf8755ae6530c22bac88d8d8c5a6e92d86432994
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="using-the-stringbuilder-class-in-net"></a>Používání třídy StringBuilder v rozhraní .NET
<xref:System.String> Objekt se nedá změnit. Pokaždé, když použijete jednu z metod v <xref:System.String?displayProperty=nameWithType> třídu, můžete vytvořit nový objekt řetězec v paměti, který vyžaduje nové přidělení místa pro tento nový objekt. V situacích, kdy potřebujete provést opakované změny řetězec, režijní náklady spojené s vytvářením novou <xref:System.String> objektu může být drahé. <xref:System.Text.StringBuilder?displayProperty=nameWithType> Třídu lze použít, pokud chcete upravit řetězec bez vytvoření nového objektu. Například pomocí <xref:System.Text.StringBuilder> třída může zvýšit výkon při zřetězení mnoha řetězců společně ve smyčce.  
  
## <a name="importing-the-systemtext-namespace"></a>Import Namespace System.Text  
 <xref:System.Text.StringBuilder> Třída se nachází v <xref:System.Text> oboru názvů.  Abyste se vyhnuli nutnosti zadejte plně kvalifikovaný typ název ve vašem kódu, můžete importovat <xref:System.Text> obor názvů:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Vytvoření instance objektu StringBuilder  
 Můžete vytvořit novou instanci třídy <xref:System.Text.StringBuilder> třída podle inicializace vaše proměnná s jedním z přetížených metod konstruktoru, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Nastavení kapacity a délky  
 I když <xref:System.Text.StringBuilder> je dynamický objekt, který umožňuje rozšířit počet znaků v řetězci, který zapouzdřit, můžete zadat hodnotu pro maximální počet znaků, které mohou být uloženy. Tato hodnota se nazývá kapacita objektu a neměla by být zaměňovat s délka řetězce, který aktuální <xref:System.Text.StringBuilder> obsahuje. Například může vytvořit novou instanci třídy <xref:System.Text.StringBuilder> třída řetězcem "Hello", který má délku 5 a může určit, že objekt obsahuje maximální kapacita 25. Při změně <xref:System.Text.StringBuilder>, ho není znovu přidělte velikost pro sebe sama dokud nebude dosaženo kapacitu. V takovém případě je automaticky přiděleno nové místo a kapacita se zdvojnásobí. Můžete zadat kapacitu <xref:System.Text.StringBuilder> třídy pomocí jedné z přetížené konstruktory. Následující příklad určuje, že `MyStringBuilder` objekt můžete rozšířit tak, aby nesmí být delší než 25 prostory.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Kromě toho můžete použít pro čtení a zápis <xref:System.Text.StringBuilder.Capacity%2A> vlastnost nastavit maximální délku objektu. Následující příklad používá **kapacity** vlastnost definovat maximální délky objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A> Metoda slouží ke kontrole kapacitu aktuální **StringBuilder**. Pokud je kapacita větší než předaná hodnota, nebudou provedeny žádné změny; Pokud je kapacita menší než hodnota předaný, aktuální kapacita změnit tak, aby odpovídala předané hodnoty.  
  
 <xref:System.Text.StringBuilder.Length%2A> Vlastnost také lze zobrazit nebo nastavit. Pokud nastavíte **délka** vlastnost na hodnotu, která je větší než **kapacity** vlastnost, **kapacity** vlastnost automaticky změní na stejnou hodnotu jako  **Délka** vlastnost. Nastavení **délka** vlastnost na hodnotu, která je menší než délka řetězce v rámci aktuální **StringBuilder** zkrátí řetězec.  
  
## <a name="modifying-the-stringbuilder-string"></a>Úprava řetězce StringBuilder  
 Následující tabulka uvádí metody můžete upravovat obsah **StringBuilder**.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Přidá na konec aktuálního informace **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Nahradí specifikátor formátu předán řetězec s formátovaný text.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Vloží zadaný index aktuálního řetězec nebo objekt **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Odebere zadaný počet znaků z aktuální **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Nahradí zadaný znak na zadaný index.|  
  
### <a name="append"></a>Připojit  
 **Připojení** metoda slouží k přidání textu nebo řetězcovou reprezentaci objektu do konce řetězce reprezentována aktuální **StringBuilder**. Tento příklad inicializuje **StringBuilder** k "Hello World" a potom připojí text na konec objektu. Automaticky podle potřeby je přiděleno místo.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat –  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> Metoda přidá na konec textu <xref:System.Text.StringBuilder> objektu. Podporuje funkci složeného formátování (Další informace najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md)) voláním <xref:System.IFormattable> implementace objektu nebo objekty, které chcete formátovat. Proto přijme standardní řetězce formátu pro číselné, datum a čas a výčet hodnot, řetězců vlastního formátu pro číselné a hodnoty data a času a řetězce formátu definované pro vlastní typy. (Informace o formátování najdete v tématu [typy formátování](../../../docs/standard/base-types/formatting-types.md).) Tuto metodu můžete použít k přizpůsobení formát proměnné a přidat tyto hodnoty do <xref:System.Text.StringBuilder>. Následující příklad používá <xref:System.Text.StringBuilder.AppendFormat%2A> metoda umístit celočíselnou hodnotu naformátovaná jako hodnota měny na konci <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Insert  
 <xref:System.Text.StringBuilder.Insert%2A> Metoda přidá řetězec nebo objekt na zadané pozici v aktuální <xref:System.Text.StringBuilder> objektu. Následující příklad používá tato metoda vložení slova do šesté pozice <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Odebrat  
 Můžete použít **odebrat** způsob odebrání zadaný počet znaků z aktuální <xref:System.Text.StringBuilder> objektů, počínaje zadaným indexem. Následující příklad používá **odebrat** metoda tak, aby zkrátil <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Nahradit  
 **Nahradit** metoda lze použít k nahrazení znaků v rámci <xref:System.Text.StringBuilder> zadaný objekt s jinou znak. Následující příklad používá **nahradit** metody na hledání <xref:System.Text.StringBuilder> objektu pro všechny instance vykřičník znak (!) a nahraďte otazník (?).  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Převádění StringBuilder objektu na řetězec  
 Je nutné převést <xref:System.Text.StringBuilder> do objektu <xref:System.String> objektu předtím, než můžete předat řetězec reprezentována <xref:System.Text.StringBuilder> objektu na metodu, která má <xref:System.String> parametr nebo zobrazit v uživatelském rozhraní. Tento převod provedete volání <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> metoda. V následujícím příkladu volání řadu <xref:System.Text.StringBuilder> metody a poté zavolá <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> metodu pro zobrazení řetězec.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
 [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
