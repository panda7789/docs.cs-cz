---
title: Oříznutí a odebrání znaků z řetězců v rozhraní .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
ms.openlocfilehash: bdbe267bb178e90c0008422e6543a23178c2c4d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159985"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Oříznutí a odebrání znaků z řetězců v rozhraní .NET
Pokud analyzujete větu na jednotlivá slova, můžete skončit se slovy, která mají prázdné mezery (nazývané také prázdné mezery) na obou koncích slova. V takovém případě můžete použít jednu z trim metody ve třídě **System.String** odebrat libovolný počet mezer nebo jiných znaků ze zadané pozice v řetězci. Následující tabulka popisuje dostupné metody oříznutí.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Odstraní bílé mezery nebo znaky zadané v poli znaků od začátku a konce řetězce.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Odebere znaky zadané v poli znaků z konce řetězce.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Odebere znaky zadané v poli znaků od začátku řetězce.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Odebere zadaný počet znaků ze zadané pozice indexu v řetězci.|  
  
## <a name="trim"></a>Trim

 Pomocí <xref:System.String.Trim%2A?displayProperty=nameWithType> metody můžete snadno odstranit prázdné znaky z obou konců řetězce, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Znaky, které zadáte v poli znaků, můžete také odebrat od začátku a konce řetězce. Následující příklad odebere prázdné znaky, tečky a hvězdičky.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>Trimend

 Metoda **String.TrimEnd** odebere znaky z konce řetězce a vytvoří nový objekt řetězce. Pole znaků je předán a tato metoda určit znaky, které mají být odebrány. Pořadí prvků v poli znaků nemá vliv na operaci oříznutí. Oříznutí se zastaví, pokud je nalezen znak, který není zadán v poli.  
  
 Následující příklad odebere poslední písmena řetězce pomocí metody **TrimEnd.** V tomto příkladu pozice `'r'` znaku `'W'` a znaku jsou obráceny pro ilustraci, že pořadí znaků v poli nezáleží. Všimněte si, že tento `MyString` kód odebere poslední slovo plus část první.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Tento kód `He` se zobrazí do konzoly.  
  
 Následující příklad odebere poslední slovo řetězce pomocí **trimend** metody. V tomto kódu čárka následuje `Hello` slovo a protože čárka není zadána v poli znaků, které mají být oříznuty, trim končí v čárce.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Tento kód `Hello,` se zobrazí do konzoly.  
  
## <a name="trimstart"></a>Trimstart

 Metoda **String.TrimStart** je podobná metodě **String.TrimEnd** s tím rozdílem, že vytvoří nový řetězec odebráním znaků ze začátku existujícího objektu řetězce. Pole znaků je předáno metodě **TrimStart,** která určuje znaky, které mají být odebrány. Stejně jako u **TrimEnd** metoda, pořadí prvků v poli znaků nemá vliv na operaci oříznutí. Oříznutí se zastaví, pokud je nalezen znak, který není zadán v poli.  
  
 Následující příklad odebere první slovo řetězce. V tomto příkladu pozice `'l'` znaku `'H'` a znaku jsou obráceny pro ilustraci, že pořadí znaků v poli nezáleží.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Tento kód `World!` se zobrazí do konzoly.  
  
## <a name="remove"></a>Odebrat

 Metoda <xref:System.String.Remove%2A?displayProperty=nameWithType> odebere zadaný počet znaků, které začínají na zadané pozici v existujícím řetězci. Tato metoda předpokládá index založený na nule.  
  
 Následující příklad odebere deset znaků z řetězce začínajícího na pozici pět indexu řetězce založeného na nule.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a>Nahradit

 Zadaný znak nebo podřetězec můžete také odebrat <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> z řetězce voláním<xref:System.String.Empty?displayProperty=nameWithType>metody a zadáním prázdného řetězce ( ) jako náhrady. Následující příklad odebere všechny čárky z řetězce.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
