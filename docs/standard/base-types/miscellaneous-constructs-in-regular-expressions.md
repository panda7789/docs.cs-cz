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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fabf1a133ca3c3b3ba39a4898ce0aceb378f76d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Různé konstrukce v regulárních výrazech
Regulární výrazy v rozhraní .NET zahrnují tři různé jazykové konstrukty. Jedno umožňuje povolit nebo zakázat určité možnosti porovnávání uprostřed vzor regulárního výrazu. Zbývající dvě umožňují zahrnout komentáře v regulárním výrazu.  
  
## <a name="inline-options"></a>Vložené možnosti  
 Můžete nastavit nebo zakázat konkrétní vzor odpovídající pomocí syntaxe možnosti pro součást regulární výraz  
  
```  
(?imnsx-imnsx)  
```  
  
 Můžete seznam možností, které chcete povolit po otazníku a možností, které chcete zakázat za znaménkem minus. Jednotlivé možnosti jsou popsány v následující tabulce. Další informace o jednotlivých možnostech najdete v tématu [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Možnost|Popis|  
|------------|-----------------|  
|`i`|Porovnávání.|  
|`m`|Víceřádkového režimu.|  
|`n`|Pouze explicitní zachycení. (Závorky není fungovat jako zachytávající skupiny.)|  
|`s`|Režim jeden řádek.|  
|`x`|Ignorovat prázdný znak a Povolit poznámky x-mode.|  
  
 Všechny změny v možnosti regulárních výrazů, které jsou definované `(?imnsx-imnsx)` vytvořit zůstane v platnosti až do konce nadřazené skupiny.  
  
> [!NOTE]
>  `(?imnsx-imnsx:` *Dílčím výrazu* `)` seskupovací konstrukce poskytuje stejné funkce pro dílčím výrazu. Další informace najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Následující příklad používá `i`, `n`, a `x` možnosti pro povolení nerozlišování a explicitní zachycování a Ignorovat prázdné znaky v vzor regulárního výrazu uprostřed regulární výraz.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 V příkladu definuje dva regulární výrazy. První, `\b(D\w+)\s(d\w+)\b`, porovnává dva po sobě jdoucí slova, která začínají velká písmena "D" a "d" jedno malé písmeno. Druhý regulární výraz, `\b(D\w+)(?ixn) \s (d\w+) \b`, používá vložené možnosti pro úpravu tohoto vzoru, jak je popsáno v následující tabulce. Porovnání výsledků potvrdí účinku `(?ixn)` vytvořit.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(D\w+)`|Porovná velké "D", za nímž následuje jeden nebo více znaků slova. Toto je první skupinu zachycení.|  
|`(?ixn)`|Z tohoto bodu nastaví porovnávání velká a malá písmena zkontrolujte pouze explicitní zaznamená a Ignorovat prázdné znaky v regulární výraz.|  
|`\s`|Porovná prázdný znak.|  
|`(d\w+)`|Odpovídat velké nebo malé "d" následuje jeden nebo více znaků slova. Tato skupina není zachycena, protože `n` byla povolena možnost (explicitní zachytávání)...|  
|`\b`|Porovná hranici slova.|  
  
## <a name="inline-comment"></a>Vložený komentář  
 `(?#` *Komentář* `)` konstrukce umožňuje zahrnout vložený komentář regulární výraz. Modul regulárních výrazů nepoužívá libovolná součást komentář v porovnávání vzorů, i když komentář je součástí řetězec, který je vrácený <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> metoda. Komentář končí první pravou závorkou.  
  
 V následujícím příkladu se opakuje první vzor regulárního výrazu z příkladu v předchozí části. Přidá dva vložené komentáře regulární výraz, který se označuje, zda je výsledkem porovnávání malá a velká písmena. Vzor regulárního výrazu `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b`, je definován následujícím způsobem.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?# case-sensitive comparison)`|Komentář. Porovnávání chování neovlivňuje.|  
|`(D\w+)`|Porovná velké "D", za nímž následuje jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(?ixn)`|Z tohoto bodu nastaví porovnávání velká a malá písmena zkontrolujte pouze explicitní zaznamená a Ignorovat prázdné znaky v regulární výraz.|  
|`(?#case-insensitive comparison)`|Komentář. Porovnávání chování neovlivňuje.|  
|`(d\w+)`|Odpovídat velké nebo malé "d" následuje jeden nebo více znaků slova. Toto je druhý skupiny zachycení.|  
|`\b`|Porovná hranici slova.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Komentář konec řádku  
 Znaménko čísla (`#`) označí x režimu komentář, který začíná znakem # neuvozené na konci regulární výraz a pokračuje v až do konce řádku. Pro použití této konstrukce, je třeba buď povolit `x` možnost (pomocí vložených možností) nebo zadejte <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> hodnotu `option` parametr při vytváření instance <xref:System.Text.RegularExpressions.Regex> objekt nebo volání statického <xref:System.Text.RegularExpressions.Regex> metoda.  
  
 Následující příklad ilustruje konstrukce komentář konec řádku. Se určuje, zda je řetězec složený formátovací řetězec, který obsahuje alespoň jednu položku formátu. Následující tabulka popisuje konstrukce v regulární výraz:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\{`|Odpovídat žádná levá složená závorka.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`(,-*\d+)*`|Porovná nula nebo jeden výskyt čárkou, za nímž následuje volitelné mínus, za nímž následuje jeden nebo více desetinných míst.|  
|`(\:\w{1,4}?)*`|Porovná nula nebo jeden výskyt dvojtečkou, za nímž následuje jeden až čtyři, ale nejmenším možném, prázdných znaků.|  
|`(?#case insensitive comparison)`|Vložený komentář. Nemá žádný vliv na porovnávání chování.|  
|`\}`|Pravé složené závorce odpovídat.|  
|`(?x)`|Povolte možnost Ignorovat vzor prázdný, tak, aby byl rozpoznán komentář konec řádku.|  
|`# Looks for a composite format item.`|Komentář konec řádku.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Všimněte si, že, místo `(?x)` vytvořit v regulárním výrazu komentář může být také rozpoznán voláním <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda a předání <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> hodnota výčtu.  
  
## <a name="see-also"></a>Viz také  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
