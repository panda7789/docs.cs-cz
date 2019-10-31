---
title: Použití třídy StringBuilder v .NET
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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121681"
---
# <a name="using-the-stringbuilder-class-in-net"></a>Použití třídy StringBuilder v .NET
Objekt <xref:System.String> je neměnný. Pokaždé, když použijete jednu z metod ve třídě <xref:System.String?displayProperty=nameWithType>, vytvoříte nový objekt String v paměti, který vyžaduje nové přidělení místa pro tento nový objekt. V situacích, kdy potřebujete provést opakované změny v řetězci, režijní náklady spojené s vytvořením nového objektu <xref:System.String> mohou být nákladné. Třídu <xref:System.Text.StringBuilder?displayProperty=nameWithType> lze použít, pokud chcete upravit řetězec bez vytvoření nového objektu. Například použití třídy <xref:System.Text.StringBuilder> může zvýšit výkon při zřetězení mnoha řetězců dohromady ve smyčce.  
  
## <a name="importing-the-systemtext-namespace"></a>Importuje se obor názvů System. text.  
 Třída <xref:System.Text.StringBuilder> se nachází v oboru názvů <xref:System.Text>.  Chcete-li se vyhnout nutnosti zadat plně kvalifikovaný název typu v kódu, můžete importovat <xref:System.Text> obor názvů:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Vytvoření instance objektu StringBuilder  
 Novou instanci třídy <xref:System.Text.StringBuilder> můžete vytvořit tak, že proměnnou inicializujete pomocí jedné z přetížených metod konstruktoru, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Nastavení kapacity a délky  
 I když je <xref:System.Text.StringBuilder> dynamický objekt, který umožňuje rozšířit počet znaků v řetězci, který zapouzdřuje, můžete zadat hodnotu maximálního počtu znaků, které může obsahovat. Tato hodnota se nazývá kapacita objektu a neměla by se zaměňovat s délkou řetězce, který obsahuje aktuální <xref:System.Text.StringBuilder>. Můžete například vytvořit novou instanci třídy <xref:System.Text.StringBuilder> s řetězcem "Hello", jehož délka je 5, a můžete určit, že má objekt maximální kapacitu 25. Když upravíte <xref:System.Text.StringBuilder>, nezmění se velikost samotného, dokud nebude dosaženo kapacity. V takovém případě se nové místo přidělí automaticky a kapacita se zdvojnásobí. Můžete určit kapacitu třídy <xref:System.Text.StringBuilder> pomocí jednoho z přetížených konstruktorů. Následující příklad určuje, že objekt `myStringBuilder` lze rozšířit na maximálně 25 znaků.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Kromě toho můžete použít vlastnost pro čtení/zápis <xref:System.Text.StringBuilder.Capacity%2A> k nastavení maximální délky objektu. Následující příklad používá vlastnost **Capacity** k definování maximální délky objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 Metodu <xref:System.Text.StringBuilder.EnsureCapacity%2A> lze použít ke kontrole kapacity aktuálního **StringBuilder**. Pokud je kapacita větší než předaná hodnota, není provedena žádná změna. Pokud je ale kapacita menší než předaná hodnota, aktuální kapacita se změní tak, aby odpovídala předané hodnotě.  
  
 Vlastnost <xref:System.Text.StringBuilder.Length%2A> lze také zobrazit nebo nastavit. Pokud nastavíte vlastnost **Length** na hodnotu, která je větší než vlastnost **Capacity** , vlastnost **Capacity** se automaticky změní na stejnou hodnotu jako vlastnost **Length** . Když nastavíte vlastnost **Length** na hodnotu, která je menší než délka řetězce v rámci aktuálního **StringBuilder** , zkrátí se řetězec.  
  
## <a name="modifying-the-stringbuilder-string"></a>Úprava řetězce StringBuilder  
 V následující tabulce jsou uvedeny metody, které lze použít k úpravě obsahu **StringBuilder**.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Připojí informace na konec aktuálního **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Nahradí specifikátor formátu předaný v řetězci s formátovaným textem.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Vloží řetězec nebo objekt do zadaného indexu aktuálního **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Odebere zadaný počet znaků z aktuálního **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Nahradí zadaný znak v zadaném indexu.|  
  
### <a name="append"></a>příloh  
 Metodu **Append** lze použít k přidání textu nebo řetězcové reprezentace objektu na konec řetězce reprezentovaného aktuálním **StringBuilder**. Následující příklad inicializuje **StringBuilder** na "Hello World" a pak na konec objektu připojí nějaký text. Místo se přiděluje automaticky podle potřeby.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 Metoda <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> přidá text na konec objektu <xref:System.Text.StringBuilder>. Podporuje funkci složeného formátování (Další informace naleznete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md)) voláním <xref:System.IFormattable> implementaci objektu nebo objektů, které mají být formátovány. Proto přijímá standardní formátovací řetězce pro číselné hodnoty, hodnoty data a času a výčty, vlastní řetězce formátu pro číselné hodnoty a hodnoty data a času a formátovací řetězce definované pro vlastní typy. (Informace o formátování naleznete v tématu [formátování typů](../../../docs/standard/base-types/formatting-types.md).) Tuto metodu lze použít k přizpůsobení formátu proměnných a k připojení těchto hodnot k <xref:System.Text.StringBuilder>. Následující příklad používá metodu <xref:System.Text.StringBuilder.AppendFormat%2A> k umístění celočíselné hodnoty formátované jako hodnota měny na konci objektu <xref:System.Text.StringBuilder>.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Insert  
 Metoda <xref:System.Text.StringBuilder.Insert%2A> přidá do zadané pozice v aktuálním objektu <xref:System.Text.StringBuilder> řetězec nebo objekt. Následující příklad používá tuto metodu pro vložení slova do šesté pozice <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Odebrány  
 Pomocí metody **Remove** můžete odebrat zadaný počet znaků z aktuálního objektu <xref:System.Text.StringBuilder>, počínaje zadaným indexem založeným na nule. Následující příklad používá metodu **Remove** pro zkrácení <xref:System.Text.StringBuilder> objektu.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>náhrady  
 Metodu **Replace** lze použít k nahrazení znaků v rámci objektu <xref:System.Text.StringBuilder> jiným zadaným znakem. Následující příklad používá metodu **Replace** k hledání <xref:System.Text.StringBuilder> objektu pro všechny výskyty znaku vykřičník (!) a jejich nahrazení znakem otazníku (?).  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Převod objektu StringBuilder na řetězec  
 Objekt <xref:System.Text.StringBuilder> musíte převést na objekt <xref:System.String> předtím, než můžete předat řetězec reprezentovaný objektem <xref:System.Text.StringBuilder> metodě, která má parametr <xref:System.String> nebo jej zobrazit v uživatelském rozhraní. Tento převod provedete voláním metody <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType>. Následující příklad volá několik metod <xref:System.Text.StringBuilder> a potom zavolá metodu <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> pro zobrazení řetězce.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>
- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
