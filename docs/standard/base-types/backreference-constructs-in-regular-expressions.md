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
ms.openlocfilehash: 87c3dbde2eb2b5a19b91f34bb2b088af5c0d1827
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290601"
---
# <a name="backreference-constructs-in-regular-expressions"></a>Konstrukce zpětných odkazů v regulárních výrazech

Zpětná reference poskytují pohodlný způsob identifikace opakovaného znaku nebo podřetězce v rámci řetězce. Například pokud vstupní řetězec obsahuje více výskytů libovolného dílčího řetězce, můžete porovnat první výskyt se zachytávající skupinou a potom použít zpětný odkaz pro vyhledání dalších výskytů podřetězce.

> [!NOTE]
> Samostatná syntaxe se používá pro odkazování na pojmenované a očíslované zachytávající skupiny v náhradních řetězcích. Další informace naleznete v tématu [nahrazování](substitutions-in-regular-expressions.md).

Rozhraní .NET definuje samostatné prvky jazyka pro odkazování na očíslované a pojmenované zachytávající skupiny. Další informace o zachycujících skupinách naleznete v tématu [Grouping konstrukcís](grouping-constructs-in-regular-expressions.md).

## <a name="numbered-backreferences"></a>Číslované zpětné odkazy

Číslovaný zpětný odkaz používá následující syntaxi:

`\`*číslo*

kde *Number* je ordinální pozice zachytávající skupiny v regulárním výrazu. Například `\4` odpovídá obsahu čtvrté zachytávající skupiny. Pokud *číslo* není definováno ve vzoru regulárního výrazu, dojde k chybě analýzy a modul regulárních výrazů vyvolá <xref:System.ArgumentException> . Například regulární výraz `\b(\w+)\s\1` je platný, protože `(\w+)` se jedná o první a pouze zachytávající skupinu ve výrazu. Na druhé straně `\b(\w+)\s\2` je neplatný a vyvolá výjimku argumentu, protože není očíslována žádná zachytávající skupina `\2` . Kromě toho, pokud *Number* identifikuje zachytávající skupinu na určitém pořadovém místě, ale u této zachytávající skupiny byl přiřazen číselný název jiný než pořadové číslo, analyzátor regulárního výrazu také vyvolá výjimku <xref:System.ArgumentException> .

Všimněte si nejednoznačnosti mezi osmičkovým řídicím kódem (například `\16` ) a `\` *number* zpětnými referencemi, které používají stejný zápis. Tato nejednoznačnost je vyřešena následujícím způsobem:

- Výrazy po `\1` `\9` jsou vždy interpretovány jako zpětné odkazy a nikoli jako osmičkové kódy.

- Pokud je první číslice výrazu s více číslicemi 8 nebo 9 (například `\80` nebo `\91` ), výraz, který je interpretován jako literál.

- Výrazy z `\10` a vyšší jsou považovány za zpětnou referenci, pokud existuje zpětný odkaz odpovídající tomuto číslu. v opačném případě jsou interpretovány jako osmičkové kódy.

- Pokud regulární výraz obsahuje zpětný odkaz na nedefinované číslo skupiny, dojde k chybě analýzy a modul regulárních výrazů vyvolá <xref:System.ArgumentException> .

Pokud je nejednoznačnost problém, můžete použít `\k<` *name* `>` notaci Name, který je nejednoznačný a nemůže být zaměněn pomocí osmičkových kódů znaků. Podobně šestnáctkové kódy, jako `\xdd` jsou nejednoznačné a nemohou být zaměňovány s zpětnými odkazy.

Následující příklad vyhledá dvojitě vyhledané znaky v řetězci. Definuje regulární výraz, `(\w)\1` , který se skládá z následujících prvků.

|Prvek|Popis|
|-------------|-----------------|
|`(\w)`|Porovnává znak slova a přiřadí ho k první zachytávající skupině.|
|`\1`|Porovnává s následujícím znakem, který je stejný jako hodnota první zachytávající skupiny.|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a>Pojmenované zpětné odkazy

Pojmenovaný zpětný odkaz je definován pomocí následující syntaxe:

`\k<`*název*`>`

nebo:

`\k'`*název*`'`

kde *Name* je název zachytávající skupiny definované ve vzoru regulárního výrazu. Pokud *název* není definován ve vzoru regulárního výrazu, dojde k chybě analýzy a modul regulárních výrazů vyvolá <xref:System.ArgumentException> .

Následující příklad vyhledá dvojitě vyhledané znaky v řetězci. Definuje regulární výraz, `(?<char>\w)\k<char>` , který se skládá z následujících prvků.

|Prvek|Popis|
|-------------|-----------------|
|`(?<char>\w)`|Porovnává znak slova a přiřadí ho k zachycené skupině s názvem `char` .|
|`\k<char>`|Porovnává s následujícím znakem, který je stejný jako hodnota `char` zachytávající skupiny.|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a>Pojmenované číselné zpětné odkazy

V pojmenovaném zpětném odkazu s `\k` , *název* může být také řetězcové vyjádření čísla. Například následující příklad používá regulární výraz `(?<2>\w)\k<2>` k vyhledání dvojitě používaných znaků v řetězci. V tomto případě příklad definuje zachytávající skupinu, která je explicitně pojmenována "2" a zpětný odkaz má odpovídající název "2".

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

Pokud je *název* řetězcové vyjádření čísla a žádná zachytávající skupina nemá tento název, `\k<` *název* `>` je stejný jako zpětný odkaz `\` , kde *Number* je pořadové *číslo*pozice zachycení. V následujícím příkladu je k dispozici jedna zachytávající skupina s názvem `char` . Konstrukce zpětného odkazování na ni odkazuje jako `\k<1>` . Jak ukazuje výstup z příkladu, volání je <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> úspěšné, protože `char` je první zachytávající skupina.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

Pokud je však *název* řetězcové vyjádření čísla a zachytávající skupina na této pozici byl explicitně přiřazen číselný název, analyzátor regulárních výrazů nemůže identifikovat zachytávající skupinu podle pořadového čísla. Místo toho vyvolá <xref:System.ArgumentException> . Jediná zachytávající skupina v následujícím příkladu je pojmenována "2". Vzhledem k tomu `\k` , že konstrukce slouží k definování zpětného odkazu s názvem "1", analyzátor regulárních výrazů nemůže identifikovat první zachytávající skupinu a vyvolá výjimku.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a>Které zpětné odkazy se shodují

Zpětný odkaz odkazuje na nejnovější definici skupiny (při porovnání zleva doprava) odkazuje na poslední definici skupiny (definice je hned vlevo). Když skupina provede více zachycení, zpětný odkaz odkazuje na nejnovější zachycení.

Následující příklad obsahuje vzor regulárního výrazu, `(?<1>a)(?<1>\1b)*` který předefinuje pojmenovanou skupinu \ 1. Následující tabulka popisuje každý vzor regulárního výrazu.

|Vzor|Popis|
|-------------|-----------------|
|`(?<1>a)`|Porovnává s znakem "a" a přiřadí výsledek do zachytávající skupiny s názvem `1` .|
|`(?<1>\1b)*`|Porovná žádný nebo více výskytů skupiny s názvem `1` společně s "b" a přiřadí výsledek do zachytávající skupiny s názvem `1` .|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

V porovnání regulárního výrazu se vstupním řetězcem ("aababb") modul regulárních výrazů provádí následující operace:

1. Začíná na začátku řetězce a úspěšně vyhledá výraz "a" `(?<1>a)` . Hodnota `1` skupiny je nyní "a".

2. Přejde na druhý znak a úspěšně se shoduje s řetězcem "AB" a výrazem `\1b` nebo "AB". Pak přiřadí výsledek "AB" do `\1` .

3. Posune se na čtvrtý znak. Výraz `(?<1>\1b)*` se musí shodovat s žádným nebo víckrát, takže úspěšně odpovídá řetězci "ABB" s výrazem `\1b` . Přiřadí výsledek "ABB" zpátky na `\1` .

V tomto příkladu `*` je kvantifikátor opakování – je vyhodnocen opakovaně, dokud se modul regulárních výrazů nemůže shodovat se vzorkem, který definuje. Kvantifikátory smyčky nevymažou definice skupin.

Pokud skupina nezaznamenala žádné podřetězce, zpětný odkaz na tuto skupinu není definován a nikdy se neshoduje. To je znázorněno vzorem regulárního výrazu `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` , který je definován následujícím způsobem:

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

## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](regular-expression-language-quick-reference.md)
