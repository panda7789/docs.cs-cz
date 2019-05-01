---
title: Ořezávání a odebírání znaků z řetězců v .NET
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
ms.openlocfilehash: 1d13d4e115caa636e5d760b65bc98e195490f911
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965162"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Ořezávání a odebírání znaků z řetězců v .NET
Pokud analyzujete větu na jednotlivá slova, může skončit s slova, která mají mezery (také nazývané prázdné znaky) na jednom konci slovo. V takovém případě můžete použít jednu z metod uvolnění dočasné paměti v **System.String** třídy odebrat libovolný počet mezery ani jiných znaků od určené pozice v řetězci. Následující tabulka popisuje dostupné metody uvolnění dočasné paměti.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Odstraní prázdné znaky nebo znaky zadané do pole znaků ze začátku a konce řetězce.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Odebere znaky zadané do pole znaků z konce řetězce.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Odebere znaky zadané do pole znaků od začátku řetězce.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Odebere zadaný počet znaků z pozice zadaným indexem v řetězci.|  
  
## <a name="trim"></a>Trim  
 Prázdné znaky z obou směru řetězce můžete snadno odebrat pomocí <xref:System.String.Trim%2A?displayProperty=nameWithType> způsob, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Můžete také odebrat znaky, které jste zadali v pole znaků ze začátku a konce řetězce. Následující příklad odstraní prázdné znaky, tečky a hvězdičky z obou stran.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>TrimEnd  
 **String.TrimEnd** metoda odstraní znaků z konce řetězce, vytvoří nový objekt řetězce. Pole znaků je předat tuto metodu za účelem zadejte znaky, které mají být odebrány. Pořadí prvků v poli znak nemá vliv na operace uvolnění dočasné paměti. Trim přestane při nalezení znaku není určené v poli.  
  
 Následující příklad odebere poslední písmena řetězce pomocí elementu **TrimEnd** metody. V tomto příkladu pozice `'r'` znak a `'W'` přehozeny pro ilustraci, že se pořadí znaků v poli není důležitá. Všimněte si, že tento kód odebere poslední slovo `MyString` plus část první.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Tento kód zobrazí `He` do konzoly.  
  
 Následující příklad odebere poslední slovo řetězce pomocí elementu **TrimEnd** metody. V tomto kódu, následuje čárka slovo `Hello` a, protože čárka není zadána jako pole znaků, které mají být odebrány, ořezávání končí čárka.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Tento kód zobrazí `Hello,` do konzoly.  
  
## <a name="trimstart"></a>TrimStart  
 **String.TrimStart** metoda je podobná **String.TrimEnd** metoda s výjimkou, že vytvoří nový řetězec tak, že odeberete znaků od začátku existující objekt řetězce. Pole znaků je předán **TrimStart** metody zadejte znaky, které mají být odebrány. Stejně jako u **TrimEnd** metoda pořadí prvků v poli znak nemá vliv na operace uvolnění dočasné paměti. Trim přestane při nalezení znaku není určené v poli.  
  
 Následující příklad odebere první slovo řetězce. V tomto příkladu pozice `'l'` znak a `'H'` přehozeny pro ilustraci, že se pořadí znaků v poli není důležitá.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Tento kód zobrazí `World!` do konzoly.  
  
## <a name="remove"></a>odebrat  
 <xref:System.String.Remove%2A?displayProperty=nameWithType> Metoda odstraní zadaný počet znaků, které začínají na určenou pozici do existujícího řetězce. Tato metoda předpokládá index založený na nule.  
  
 Následující příklad odebere deset znaků od začátku řetězce na pozici pět z nuly vycházející index řetězce.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 Můžete také odebrat zadaný znak nebo podřetězec z řetězce pomocí volání <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda a zadáte prázdný řetězec (<xref:System.String.Empty?displayProperty=nameWithType>) jako náhrada. Následující příklad odebere všechny mezery v řetězci.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Viz také:

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
