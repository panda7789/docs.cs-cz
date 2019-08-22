---
title: Interpolované řetězce (Visual Basic)
ms.date: 10/31/2017
ms.openlocfilehash: b9dd055154c86da370a984a465ed412f1fd9908c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666941"
---
# <a name="interpolated-strings-visual-basic-reference"></a>Interpolované řetězce (Visual Basic Reference)

Slouží k vytváření řetězců.  Interpolovaná řetězcová událost vypadá jako řetězec šablony, který obsahuje *interpolované výrazy*.  Interpolovaná řetězcová funkce vrátí řetězec, který nahradí interpolované výrazy, které obsahuje, spolu s jejich řetězcovými reprezentacemi. Tato funkce je k dispozici v Visual Basic 14 a novějších verzích.

Argumenty interpolované řetězcové řetězce jsou snazší pochopit než [složený formátovací řetězec](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Například interpolovaná řetězcová

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

obsahuje dva interpolované výrazy {Name} a {hours: hh}. Ekvivalentní řetězec složeného formátu je:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);
```

Struktura interpolované řetězcové řetězce je:

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

kde:

- *Šířka pole* je celé číslo se znaménkem, které označuje počet znaků v poli. Pokud je kladné, pole je zarovnáno vpravo; If negativně zarovnaný doleva.

- *řetězec formátu* je řetězec formátu vhodný pro typ objektu, který se má formátovat. Například pro <xref:System.DateTime> hodnotu může být [standardní formátovací řetězec data a času](../../../../standard/base-types/standard-date-and-time-format-strings.md) , například "d" nebo "d".

> [!IMPORTANT]
> Mezi `$` znakem `"` a, který začíná řetězcem, nemůže být mezera. V důsledku toho dojde k chybě kompilátoru.

Můžete použít interpolované řetězce kdekoli, kde můžete použít řetězcový literál.  Interpolovaná řetězcová doba je vyhodnocena pokaždé, když se spustí kód s interpolovaná řetězcovou dobou. To umožňuje oddělit definici a vyhodnocení interpolované řetězcové lhůty.

Chcete-li zahrnout složenou závorku ("{" nebo "}") do interpolované řetězcové řetězce, použijte dvě složené závorky, "{{" nebo "}}".  Další podrobnosti najdete v části implicitní převody.

Pokud interpolovaná řetězec obsahuje jiné znaky se zvláštními významy v interpolované řetězci, například uvozovky ("), dvojtečka (:) nebo čárka (,), měla by být uvozena řídicím znakem, pokud k nim dojde v textovém literálu, nebo by měly být zahrnuty ve výrazu odděleném závorky, pokud jsou prvky jazyka zahrnuté do interpolované výrazu. Následující příklad označuje uvozovky, které mají být zahrnuty ve výsledném řetězci, a používá závorky k vymezení výrazu `(age == 1 ? "" : "s")` tak, aby dvojtečka nebyla interpretována jako začátek řetězce formátu.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a>Implicitní převody

Existují tři implicitní převody typu z interpolované řetězce:

1. Konverze interpolované řetězcové na <xref:System.String>. Následující příklad vrátí řetězec, jehož interpolované řetězcové výrazy byly nahrazeny svými reprezentacemi řetězců. Příklad:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   Toto je konečný výsledek interpretace řetězce. Všechny výskyty dvojitých složených závorek ("{{" a "}}") jsou převedeny na jednu složenou závorku.

2. Převod interpolované řetězce na <xref:System.IFormattable> proměnnou, která umožňuje vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z jedné <xref:System.IFormattable> instance. To je užitečné pro zahrnutí takových věcí jako správných formátů číselného a data pro jednotlivé kultury.  Všechny výskyty dvojitých složených závorek ("{{" a "}}") zůstávají jako dvojité složené závorky, dokud řetězec neformátujete explicitně nebo implicitně voláním <xref:System.Object.ToString> metody.  Všechny obsažené výrazy interpolace jsou převedeny na {0}, {1}a tak dále.

   Následující příklad používá reflexi k zobrazení členů a hodnot pole a vlastností <xref:System.IFormattable> proměnné, která je vytvořena z interpolované řetězcové hodnoty. Také předá <xref:System.IFormattable> proměnnou <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodě.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   Všimněte si, že interpolovaná řetězcová operace může být zkontrolována pouze pomocí reflexe. Pokud je předána metodě formátování řetězce, například <xref:System.Console.WriteLine(System.String)>, jsou vyřešeny jeho položky formátu a výsledný řetězec je vrácen.

3. Konverze interpolované řetězce na <xref:System.FormattableString> proměnnou, která představuje řetězec složeného formátu. Kontrola složeného formátovacího řetězce a jeho vykreslení jako výsledný řetězec může například přispět k ochraně proti útoku prostřednictvím injektáže, pokud jste sestavování dotazu. Zahrnuje <xref:System.FormattableString> také:

      - Přetížení, které vytváří výsledný řetězec <xref:System.Globalization.CultureInfo.CurrentCulture>pro. <xref:System.FormattableString.ToString>

      - Metoda, která vytváří řetězec <xref:System.Globalization.CultureInfo.InvariantCulture>pro. <xref:System.FormattableString.Invariant%2A>

      - <xref:System.FormattableString.ToString(System.IFormatProvider)> Metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi.

    Všechny výskyty dvojitých složených závorek ("{{" a "}}") zůstávají jako dvojité složené závorky, dokud je neformátujete.  Všechny obsažené výrazy interpolace jsou převedeny na {0}, {1}a tak dále.

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a>Viz také:

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [Referenční příručka jazyka Visual Basic](index.md)
