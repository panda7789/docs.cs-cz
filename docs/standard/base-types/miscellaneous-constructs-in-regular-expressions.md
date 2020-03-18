---
title: Různé konstrukce v regulárních výrazech
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- constructs, miscellaneous
- .NET Framework regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
ms.openlocfilehash: a43ce44e11a9231dee2961ee02bac745d9ca71cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141602"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Různé konstrukce v regulárních výrazech
Regulární výrazy v rozhraní .NET zahrnují tři různé jazykové konstrukce. Jeden umožňuje povolit nebo zakázat konkrétní možnosti párování uprostřed vzoru regulárního výrazu. Zbývající dva umožňují zahrnout komentáře do regulárního výrazu.  
  
## <a name="inline-options"></a>Možnosti vsazení  
 Můžete nastavit nebo zakázat určité možnosti porovnávání vzorů pro část regulárního výrazu pomocí syntaxe  
  
`(?imnsx-imnsx)`  
  
 Můžete uvést možnosti, které chcete povolit za otazníkem a možnosti, které chcete zakázat po znaménko mínus. Jednotlivé možnosti jsou popsány v následující tabulce. Další informace o jednotlivých možnostech naleznete v [tématu Možnosti regulárního výrazu](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Možnost|Popis|  
|------------|-----------------|  
|`i`|Porovnávání bez rozlišování velkých a malých písmen.|  
|`m`|Víceřádkový režim.|  
|`n`|Pouze explicitní zachycení. (Závorky nepůsobí jako zachytávající skupiny.)|  
|`s`|Jednořádkový režim.|  
|`x`|Ignorujte prázdné znaky bez řídicích míst a povolte komentáře v režimu x.|  
  
 Jakákoli změna v možnostech `(?imnsx-imnsx)` regulárních výrazů definovaná konstrukcí zůstává v platnosti až do konce ohraničující skupiny.  
  
> [!NOTE]
> Konstrukce `(?imnsx-imnsx:`seskupení *podvýrazů* `)` poskytuje identické funkce pro podvýraz. Další informace naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Následující příklad používá `i` `n`možnosti `x` , a umožňuje nerozlišování malých a velkých písmen a explicitní zachycení a ignoruje prázdné znaky ve vzoru regulárního výrazu uprostřed regulárního výrazu.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 Příklad definuje dva regulární výrazy. První , `\b(D\w+)\s(d\w+)\b`odpovídá dvě po sobě jdoucí slova, která začínají velkými písmeny "D" a malé "d". Druhý regulární `\b(D\w+)(?ixn) \s (d\w+) \b`výraz , používá k úpravě tohoto vzoru včleněné možnosti, jak je popsáno v následující tabulce. Porovnání výsledků potvrzuje účinek `(?ixn)` konstrukce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(D\w+)`|Porovná velké "D" následované jedním nebo více slovními znaky. Toto je první skupina zachycení.|  
|`(?ixn)`|Od tohoto okamžiku proveďte porovnání bez rozlišování velkých a malých písmen, proveďte pouze explicitní zachycení a ignorujte prázdné místo ve vzoru regulárního výrazu.|  
|`\s`|Porovná prázdný znak.|  
|`(d\w+)`|Porovná velká nebo malá písmena "d" následovaná jedním nebo více slovními znaky. Tato skupina není zachycena, protože byla povolena `n` možnost (explicitní zachycení).|  
|`\b`|Porovná hranici slova.|  
  
## <a name="inline-comment"></a>Vsazená poznámka  
 Konstrukce `(?#` *komentáře* `)` umožňuje zahrnout vsazený komentář do regulárního výrazu. Modul regulárních výrazů nepoužívá žádnou část komentáře v porovnávání vzorů, i <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> když komentář je součástí řetězce, který je vrácen metodou. Komentář končí první pravou závorkou.  
  
 Následující příklad opakuje první vzor regulárního výrazu z příkladu v předchozí části. Přidá dva včleněné komentáře k regulárnímu výrazu k označení, zda je porovnání rozlišování velkých a malých písmen. Vzor regulárního výrazu , `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`je definován takto.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?# case-sensitive comparison)`|Komentář. Nemá vliv na chování porovnávání vzorů.|  
|`(D\w+)`|Porovná velké "D" následované jedním nebo více slovními znaky. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(?ixn)`|Od tohoto okamžiku proveďte porovnání bez rozlišování velkých a malých písmen, proveďte pouze explicitní zachycení a ignorujte prázdné místo ve vzoru regulárního výrazu.|  
|`(?#case-insensitive comparison)`|Komentář. Nemá vliv na chování porovnávání vzorů.|  
|`(d\w+)`|Porovná velká nebo malá písmena "d" následovaná jedním nebo více slovními znaky. Toto je druhá skupina zachycení.|  
|`\b`|Porovná hranici slova.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Komentář na konci řádku  
 Znak čísla`#`( )označuje komentář v režimu x, který začíná znakem unescaped # na konci vzoru regulárního výrazu a pokračuje až do konce řádku. Chcete-li použít tuto konstrukci, musíte buď povolit `x` možnost <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> (prostřednictvím vsazených voleb) nebo zadat hodnotu `option` parametru při vytváření instancí objektu <xref:System.Text.RegularExpressions.Regex> nebo volání statické <xref:System.Text.RegularExpressions.Regex> metody.  
  
 Následující příklad ilustruje konstrukci komentáře na konci řádku. Určuje, zda je řetězec složený formát řetězec, který obsahuje alespoň jednu položku formátu. Následující tabulka popisuje konstrukce ve vzoru regulárního výrazu:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\{`|Porovnejte úvodní ortézu.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`(,-*\d+)*`|Porovná nulový nebo jeden výskyt čárky následovaný volitelným znaménkem mínus následovaným jedním nebo více desetinnými číslicemi.|  
|`(\:\w{1,4}?)*`|Porovná nulový nebo jeden výskyt dvojtečky, následovaný jedním až čtyřmi, ale co nejméně nemezerovými znaky.|  
|`\}`|Porovná se s složenou závorkou.|  
|`(?x)`|Povolte možnost ignorovat vzorek prázdné místo tak, aby komentář na konci řádku bude rozpoznán.|  
|`# Looks for a composite format item.`|Komentář na konci řádku.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Všimněte si, že `(?x)` místo poskytnutí konstrukce v regulárním výrazu <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> komentář mohl <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> být také rozpoznán voláním metody a předáním hodnoty výčtu.  
  
## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
