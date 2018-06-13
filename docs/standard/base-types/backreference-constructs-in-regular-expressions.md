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
ms.openlocfilehash: 5b16cfeda88b8e700c4d473962155a8510ce7df2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574605"
---
# <a name="backreference-constructs-in-regular-expressions"></a>Konstrukce zpětných odkazů v regulárních výrazech
Zpětné odkazy poskytují pohodlný způsob, jak identifikovat opakovaných znaku nebo podřetězce v řetězci. Například pokud vstupní řetězec obsahuje více výskytů libovolného dílčího řetězce, můžete porovnat první výskyt se skupinou zaznamenávání a pak použít zpětný odkaz pro porovnání dalších výskytů dílčí řetězec.  
  
> [!NOTE]
>  Samostatná syntaxe slouží k odkazování na pojmenované a číslované zachytávající skupiny v náhradní řetězce. Další informace najdete v tématu [náhrady](substitutions-in-regular-expressions.md).  
  
 Rozhraní .NET definuje samostatné jazykové elementy označují číslem a pojmenované zachytávající skupiny. Další informace o zaznamenání skupin najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="numbered-backreferences"></a>Číslované zpětné odkazy  
 Číslovaný zpětný odkaz používá následující syntaxe:  
  
 `\` *Číslo*  
  
 kde *číslo* je pořadové číslo pozice zachytávající skupiny v regulárním výrazu. Například `\4` odpovídá obsah čtvrtý zachycující skupiny. Pokud *číslo* není definovaná v regulární výraz, dojde k chybě analýzy a vyvolá modul regulárních výrazů <xref:System.ArgumentException>. Například regulární výraz `\b(\w+)\s\1` je platný, protože `(\w+)` je první a pouze zaznamenávání skupiny ve výrazu. Na druhé straně `\b(\w+)\s\2` je neplatný a vyvolá výjimku argument, protože neexistuje žádná zachytávající skupina s číslem `\2`. Kromě toho pokud *číslo* identifikuje skupinu zachycení v konkrétní pořadí, ale, že zaznamenávání skupiny byl přiřazen jednu číslici název liší od jeho pořadové číslo pozice, také vyvolá analyzátorregulárníchvýrazů<xref:System.ArgumentException>. 
  
 Všimněte si nejednoznačnosti mezi osmičková řídicí kódy (například `\16`) a `\` *číslo* používajících stejnou zápis. Tato nejednoznačnost je přeložit takto:  
  
-   Výrazy `\1` prostřednictvím `\9` jsou vždy interpretovány jako zpětné odkazy a ne jako osmičková kódy.  
  
-   Pokud je první číslice vícečíslicového výrazu 8 nebo 9 (například `\80` nebo `\91`), jak interpretovat jako literál výrazu.  
  
-   Výrazy z `\10` a větší jsou považovány za zpětné odkazy, pokud je zpětný odkaz odpovídající, na který číslo; jinak hodnota, se interpretují jako osmičkové kódy.  
  
-   Pokud regulární výraz obsahuje zpětný odkaz na nedefinované číslo skupiny, dojde k chybě analýzy a vyvolá modul regulárních výrazů <xref:System.ArgumentException>.  
  
 Pokud je nejednoznačnost problém, můžete použít `\k<` *název* `>` zápis, což je jednoznačné a nelze zaměňovat s kódy osmičková znaků. Podobně, jako například šestnáctková kódy `\xdd` jsou jednoznačné a nelze zaměňovat s zpětné odkazy.  
  
 Následující příklad vyhledá zdvojené znaky slova v řetězci. Definuje regulární výraz, `(\w)\1`, která zahrnuje následující prvky.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`(\w)`|Porovná znak slova a přiřaďte ho ke skupině první zaznamenávání.|  
|`\1`|Porovná další znak, který je stejná jako hodnota první zachycující skupiny.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a>Pojmenované zpětné odkazy  
 Pojmenované zpětných odkazů se definuje pomocí následující syntaxe:  
  
 `\k<` *Jméno* `>`  
  
 nebo:  
  
 `\k'` *Jméno* `'`  
  
 kde *název* je název zachytávající skupiny definované v regulární výraz. Pokud *název* není definovaná v regulární výraz, dojde k chybě analýzy a vyvolá modul regulárních výrazů <xref:System.ArgumentException>.  
  
 Následující příklad vyhledá zdvojené znaky slova v řetězci. Definuje regulární výraz, `(?<char>\w)\k<char>`, která zahrnuje následující prvky.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`(?<char>\w)`|Porovná znak slova a přiřaďte ho k zaznamenávání skupina s názvem `char`.|  
|`\k<char>`|Porovná další znak, který je stejná jako hodnota `char` zaznamenávání skupiny.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  

## <a name="named-numeric-backreferences"></a>S názvem číselné zpětné odkazy

V pojmenované zpětných odkazů s `\k`, *název* může být také řetězcovou reprezentaci číslo. Například následující příklad používá regulární výraz `(?<2>\w)\k<2>` k nalezení zdvojených znaků slova v řetězci. V takovém případě příkladu definuje zaznamenávání skupinu, která je explicitně s názvem "2" a zpětný odkaz je odpovídajícím způsobem s názvem "2". 
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  

Pokud *název* je řetězcová reprezentace číslo a žádná zaznamenávání skupina má tento název `\k<` *název* `>` je stejný jako zpětných odkazů `\`  *číslo*, kde *číslo* je pořadová čísla zachytávání. V následujícím příkladu je jediné zachytávající skupiny s názvem `char`. Konstrukce zpětných odkazů odkazuje na jej jako `\k<1>`. Jako výstup z příklad ukazuje, volání <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> úspěšné, protože `char` je první zachytávající skupina.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]  

Ale pokud *název* je řetězcová reprezentace číslo a zaznamenávání skupiny v, pozice byla explicitně přiřazena číselné název, analyzátor regulární výraz nelze identifikovat zaznamenávání Seskupit podle jeho pořadové číslo pozice . Místo toho vyvolá <xref:System.ArgumentException>. Skupina pouze zaznamenávání v následujícím příkladu je s názvem "2". Protože `\k` konstrukce se používá k definování zpětný odkaz s názvem "1", analyzátor regulárních výrazů se nepodařilo zjistit první skupinu zaznamenávání a vyvolá výjimku.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]  

## <a name="what-backreferences-match"></a>Co porovnávají  
 Zpětný odkaz odkazuje na nejnovější definice skupiny (definici nejvíce okamžitě na levé straně při kontrole shody zleva doprava). Pokud skupina provádí více zachycení, zpětný odkaz odkazuje na nejnovější zachycení.  
  
 Následující příklad obsahuje vzor regulárního výrazu `(?<1>a)(?<1>\1b)*`, který definuje nové \1 s názvem skupiny. Následující tabulka popisuje každý vzor v regulárním výrazu.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(?<1>a)`|Porovná znak "a" a přiřadit výsledek, který má zaznamenávání skupiny s názvem `1`.|  
|`(?<1>\1b)*`|Shoda 0 nebo 1 výskyt skupiny s názvem `1` spolu s "b" a přiřaďte výsledek zachycující skupiny s názvem `1`.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 Modul regulárních výrazů v porovnání s regulárním výrazem se vstupní řetězec ("aababb"), provede následující operace:  
  
1.  Začne od začátku řetězce a úspěšně odpovídá "a" názvem výraz `(?<1>a)`. Hodnota `1` skupiny je nyní "a".  
  
2.  Přejde na druhý znak a úspěšně shoduje s řetězcem "ab" s výraz `\1b`, nebo "ab". Poté přiřadí výsledek, "ab" k `\1`.  
  
3.  Přejde na čtvrtý znak. Výraz `(?<1>\1b)` je porovnán nula nebo vícekrát, takže úspěšně shoduje s řetězcem "abb" s výraz `\1b`. Přiřadí výsledek "abb" zpět na `\1`.  
  
 V tomto příkladu `*` je kvantifikátor opakování je vyhodnocen jako opakovaně dokud modul regulární výraz nelze shodují se vzorem definuje. Kvantifikátory opakování nerušte zaškrtnutí definice skupin.  
  
 Pokud skupina nezachytila žádný podřetězec, zpětných odkazů na tuto skupinu není definováno a nikdy odpovídá. Tento koncept je znázorněn podle regulární výraz `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, který je definován následujícím způsobem:  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnávání na hranici slova.|  
|`(\p{Lu}{2})`|Porovná dvě velká písmena. Toto je první zachytávající skupina.|  
|`(\d{2})?`|Porovná nula nebo jeden výskyt dvou desetinných míst. Toto je druhá zachytávající skupina.|  
|`(\p{Lu}{2})`|Porovná dvě velká písmena. Toto je třetí zachytávající skupina.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vstupní řetězec můžete tento regulárním výrazům neodpovídá, i když nejsou k dispozici dva desetinných číslic, které jsou definované za druhé zachytávající skupině. Následující příklad ukazuje, že přestože shody je úspěšné, prázdné skupiny zaznamenávání nalézt mezi dvěma skupinami zaznamenávání úspěšné.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
