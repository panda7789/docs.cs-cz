---
title: Použití třídy StringBuilder v rozhraní .NET
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
ms.openlocfilehash: 19ee90f3300e3b610eeefd4949baa2759b834a60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121681"
---
# <a name="using-the-stringbuilder-class-in-net"></a>Použití třídy StringBuilder v rozhraní .NET
Objekt <xref:System.String> je neměnný. Pokaždé, když použijete jednu <xref:System.String?displayProperty=nameWithType> z metod ve třídě, vytvoříte nový řetězec objektu v paměti, který vyžaduje nové přidělení místa pro tento nový objekt. V situacích, kdy je třeba provést opakované změny řetězce, <xref:System.String> režie spojená s vytvořením nového objektu může být nákladné. Třídu <xref:System.Text.StringBuilder?displayProperty=nameWithType> lze použít, pokud chcete upravit řetězec bez vytvoření nového objektu. Například pomocí <xref:System.Text.StringBuilder> třídy můžete zvýšit výkon při zřetězení mnoho řetězců dohromady ve smyčce.  
  
## <a name="importing-the-systemtext-namespace"></a>Import oboru názvů System.Text  
 Třída <xref:System.Text.StringBuilder> se nachází <xref:System.Text> v oboru názvů.  Chcete-li se vyhnout nutnosti zadat plně kvalifikovaný název <xref:System.Text> typu v kódu, můžete importovat obor názvů:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Vytvoření instance objektu StringBuilder  
 Můžete vytvořit novou instanci <xref:System.Text.StringBuilder> třídy inicializací proměnné s jednou z přetížených metod konstruktoru, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Nastavení kapacity a délky  
 Přestože <xref:System.Text.StringBuilder> je dynamický objekt, který umožňuje rozbalit počet znaků v řetězci, který zapouzdřuje, můžete zadat hodnotu pro maximální počet znaků, které může obsahovat. Tato hodnota se nazývá kapacita objektu a neměla by být zaměňována s délkou řetězce, který aktuální <xref:System.Text.StringBuilder> drží. Můžete například vytvořit novou instanci <xref:System.Text.StringBuilder> třídy s řetězcem "Hello", který má délku 5 a můžete určit, že objekt má maximální kapacitu 25. Při úpravě <xref:System.Text.StringBuilder>, není přerozdělit velikost pro sebe, dokud není dosaženo kapacity. V takovém případě je nová mezera přidělena automaticky a kapacita se zdvojnásobí. Můžete určit kapacitu třídy <xref:System.Text.StringBuilder> pomocí jednoho z přetížených konstruktorů. Následující příklad určuje, `myStringBuilder` že objekt lze rozšířit na maximálně 25 mezer.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Kromě toho můžete použít vlastnost <xref:System.Text.StringBuilder.Capacity%2A> pro čtení a zápis k nastavení maximální délky objektu. Následující příklad používá **Vlastnost Capacity** k definování maximální délky objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 Metodu <xref:System.Text.StringBuilder.EnsureCapacity%2A> lze použít ke kontrole kapacity **aktuálnístringbuilder**. Pokud je kapacita větší než předaná hodnota, nedojde k žádné změně; pokud je však kapacita menší než předaná hodnota, aktuální kapacita se změní tak, aby odpovídala předané hodnotě.  
  
 Vlastnost <xref:System.Text.StringBuilder.Length%2A> lze také zobrazit nebo nastavit. Pokud nastavíte **Vlastnost Length** na hodnotu, která je větší než **Vlastnost Capacity,** vlastnost **Capacity** se automaticky změní na stejnou hodnotu jako vlastnost **Length.** Nastavení **Length** vlastnost hodnotu, která je menší než délka řetězce v rámci aktuální **StringBuilder** zkracuje řetězec.  
  
## <a name="modifying-the-stringbuilder-string"></a>Úprava řetězce StringBuilder  
 V následující tabulce jsou uvedeny metody, které můžete použít k úpravě obsahu **StringBuilder**.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Připojí informace na konec aktuální **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Nahradí specifikátor formátu předaný v řetězci formátovaný text.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Vloží řetězec nebo objekt do zadaného indexu aktuálního **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Odebere zadaný počet znaků z aktuálního **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Nahradí zadaný znak v zadaném indexu.|  
  
### <a name="append"></a>Připojit  
 **Append** Metoda slouží k přidání textu nebo řetězcové reprezentace objektu na konec řetězce reprezentovaného aktuální **StringBuilder**. Následující příklad inicializuje **StringBuilder** na "Hello World" a potom připojí nějaký text na konec objektu. Místo je přiděleno automaticky podle potřeby.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>Připojit formát  
 Metoda <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> přidá text na konec <xref:System.Text.StringBuilder> objektu. Podporuje funkci složeného formátování (další informace naleznete [v tématu Složené formátování](../../../docs/standard/base-types/composite-formatting.md)) voláním <xref:System.IFormattable> implementace objektu nebo objektů, které mají být formátovány. Proto přijímá standardní formátovací řetězce pro číselné, datum a čas a hodnoty výčtu, vlastní formátovací řetězce pro číselné a hodnoty data a času a formátovací řetězce definované pro vlastní typy. (Informace o formátování naleznete v [tématu Typy formátování](../../../docs/standard/base-types/formatting-types.md).) Pomocí této metody můžete přizpůsobit formát proměnných a připojit <xref:System.Text.StringBuilder>tyto hodnoty k aplikaci . Následující příklad používá <xref:System.Text.StringBuilder.AppendFormat%2A> metodu k umístění celé hodnoty formátované jako hodnota <xref:System.Text.StringBuilder> měny na konec objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Vložit  
 Metoda <xref:System.Text.StringBuilder.Insert%2A> přidá řetězec nebo objekt do zadané <xref:System.Text.StringBuilder> pozice v aktuálním objektu. Následující příklad používá tuto metodu k vložení slova <xref:System.Text.StringBuilder> do šesté pozice objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Odebrat  
 Metodu **Remove** můžete použít k odebrání zadaného <xref:System.Text.StringBuilder> počtu znaků z aktuálního objektu, počínaje zadaným indexem založeným na nule. Následující příklad používá **Remove** metoda <xref:System.Text.StringBuilder> zkrátit objekt.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Nahradit  
 Metodu **Replace** lze použít k <xref:System.Text.StringBuilder> nahrazení znaků v objektu jiným zadaným znakem. Následující příklad používá **metodu** Replace <xref:System.Text.StringBuilder> k hledání objektu pro všechny instance znaku vykřičníku (!)a nahraďte je znakem otazníku (?).  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Převod objektu StringBuilder na řetězec  
 Před předáním <xref:System.Text.StringBuilder> řetězce <xref:System.String> reprezentovaného <xref:System.Text.StringBuilder> objektem na metodu, <xref:System.String> která má parametr nebo jej zobrazit v uživatelském rozhraní, je nutné objekt převést na objekt. Tento převod provést voláním <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> metody. Následující příklad volá řadu <xref:System.Text.StringBuilder> metod a <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> potom volá metodu k zobrazení řetězce.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>
- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
