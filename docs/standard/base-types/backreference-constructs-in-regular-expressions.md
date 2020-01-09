---
title: Konstrukce zpětných odkazů v regulárních výrazech .NET
description: Naučte se identifikovat opakující se elementy textu pomocí konstrukcí zpětných odkazů v regulárním výrazu.
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
ms.openlocfilehash: 905578d763ebe5d5b8eb96a9056fbe11fbfab137
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711529"
---
# <a name="backreference-constructs-in-regular-expressions"></a>Konstrukce zpětných odkazů v regulárních výrazech

Zpětná reference poskytují pohodlný způsob identifikace opakovaného znaku nebo podřetězce v rámci řetězce. Například pokud vstupní řetězec obsahuje více výskytů libovolného dílčího řetězce, můžete porovnat první výskyt se zachytávající skupinou a potom použít zpětný odkaz pro vyhledání dalších výskytů podřetězce.

> [!NOTE]
> Samostatná syntaxe se používá pro odkazování na pojmenované a očíslované zachytávající skupiny v náhradních řetězcích. Další informace naleznete v tématu [nahrazování](substitutions-in-regular-expressions.md).

Rozhraní .NET definuje samostatné prvky jazyka pro odkazování na očíslované a pojmenované zachytávající skupiny. Další informace o zachycujících skupinách naleznete v tématu [Grouping konstrukcís](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="numbered-backreferences"></a>Číslované zpětné odkazy

Číslovaný zpětný odkaz používá následující syntaxi:

`\` *číslo*

kde *Number* je ordinální pozice zachytávající skupiny v regulárním výrazu. `\4` například odpovídá obsahu čtvrté zachytávající skupiny. Pokud *číslo* není definováno ve vzoru regulárního výrazu, dojde k chybě analýzy a modul regulárních výrazů vyvolá <xref:System.ArgumentException>. Například regulární výraz `\b(\w+)\s\1` je platný, protože `(\w+)` je první a pouze zachytávající skupina ve výrazu. Na druhé straně `\b(\w+)\s\2` není platný a vyvolá výjimku argumentu, protože není k dispozici žádná zachytávající skupina, která je očíslována `\2`. Kromě toho, pokud *Number* identifikuje zachytávající skupinu na určitém pořadovém místě, ale u této zachytávající skupiny byl přiřazen číselný název jiný než pořadové číslo, analyzátor regulárního výrazu vyvolá také <xref:System.ArgumentException>.

Všimněte si nejednoznačnosti mezi osmičkovým řídicím kódem (například `\16`) *a `\`mi* zpětnými referencemi, které používají stejný zápis. Tato nejednoznačnost je vyřešena následujícím způsobem:

- Výrazy `\1` prostřednictvím `\9` jsou vždy interpretovány jako zpětné odkazy a nikoli jako osmičkové kódy.

- Pokud je první číslice výrazu s více číslicemi 8 nebo 9 (například `\80` nebo `\91`), výraz, který je interpretován jako literál.

- Výrazy z `\10` a větší jsou považovány za zpětné odkazy, pokud existuje zpětný odkaz odpovídající tomuto číslu; v opačném případě jsou interpretovány jako osmičkové kódy.

- Pokud regulární výraz obsahuje zpětný odkaz na nedefinované číslo skupiny, dojde k chybě analýzy a modul regulárních výrazů vyvolá <xref:System.ArgumentException>.

Pokud je nejednoznačnost problém, můžete použít `\k<`*název*`>` Notation, který je nejednoznačný a nemůže být zaměněn pomocí osmičkových kódů znaků. Podobně šestnáctkové kódy jako `\xdd` jsou jednoznačné a nelze je zaměňovat s zpětnými odkazy.

Následující příklad vyhledá dvojitě vyhledané znaky v řetězci. Definuje regulární výraz `(\w)\1`, který se skládá z následujících prvků.

|Prvek|Popis|
|-------------|-----------------|
|`(\w)`|Porovnává znak slova a přiřadí ho k první zachytávající skupině.|
|`\1`|Porovnává s následujícím znakem, který je stejný jako hodnota první zachytávající skupiny.|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a>Pojmenované zpětné odkazy

Pojmenovaný zpětný odkaz je definován pomocí následující syntaxe:

*název* `\k<` `>`

nebo:

*název* `\k'` `'`

kde *Name* je název zachytávající skupiny definované ve vzoru regulárního výrazu. Pokud *název* není definován ve vzoru regulárního výrazu, dojde k chybě analýzy a modul regulárních výrazů vyvolá <xref:System.ArgumentException>.

Následující příklad vyhledá dvojitě vyhledané znaky v řetězci. Definuje regulární výraz `(?<char>\w)\k<char>`, který se skládá z následujících prvků.

|Prvek|Popis|
|-------------|-----------------|
|`(?<char>\w)`|Porovnává znak slova a přiřadí ho do zachytávající skupiny s názvem `char`.|
|`\k<char>`|Porovnává s následujícím znakem, který je stejný jako hodnota `char` zachytávající skupiny.|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a>Pojmenované číselné zpětné odkazy

V pojmenovaném zpětném odkazu s `\k`může být *název* také řetězcové vyjádření čísla. Například následující příklad používá regulární výraz `(?<2>\w)\k<2>` k vyhledání dvojitě používaných znaků v řetězci. V tomto případě příklad definuje zachytávající skupinu, která je explicitně pojmenována "2" a zpětný odkaz má odpovídající název "2".

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

Pokud je *název* řetězcové vyjádření čísla a žádná zachytávající skupina nemá tento název, `\k<`*název*`>` je stejný jako zpětný odkaz `\`*číslo*, kde *Number* je pořadové číslo pozice zachycení. V následujícím příkladu je k dispozici jedna zachytávající skupina s názvem `char`. Konstrukce zpětného odkazování odkazuje na ni jako `\k<1>`. Jak ukazuje výstup z příkladu, volání <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> je úspěšné, protože `char` je první zachytávající skupina.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

Pokud je však *název* řetězcové vyjádření čísla a zachytávající skupina na této pozici byl explicitně přiřazen číselný název, analyzátor regulárních výrazů nemůže identifikovat zachytávající skupinu podle pořadového čísla. Místo toho vyvolá <xref:System.ArgumentException>. Jediná zachytávající skupina v následujícím příkladu je pojmenována "2". Vzhledem k tomu, že konstrukce `\k` slouží k definování zpětného odkazu s názvem "1", analyzátor regulárních výrazů nemůže identifikovat první zachytávající skupinu a vyvolá výjimku.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a>Které zpětné odkazy se shodují

Zpětný odkaz odkazuje na nejnovější definici skupiny (při porovnání zleva doprava) odkazuje na poslední definici skupiny (definice je hned vlevo). Když skupina provede více zachycení, zpětný odkaz odkazuje na nejnovější zachycení.

Následující příklad obsahuje vzor regulárního výrazu, `(?<1>a)(?<1>\1b)*`, který znovu definuje pojmenovanou skupinu \ 1. Následující tabulka popisuje každý vzor regulárního výrazu.

|Vzor|Popis|
|-------------|-----------------|
|`(?<1>a)`|Porovnává s znakem "a" a přiřadí výsledek do zachytávající skupiny s názvem `1`.|
|`(?<1>\1b)*`|Porovná žádný nebo více výskytů skupiny s názvem `1` společně s "b" a výsledek přiřadí zachycené skupině s názvem `1`.|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

V porovnání regulárního výrazu se vstupním řetězcem ("aababb") modul regulárních výrazů provádí následující operace:

1. Začíná na začátku řetězce a úspěšně porovná "a" s výrazem `(?<1>a)`. Hodnota skupiny `1` je nyní "a".

2. Přejde na druhý znak a úspěšně se shoduje s řetězcem "AB" s výrazem `\1b`nebo "AB". Pak přiřadí výsledek "AB" do `\1`.

3. Posune se na čtvrtý znak. Výraz `(?<1>\1b)*` musí být stejný jako nula nebo vícekrát, takže úspěšně odpovídá řetězci "ABB" s výrazem `\1b`. Přiřadí výsledek "ABB" zpátky na `\1`.

V tomto příkladu je `*` kvantifikátoru smyček – je vyhodnocen opakovaně, dokud se modul regulárních výrazů neshoduje se vzorem, který definuje. Kvantifikátory smyčky nevymažou definice skupin.

Pokud skupina nezaznamenala žádné podřetězce, zpětný odkaz na tuto skupinu není definován a nikdy se neshoduje. To je znázorněno vzorem regulárního výrazu `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, který je definován následujícím způsobem:

|Vzor|Popis|
|-------------|-----------------|
|`\b`|Zahajte shodu na hranici slova.|
|`(\p{Lu}{2})`|Porovnává dvě velká písmena. Toto je první zachytávající skupina.|
|`(\d{2})?`|Porovná žádný nebo jeden výskyt dvou desítkových číslic. Toto je druhá zachytávající skupina.|
|`(\p{Lu}{2})`|Porovnává dvě velká písmena. Toto je třetí zachytávající skupina.|
|`\b`|Ukončí porovnávání na hranici slova.|

Vstupní řetězec může odpovídat tomuto regulárnímu výrazu i v případě, že nejsou k dispozici dvě desítkové číslice definované druhou zachytávající skupinou. Následující příklad ukazuje, že i když je shoda úspěšná, našla se prázdná zachytávající skupina mezi dvěma úspěšnými zachycenými skupinami.

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
