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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141602"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Různé konstrukce v regulárních výrazech
Regulární výrazy v rozhraní .NET zahrnují tři jazykové konstrukce. Jedna umožňuje povolit nebo zakázat konkrétní možnosti porovnávání uprostřed vzoru regulárního výrazu. Zbývající dvě umožňují vkládat komentáře do regulárního výrazu.  
  
## <a name="inline-options"></a>Vložené možnosti  
 Můžete nastavit nebo zakázat konkrétní možnosti porovnávání vzorů pro část regulárního výrazu pomocí syntaxe.  
  
`(?imnsx-imnsx)`  
  
 Zobrazí se seznam možností, které chcete povolit po otazníku, a možnosti, které chcete zakázat za znaménkem mínus. Jednotlivé možnosti jsou popsány v následující tabulce. Další informace o jednotlivých možnostech najdete v tématu [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Možnost|Popis|  
|------------|-----------------|  
|`i`|Porovnávání bez rozlišení velkých a malých písmen.|  
|`m`|Víceřádkový režim.|  
|`n`|Pouze explicitní zachycení. (Kulaté závorky nefungují jako zachytávající skupiny.)|  
|`s`|Jednořádkový režim.|  
|`x`|Ignoruje prázdné znaky bez řídicího znaku a povoluje komentáře v režimu x.|  
  
 Jakékoli změny v regulárních výrazech, které jsou definovány konstrukcí `(?imnsx-imnsx)`, zůstávají v platnosti až do konce ohraničující skupiny.  
  
> [!NOTE]
> Konstrukce `(?imnsx-imnsx:`dílčího *výrazu*`)` seskupení poskytuje identické funkce pro dílčí výraz. Další informace naleznete v tématu [seskupovací konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Následující příklad používá možnosti `i`, `n`a `x` k povolení nerozlišování velkých a malých písmen a explicitních zachycení a k ignorování prázdných znaků ve vzoru regulárního výrazu uprostřed regulárního výrazu.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 Příklad definuje dva regulární výrazy. První, `\b(D\w+)\s(d\w+)\b`, odpovídá dvěma po sobě jdoucími slovy, která začínají velkým písmenem "D" a malým písmenem "d". Druhý regulární výraz, `\b(D\w+)(?ixn) \s (d\w+) \b`, používá vloženou možnost pro úpravu tohoto modelu, jak je popsáno v následující tabulce. Porovnání výsledků potvrdí účinek `(?ixn)` konstrukce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(D\w+)`|Porovnává velké písmeno "D" následovaný jedním nebo více znaky slova. Toto je první skupina zachycení.|  
|`(?ixn)`|Od tohoto okamžiku při porovnávání nerozlišuje velká a malá písmena, provedou pouze explicitní zachycení a ignoruje prázdné znaky ve vzoru regulárního výrazu.|  
|`\s`|Porovná prázdný znak.|  
|`(d\w+)`|Porovnává velká a malá písmena "d" následovaná jedním nebo více znaky slova. Tato skupina není zachycena, protože byla povolena možnost `n` (explicitní zachycení).|  
|`\b`|Porovná hranici slova.|  
  
## <a name="inline-comment"></a>Vložený komentář  
 `(?#` *komentář*`)` konstrukce umožňuje zahrnout vloženou poznámku do regulárního výrazu. Modul regulárních výrazů nepoužívá žádnou část komentáře v porovnávání vzorů, i když je komentář obsažen v řetězci, který je vrácen metodou <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType>. Komentář končí první pravou závorkou.  
  
 Následující příklad opakuje první vzor regulárního výrazu z příkladu v předchozí části. Přidá dva vložené komentáře k regulárnímu výrazu k označení, zda porovnávání rozlišuje malá a velká písmena. Vzor regulárního výrazu, `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`, je definován následujícím způsobem.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?# case-sensitive comparison)`|Komentář. Nemá vliv na chování porovnávání vzorů.|  
|`(D\w+)`|Porovnává velké písmeno "D" následovaný jedním nebo více znaky slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(?ixn)`|Od tohoto okamžiku při porovnávání nerozlišuje velká a malá písmena, provedou pouze explicitní zachycení a ignoruje prázdné znaky ve vzoru regulárního výrazu.|  
|`(?#case-insensitive comparison)`|Komentář. Nemá vliv na chování porovnávání vzorů.|  
|`(d\w+)`|Porovnává velká a malá písmena "d" následovaná jedním nebo více znaky slova. Toto je druhá skupina zachycení.|  
|`\b`|Porovná hranici slova.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Konec řádku komentáře  
 Číselný symbol (`#`) označuje komentář v režimu x, který začíná neřídicím znakem # na konci vzoru regulárního výrazu a pokračuje až do konce řádku. Chcete-li použít tuto konstrukci, musíte buď povolit možnost `x` (prostřednictvím vložených možností), nebo zadat <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> hodnotu parametru `option` při vytváření instance objektu <xref:System.Text.RegularExpressions.Regex> nebo volání statické metody <xref:System.Text.RegularExpressions.Regex>.  
  
 Následující příklad ilustruje konstrukci komentáře na konci řádku. Určuje, zda je řetězec složený formátovací řetězec, který obsahuje alespoň jednu položku formátu. V následující tabulce jsou popsány konstrukce ve vzoru regulárního výrazu:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\{`|Porovnává levou složenou závorku.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`(,-*\d+)*`|Porovná žádný nebo jeden výskyt čárky následovaný volitelným znaménkem mínus následovaným jednou nebo více desítkovými číslicemi.|  
|`(\:\w{1,4}?)*`|Porovná žádný nebo jeden výskyt dvojtečky následovaný jedním až čtyř, ale co nejmenším možným prázdným znakem.|  
|`\}`|Porovnává pravou složenou závorku.|  
|`(?x)`|Povolte možnost Ignorovat prázdné místo vzorku, aby se rozpoznal komentář k konci řádku.|  
|`# Looks for a composite format item.`|Komentář k koncovému řádku.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Všimněte si, že místo poskytnutí `(?x)` konstrukce v regulárním výrazu může být komentář také rozpoznán voláním metody <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> a předáním hodnoty <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> výčtu.  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
