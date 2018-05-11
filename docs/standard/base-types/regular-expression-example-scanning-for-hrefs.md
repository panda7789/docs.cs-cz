---
title: 'Regulární výraz příklad: Vyhledávání atributů href'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9df41a404c091bb76490d762b55580c36cf33f62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Regulární výraz příklad: Vyhledávání atributů href
Následující příklad prohledá vstupní řetězec a zobrazí všechny href = "..." a jejich umístění v řetězci.  
  
## <a name="the-regex-object"></a>Objekt Regex  
 Protože `DumpHRefs` metodu lze volat vícekrát z uživatelského kódu, použije `static` (`Shared` v jazyce Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda. To umožňuje modul regulárních výrazů pro ukládání do mezipaměti regulárnímu výrazu a zabraňuje režijní náklady na vytvoření nové instance <xref:System.Text.RegularExpressions.Regex> objekt pokaždé, když je volána metoda. A <xref:System.Text.RegularExpressions.Match> objekt se pak použije k iteraci v rámci všechny shody v řetězci.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Následující příklad ukazuje volání `DumpHRefs` metoda.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Regulární výraz `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`href`|Odpovídat řetězcového literálu "href". Shoda nerozlišuje malá a velká písmena.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`=`|Odpovídat symbolem rovná se.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|<code>(?:\["'\](?<1>\[^"'\]*)"&#124;(?<1>\S+))</code>|Shodovat s jedním z následujících akcí bez výsledek přiřazení k zaznamenané skupiny:<br /> <ul><li><p>Dvojité uvozovky nebo apostrof, za nímž následuje nula nebo více výskytů libovolného znaku než uvozovky nebo apostrof, za nímž následuje znak uvozovek nebo apostrof. Skupina s názvem `1` je součástí tohoto vzoru.</p></li><li><p>Jeden nebo více znaků prázdné znaky. Skupina s názvem `1` je součástí tohoto vzoru.</p></li></ul>|  
|`(?<1>[^"']*)`|Přiřadit nula nebo více výskytů libovolného znaku než uvozovky nebo apostrofu zachycující skupiny s názvem `1`.|  
|`"(?<1>\S+)`|Přiřadit jeden nebo více znaků prázdné znaky zachycující skupiny s názvem `1`.|  
  
## <a name="match-result-class"></a>Porovnávání třídy výsledků  
 Výsledky hledání jsou uloženy v <xref:System.Text.RegularExpressions.Match> třídy, která poskytuje přístup ke všem dílčím řetězcům extrahovaným při hledání. Pamatuje také řetězec a regulární výraz, který používají, aby bylo možno zavolat <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodu za účelem dalšího vyhledávání od kde skončilo poslední.  
  
## <a name="explicitly-named-captures"></a>Explicitně pojmenované zachycování  
 V tradiční regulární výrazy zaznamenávání závorkách jsou automaticky číslované. To vede k dva problémy. Nejprve regulární výraz je změnit jejich vložením či odstraněním sady závorek, je nutné všechen kód, který odkazuje na číslované zachycování přepsat tak, aby odrážely novou číslování. Druhý protože různé sady závorek často používané k zajištění dva alternativní výrazy pro přijatelné shody, může být obtížné určit, které ze dvou výrazů skutečně vrátil výsledek.  
  
 K řešení těchto problémů <xref:System.Text.RegularExpressions.Regex> třída podporuje syntaxi `(?<name>…)` pro zachycení shody do zadaného slotu (slot můžete pojmenovat pomocí řetězce nebo celé číslo; rychleji můžete třeba připomenout celá čísla). Proto alternativní shoda pro stejný řetězec, který všechny můžete přesměrováni na jednom místě. V případě konfliktu je poslední shoda uložená do slotu úspěšná shoda. (Úplný seznam více shod pro jeden slot je však k dispozici. Najdete v článku <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekce podrobnosti.)  
  
## <a name="see-also"></a>Viz také  
 [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
