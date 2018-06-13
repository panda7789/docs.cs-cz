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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02704ed5e396e973101bab4e5306d81f5a169d0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569886"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Ořezávání a odstraňování znaků z řetězců v .NET
Pokud analyzujete věty do jednotlivých slov, budete muset zvýšit slova, která mají mezery (také nazývané mezer) na obou koncích aplikace word. V takovém případě můžete použít jednu z metod trim v **System.String** třída odebrat libovolný počet mezery ani jiné znaky ze zadané pozici v řetězci. Následující tabulka popisuje dostupné metody uvolnění dočasné paměti.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Odebere mezery nebo znaky zadané v poli znaků od začátku a konce řetězce.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Odebere zadané v poli znaků od konce řetězce znaků.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Odebere zadané v poli znaků od začátku řetězce znaků.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Odebere zadaný počet znaků z pozice zadaného indexu v řetězci.|  
  
## <a name="trim"></a>Uvolnění dočasné paměti  
 Prázdné znaky z obou konců řetězce můžete snadno odebrat pomocí <xref:System.String.Trim%2A?displayProperty=nameWithType> metoda, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Můžete také odebrat znaky, které zadáte v poli znaků od začátku a konce řetězce. Následující příklad odebere prázdné znaky, tečky a hvězdičky.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>TrimEnd  
 **String.TrimEnd** metoda odebere znaků z konce řetězce a vytvoří nový objekt řetězce. Pole znaků je předán tuto metodu za účelem určení znaků, které mají být odebrány. Pořadí prvků v poli znak nemá vliv na operace uvolnění dočasné paměti. Ořezávání zastaví, když je nalezen znak není zadaný v poli.  
  
 Následující příklad odebere poslední písmena řetězec pomocí **TrimEnd** metoda. V tomto příkladu pozici `'r'` znak a `'W'` znak se vrátit k objasnění, že pořadí znaků v poli nezáleží. Všimněte si, že tento kód odstraní poslední slovo `MyString` plus součástí první.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Tento kód zobrazí `He` ke konzole.  
  
 Následující příklad odebere poslední slovo řetězec pomocí **TrimEnd** metoda. V tomto kódu čárka následuje slovo `Hello` a protože čárkou není zadané v poli znaků, oříznout, ořezávání končí čárkou.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Tento kód zobrazí `Hello,` ke konzole.  
  
## <a name="trimstart"></a>TrimStart  
 **String.TrimStart** metoda je podobná **String.TrimEnd** metoda s výjimkou, že vytvoří nový řetězec odebráním znaků od začátku existujícího objektu řetězce. Předaný pole znaků **TrimStart** metodu za účelem určení znaků, které mají být odebrány. Stejně jako u **TrimEnd** metoda pořadí prvků v poli znak nemá vliv na operace uvolnění dočasné paměti. Ořezávání zastaví, když je nalezen znak není zadaný v poli.  
  
 Následující příklad odebere první slovo řetězce. V tomto příkladu pozici `'l'` znak a `'H'` znak se vrátit k objasnění, že pořadí znaků v poli nezáleží.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Tento kód zobrazí `World!` ke konzole.  
  
## <a name="remove"></a>Odebrat  
 <xref:System.String.Remove%2A?displayProperty=nameWithType> Metoda odebere zadaný počet znaků, které začínají na zadané pozici v existujícím řetězci. Tato metoda předpokládá index počítaný od nuly.  
  
 Následující příklad odebere deset znaků z řetězce počínaje pozicí pět index počítaný od nuly řetězce.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 Rovněž můžete odebrat zadaný znak nebo dílčí řetězec z řetězce voláním <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda a zadání prázdný řetězec (<xref:System.String.Empty?displayProperty=nameWithType>) jako náhrada. Následující příklad odebere všechny čárkami v řetězci.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Viz také  
 [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
