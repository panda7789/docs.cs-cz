---
title: 'Příklad regulárního výrazu: vyhledávání HREF atributů'
description: Podívejte se na příklad regulárních výrazů v .NET. V příkladu se prohledá vstupní řetězec a zobrazí všechny hodnoty atributů href a jejich umístění.
ms.date: 06/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
ms.openlocfilehash: 7bcc2a4242bfaed3e3340347a30e97e7e4060794
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802846"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Příklad regulárního výrazu: vyhledávání HREF atributů
Následující příklad vyhledá vstupní řetězec a zobrazí všechny atributy href = "..." hodnoty a jejich umístění v řetězci.  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="the-regex-object"></a>Objekt Regex
 Vzhledem k tomu `DumpHRefs` , že metodu lze volat víckrát z uživatelského kódu, používá `static` metodu ( `Shared` v Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> . To umožňuje modulu regulárních výrazů ukládat do mezipaměti regulární výraz a vyhnout se režii při vytváření instancí nového <xref:System.Text.RegularExpressions.Regex> objektu pokaždé, když je metoda volána. <xref:System.Text.RegularExpressions.Match>Objekt je pak použit k iterování všech shod v řetězci.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Následující příklad ukazuje volání `DumpHRefs` metody.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Vzor regulárního výrazu `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`href`|Porovnává řetězcový literál "href". U porovnávání se nerozlišují malá a velká písmena.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`=`|Porovná znaménko rovná se.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|Porovnává jednu z následujících možností bez přiřazení výsledku k zachycené skupině:<br /> <ul><li><p>Uvozovky nebo apostrof, následované nula nebo více výskytů libovolného znaku, který je jiný než znak uvozovek nebo apostrof, následovaný znakem uvozovek nebo apostrofem. `1`V tomto vzoru je obsažena skupina s názvem.</p></li><li><p>Jeden nebo více prázdných znaků. `1`V tomto vzoru je obsažena skupina s názvem.</p></li></ul>|  
|`(?<1>[^"']*)`|Přiřaďte nula nebo více výskytů libovolného znaku jiného než uvozovky nebo apostrof na zachytávající skupinu s názvem `1` .|  
|`(?<1>\S+)`|Přiřaďte k zachycené skupině s názvem jeden nebo více neprázdných znaků `1` .|  
  
## <a name="match-result-class"></a>Shoda třídy výsledků  
 Výsledky hledání jsou uloženy ve <xref:System.Text.RegularExpressions.Match> třídě, která poskytuje přístup ke všem podřetězcům extrahovaným hledáním. Také pamatuje hledaný řetězec a používaný regulární výraz, takže může volat <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodu pro provedení jiného hledání od posledního ukončení.  
  
## <a name="explicitly-named-captures"></a>Explicitně pojmenovaná zachycení  
 V tradičních regulárních výrazech se zachytávání kulatých závorek automaticky očísluje. To vede k dvěma problémům. Za prvé, pokud je regulární výraz upraven vložením nebo odebráním sady závorek, musí být přepsán veškerý kód, který odkazuje na očíslované zachycení, aby odrážel nové číslování. Za druhé, protože různé sady kulatých závorek jsou často používány k poskytování dvou alternativních výrazů pro přijatelnou shodu, může být obtížné určit, který z těchto dvou výrazů skutečně vrátil výsledek.  
  
 Aby tato řešení vyřešila tyto problémy, <xref:System.Text.RegularExpressions.Regex> Třída podporuje syntaxi `(?<name>…)` pro zachycení shody do zadané patice (slot lze pojmenovat pomocí řetězce nebo celého čísla; celá čísla lze odvolat rychleji). Proto mohou být alternativní shody stejného řetězce směrovány na stejné místo. V případě konfliktu je poslední shoda odhozena do slotu úspěšná. (K dispozici je však úplný seznam více shod pro jednu oblast. Podrobnosti najdete v <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekci.)  
  
## <a name="see-also"></a>Viz také:

- [Regulární výrazy .NET](regular-expressions.md)
