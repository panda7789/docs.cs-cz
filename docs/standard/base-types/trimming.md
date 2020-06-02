---
title: Ořezávání a odstraňování znaků z řetězců v .NET
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
ms.openlocfilehash: 0777ba7348d13697fd53f556ac69cba3f98d1e4d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290873"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Ořezávání a odstraňování znaků z řetězců v .NET
Pokud analyzujete větu na jednotlivá slova, může se stát, že se na konci slova dokončí slova, která obsahují prázdné mezery (označované také jako prázdné znaky). V této situaci můžete použít jednu z metod Trim třídy **System. String** k odebrání libovolného počtu mezer nebo jiných znaků ze zadané pozice v řetězci. Následující tabulka popisuje dostupné metody Trim.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Odstraní prázdné znaky nebo znaky zadané v poli znaků od začátku a konce řetězce.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Odebere znaky zadané v poli znaků z konce řetězce.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Odebere znaky zadané v poli znaků od začátku řetězce.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Odebere zadaný počet znaků ze zadané pozice indexu v řetězci.|  
  
## <a name="trim"></a>Trim

 Pomocí metody lze snadno odebrat prázdné znaky z obou konců řetězce <xref:System.String.Trim%2A?displayProperty=nameWithType> , jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Můžete také odebrat znaky, které zadáte v poli znaků od začátku a konce řetězce. Následující příklad odebere prázdné znaky, tečky a hvězdičky.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>TrimEnd

 Metoda **String. TrimEnd** odstraní znaky z konce řetězce a vytvoří nový objekt řetězce. Pole znaků je předáno této metodě pro určení znaků, které mají být odebrány. Pořadí prvků v poli znaků nemá vliv na operaci ořezávání. Ořezávání se zastaví, když se najde znak, který není zadaný v poli.  
  
 Následující příklad odebere poslední písmena řetězce pomocí metody **trimEnd** . V tomto příkladu je pozice `'r'` znaku a `'W'` znaku obrácena k ilustraci, že pořadí znaků v poli nezáleží. Všimněte si, že tento kód odstraní poslední slovo `MyString` a část první.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Tento kód `He` se zobrazí v konzole nástroje.  
  
 Následující příklad odebere poslední slovo řetězce pomocí metody **trimEnd** . V tomto kódu čárka následuje za slovem `Hello` a, protože čárka není určena v poli znaků, které mají být oříznuty, ořezávání končí čárkou.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Tento kód `Hello,` se zobrazí v konzole nástroje.  
  
## <a name="trimstart"></a>TrimStart

 Metoda **String. TrimStart** je podobná metodě **String. TrimEnd** s tím rozdílem, že vytvoří nový řetězec odebráním znaků ze začátku existujícího objektu řetězce. Pole znaků je předáno metodě **trimStart** pro určení znaků, které mají být odebrány. Stejně jako u metody **trimEnd** nemá pořadí prvků v poli znaků vliv na operaci ořezávání. Ořezávání se zastaví, když se najde znak, který není zadaný v poli.  
  
 Následující příklad odebere první slovo řetězce. V tomto příkladu je pozice `'l'` znaku a `'H'` znaku obrácena k ilustraci, že pořadí znaků v poli nezáleží.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Tento kód `World!` se zobrazí v konzole nástroje.  
  
## <a name="remove"></a>Odebrat

 <xref:System.String.Remove%2A?displayProperty=nameWithType>Metoda odstraní zadaný počet znaků, který začíná na zadané pozici v existujícím řetězci. Tato metoda předpokládá index založený na nule.  
  
 Následující příklad odebere deset znaků z řetězce, který začíná na pozici pět nul indexu řetězce.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a>Nahradit

 Můžete také odebrat zadaný znak nebo podřetězec z řetězce voláním <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody a zadáním prázdného řetězce ( <xref:System.String.Empty?displayProperty=nameWithType> ) jako náhrady. Následující příklad odebere všechny čárky z řetězce.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](basic-string-operations.md)
