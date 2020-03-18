---
title: Konstrukce zpětného odkazu v regulárních výrazech rozhraní .NET
description: Zjistěte, jak identifikovat opakované textové prvky pomocí konstrukce zpětného odkazu v regulárním výrazu.
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711529"
---
# <a name="backreference-constructs-in-regular-expressions"></a>Konstrukce zpětných odkazů v regulárních výrazech

Zpětné odkazy poskytují pohodlný způsob, jak identifikovat opakovaný znak nebo podřetězec v řetězci. Pokud například vstupní řetězec obsahuje více výskytů libovolného podřetězce, můžete porovnat první výskyt se zachytávající skupinou a potom použít zpětný odkaz tak, aby odpovídal následným výskytům podřetězce.

> [!NOTE]
> Samostatná syntaxe se používá k odkazování na pojmenované a číslované zachytávající skupiny v náhradních řetězcích. Další informace naleznete v [tématu Substituce](substitutions-in-regular-expressions.md).

Rozhraní .NET definuje samostatné prvky jazyka, které odkazují na číslované a pojmenované zachytávající skupiny. Další informace o zachycení skupin naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="numbered-backreferences"></a>Číslované zpětné odkazy

Číslovaný zpětný odkaz používá následující syntaxi:

`\`*číslo*

kde *číslo* je řadová pozice zachytávající skupiny v regulárním výrazu. Například `\4` odpovídá obsahu čtvrté zachytávající skupiny. Pokud *není ve* vzoru regulárního výrazu definována chyba analýzy a modul <xref:System.ArgumentException>regulárních výrazů vyvolá . Například regulární `\b(\w+)\s\1` výraz je `(\w+)` platný, protože je první a jediná zachytávající skupina ve výrazu. Na druhé straně `\b(\w+)\s\2` je neplatný a vyvolá výjimku argumentu, protože `\2`neexistuje žádná zachytávající skupina očíslovaná . Kromě toho pokud *číslo* identifikuje zachytávající skupinu v určité řadové pozici, ale této zachytávající skupině byl přiřazen číselný název odlišný <xref:System.ArgumentException>od své ordinální pozice, analyzátor regulárních výrazů také vyvolá .

Všimněte si nejednoznačnosti mezi osmičkovými řídicími kódy (například) `\16`a `\`zpětných odkazů *čísel,* které používají stejný zápis. Tato nejednoznačnost je vyřešena takto:

- Výrazy `\1` prostřednictvím `\9` jsou vždy interpretovány jako zpětné odkazy a nikoli jako osmičkové kódy.

- Pokud je první číslice vícemístného výrazu `\80` 8 `\91`nebo 9 (například nebo ), výraz interpretován jako literál.

- Výrazy `\10` od a větší jsou považovány za zpětné odkazy, pokud existuje zpětný odkaz odpovídající tomuto číslu; v opačném případě jsou interpretovány jako osmičkové kódy.

- Pokud regulární výraz obsahuje zpětný odkaz na nedefinované číslo skupiny, dojde k chybě <xref:System.ArgumentException>analýzy a modul regulárních výrazů vyvolá .

Pokud je problém nejednoznačnosti, můžete `\k<`použít *název* `>` zápisu, který je jednoznačný a nemůže být zaměňován s osmičkovými znakovými kódy. Podobně šestnáctkové kódy, jako `\xdd` jsou jednoznačné a nelze je zaměnit se zpětnými odkazy.

Následující příklad najde v řetězci zdvojené znaky slova. Definuje regulární výraz `(\w)\1`, který se skládá z následujících prvků.

|Element|Popis|
|-------------|-----------------|
|`(\w)`|Porovnejte znak slova a přiřaďte jej první zachytávající skupině.|
|`\1`|Porovná další znak, který je stejný jako hodnota první zachytávající skupiny.|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a>Pojmenované zpětné odkazy

Pojmenovaný zpětný odkaz je definován pomocí následující syntaxe:

`\k<`*název*`>`

nebo:

`\k'`*název*`'`

kde *název* je název zachytávající skupiny definovaný ve vzoru regulárního výrazu. Pokud *název* není definován ve vzoru regulárního výrazu, dojde k chybě <xref:System.ArgumentException>analýzy a modul regulárních výrazů vyvolá .

Následující příklad najde v řetězci zdvojené znaky slova. Definuje regulární výraz `(?<char>\w)\k<char>`, který se skládá z následujících prvků.

|Element|Popis|
|-------------|-----------------|
|`(?<char>\w)`|Porovnejte znak slova a přiřaďte jej zachytávající skupině s názvem `char`.|
|`\k<char>`|Porovná další znak, který je stejný `char` jako hodnota zachytávající skupiny.|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a>Pojmenované číselné zpětné odkazy

V pojmenované zpětném `\k`odkazu s může být *název* také řetězcovou reprezentací čísla. Například následující příklad používá regulární výraz `(?<2>\w)\k<2>` k nalezení zdvojené znaky slova v řetězci. V tomto případě příklad definuje zachytávající skupinu, která je explicitně pojmenována "2" a zpětný odkaz je odpovídajícím způsobem pojmenován "2".

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

Pokud je *název* řetězcovou reprezentací čísla a žádná `\k<`zachytávající skupina nemá tento název, *název* `>` je stejný jako číslo zpětného `\` *odkazu*, kde *číslo* je řadová pozice zachycení. V následujícím příkladu je jedna zachytávající skupina s názvem `char`. Konstrukce zpětného odkazu odkazuje `\k<1>`na něj jako . Jak ukazuje výstup z příkladu, <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> volání úspěšné, protože `char` je první zachytávající skupina.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

Pokud je však *název* řetězcovou reprezentací čísla a zachytávající skupině na této pozici byl explicitně přiřazen číselný název, analyzátor regulárních výrazů nemůže identifikovat zachytávající skupinu podle své ordinální pozice. Místo toho hodí <xref:System.ArgumentException>. Jediná zachytávající skupina v následujícím příkladu se nazývá "2". Vzhledem `\k` k tomu, že konstrukce se používá k definování zpětného odkazu s názvem "1", analyzátor regulárních výrazů není schopen identifikovat první zachytávající skupinu a vyvolá výjimku.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a>Co zpětné odkazy shoda

Zpětný odkaz odkazuje na nejnovější definici skupiny (definice nejvíce bezprostředně vlevo, při porovnávání zleva doprava). Když skupina provede více zachycení, zpětný odkaz odkazuje na nejnovější zachycení.

Následující příklad obsahuje vzor regulárního výrazu , `(?<1>a)(?<1>\1b)*`který předefinuje skupinu \1 s názvem. Následující tabulka popisuje každý vzorek v regulárním výrazu.

|Vzor|Popis|
|-------------|-----------------|
|`(?<1>a)`|Porovná znak "a" a přiřadí výsledek zachytávající skupině s názvem `1`.|
|`(?<1>\1b)*`|Porovná nula nebo více výskytů skupiny s názvem `1` spolu s "b" `1`a přiřadí výsledek zachytávající skupině s názvem .|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

Při porovnávání regulárního výrazu se vstupním řetězcem ("aababb") provádí modul regulárních výrazů následující operace:

1. Začíná na začátku řetězce a úspěšně odpovídá "a" `(?<1>a)`s výrazem . Hodnota skupiny `1` je nyní "a".

2. Přejde na druhý znak a úspěšně odpovídá řetězci "ab" s výrazem `\1b`, nebo "ab". Potom přiřadí výsledek, "ab" `\1`na .

3. Posouvá se na čtvrtou postavu. Výraz `(?<1>\1b)*` má odpovídat nula nebo vícekrát, takže úspěšně odpovídá řetězci "abb" s výrazem `\1b`. Přiřadí výsledek, "abb", zpět `\1`na .

V tomto `*` příkladu je opakování kvantifikátoru -- je vyhodnocován opakovaně, dokud modul regulárních výrazů nemůže odpovídat vzoru, který definuje. Opakování kvantifikátorů nevymaže definice skupin.

Pokud skupina nezachytila žádné podřetězce, zpětný odkaz na tuto skupinu není definován a nikdy se neshoduje. To je znázorněno vzorem `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`regulárního výrazu , který je definován následovně:

|Vzor|Popis|
|-------------|-----------------|
|`\b`|Začněte shodu na hranici slova.|
|`(\p{Lu}{2})`|Porovná dvě velká písmena. Toto je první zachytávající skupina.|
|`(\d{2})?`|Porovná nulový nebo jeden výskyt dvou desetinných míst. Toto je druhá zachytávající skupina.|
|`(\p{Lu}{2})`|Porovná dvě velká písmena. Toto je třetí zachytávající skupina.|
|`\b`|Ukončite shodu na hranici slova.|

Vstupní řetězec může odpovídat tomuto regulárnímu výrazu i v případě, že dvě desetinné číslice, které jsou definovány druhou zachytávající skupinou, nejsou k dispozici. Následující příklad ukazuje, že i když je shoda úspěšná, je mezi dvěma úspěšnými zachytávajícími skupinami nalezena prázdná zachytávající skupina.

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
