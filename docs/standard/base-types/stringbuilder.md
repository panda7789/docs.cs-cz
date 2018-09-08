---
title: Používání třídy StringBuilder v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 099e2de40458e42c9df34e74dee8d9fc7c425dea
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197311"
---
# <a name="using-the-stringbuilder-class-in-net"></a>Používání třídy StringBuilder v .NET
<xref:System.String> Objektu je neměnný. Pokaždé, když používáte jednu z metod v <xref:System.String?displayProperty=nameWithType> třídy, můžete vytvořit nový objekt řetězce v paměti, která vyžaduje nové přidělení místa pro tento nový objekt. V situacích, kdy je potřeba provést opakované změny na řetězec, režie spojené s vytvořením nového <xref:System.String> objekt může být nákladné. <xref:System.Text.StringBuilder?displayProperty=nameWithType> Třídu lze použít, pokud chcete upravit řetězec bez vytvoření nového objektu. Například použití <xref:System.Text.StringBuilder> třída může zvýšit výkon při zřetězení řetězců mnoho společně ve smyčce.  
  
## <a name="importing-the-systemtext-namespace"></a>Import Namespace System.Text slouží  
 <xref:System.Text.StringBuilder> Třídy se nachází v <xref:System.Text> oboru názvů.  Abyste nemuseli jako úplný název ve vašem kódu, můžete importovat <xref:System.Text> obor názvů:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Vytvoření instance objektu StringBuilder  
 Můžete vytvořit novou instanci třídy <xref:System.Text.StringBuilder> třídy inicializaci proměnné s některou z přetížených metod konstruktoru, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Nastavení kapacity a délka  
 I když <xref:System.Text.StringBuilder> je dynamický objekt, který umožňuje rozšířit počet znaků v řetězci, který zapouzdřuje, můžete zadat hodnotu pro maximální počet znaků, které může obsahovat. Tato hodnota se nazývá Capacity kapacita objektu a neměly by být zaměňovány délku řetězce, který aktuální <xref:System.Text.StringBuilder> obsahuje. Například může vytvořit novou instanci třídy <xref:System.Text.StringBuilder> třídy pomocí řetězce "Hello", který má délku 5 kde můžete určit, že objekt má maximální kapacitu 25. Při změně <xref:System.Text.StringBuilder>, to není přidělit jinému uživateli velikost pro samotný dokud není dosaženo kapacity. Pokud k tomu dojde, je automaticky přiděleno nové místo a kapacita se zdvojnásobí. Můžete určit kapacitu <xref:System.Text.StringBuilder> třídy pomocí některé z přetížených konstruktorů. Následující příklad určuje, že `myStringBuilder` objektu lze rozšířit na maximální počet 25 mezery.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Kromě toho můžete použít ke čtení a zápisu <xref:System.Text.StringBuilder.Capacity%2A> vlastnosti chcete nastavit maximální délku objektu. V následujícím příkladu **kapacity** vlastnost pro definování maximální délky objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A> Metoda lze použít ke kontrole aktuální kapacita **StringBuilder**. Pokud je kapacita větší než hodnota předaná, se neprovedly žádné změny, Pokud kapacita je menší než hodnotu úspěch, aktuální kapacita změnit tak, aby odpovídaly předané hodnoty.  
  
 <xref:System.Text.StringBuilder.Length%2A> Vlastnosti také můžete zobrazit nebo nastavit. Pokud jste nastavili **délka** vlastnost na hodnotu, která je větší než **kapacity** vlastnost, **kapacity** vlastností se automaticky změní na stejnou hodnotu jako  **Délka** vlastnost. Nastavení **délka** vlastnost na hodnotu, která je menší než délka řetězce v aktuálním **StringBuilder** zkrátí řetězec.  
  
## <a name="modifying-the-stringbuilder-string"></a>Úprava řetězce StringBuilder  
 Následující tabulka shrnuje metody, můžete použít k úpravě obsahu **StringBuilder**.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Připojí na konec aktuálního informace **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Nahradí specifikátoru formátu předaný řetězec formátovaný text.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Vloží zadaný index aktuálního řetězec nebo objekt **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Odebere zadaný počet znaků z aktuální **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Nahradí zadaný znak na zadaném indexu.|  
  
### <a name="append"></a>Připojení  
 **Append** metodu je možné do konce řetězce reprezentované aktuální přidat text nebo řetězcová reprezentace objektu **StringBuilder**. Následující příklad inicializuje **StringBuilder** na "Hello World" a potom připojí na konec objektu nějaký text. Automaticky podle potřeby není přiděleno místo.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat –  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> Metoda přidá na konec textu <xref:System.Text.StringBuilder> objektu. Podporuje funkci složeného formátování (Další informace najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md)) voláním <xref:System.IFormattable> implementace objektů má být formátováno. Proto se přijme standardní formátovací řetězce pro číselné, datum a čas a výčet hodnot, vlastní formátovací řetězce pro číselné a hodnoty data a času a řetězce formátu definované pro vlastní typy. (Informace o formátování najdete v tématu [Formatting Types](../../../docs/standard/base-types/formatting-types.md).) Můžete použít tuto metodu můžete přizpůsobit formát proměnné a přidat tyto hodnoty <xref:System.Text.StringBuilder>. V následujícím příkladu <xref:System.Text.StringBuilder.AppendFormat%2A> metodu pro umístění celočíselné hodnoty formátovaný jako hodnota měny na konci <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Insert  
 <xref:System.Text.StringBuilder.Insert%2A> Metoda přidá řetězec nebo objekt do zadané pozice v aktuální <xref:System.Text.StringBuilder> objektu. Následující příklad používá tuto metodu k vložení do šestého pozice slovo <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>odebrat  
 Můžete použít **odebrat** metoda odebrání zadaný počet znaků z aktuální <xref:System.Text.StringBuilder> objektů, počínaje zadaným indexem. V následujícím příkladu **odebrat** metoda ke zkrácení <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>nahradit  
 **Nahradit** metodu lze použít k nahrazení znaků v rámci <xref:System.Text.StringBuilder> objekt s jiným zadaný znak. V následujícím příkladu **nahradit** metody na hledání <xref:System.Text.StringBuilder> objektu pro všemi instancemi vykřičník znak (!) a nahraďte znak otazníku (?).  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Převod objektu StringBuilder na řetězec  
 Je nutné převést <xref:System.Text.StringBuilder> do objektu <xref:System.String> objektu před předáním řetězce reprezentována <xref:System.Text.StringBuilder> objekt pro metodu, která má <xref:System.String> parametr nebo zobrazit v uživatelském rozhraní. Tento převod lze provést zavoláním <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> metody. Následující příklad volá celou řadou <xref:System.Text.StringBuilder> metody a pak zavolá <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> metodu pro zobrazení řetězce.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)  
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
