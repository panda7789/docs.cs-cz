---
title: Co je nového
ms.date: 10/24/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
ms.openlocfilehash: e9ab745a60cd9eb646bee57a9a6838c30add77c5
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359204"
---
# <a name="whats-new-for-visual-basic"></a>Co je nového pro Visual Basic

V tomto tématu je uveden seznam klíčových funkcí pro jednotlivé verze Visual Basic s podrobným popisem nových a vylepšených funkcí v nejnovějších verzích jazyka.

## <a name="current-version"></a>Aktuální verze

Visual Basic 16,0/Visual Studio 2019 verze 16,0 \
Nové funkce najdete v tématu [Visual Basic 16,0](#visual-basic-160).

## <a name="previous-versions"></a>Předchozí verze

Visual Basic 15,8/Visual Studio 2017 verze 15,8 \
Nové funkce najdete v tématu [Visual Basic 15,8](#visual-basic-158).

Visual Basic 15,5/Visual Studio 2017 verze 15,5 \
Nové funkce najdete v tématu [Visual Basic 15,5](#visual-basic-155).

Visual Basic 15,3/Visual Studio 2017 verze 15,3 \
Nové funkce najdete v tématu [Visual Basic 15,3](#visual-basic-153).

Visual Basic 2017/Visual Studio 2017 \
Nové funkce najdete v tématu [Visual Basic 2017](#visual-basic-2017).

Visual Basic/Visual Studio 2015 \
Nové funkce najdete v tématu [Visual Basic 14](#visual-basic-14).

Visual Basic/Visual Studio 2013 \
Verze Preview .NET Compiler Platform pro technologie ("Roslyn")

Visual Basic/Visual Studio 2012 \
`Async` a `await` klíčová slova, iterátory, atributy informací o volajícím

Visual Basic, Visual Studio 2010 \
Automaticky implementované vlastnosti, inicializátory kolekce, implicitní pokračování řádku, dynamická, obecná kovariantní odchylka, globální přístup k oboru názvů

Visual Basic/Visual Studio 2008 \
Language Integrated Query (LINQ), literály XML, odvození místního typu, Inicializátory objektů, anonymní typy, metody rozšíření, `var` odvození místního typu, výrazy lambda, `if` operátor, částečné metody, typy hodnot s možnou hodnotou null

Visual Basic/Visual Studio 2005 \
`My`Typ a pomocné typy (přístup k aplikaci, počítač, systém souborů, síť)

Visual Basic/Visual Studio .NET 2003 \
Operátory bitového posunutí, deklarace proměnné smyčky

Visual Basic/Visual Studio .NET 2002 \
První vydání rozhraní Visual Basic .NET

## <a name="visual-basic-160"></a>Visual Basic 16,0

Visual Basic 16,0 se zaměřuje na poskytnutí více funkcí modulu runtime Visual Basic (microsoft.visualbasic.dll) do .NET Core a je první verzí Visual Basic zaměřená na .NET Core. Mnoho částí modulu runtime Visual Basic závisí na WinForms a ty budou přidány v novější verzi Visual Basic.

**Komentáře povolené na více místech v rámci příkazů**

V Visual Basic 15,8 a dřívějších verzích jsou komentáře povoleny pouze na prázdných řádcích, na konci příkazu nebo na specifických místech v rámci příkazu, kde je povoleno implicitní pokračování řádku. Počínaje Visual Basic 16,0 jsou komentáře povoleny také po explicitním pokračování řádku a v rámci příkazu na řádku, který začíná mezerou následovanou podtržítkem.

```vb
Public Sub Main()
    cmd.CommandText = ' Comment is allowed here without _
        "SELECT * FROM Titles JOIN Publishers " _ ' This is a comment
        & "ON Publishers.PubId = Titles.PubID " _
 _ ' This is a comment on a line without code
        & "WHERE Publishers.State = 'CA'"
End Sub
```

## <a name="visual-basic-158"></a>Visual Basic 15,8

**Konverze optimalizované na celočíselnou desetinnou čárku**

V předchozích verzích Visual Basic se konverze [dvojitých](../language-reference/data-types/double-data-type.md) a [jednoduchých](../language-reference/data-types/single-data-type.md) hodnot na celá čísla, která nabízí relativně špatný výkon. Visual Basic 15,8 významně vylepšuje výkon převodů s plovoucí desetinnou čárkou na celá čísla, Pokud předáte hodnotu vrácenou některou z následujících metod pro jednu z hodnot [vnitřní Visual Basic celočíselné funkce pro převod](../language-reference/functions/type-conversion-functions.md) (CByte, CShort, CInt, CLng, CSByte, CUShort, CUInt, CULng) nebo pokud je hodnota vrácená některou z následujících metod implicitně převedena na celočíselný typ, pokud je [možnost Strict](../language-reference/statements/option-strict-statement.md) nastavena na `Off` :

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

Tato optimalizace umožňuje, aby kód běžel rychleji – až dvakrát pro kód, který provádí velký počet převodů na celočíselné typy. Následující příklad ilustruje některá volání jednoduchých metod, která jsou ovlivněna touto optimalizací:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

Všimněte si, že se zkrátí místo zaokrouhlení hodnot s plovoucí desetinnou čárkou.

## <a name="visual-basic-155"></a>Visual Basic 15,5

[Nekoncové pojmenované argumenty](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

V Visual Basic 15,3 a starších verzích, pokud volání metody zahrnuje argumenty podle umístění a podle názvu, musely být Poziční argumenty předcházet pojmenovaným argumentům. Počínaje Visual Basic 15,5 se poziční a pojmenované argumenty mohou objevit v libovolném pořadí, pokud jsou všechny argumenty až do posledního pozičního argumentu ve správné pozici. To je užitečné hlavně v případě, že se pojmenované argumenty používají k čitelnějšímu čitelnosti kódu.

Například následující volání metody má dva Poziční argumenty mezi pojmenovaným argumentem. Pojmenovaný argument umožňuje vymazat, že hodnota 19 představuje stáří.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected` modifikátor přístupu ke členu](../language-reference/modifiers/private-protected.md)

Tato nová kombinace klíčových slov definuje člena, ke kterému mají přístup všichni členové ve své nadřazené třídě, a také typy odvozené z nadřazené třídy, ale pouze v případě, že jsou také v nadřazeném sestavení. Protože struktury nelze zdědit, `Private Protected` lze použít pouze pro členy třídy.

**Počáteční hex/binární/osmičkový oddělovač**

Visual Basic 2017 byla přidána podpora znaku podtržítka ( `_` ) jako oddělovače číslic. Počínaje Visual Basic 15,5 můžete použít znak podtržítka jako úvodní oddělovač mezi předponou a hexadecimální, binární nebo osmičkovou číslicí. Následující příklad používá úvodní oddělovač číslic k definování 3 271 948 384 jako šestnáctkového čísla:

```vb
Dim number As Integer = &H_C305_F860
```

Chcete-li použít znak podtržítka jako úvodní oddělovač, je nutné přidat následující prvek do souboru Visual Basic projektu ( \* . vbproj):

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15,3

[**Odvození pojmenované řazené kolekce členů**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Pokud přiřadíte hodnotu prvků řazené kolekce členů z proměnných, Visual Basic odvodí název prvků řazené kolekce členů z odpovídajících názvů proměnných; nemusíte explicitně pojmenovat prvek řazené kolekce členů. Následující příklad používá odvození pro vytvoření řazené kolekce členů se třemi pojmenovanými prvky, `state` , `stateName` a `capital` .

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Další přepínače kompilátoru**

Kompilátor příkazového řádku Visual Basic nyní podporuje možnosti kompilátoru [**-refout**](../reference/command-line-compiler/refout-compiler-option.md) a [**-nepoužívejte refout**](../reference/command-line-compiler/refonly-compiler-option.md) pro řízení výstupu referenčních sestavení. **-refout** definuje výstupní adresář referenčního sestavení a **-nepoužívejte refout** určuje, že kompilace bude výstupem pouze referenční sestavení.

## <a name="visual-basic-2017"></a>Visual Basic 2017

[**Řazené kolekce členů**](../programming-guide/language-features/data-types/tuples.md)

Řazené kolekce členů jsou odlehčené datové struktury, které nejčastěji slouží k vracení více hodnot z jednoho volání metody. Aby bylo možné vracet více hodnot z metody, je obvykle nutné provést jednu z následujících akcí:

- Definujte vlastní typ (a `Class` nebo `Structure` ). Toto je těžké řešení.

- Definujte jeden nebo více `ByRef` parametrů, kromě vrácení hodnoty z metody.

Podpora Visual Basic řazených kolekcí členů vám umožní rychle definovat řazenou kolekci členů, volitelně přiřadit sémantické názvy k jejím hodnotám a rychle načíst její hodnoty. Následující příklad zalomí volání <xref:System.Int32.TryParse%2A> metody a vrátí řazenou kolekci členů.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Pak můžete zavolat metodu a zpracovat vrácenou řazenou kolekci členů s kódem podobným následujícímu.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**Binární literály a oddělovače číslic**

Můžete definovat binární literál pomocí předpony `&B` nebo `&b` . Kromě toho můžete ke zlepšení čitelnosti použít znak podtržítka, `_` jako oddělovač číslic. Následující příklad používá obě funkce k přiřazení `Byte` hodnoty a k jejich zobrazení jako desítkové, šestnáctkové a binární číslo.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Další informace naleznete v části "přiřazení literálů" v datových typech [Byte](../language-reference/data-types/byte-data-type.md#literal-assignments), [Integer](../language-reference/data-types/integer-data-type.md#literal-assignments), [Long](../language-reference/data-types/long-data-type.md#literal-assignments), [short](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [UInteger –](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ulong](../language-reference/data-types/ulong-data-type.md#literal-assignments)a [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) .

[**Podpora vrácených hodnot odkazů jazyka C#**](../programming-guide/language-features/procedures/ref-return-values.md)

Počínaje jazykem C# 7,0 podporuje jazyk C# návratové hodnoty odkazů. To znamená, že když volající metoda obdrží hodnotu vrácenou odkazem, může změnit hodnotu odkazu. Visual Basic neumožňuje vytvářet metody s návratovými hodnotami odkazů, ale umožňuje využívat a upravovat návratové hodnoty odkazů.

Například následující `Sentence` Třída napsaná v jazyce C# obsahuje `FindNext` metodu, která najde další slovo ve větě začínající zadaným podřetězcem. Řetězec je vrácen jako návratová hodnota odkazu a `Boolean` Proměnná předaná odkazem na metodu označuje, zda bylo hledání úspěšné. To znamená, že kromě přečtení vrácené hodnoty ho může volající také změnit a tato změna se projeví ve `Sentence` třídě.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

V nejjednodušším tvaru můžete změnit slovo, které se nachází ve větě, pomocí kódu podobného následujícímu. Všimněte si, že nepřiřazujete hodnotu metodě, ale spíše výrazu, který metoda vrátí, což je návratová hodnota odkazu.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Problém s tímto kódem je však v případě, že není nalezena shoda, metoda vrátí první slovo. Vzhledem k tomu, že tento příklad neověřuje hodnotu `Boolean` argumentu k určení, zda je nalezena shoda, upraví první slovo, pokud se neshoduje. Následující příklad tento problém opraví nahrazením prvního slova samotným, pokud se neshodují.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Lepším řešením je použití pomocné metody, na kterou je návratová hodnota odkazu předána odkazem. Pomocná metoda pak může upravit argument předaný do něj odkazem. V následujícím příkladu je to.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Další informace najdete v tématu [referenční návratové hodnoty](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[NameOf](../language-reference/operators/nameof.md)

Můžete získat Nekvalifikovaný název řetězce typu nebo člena pro použití v chybové zprávě bez pevného kódování řetězce.  To umožňuje, aby kód zůstal správný při refaktoringu.  Tato funkce je užitečná také pro zapojení odkazů Model-View-Controller a při vyvolávání událostí změněných vlastností.

[Interpolace řetězců](../programming-guide/language-features/strings/interpolated-strings.md)

Výrazy interpolace řetězce lze použít k sestavení řetězců.  Výraz interpolující řetězcové řetězce vypadá jako řetězec šablony, který obsahuje výrazy.  Interpolovaná řetězcová řetězec je snazší pochopit s ohledem na argumenty, než je [složené formátování](../../standard/base-types/composite-formatting.md).

[Přístup k podmíněnému přístupu a indexování člena s hodnotou null](../language-reference/operators/null-conditional-operators.md)

Před provedením operace přístup k členu ( `?.` ) nebo indexu () je možné otestovat pro hodnotu null v velmi lehké syntaktické syntaxi `?[]` .  Tyto operátory vám pomůžou napsat méně kódu pro zpracování kontrol s hodnotou null, zejména pro sestupné seřazení do datových struktur.  Pokud levý operand nebo odkaz na objekt má hodnotu null, operace vrátí hodnotu null.

[Víceřádkové řetězcové literály](../programming-guide/language-features/strings/string-basics.md)

Řetězcové literály mohou obsahovat sekvence nového řádku.  Nebudete už potřebovat používání staré práce `<xml><![CDATA[...text with newlines...]]></xml>.Value`

**Komentáře**

Komentáře lze vložit po implicitním pokračování řádku, uvnitř výrazů inicializátorů a mezi výrazy výrazu LINQ.

**Plně kvalifikované rozlišení názvů pro inteligentnější**

Daný kód, jako `Threading.Thread.Sleep(1000)` je Visual Basic, který se používá k vyhledání oboru názvů "Threading", zjistí, že byl nejednoznačný mezi System. Threading a System. Windows. Threading a pak hlásí chybu.  Visual Basic nyní posuzuje jak možné obory názvů současně.  Pokud zobrazíte seznam dokončení, Editor sady Visual Studio vypíše členy z obou typů v seznamu pro doplňování.

**Literály počátečního data roku**

Ve formátu RRRR-MM-DD můžete mít literály kalendářních dat `#2015-03-17 16:10 PM#` .

**Vlastnosti rozhraní jen pro čtení**

Vlastnosti rozhraní jen pro čtení můžete implementovat pomocí vlastnosti. Rozhraní garantuje minimální funkčnost a neukončí implementující třídu, která umožňuje nastavit vlastnost.

[TypeOf \<expr> IsNot \<type>](../language-reference/operators/typeof-operator.md)

Pro lepší čitelnost kódu můžete nyní použít `TypeOf` s `IsNot` .

[Upozornění #Disable \<ID> a upozornění #Enable \<ID>](../language-reference/directives/index.md)

Můžete zakázat a povolit specifická upozornění pro oblasti v rámci zdrojového souboru.

**Vylepšení komentářů k dokumentu XML**

Při psaní komentářů k dokumentům získáte inteligentní Editor a podporu sestavení pro ověřování názvů parametrů, správného zpracování `crefs` (obecných typů, operátorů atd.), Colorizing a refaktoringu.

[Definice částečný modul a rozhraní](../language-reference/modifiers/partial.md)

Kromě tříd a struktur můžete deklarovat částečné moduly a rozhraní.

[Direktivy #Region uvnitř těla metody](../language-reference/directives/region-directive.md)

#Region... #End oddělovače oblastí můžete umístit kdekoli v souboru, uvnitř funkcí a dokonce i napříč různými oblastmi funkcí.

[Definice přepsání jsou implicitně přetížení.](../language-reference/modifiers/overrides.md)

Pokud přidáte `Overrides` modifikátor do definice, kompilátor implicitně přidá, `Overloads` takže můžete v běžných případech napsat méně kódu.

**CObj povolený v argumentech atributů**

Kompilátor použitý k chybě, která CObj (...), není při použití v konstrukcích atributů konstanta.

**Deklarace a využívání dvojznačných metod z různých rozhraní**

Dříve následující kód vrátil chyby, které vám zabraňují v deklarování `IMock` nebo volání `GetDetails` (pokud jsou deklarovány v jazyce C#):

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

Nyní kompilátor použije normální pravidla pro rozlišení přetížení k výběru nejvhodnějšího `GetDetails` pro volání a můžete deklarovat vztahy rozhraní v Visual Basic jako ty, které jsou uvedeny v ukázce.

## <a name="see-also"></a>Viz také

- [Co je nového v aplikaci Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017)
- [Novinky v sadě Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019)
