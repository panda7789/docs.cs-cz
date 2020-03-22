---
title: Co je nového v jazyce Visual Basic
ms.date: 10/24/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
ms.openlocfilehash: 3ab468f6c68429a3a5cb8706152288afae520df3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187146"
---
# <a name="whats-new-for-visual-basic"></a>Co je nového v jazyce Visual Basic

Toto téma obsahuje seznam názvů klíčových funkcí pro každou verzi jazyka Visual Basic s podrobným popisem nových a vylepšených funkcí v nejnovějších verzích jazyka.

## <a name="current-version"></a>Aktuální verze

Visual Basic 16.0 / Visual Studio 2019 verze 16.0\
Nové funkce naleznete v [tématu Visual Basic 16.0](#visual-basic-160).

## <a name="previous-versions"></a>Předchozí verze

Visual Basic 15.8 / Visual Studio 2017 verze 15.8\
Nové funkce naleznete v [tématu Visual Basic 15.8](#visual-basic-158).

Visual Basic 15.5 / Visual Studio 2017 verze 15.5\
Nové funkce naleznete v [tématu Visual Basic 15.5](#visual-basic-155).

Visual Basic 15.3 / Visual Studio 2017 verze 15.3\
Nové funkce naleznete v [tématu Visual Basic 15.3](#visual-basic-153).

Visual Basic 2017 / Visual Studio 2017\
Nové funkce najdete v [tématu Visual Basic 2017](#visual-basic-2017).

Visual Basic / Visual Studio 2015\
Nové funkce naleznete v [tématu Visual Basic 14](#visual-basic-14).

Visual Basic / Visual Studio 2013\
Technologické náhledy platformy kompilátoru .NET ("Roslyn")

Visual Basic / Visual Studio 2012\
`Async`a `await` klíčová slova, iterátory, atributy informací o volajícím

Visual Basic, Visual Studio 2010\
Automaticky implementované vlastnosti, inicializátory kolekce, implicitní pokračování řádku, dynamické, obecné odchylky co/contra, globální přístup k oboru názvů

Visual Basic / Visual Studio 2008\
Jazykový integrovaný dotaz (LINQ), literály XML, odvození místního typu, inicializátory objektů, anonymní typy, metody rozšíření, odvození místního `var` typu, výrazy lambda, `if` operátor, částečné metody, typy hodnot s možnou hodnotou s možnou hodnotou

Visual Basic / Visual Studio 2005\
Typy `My` typů a pomocníků (přístup k aplikaci, počítači, systému souborů, síti)

Visual Basic / Visual Studio .NET 2003\
Operátory bitového posunu, deklarace proměnné smyčky

Visual Basic / Visual Studio .NET 2002\
První vydání jazyka Visual Basic .NET

## <a name="visual-basic-160"></a>Visual Basic 16.0

Visual Basic 16.0 se zaměřuje na poskytování více funkcí visual basic runtime (microsoft.visualbasic.dll) na .NET Core a je první verze jazyka Visual Basic zaměřené na .NET Core. Mnoho částí visual basic runtime závisí na WinForms a tyto budou přidány v novější verzi jazyka Visual Basic.

**Komentáře povolené na více místech v rámci prohlášení**

V jazyce Visual Basic 15.8 a starší verze komentáře jsou povoleny pouze na prázdné řádky, na konci příkazu nebo na určitých místech v rámci příkazu, kde je povoleno implicitní pokračování řádku. Počínaje Visual Basic 16.0 komentáře jsou také povoleny po explicitní pokračování řádku a v rámci příkazu na řádku začínající mezerou následuje podtržítko.

```vb
Public Sub Main()
    cmd.CommandText = ' Comment is allowed here without _
        "SELECT * FROM Titles JOIN Publishers " _ ' This is a comment
        & "ON Publishers.PubId = Titles.PubID " _
 _ ' This is a comment on a line without code
        & "WHERE Publishers.State = 'CA'"
End Sub
```

## <a name="visual-basic-158"></a>Visual Basic 15.8

**Optimalizovaný převod s plovoucí desetinnou desetinnou na celé číslo**

V předchozích verzích jazyka Visual Basic převod [Double](../language-reference/data-types/double-data-type.md) a [Single](../language-reference/data-types/single-data-type.md) hodnoty na celá čísla nabízí relativně nízký výkon. Visual Basic 15.8 výrazně zvyšuje výkon převody s plovoucí desetinnou desetinnou hodnotou na celá čísla při předání hodnoty vrácené některou z následujících metod na jednu z [vnitřních funkcí převodu celého čísla jazyka](../language-reference/functions/type-conversion-functions.md) (CByte, CShort, CInt, CLng, CSByte, `Off`CUShort, CUInt, CULng), nebo když je hodnota vrácená některou z následujících metod implicitně přetypována na integrální typ, když je [nastavena](../language-reference/statements/option-strict-statement.md) na :

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Tato optimalizace umožňuje rychlejší spuštění kódu – až dvakrát rychleji pro kód, který provádí velký počet převodů na typy celých čísel. Následující příklad ilustruje některé jednoduché volání metod, které jsou ovlivněny touto optimalizací:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

Všimněte si, že to zkrátí spíše než zaokrouhlit hodnoty s plovoucí desetinnou desetinnou desetinnou hodnotou.

## <a name="visual-basic-155"></a>Visual Basic 15.5

[Nekoncové pojmenované argumenty](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

V jazyce Visual Basic 15.3 a staršíverze, když volání metody zahrnuty argumenty podle pozice a podle názvu, poziční argumenty musel předcházet pojmenované argumenty. Počínaje Visual Basic 15.5, poziční a pojmenované argumenty se mohou zobrazit v libovolném pořadí, pokud jsou všechny argumenty až do posledního pozičního argumentu ve správné poloze. To je užitečné zejména při pojmenované argumenty se používají k kódu čitelnější.

Například následující volání metody má dva poziční argumenty mezi pojmenovaný míchaný argument. Pojmenovaný argument jasně ukazuje, že hodnota 19 představuje stáří.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected`modifikátor přístupu členů](../language-reference/modifiers/private-protected.md)

Tato nová kombinace klíčových slov definuje člen, který je přístupný všem členům v jeho obsahující třídy, jakož i typy odvozené z obsahující třídy, ale pouze v případě, že jsou také nalezeny v obsahující sestavení. Vzhledem k tomu, `Private Protected` že struktury nelze zdědit, lze použít pouze pro členy třídy.

**Přední hex/binární/osmičkový oddělovač**

Visual Basic 2017 přidal podporu`_`znaku podtržítka ( ) jako oddělovač číslic. Počínaje jazykem Visual Basic 15.5 můžete použít znak podtržítka jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi. Následující příklad používá oddělovač úvodní číslice k definování 3 271 948 384 jako šestnáctkové číslo:

```vb
Dim number As Integer = &H_C305_F860
```

Chcete-li použít znak podtržítka jako úvodní oddělovač,\*musíte do souboru projektu jazyka Visual Basic (.vbproj) přidat následující prvek:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15.3

[**Pojmenovaný odvození n-tice**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Při přiřazení hodnoty n-tice prvky z proměnných, Visual Basic odvodí název n-tice prvky z odpovídající názvy proměnných; není třeba explicitně pojmenovat prvek řazené kolekce členů. Následující příklad používá odvození k vytvoření řazené `state` `stateName`kolekce `capital`členů se třemi pojmenovanými prvky , , a .

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Další přepínače kompilátoru**

Kompilátor příkazového řádku jazyka Visual Basic nyní podporuje možnosti kompilátoru [**-refout**](../reference/command-line-compiler/refout-compiler-option.md) a [**-refonly**](../reference/command-line-compiler/refonly-compiler-option.md) pro řízení výstupu referenčních sestavení. **-refout** definuje výstupní adresář referenčního sestavení a **-refonly** určuje, že pouze referenční sestavení má být výstupem kompilací.

## <a name="visual-basic-2017"></a>Visual Basic 2017

[**Záznamů**](../programming-guide/language-features/data-types/tuples.md)

Řazené kolekce členů jsou zjednodušené datové struktury, které se nejčastěji používá k vrácení více hodnot z volání jedné metody. Obvykle chcete-li vrátit více hodnot z metody, musíte provést jednu z následujících akcí:

- Definujte vlastní typ `Class` (a nebo a). `Structure` Jedná se o těžké řešení.

- Definujte jeden `ByRef` nebo více parametrů, kromě vrácení hodnoty z metody.

Podpora kolekce členů visual basic u n-tice umožňuje rychle definovat řazené kolekce členů, volitelně přiřadit sémantické názvy k jeho hodnotám a rychle načíst jeho hodnoty. Následující příklad zalomí volání <xref:System.Int32.TryParse%2A> metody a vrátí řazené kolekce členů.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Potom můžete volat metodu a zpracování vrácené řazené kolekce členů s kódem, jako je následující.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**Binární literály a oddělovače číslic**

Binární literál můžete definovat pomocí `&B` předpony nebo `&b`. Kromě toho můžete použít znak `_`podtržítka , jako oddělovač číslic pro zvýšení čitelnosti. Následující příklad používá obě funkce `Byte` k přiřazení hodnoty a k její zobrazení jako desetinného, šestnáctkového a binárního čísla.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Další informace naleznete v části "Přiřazení literálu" datových typů [Bajt](../language-reference/data-types/byte-data-type.md#literal-assignments), [Celé číslo](../language-reference/data-types/integer-data-type.md#literal-assignments), [Dlouhé](../language-reference/data-types/long-data-type.md#literal-assignments), [Krátké](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [UInteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments)a [UShort.](../language-reference/data-types/ushort-data-type.md#literal-assignments)

[**Podpora pro c# referenční vrácené hodnoty**](../programming-guide/language-features/procedures/ref-return-values.md)

Počínaje C# 7.0, C# podporuje vrácené hodnoty odkazu. To znamená, že když volající metoda obdrží hodnotu vrácenou odkazem, může změnit hodnotu odkazu. Visual Basic neumožňuje vytvářet metody s referenčními vrácenými hodnotami, ale umožňuje využívat a upravovat referenční vrácené hodnoty.

Například následující `Sentence` třída napsaná v `FindNext` c# obsahuje metodu, která najde další slovo ve větě, která začíná zadaným podřetězcem. Řetězec je vrácen jako referenční vrácená `Boolean` hodnota a proměnná předaná odkazem na metodu označuje, zda bylo hledání úspěšné. To znamená, že kromě čtení vrácené hodnoty volající také upravit a že `Sentence` změna se projeví ve třídě.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

V nejjednodušší podobě můžete upravit slovo nalezené ve větě pomocí kódu, jako je následující. Všimněte si, že nepřiřazujete hodnotu metodě, ale spíše výrazu, který metoda vrací, což je referenční vrácená hodnota.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Problém s tímto kódem, i když je, že pokud není nalezen a shoda, metoda vrátí první slovo. Vzhledem k tomu, že `Boolean` příklad nezkoumá hodnotu argumentu k určení, zda je nalezena shoda, upraví první slovo, pokud neexistuje žádná shoda. Následující příklad opravuje tím, že nahradí první slovo se sebou, pokud neexistuje žádná shoda.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Lepším řešením je použít pomocnou metodu, na kterou je předána referenční vrácená hodnota odkazem. Pomocná metoda pak můžete upravit argument předán odkazem. Následující příklad to dělá.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Další informace naleznete v [tématu Reference Return Values](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[Název](../language-reference/operators/nameof.md)

Můžete získat neúplný název řetězce typu nebo člena pro použití v chybové zprávě bez pevného kódování řetězce.  To umožňuje, aby váš kód zůstal správný při refaktoringu.  Tato funkce je také užitečná pro připojení propojení MVC řadiče zobrazení modelu a události změny vlastnosti vypalování.

[Interpolace řetězců](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)

K vytvoření řetězců můžete použít výrazy interpolace řetězců.  Interpolovaný řetězcový výraz vypadá jako řetězec šablony, který obsahuje výrazy.  Interpolovaný řetězec je srozumitelnější s ohledem na argumenty než [složené formátování](../../standard/base-types/composite-formatting.md).

[Přístup a indexování členů s nulovým podmíněným podmínkou](../language-reference/operators/null-conditional-operators.md)

Před provedením operace přístupu člena (`?.`) nebo indexu (`?[]`) můžete otestovat hodnotu null velmi lehkým syntaktním způsobem.  Tyto operátory vám pomohou napsat méně kódu pro zpracování null kontroly, zejména pro sestupdo datových struktur.  Pokud je levý operand nebo odkaz na objekt null, operace vrátí hodnotu null.

[Víceřádkové řetězcové literály](../../visual-basic/programming-guide/language-features/strings/string-basics.md)

Řetězcové literály mohou obsahovat nové řádkové sekvence.  Už nepotřebujete staré řešení používání`<xml><![CDATA[...text with newlines...]]></xml>.Value`

**Komentáře**

Komentáře můžete umístit za implicitní pokračování řádku, uvnitř výrazů inicializátoru a mezi výrazy výrazu LINQ.

**Inteligentnější plně kvalifikované rozlišení názvů**

Daný kód, `Threading.Thread.Sleep(1000)`například , Visual Basic slouží k vyhledat obor názvů "Threading", zjistit, že byl nejednoznačný mezi System.Threading a System.Windows.Threading a potom nahlásit chybu.  Visual Basic nyní zvažuje oba možné obory názvů společně.  Pokud zobrazíte seznam dokončení, editor sady Visual Studio uvádí členy z obou typů v seznamu dokončení.

**Literály prvního roku**

Můžete mít literály data ve formátu yyyy-mm-dd . `#2015-03-17 16:10 PM#`

**Vlastnosti rozhraní jen pro čtení**

Vlastnosti rozhraní jen pro čtení můžete implementovat pomocí vlastnosti write. Rozhraní zaručuje minimální funkčnost a nezastaví implementující třídu od povolení nastavení vlastnosti.

[TypeOf \<expr> \<IsNot typ>](../../visual-basic/language-reference/operators/typeof-operator.md)

Pro větší čitelnost kódu, můžete `TypeOf` nyní `IsNot`použít s .

[#Disable \<>> a \<#Enable ID upozornění](../../visual-basic/language-reference/directives/index.md)

Můžete zakázat a povolit konkrétní upozornění pro oblasti ve zdrojovém souboru.

**Vylepšení komentářů dokumentu XML**

Při psaní komentáře doc, získáte inteligentní editor a vytvořit podporu `crefs` pro ověřování názvů parametrů, správné zpracování (generika, operátory, atd.), vybarvení a refaktoring.

[Definice dílčích modulů a rozhraní](../../visual-basic/language-reference/modifiers/partial.md)

Kromě tříd a struktur můžete deklarovat částečné moduly a rozhraní.

[#Region direktivy uvnitř těl a metod](../../visual-basic/language-reference/directives/region-directive.md)

Oddělovače #Region...#End oblast můžete umístit kamkoli do souboru, do funkcí a dokonce i do těl a napříč těly funkcí.

[Definice přepsání jsou implicitně přetížení](../../visual-basic/language-reference/modifiers/overrides.md)

Pokud přidáte `Overrides` modifikátor do definice, kompilátor implicitně přidá `Overloads` tak, že můžete zadat méně kódu v běžných případech.

**CObj povoleno v argumentech atributů**

Kompilátor slouží k poskytnutí chyby, která CObj(...) nebyla konstanta při použití v konstrukcích atributů.

**Deklarování a využívání nejednoznačných metod z různých rozhraní**

Dříve následující kód přinesl chyby, které `IMock` vám zabránily deklarovat nebo volat `GetDetails` (pokud byly deklarovány v c#):

```vb
Interface ICustomer
  Sub GetDetails(x As Integer)
End Interface

Interface ITime
  Sub GetDetails(x As String)
End Interface

Interface IMock : Inherits ICustomer, ITime
  Overloads Sub GetDetails(x As Char)
End Interface

Interface IMock2 : Inherits ICustomer, ITime
End Interface
```

Nyní kompilátor použije normální pravidla řešení přetížení `GetDetails` zvolit nejvhodnější pro volání a můžete deklarovat vztahy rozhraní v jazyce Visual Basic, jako jsou uvedeny v ukázce.

## <a name="see-also"></a>Viz také

- [Novinky v sadě Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017)
- [Co je nového ve Visual Studiu 2019](/visualstudio/ide/whats-new-visual-studio-2019)
