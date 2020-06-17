---
title: Použití třídy StringBuilder v .NET
description: Naučte se používat třídu StringBuilder v .NET. Tato třída slouží k úpravě řetězce bez vytvoření nového objektu.
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
ms.openlocfilehash: 83d4b9327b55c511e2a46486e519e3cd0c77b1a3
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803229"
---
# <a name="using-the-stringbuilder-class-in-net"></a>Použití třídy StringBuilder v .NET
<xref:System.String>Objekt je neměnný. Pokaždé, když použijete jednu z metod ve <xref:System.String?displayProperty=nameWithType> třídě, vytvoříte nový objekt String v paměti, který vyžaduje nové přidělení místa pro tento nový objekt. V situacích, kdy potřebujete provést opakované úpravy řetězce, může být režie spojená s vytvářením nového <xref:System.String> objektu náročná. <xref:System.Text.StringBuilder?displayProperty=nameWithType>Třída může být použita, pokud chcete upravit řetězec bez vytvoření nového objektu. Například použití <xref:System.Text.StringBuilder> třídy může zvýšit výkon při zřetězení mnoha řetězců dohromady ve smyčce.  
  
## <a name="importing-the-systemtext-namespace"></a>Importuje se obor názvů System. text.  
 <xref:System.Text.StringBuilder>Třída se nachází v <xref:System.Text> oboru názvů.  Chcete-li se vyhnout nutnosti zadat plně kvalifikovaný název typu v kódu, můžete importovat <xref:System.Text> obor názvů:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Vytvoření instance objektu StringBuilder  
 Novou instanci třídy můžete vytvořit <xref:System.Text.StringBuilder> tak, že proměnnou inicializujete pomocí jedné z přetížených metod konstruktoru, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Nastavení kapacity a délky  
 I když <xref:System.Text.StringBuilder> je dynamický objekt, který umožňuje rozšířit počet znaků v řetězci, který zapouzdřuje, můžete zadat hodnotu maximálního počtu znaků, které může obsahovat. Tato hodnota se nazývá kapacita objektu a neměla by se zaměňovat s délkou řetězce, který je aktuálně <xref:System.Text.StringBuilder> uložený. Můžete například vytvořit novou instanci <xref:System.Text.StringBuilder> třídy s řetězcem "Hello", jehož délka je 5, a můžete určit, že má objekt maximální kapacitu 25. Když upravíte, nebude znovu <xref:System.Text.StringBuilder> přidělena velikost samotného, dokud nebude dosaženo kapacity. V takovém případě se nové místo přidělí automaticky a kapacita se zdvojnásobí. Můžete určit kapacitu <xref:System.Text.StringBuilder> třídy pomocí jednoho z přetížených konstruktorů. Následující příklad určuje, že `myStringBuilder` objekt lze rozšířit na maximálně 25 znaků.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Kromě toho můžete použít vlastnost pro čtení/zápis <xref:System.Text.StringBuilder.Capacity%2A> k nastavení maximální délky objektu. Následující příklad používá vlastnost **Capacity** k definování maximální délky objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A>Metoda může být použita ke kontrole kapacity aktuálního **StringBuilder**. Pokud je kapacita větší než předaná hodnota, není provedena žádná změna. Pokud je ale kapacita menší než předaná hodnota, aktuální kapacita se změní tak, aby odpovídala předané hodnotě.  
  
 <xref:System.Text.StringBuilder.Length%2A>Vlastnost lze také zobrazit nebo nastavit. Pokud nastavíte vlastnost **Length** na hodnotu, která je větší než vlastnost **Capacity** , vlastnost **Capacity** se automaticky změní na stejnou hodnotu jako vlastnost **Length** . Když nastavíte vlastnost **Length** na hodnotu, která je menší než délka řetězce v rámci aktuálního **StringBuilder** , zkrátí se řetězec.  
  
## <a name="modifying-the-stringbuilder-string"></a>Úprava řetězce StringBuilder  
 V následující tabulce jsou uvedeny metody, které lze použít k úpravě obsahu **StringBuilder**.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Připojí informace na konec aktuálního **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Nahradí specifikátor formátu předaný v řetězci s formátovaným textem.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Vloží řetězec nebo objekt do zadaného indexu aktuálního **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Odebere zadaný počet znaků z aktuálního **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Nahradí všechny výskyty zadaného znaku nebo řetězce v aktuálním **StringBuilder** pomocí jiného zadaného znaku nebo řetězce.|  
  
### <a name="append"></a>Připojit  
 Metodu **Append** lze použít k přidání textu nebo řetězcové reprezentace objektu na konec řetězce reprezentovaného aktuálním **StringBuilder**. Následující příklad inicializuje **StringBuilder** na "Hello World" a pak na konec objektu připojí nějaký text. Místo se přiděluje automaticky podle potřeby.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>Metoda přidá text na konec <xref:System.Text.StringBuilder> objektu. Podporuje funkci složeného formátování (Další informace naleznete v tématu [složené formátování](composite-formatting.md)) voláním <xref:System.IFormattable> implementace objektu nebo objektů, které mají být formátovány. Proto přijímá standardní formátovací řetězce pro číselné hodnoty, hodnoty data a času a výčty, vlastní řetězce formátu pro číselné hodnoty a hodnoty data a času a formátovací řetězce definované pro vlastní typy. (Informace o formátování naleznete v tématu [formátování typů](formatting-types.md).) Tuto metodu lze použít k přizpůsobení formátu proměnných a k připojení těchto hodnot k <xref:System.Text.StringBuilder> . Následující příklad používá <xref:System.Text.StringBuilder.AppendFormat%2A> metodu k umístění celočíselné hodnoty formátované jako hodnota měny na konci <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Vložit  
 <xref:System.Text.StringBuilder.Insert%2A>Metoda přidá řetězec nebo objekt do zadané pozice v aktuálním <xref:System.Text.StringBuilder> objektu. Následující příklad používá tuto metodu pro vložení slova do šesté pozice <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Odebrat  
 Pomocí metody **Remove** můžete odebrat zadaný počet znaků z aktuálního <xref:System.Text.StringBuilder> objektu, počínaje zadaným indexem založeným na nule. Následující příklad používá metodu **Remove** pro zkrácení <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Nahradit  
 Metodu **Replace** lze použít k nahrazení znaků v rámci <xref:System.Text.StringBuilder> objektu jiným zadaným znakem. Následující příklad používá metodu **Replace** k hledání <xref:System.Text.StringBuilder> objektu pro všechny výskyty znaku vykřičníku (!) a jejich nahrazení znakem otazníku (?).  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Převod objektu StringBuilder na řetězec  
 Objekt je nutné převést <xref:System.Text.StringBuilder> na <xref:System.String> objekt před předáním řetězce reprezentovaného <xref:System.Text.StringBuilder> objektem metodě, která má <xref:System.String> parametr nebo jej zobrazit v uživatelském rozhraní. Tento převod provedete voláním <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> metody. Následující příklad volá několik <xref:System.Text.StringBuilder> metod a poté volá <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> metodu pro zobrazení řetězce.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>
- [Základní operace s řetězci](basic-string-operations.md)
- [Typy formátování](formatting-types.md)
