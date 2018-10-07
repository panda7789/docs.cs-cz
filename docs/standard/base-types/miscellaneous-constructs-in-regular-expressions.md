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
ms.openlocfilehash: 8956726915ebe1c0b1c7654e62e2e28620274b4a
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836281"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Různé konstrukce v regulárních výrazech
Regulární výrazy v rozhraní .NET obsahovat tři různé jazykové konstrukce. Jeden vám umožňuje povolit nebo zakázat určité možnosti porovnávání vzoru regulárního výrazu. Zbývající dvě umožní zahrnutí komentářů v regulárním výrazu.  
  
## <a name="inline-options"></a>Vložené možnosti  
 Můžete nastavit nebo zakázat konkrétní porovnávání vzorů možnosti pro část regulárního výrazu s využitím syntaxe  
  
```  
(?imnsx-imnsx)  
```  
  
 Můžete seznam možností, které chcete povolit po otazník a možnostech, které chcete zakázat po znaménko minus. Jednotlivé možnosti jsou popsány v následující tabulce. Další informace o jednotlivých možnostech najdete v tématu [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Možnost|Popis|  
|------------|-----------------|  
|`i`|Porovnávání.|  
|`m`|Víceřádkový režim.|  
|`n`|Pouze explicitní zachycení. (Závorek není fungovat jako zachytávající skupiny.)|  
|`s`|Jednořádkový režim.|  
|`x`|Ignorovat prázdné znaky bez řídících a Povolit poznámky x-mode.|  
  
 Žádné změny v možnosti regulárních výrazů, které jsou definované `(?imnsx-imnsx)` vytvořit zůstane v platnosti až do konce nadřazené skupiny.  
  
> [!NOTE]
>  `(?imnsx-imnsx:` *Dílčí výraz* `)` seskupovací konstrukce poskytuje stejné funkce pro podvýrazu. Další informace najdete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 V následujícím příkladu `i`, `n`, a `x` možnosti pro povolení nerozlišování velikosti písmen a explicitní zachycení a pro ignorování prázdných ve vzoru regulárního výrazu uprostřed regulární výraz.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 Příklad definuje dva regulární výrazy. První s názvem `\b(D\w+)\s(d\w+)\b`, odpovídá dvě po sobě jdoucích slova, která začínají velkým "D" a malých písmen "d". Druhý regulární výraz `\b(D\w+)(?ixn) \s (d\w+) \b`, používá vložené možnosti pro úpravu tohoto modelu, jak je popsáno v následující tabulce. Porovnání výsledků potvrdí platnost `(?ixn)` vytvořit.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(D\w+)`|Porovná "D", za nímž následuje jedna nebo více znaků slova velké. Toto je první skupiny zachycení.|  
|`(?ixn)`|Od tohoto okamžiku, porovnáním velkých a malých písmen zkontrolujte pouze explicitní zachytí a ignoruje prázdný znak ve vzorku regulárního výrazu.|  
|`\s`|Porovná prázdný znak.|  
|`(d\w+)`|Porovná velkými nebo malými "d" za nímž následuje jedna nebo více znaků slova. Tato skupina není zachycena, protože `n` byla povolená možnost (explicitní zachycení)...|  
|`\b`|Porovná hranici slova.|  
  
## <a name="inline-comment"></a>Vložený komentář  
 `(?#` *Komentář* `)` konstrukce umožňuje zahrnout vložený komentář v regulárním výrazu. Modul regulárních výrazů nepoužívá žádnou část komentář v porovnávání vzorů, ale komentář je součástí řetězec, který je vrácený <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> metody. Komentář končí první pravou závorkou.  
  
 V následujícím příkladu se opakuje, první vzor regulárního výrazu z příkladu v předchozí části. Přidá dvě vložené komentáře do regulární výraz k určení, jestli je porovnání velká a malá písmena. Vzor regulárního výrazu `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`, je definovaná následujícím způsobem.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`(?# case-sensitive comparison)`|Komentář. Neovlivňuje chování porovnávání vzorů.|  
|`(D\w+)`|Porovná "D", za nímž následuje jedna nebo více znaků slova velké. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(?ixn)`|Od tohoto okamžiku, porovnáním velkých a malých písmen zkontrolujte pouze explicitní zachytí a ignoruje prázdný znak ve vzorku regulárního výrazu.|  
|`(?#case-insensitive comparison)`|Komentář. Neovlivňuje chování porovnávání vzorů.|  
|`(d\w+)`|Porovná velkými nebo malými "d" za nímž následuje jedna nebo více znaků slova. Toto je druhá skupině zachycení.|  
|`\b`|Porovná hranici slova.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Komentář na konci řádku  
 Znak čísla (`#`) označí komentář x-mode, který začíná znakem # znak na konci vzoru regulárního výrazu a pokračuje až do konce řádku. Pokud chcete použít tento konstruktor, musíte buď povolit `x` možnost (pomocí vložených možností) nebo zadat <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> hodnota, která se `option` parametr při vytváření instance <xref:System.Text.RegularExpressions.Regex> objektu nebo voláním statické <xref:System.Text.RegularExpressions.Regex> – metoda.  
  
 Následující příklad ukazuje konstrukce komentář na konci řádku. Určuje, zda je řetězec složený řetězec formátu, který obsahuje alespoň jednu položku formátu. Následující tabulka popisuje, jaké konstrukty jsou ve vzoru regulárního výrazu:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\{`|Porovná levá složená závorka.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`(,-*\d+)*`|Porovná žádný nebo jeden výskyt čárku, za nímž následuje volitelným znakem minus, za nímž následuje jedna nebo více desítkových číslic.|  
|`(\:\w{1,4}?)*`|Porovná žádný nebo jeden výskyt dvojtečkou, následovaných jednou až čtyřmi, ale co nejméně co nejlépe, prázdných znaků.|  
|`\}`|Porovná pravou složenou závorku.|  
|`(?x)`|Povolte možnost Ignorovat vzor prázdné místo tak, aby byl rozpoznán komentář na konci řádku.|  
|`# Looks for a composite format item.`|Komentář konci řádku.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Všimněte si, že namísto zadávání `(?x)` vytvořit v regulárním výrazu komentář může také obsahovat uznávaná voláním <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda a předají se jí <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> hodnota výčtu.  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
