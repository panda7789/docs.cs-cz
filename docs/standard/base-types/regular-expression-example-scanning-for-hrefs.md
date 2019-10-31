---
title: 'Příklad regulárního výrazu: vyhledávání HREF atributů'
ms.date: 03/30/2017
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
ms.openlocfilehash: d8546980dd0cf58ca7c095750f2749d5a6bc7723
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084215"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Příklad regulárního výrazu: vyhledávání HREF atributů
Následující příklad vyhledá vstupní řetězec a zobrazí všechny atributy href = "..." hodnoty a jejich umístění v řetězci.  
  
## <a name="the-regex-object"></a>Objekt Regex  
 Vzhledem k tomu, že metoda `DumpHRefs` může být volána víckrát z uživatelského kódu, používá <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metodu `static` (`Shared` v Visual Basic). To umožňuje modulu regulárních výrazů ukládat do mezipaměti regulární výraz a vyhnout se režii při vytváření instancí nového objektu <xref:System.Text.RegularExpressions.Regex> pokaždé, když je metoda volána. Objekt <xref:System.Text.RegularExpressions.Match> se pak použije k iterování všech shod v řetězci.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Následující příklad ukazuje volání metody `DumpHRefs`.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Vzor regulárního výrazu `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`href`|Porovnává řetězcový literál "href". U porovnávání se nerozlišují malá a velká písmena.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`=`|Porovná znaménko rovná se.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|Porovnává jednu z následujících možností bez přiřazení výsledku k zachycené skupině:<br /> <ul><li><p>Uvozovky nebo apostrof, následované nula nebo více výskytů libovolného znaku, který je jiný než znak uvozovek nebo apostrof, následovaný znakem uvozovek nebo apostrofem. V tomto vzoru je obsažena skupina s názvem `1`.</p></li><li><p>Jeden nebo více prázdných znaků. V tomto vzoru je obsažena skupina s názvem `1`.</p></li></ul>|  
|`(?<1>[^"']*)`|Přiřaďte nula nebo více výskytů libovolného znaku jiného než uvozovky nebo apostrof pro zachytávající skupinu s názvem `1`.|  
|`(?<1>\S+)`|Přiřaďte do zachycující skupiny s názvem `1`jeden nebo více neprázdných znaků.|  
  
## <a name="match-result-class"></a>Shoda třídy výsledků  
 Výsledky hledání jsou uloženy ve třídě <xref:System.Text.RegularExpressions.Match>, která poskytuje přístup ke všem podřetězcům extrahovaným hledáním. Také pamatuje hledaný řetězec a používaný regulární výraz, takže může volat metodu <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> k provedení dalšího hledání, od kterého skončil poslední konec.  
  
## <a name="explicitly-named-captures"></a>Explicitně pojmenovaná zachycení  
 V tradičních regulárních výrazech se zachytávání kulatých závorek automaticky očísluje. To vede k dvěma problémům. Za prvé, pokud je regulární výraz upraven vložením nebo odebráním sady závorek, musí být přepsán veškerý kód, který odkazuje na očíslované zachycení, aby odrážel nové číslování. Za druhé, protože různé sady kulatých závorek jsou často používány k poskytování dvou alternativních výrazů pro přijatelnou shodu, může být obtížné určit, který z těchto dvou výrazů skutečně vrátil výsledek.  
  
 Aby bylo možné tyto problémy vyřešit, třída <xref:System.Text.RegularExpressions.Regex> podporuje syntaxi `(?<name>…)` pro zachycení shody do zadané patice (slot může být pojmenován pomocí String nebo integer; celá čísla lze znovu zavolat rychleji). Proto mohou být alternativní shody stejného řetězce směrovány na stejné místo. V případě konfliktu je poslední shoda odhozena do slotu úspěšná. (K dispozici je však úplný seznam více shod pro jednu oblast. Podrobnosti najdete v kolekci <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>.)  
  
## <a name="see-also"></a>Viz také:

- [Regulární výrazy .NET](../../../docs/standard/base-types/regular-expressions.md)
