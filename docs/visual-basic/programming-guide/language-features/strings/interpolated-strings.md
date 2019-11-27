---
title: Interpolované řetězce
ms.date: 10/31/2017
ms.openlocfilehash: d1220f3804d571f6da229dc5dfa099a22ab1478d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344326"
---
# <a name="interpolated-strings-visual-basic-reference"></a>Interpolované řetězce (Visual Basic Reference)

Slouží k vytváření řetězců.  Interpolovaná řetězcová událost vypadá jako řetězec šablony, který obsahuje *interpolované výrazy*.  Interpolovaná řetězcová funkce vrátí řetězec, který nahradí interpolované výrazy, které obsahuje, spolu s jejich řetězcovými reprezentacemi. Tato funkce je k dispozici v Visual Basic 14 a novějších verzích.

Argumenty interpolované řetězcové řetězce jsou snazší pochopit než [složený formátovací řetězec](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Například interpolovaná řetězcová

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

obsahuje dva interpolované výrazy {Name} a {hours: hh}. Ekvivalentní řetězec složeného formátu je:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours)
```

Struktura interpolované řetězcové řetězce je:

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

kde:

- *Šířka pole* je celé číslo se znaménkem, které označuje počet znaků v poli. Pokud je kladné, pole je zarovnáno vpravo; If negativně zarovnaný doleva.

- *řetězec formátu* je řetězec formátu vhodný pro typ objektu, který se má formátovat. Například u <xref:System.DateTime> hodnoty může to být [standardní formátovací řetězec data a času](../../../../standard/base-types/standard-date-and-time-format-strings.md) , například "d" nebo "d".

> [!IMPORTANT]
> Mezi `$` a `"`, které spouští řetězec, nelze mít žádné prázdné znaky. V důsledku toho dojde k chybě kompilátoru.

Můžete použít interpolované řetězce kdekoli, kde můžete použít řetězcový literál.  Interpolovaná řetězcová doba je vyhodnocena pokaždé, když se spustí kód s interpolovaná řetězcovou dobou. To umožňuje oddělit definici a vyhodnocení interpolované řetězcové lhůty.

Chcete-li zahrnout složenou závorku ("{" nebo "}") do interpolované řetězcové řetězce, použijte dvě složené závorky, "{{" nebo "}}".  Další podrobnosti najdete v části implicitní převody.

Pokud interpolovaná řetězec obsahuje jiné znaky se zvláštními významy v interpolované řetězci, například uvozovky ("), dvojtečka (:) nebo čárka (,), měla by být uvozena řídicím znakem, pokud k nim dojde v textovém literálu, nebo by měly být zahrnuty ve výrazu odděleném závorky, pokud jsou prvky jazyka zahrnuté do interpolované výrazu. Následující příklad označuje uvozovky, které se mají zahrnout do výsledného řetězce, a používá závorky k vymezení výrazu `(age == 1 ? "" : "s")` tak, že dvojtečka není interpretována jako začátek řetězce formátu.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a>Implicitní převody

Existují tři implicitní převody typu z interpolované řetězce:

1. Konverze interpolované řetězcové <xref:System.String>. Následující příklad vrátí řetězec, jehož interpolované řetězcové výrazy byly nahrazeny svými reprezentacemi řetězců. Příklad:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   Toto je konečný výsledek interpretace řetězce. Všechny výskyty dvojitých složených závorek ("{{" a "}}") jsou převedeny na jednu složenou závorku.

2. Převod interpolované řetězcové proměnné na <xref:System.IFormattable>, která umožňuje vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z jedné instance <xref:System.IFormattable>. To je užitečné pro zahrnutí takových věcí jako správných formátů číselného a data pro jednotlivé kultury.  Všechny výskyty dvojitých složených závorek ("{{" a "}}") zůstávají jako dvojité složené závorky, dokud řetězec neformátujete explicitně nebo implicitně voláním metody <xref:System.Object.ToString>.  Všechny obsažené výrazy interpolace jsou převedeny na {0}, {1}a tak dále.

   Následující příklad používá reflexi k zobrazení členů a hodnot pole a vlastností <xref:System.IFormattable> proměnné, která je vytvořena z interpolované řetězcové hodnoty. Také předává <xref:System.IFormattable> proměnnou metodě <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   Všimněte si, že interpolovaná řetězcová operace může být zkontrolována pouze pomocí reflexe. Pokud je předána metodě formátování řetězce, jako je například <xref:System.Console.WriteLine(System.String)>, jsou vyřešeny položky formátu a výsledný řetězec je vrácen.

3. Konverze interpolované řetězcové proměnné na <xref:System.FormattableString>, která představuje řetězec složeného formátu. Kontrola složeného formátovacího řetězce a jeho vykreslení jako výsledný řetězec může například přispět k ochraně proti útoku prostřednictvím injektáže, pokud jste sestavování dotazu. <xref:System.FormattableString> také zahrnuje:

      - <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.

      - <xref:System.FormattableString.Invariant%2A> metoda, která vytvoří řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.

      - <xref:System.FormattableString.ToString(System.IFormatProvider)> metoda, která vytváří výsledný řetězec pro určenou jazykovou verzi.

    Všechny výskyty dvojitých složených závorek ("{{" a "}}") zůstávají jako dvojité složené závorky, dokud je neformátujete.  Všechny obsažené výrazy interpolace jsou převedeny na {0}, {1}a tak dále.

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a>Viz také:

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [Referenční příručka jazyka Visual Basic](index.md)
