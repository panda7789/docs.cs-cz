---
title: 'Příklad regulárního výrazu: Hledání hrefů'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084215"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Příklad regulárního výrazu: Hledání hrefů
Následující příklad vyhledá vstupní řetězec a zobrazí všechny href="..." hodnoty a jejich umístění v řetězci.  
  
## <a name="the-regex-object"></a>Objekt Regex  
 Vzhledem `DumpHRefs` k tomu, že metoda může být `static` `Shared` volána vícekrát z uživatelského kódu, používá metodu ( v jazyce <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> Visual Basic. To umožňuje modulu regulárních výrazů ukládat regulární výraz <xref:System.Text.RegularExpressions.Regex> do mezipaměti a zabraňuje režii vytváření instancí nového objektu při každém volání metody. Objekt <xref:System.Text.RegularExpressions.Match> se pak používá k iterátu přes všechny shody v řetězci.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Následující příklad pak ilustruje volání `DumpHRefs` metody.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Vzor regulárního výrazu `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`href`|Porovná literál řetězce "href". Shoda nerozlišuje malá a velká písmena.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`=`|Porovná znaménko rovná se.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|Porovnejte jednu z následujících možností bez přiřazení výsledku zachycené skupině:<br /> <ul><li><p>Uvozovky nebo apostrof, následované nulou nebo více výskyty libovolného znaku jiného než uvozovky nebo apostrofu, následované uvozovkami nebo apostrofem. Skupina s `1` názvem je součástí tohoto vzoru.</p></li><li><p>Jeden nebo více neprázdné znaky. Skupina s `1` názvem je součástí tohoto vzoru.</p></li></ul>|  
|`(?<1>[^"']*)`|Přiřadit zachytávající skupině s názvem `1`přiřadit nulu nebo více výskytů libovolného znaku jiného než uvozovky nebo apostrofu .|  
|`(?<1>\S+)`|Přiřaďte zachytávající skupině jeden nebo `1`více neprázdné znaky s názvem .|  
  
## <a name="match-result-class"></a>Třída výsledků shody  
 Výsledky hledání jsou uloženy <xref:System.Text.RegularExpressions.Match> ve třídě, která poskytuje přístup ke všem podřetězcům extrahovaným hledáním. Také si pamatuje řetězec prohledávaný a používaný regulární výraz, takže může volat metodu <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> k provedení jiného hledání od místa, kde skončil poslední.  
  
## <a name="explicitly-named-captures"></a>Explicitně pojmenovaná zachycení  
 V tradičních regulárních výrazech jsou zachytávající závorky automaticky číslovány postupně. To vede ke dvěma problémům. Nejprve pokud je regulární výraz změněn vložením nebo odebráním sady závorek, musí být přepsán veškerý kód, který odkazuje na číslované sběry, aby odrážel nové číslování. Za druhé, protože různé sady závorek se často používají k poskytnutí dvou alternativních výrazů pro přijatelnou shodu, může být obtížné určit, který z těchto dvou výrazů skutečně vrátil výsledek.  
  
 Chcete-li tyto <xref:System.Text.RegularExpressions.Regex> problémy vyřešit, třída podporuje syntaxi `(?<name>…)` pro zachycení shody do zadaného slotu (patice může být pojmenována pomocí řetězce nebo celé holčičí; celá čísla lze připomenout rychleji). Alternativní shody pro stejný řetězec tedy mohou být směrovány na stejné místo. V případě konfliktu je poslední shoda, která spadla do slotu, úspěšná shoda. (Je však k dispozici úplný seznam více shod pro jeden slot. Podrobnosti <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> naleznete v kolekci.)  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
