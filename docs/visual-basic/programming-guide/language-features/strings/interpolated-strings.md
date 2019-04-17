---
title: Interpolované řetězce (Visual Basic)
ms.date: 10/31/2017
ms.openlocfilehash: 408f3232258b3b4c7fe6ec160149f8ac70b84b03
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610675"
---
# <a name="interpolated-strings-visual-basic-reference"></a>Interpolované řetězce (referenční dokumentace jazyka Visual Basic)

Použít k vytvoření řetězce.  Interpolovaný řetězec vypadá jako řetězec šablony, který obsahuje *interpolovaných výrazů*.  Interpolované řetězce vrátí řetězec, který nahradí interpolovaných výrazů, které obsahuje jejich řetězcové vyjádření. Tato funkce je dostupná v jazyce Visual Basic, 14 a novějších verzích.

Jsou Jednoduší na porozumění než argumenty interpolovaném řetězci [složený řetězec formátu](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Například interpolovaný řetězec

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

obsahuje dva interpolovaných výrazů {name}"a"{hodin: hh}". Je ekvivalentní složeném formátovacím řetězci:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);
```

Struktura interpolovaného řetězce je:

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

kde:

- *Šířka pole* je celé číslo se znaménkem, která určuje počet znaků v poli. Pokud je pozitivní, pole zarovnané vpravo; Pokud je záporná, zarovnané vlevo.

- *řetězec formátu* formátovací řetězec odpovídá typu formátovaného objektu. Třeba <xref:System.DateTime> hodnotu, může to být [řetězec formátu data a času](~/docs/standard/base-types/standard-date-and-time-format-strings.md) jako je například "D" nebo "d".

> [!IMPORTANT]
> Nemůže obsahovat žádné prázdné znaky. mezi `$` a `"` na začátku řetězce. To způsobí chybu kompilátoru.

Můžete použít interpolovaném řetězci kdekoli můžete použít textový literál.  Interpolované řetězce se vyhodnocuje pokaždé, když spustí kód interpolovaném řetězci. To umožňuje oddělit definici a hodnocení interpolovaného řetězce.

Zahrnout složenou závorku ("{" nebo "}") v interpolovaném řetězci, použijte dvě složené závorky, "{{" nebo "}}".  Další podrobnosti v části implicitní převody.

Pokud interpolovaný řetězec obsahuje jiné znaky zvláštní význam v interpolovaném řetězci, jako je například dvojité uvozovky ("), dvojtečka (:) nebo čárka (,), že by měly být ukončeny Pokud k nim dojde v textovém literálu nebo by měla být součástí výrazu odděleny závorky, pokud jsou prvky jazyka, které jsou součástí interpolovaným výrazem. Následující příklad řídicí sekvence uvozovek pro zahrnutí ve výsledném řetězci a používá závorky pro vymezení výraz `(age == 1 ? "" : "s")` tak, aby dvojtečka není interpretován jako od řetězec formátu.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a>Implicitní převody

Existují tři implicitních převodech typů v interpolovaném řetězci:

1. Převod interpolované řetězce, který se <xref:System.String>. Následující příklad vrátí řetězec, jehož interpolovaném řetězci výrazy byly nahrazeny jejich řetězcové vyjádření. Příklad:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   Toto je konečný výsledek interpretace řetězce. Všechny výskyty dvojitých složených závorek ("{{" a "}}") jsou převedeny na jednu složenou závorku.

2. Převod interpolovaného řetězce do <xref:System.IFormattable> proměnné, která umožňuje vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance. To je užitečné pro včetně prvků jako správný číselné a číselné formáty pro jednotlivé jazykové verze.  Všechny výskyty dvojitých složených závorek ("{{" a "}}") zůstanou jako dvojitých složených závorek, dokud je naformátovat řetězec voláním explicitně nebo implicitně <xref:System.Object.ToString> metody.  Všechny obsažené interpolace výrazy jsou převedeny na {0}, {1}, a tak dále.

   Následující příklad používá reflexi k zobrazení členů, jakož i hodnoty polí a vlastností <xref:System.IFormattable> proměnná, která je vytvořena z interpolovaného řetězce. Také předá <xref:System.IFormattable> proměnnou <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metoda.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   Mějte na paměti, můžete ho zkontrolovat interpolovaném řetězci pouze pomocí reflexe. Pokud je předán do řetězce formátování, jako například <xref:System.Console.WriteLine(System.String)>, jeho položkami formátu jsou vyřešeny a vrátí výsledný řetězec.

3. Převod interpolované řetězce, který se <xref:System.FormattableString> proměnné, která představuje složený řetězec formátu. Kontrola složeném formátovacím řetězci a jak se vykresluje v důsledku řetězec, například vám můžou pomoct chránit před útoky prostřednictvím injektáže, pokud vytváříte dotazu. A <xref:System.FormattableString> také zahrnuje:

      - A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.

      - A <xref:System.FormattableString.Invariant%2A> metodu, která vytvoří řetězec <xref:System.Globalization.CultureInfo.InvariantCulture>.

      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu, která vytváří výsledný řetězec pro zadanou jazykovou verzi.

    Všechny výskyty dvojitých složených závorek ("{{" a "}}") zůstanou jako dvojitých složených závorek, dokud je naformátovat.  Všechny obsažené interpolace výrazy jsou převedeny na {0}, {1}, a tak dále.

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a>Viz také:

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [Referenční příručka jazyka Visual Basic](index.md)
