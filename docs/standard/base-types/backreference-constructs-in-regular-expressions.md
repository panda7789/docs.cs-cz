---
title: Konstrukce zpětných odkazů v regulárních výrazech
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7953e34f76e23e3f9f4913726adc4b2176b172c9
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511536"
---
# <a name="backreference-constructs-in-regular-expressions"></a>Konstrukce zpětných odkazů v regulárních výrazech
Zpětné odkazy poskytují pohodlný způsob, jak identifikovat opakovaných nebo podřetězec v rámci řetězce. Například pokud vstupní řetězec obsahuje více výskytů libovolného dílčí řetězec, můžete porovnat první výskyt zachytávající skupinou a pak použijte zpětný odkaz tak, aby odpovídaly další výskyty tohoto dílčí řetězec.  
  
> [!NOTE]
>  Samostatná syntaxe se používá k odkazování na pojmenované a číslované zachytávající skupiny v řetězci pro nahrazení. Další informace najdete v tématu [náhrady](substitutions-in-regular-expressions.md).  
  
 .NET definuje samostatné jazykové prvky k odkazování na číslem a pojmenovaných zachytávajících skupinách. Další informace o zachycující skupiny, najdete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="numbered-backreferences"></a>Číslované zpětné odkazy  
 Zpětný odkaz číselného používá následující syntaxi:  
  
 `\` *Číslo*  
  
 kde *číslo* je pořadové umístění zachytávající skupinu v regulárním výrazu. Například `\4` odpovídá obsahu čtvrtý zachytávající skupina. Pokud *číslo* není definován ve vzoru regulárního výrazu, dojde k chybě analýzy a vyvolá se modul regulárních výrazů <xref:System.ArgumentException>. Například regulární výraz `\b(\w+)\s\1` je platný, protože `(\w+)` je první a jediný zachytávající skupinu ve výrazu. Na druhé straně `\b(\w+)\s\2` není platný a vyvolá výjimku argument, protože neexistuje žádná zachytávající skupina číslované `\2`. Kromě toho pokud *číslo* identifikuje zachytávající skupinu v konkrétní pořadí, ale, že zachycující skupina má přiřazenou číselnou název jiné než její pořadové umístění, takévyvoláanalyzátorregulárníchvýrazů<xref:System.ArgumentException>. 
  
 Poznámka: byla zjištěna dvojznačnost mezi osmičkovými řídícími kódy (například `\16`) a `\` *číslo* zpětných odkazech, který se používá stejná notace. Tuto nejednoznačnost vyřešen následujícím způsobem:  
  
-   Výrazy `\1` prostřednictvím `\9` vždy interpretováno jako zpětné odkazy a ne jako osmičkové kódy.  
  
-   Pokud první číslice vícečíslicového výrazu je 8 a 9 (například `\80` nebo `\91`), výraz, protože je interpretován jako literální.  
  
-   Výrazy z `\10` a vyšší jsou považovány za zpětné odkazy, pokud je zpětný odkaz odpovídá na to číslo, jinak, jsou interpretovány jako osmičková kódy.  
  
-   Obsahuje-li regulární výraz zpětný odkaz na nedefinované číslo skupiny, dojde k chybě analýzy, a vyvolá se modul regulárních výrazů <xref:System.ArgumentException>.  
  
 Pokud nejednoznačnost je nějaký problém, můžete použít `\k<` *název* `>` zápisu, která je jednoznačný a nesmí být zaměněny s osmičkovými kódy. Podobně šestnáctkové kódy, jako `\xdd` jsou jednoznačný a nesmí být zaměňovány zpětné odkazy.  
  
 Následující příklad najde zdvojené znaky v řetězci. Definuje regulární výraz `(\w)\1`, který se skládá z následujících elementů.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`(\w)`|Odpovídá znaku slova a přiřaďte ho k první zachytávající skupina.|  
|`\1`|Porovná další znak, který je stejná jako hodnota první zachytávající skupina.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a>Pojmenované zpětné odkazy  
 Pojmenovaný zpětný odkaz je definován pomocí následující syntaxe:  
  
 `\k<` *Jméno* `>`  
  
 nebo:  
  
 `\k'` *Jméno* `'`  
  
 kde *název* je název zachytávající skupinu definovanou ve vzoru regulárního výrazu. Pokud *název* není definován ve vzoru regulárního výrazu, dojde k chybě analýzy a vyvolá se modul regulárních výrazů <xref:System.ArgumentException>.  
  
 Následující příklad najde zdvojené znaky v řetězci. Definuje regulární výraz `(?<char>\w)\k<char>`, který se skládá z následujících elementů.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`(?<char>\w)`|Odpovídá znaku slova a přiřaďte ho ke zachytávající skupina s názvem `char`.|  
|`\k<char>`|Další znak, který je stejná jako hodnota odpovídat `char` zachytávající skupinu.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  

## <a name="named-numeric-backreferences"></a>Pojmenované číselné zpětné odkazy

V pojmenovaný zpětný odkaz s `\k`, *název* může také být řetězcové vyjádření čísla. Například následující příklad používá regulární výraz `(?<2>\w)\k<2>` najít zdvojené znaky v řetězci. V tomto případě v příkladu je definována zachytávající skupinu, která je explicitně s názvem "2" a zpětný odkaz je odpovídajícím způsobem s názvem "2". 
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  

Pokud *název* je řetězcové vyjádření čísla a žádná zachytávající skupina nemá název, `\k<` *název* `>` je stejné jako zpětný odkaz `\`  *číslo*, kde *číslo* je pořadové číslo pozice v zachytávání. V následujícím příkladu je jeden zachytávající skupina s názvem `char`. Konstrukce zpětných odkazů odkazuje na jako `\k<1>`. Jak výstup z příkladu, volání <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> proběhne úspěšně, protože `char` je první zachytávající skupina.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]  

Nicméně pokud *název* je řetězcové vyjádření čísla a zachytávající skupinu ve, pozice byly explicitně přiřazeny číselné název, analyzátor regulárních výrazů nemůže identifikovat zachytávající skupinu podle její pořadové umístění . Místo toho se vyvolá <xref:System.ArgumentException>. Pouze zachytávající skupina v následujícím příkladu má název "2". Vzhledem k tomu, `\k` konstruktor se používá k definování zpětný odkaz s názvem "1", analyzátor regulárních výrazů se nepodařilo zjistit první zachytávající skupina a vyvolá výjimku.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]  

## <a name="what-backreferences-match"></a>Co porovnávají  
 Zpětný odkaz odkazuje na poslední definici skupiny (definice bezprostředně nalevo, při porovnávání zleva doprava). Pokud skupina provádí více zachycení, zpětný odkaz odkazuje na nejnovější snímek.  
  
 Následující příklad obsahuje vzor regulárního výrazu, `(?<1>a)(?<1>\1b)*`, které předefinuje \1 pojmenované skupiny. Následující tabulka popisuje každý vzorek regulárního výrazu.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(?<1>a)`|Porovná znak "a" a přiřadit výsledek, který má zachytávající skupina s názvem `1`.|  
|`(?<1>\1b)*`|0 nebo 1 shoda výskyt skupina s názvem `1` spolu s "b" a přiřadit výsledek, který má zachytávající skupina s názvem `1`.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 V porovnávání regulárních výrazů se vstupním řetězcem ("aababb"), modul regulárních výrazů provádí následující operace:  
  
1.  Začne na začátku řetězce a úspěšně odpovídá "a" s výrazem `(?<1>a)`. Hodnota `1` skupina je nyní "a".  
  
2.  Přejde na druhém znaku a úspěšně shoduje s řetězcem "ab" s výrazem `\1b`, nebo "ab". Poté přiřadí výsledek, "ab" k `\1`.  
  
3.  Přejde na čtvrté znak. Výraz `(?<1>\1b)` je porovnán nula nebo vícekrát, takže úspěšně odpovídá řetězci "abb" s výrazem `\1b`. Přiřadí výsledek "abb", zpět do `\1`.  
  
 V tomto příkladu `*` je kvantifikátor opakování je vyhodnocen jako opakovaně dokud modul regulárních výrazů neodpovídá vzoru definuje. Kvantifikátory opakování nerušte zaškrtnutí políčka definice skupiny.  
  
 Pokud skupinu nezachytila žádný podřetězec, zpětný odkaz na tuto skupinu není definováno a nikdy odpovídá. To je znázorněn ve vzoru regulárního výrazu `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, která je definovaná následujícím způsobem:  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\p{Lu}{2})`|Porovná dvě velká písmena. Toto je první zachytávající skupina.|  
|`(\d{2})?`|Porovná žádný nebo jeden výskyt dvě desetinné číslice. Toto je druhá zachytávající skupina.|  
|`(\p{Lu}{2})`|Porovná dvě velká písmena. Toto je třetí zachytávající skupina.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vstupní řetězec může odpovídat tomuto regulárnímu výrazu i v případě, že nejsou k dispozici dvě desetinné číslice, které jsou definovány tak druhá zachytávající skupina. Následující příklad ukazuje, že i když tato shoda je úspěšná, prázdnou zachytávající skupinou nachází mezi dvěma úspěšné zachytávajících skupinách.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
