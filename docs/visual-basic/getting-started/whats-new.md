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
ms.openlocfilehash: 5b1547f596a0ff1c52a402f90457dced6ef604a0
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611793"
---
# <a name="whats-new-for-visual-basic"></a>Co je nového v jazyce Visual Basic

Toto téma obsahuje seznam názvů klíčovou funkcí pro každou verzi jazyka Visual Basic s podrobný popis nové a vylepšené funkce v nejnovějších verzích tohoto jazyka.

## <a name="current-version"></a>Aktuální verze

Visual Basic 15,8 / Visual Studio 2017 verze 15.8 pro nové funkce, najdete v článku [15.8 jazyka Visual Basic](#visual-basic-158)

## <a name="previous-versions"></a>Předchozí verze

Visual Basic verzi 15.5 / Visual Studio 2017 verze 15.5 pro nové funkce, najdete v článku [15.5 jazyka Visual Basic](#visual-basic-155)

Visual Basic 15.3 / Visual Studio 2017 verze 15.3 pro nové funkce, najdete v článku [15.3 jazyka Visual Basic](#visual-basic-153)

Visual Basic 2017 / Visual Studio 2017 pro nové funkce, najdete v článku [2017 jazyka Visual Basic](#visual-basic-2017)

Visual Basic / 2015 Visual Studio pro nové funkce, viz [14 jazyka Visual Basic](#visual-basic-14)

Visual Basic nebo Visual Studio 2013 Technology Preview platformy kompilátoru .NET ("Roslyn")

Visual Basic nebo Visual Studio 2012 `Async` a `await` klíčová slova, iterátory, atributy informace o volajícím

Visual Basic, Visual Studio 2010 automaticky implementované vlastnosti inicializátory kolekce, implicitní pokračování řádku, odchylka dynamické, obecný co/opravné položky ke globální obor názvů přístup,

Visual Basic nebo Visual Studio 2008 Language Integrated Query (LINQ), literály XML, odvození místního typu objektu inicializátory, anonymní typy, metody rozšíření, místní `var` odvození, výrazů lambda, typu `if` částečné – operátor metody, typy s možnou hodnotou Null

Visual Basic nebo Visual Studio 2005 na `My` typy typu a pomocné rutiny (přístup k aplikaci, počítače, systém souborů, sítě)

Visual Basic nebo Visual Studio .NET 2003 bitové posunutí – operátory, smyčky deklarace proměnné

Visual Basic nebo Visual Studio .NET 2002 v první verzi jazyka Visual Basic .NET

## <a name="visual-basic-158"></a>Visual Basic 15.8

**Optimalizované pro převod celého čísla s plovoucí desetinnou čárkou**

V předchozích verzích jazyka Visual Basic, převod [Double](../language-reference/data-types/double-data-type.md) a [jeden](../language-reference/data-types/single-data-type.md) hodnoty na celá čísla nabízí relativně nízký výkon. Visual Basic 15.8 významně zvyšuje výkon převody s plovoucí desetinnou čárkou na celá čísla při předání hodnoty vrácené některý z následujících metod do jednoho z [vnitřní funkce pro převod celého čísla jazyka Visual Basic](../language-reference/functions/type-conversion-functions.md) () CByte CShort, CInt, CLng, csbyte –, cushort –, cuint –, culng –), nebo pokud hodnota vrácená pomocí některé z následujících metod je implicitně přetypován na celočíselný typ při [Option Strict](~/docs/visual-basic/language-reference/statements/option-strict-statement.md) je nastavena na `Off`:

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

Tyto optimalizace umožňuje kód ke spuštění rychleji – až dvakrát jako rychlé pro kód, který nemá velký počet převody na typy celých čísel. Následující příklad ukazuje některé jednoduchý způsob volání, které jsou ovlivněny tyto optimalizace:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174

```

Mějte na paměti, že to zkrátí místo hodnoty zaokrouhlí číslo s plovoucí desetinnou čárkou.

## <a name="visual-basic-155"></a>Visual Basic 15.5

[Nekoncové pojmenované argumenty](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

V jazyce Visual Basic 15.3 a dřívějších verzích volání metody obsažen argumentů podle pozice a podle názvu, měl poziční argumenty předcházet pojmenované argumenty. Od verze 15.5 jazyka Visual Basic, můžete poziční a pojmenované argumenty objevit v libovolném pořadí, pokud jsou všechny argumenty až po poslední poziční argument ve správné pozici. To je zvlášť užitečné, když pojmenované argumenty se používají k zajištění kód lépe čitelný.

Například následující volání metody, které má dva poziční argumenty mezi pojmenovaný argument. Pojmenovaný argument vyjasňuje, která představuje hodnotu 19 stáří.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected` členský modifikátor přístupu](../language-reference/modifiers/private-protected.md)

Tato nová kombinace – klíčové slovo definuje člen, který je přístupný podle všech členů v jeho obsahující třídy a typy odvozené od obsahující třídy, ale pouze v případě, které také najdete v něm obsažené sestavení. Vzhledem k tomu, že nelze dědit struktury, `Private Protected` může používat jedině pro členy třídy.

**Hex/binární soubor/osmičkové počáteční oddělovač**

Visual Basic 2017, přidali jsme podporu pro znak podtržítka (`_`) jako oddělovač číslic. Od verze 15.5 jazyka Visual Basic, můžete použít znak podtržítka jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice. Následující příklad používá oddělovač úvodní číslice k definování 3,271,948,384 jako šestnáctkové číslo:

```vb
Dim number As Integer = &H_C305_F860
```

Pokud chcete použít jako oddělovač úvodní znak podtržítka, je nutné přidat následující prvek do projektu jazyka Visual Basic (\*.vbproj) souboru:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15.3

[**Odvození pojmenované řazené kolekce členů**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Když přiřadíte hodnotu elementů řazené kolekce členů z proměnných, Visual Basic odvodí z něj název elementů řazené kolekce členů z odpovídající názvy proměnných; není nutné explicitně název elementu řazené kolekce členů. Následující příklad používá k vytvoření n-tice s tři pojmenované elementy odvození `state`, `stateName`, a `capital`.

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Další přepínače kompilátoru**

Teď podporuje příkazového řádku kompilátoru jazyka Visual Basic [ **- refout** ](../reference/command-line-compiler/refout-compiler-option.md) a [ **- refout** ](../reference/command-line-compiler/refonly-compiler-option.md) možnosti řízení výstup kompilátoru referenční sestavení. **-refout** definuje výstupní adresář referenční sestavení a **- refout** Určuje, že má být výstupem kompilace pouze odkaz na sestavení.

## <a name="visual-basic-2017"></a>Visual Basic 2017

[**Řazené kolekce členů**](../programming-guide/language-features/data-types/tuples.md)

Řazené kolekce členů jsou jednoduché datové struktury, které se nejčastěji používá k vrácení více hodnot z jedné metody volání. Obvykle vrátit více hodnot z metody, je nutné provést jednu z následujících:

- Definice vlastního typu ( `Class` nebo `Structure`). Toto je těžký řešení.

- Definovat jeden nebo více `ByRef` parametry, než návratová hodnota z metody.

Podpora jazyka Visual Basic pro řazených kolekcí členů umožňuje rychle definovat řazené kolekce členů, Volitelně můžete přiřadit hodnoty sémantického názvy a rychle načíst jeho hodnoty. V následujícím příkladu zabalí volání <xref:System.Int32.TryParse%2A> metodu a vrátí řazené kolekce členů.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Potom můžete volat metodu a zpracovat vrácené řazené kolekce členů s kódem, jako je následující.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**Binární literály a oddělovače číslic:**

Binární literál můžete definovat pomocí předpony `&B` nebo `&b`. Kromě toho můžete použít znak podtržítka `_`, jako oddělovač číslic vylepšit čitelnost. Následující příklad používá obě funkce přiřazení `Byte` hodnotu a zobrazit ho jako desítkové, hexadecimální a binární číslo.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Další informace najdete v tématu v části "Přiřazení literál" [bajtů](../language-reference/data-types/byte-data-type.md#literal-assignments), [celé číslo](../language-reference/data-types/integer-data-type.md#literal-assignments), [dlouhé](../language-reference/data-types/long-data-type.md#literal-assignments), [krátký](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte ](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [Uinteger –](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments), a [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) datové typy.

[**Podporu pro C# referenční návratové hodnoty**](../programming-guide/language-features/procedures/ref-return-values.md)

Od verze C# 7.0, podporuje referenční dokumentace jazyka C# návratové hodnoty. To znamená když volání metody obdrží hodnotu vrácenou příkazem odkaz, můžete změnit hodnotu odkazu. Visual Basic neumožňuje tvorbu metody s odkazem na návratové hodnoty, ale umožní vám využívat a změnit referenční návratové hodnoty.

Například následující `Sentence` zahrnuje třídy napsané v jazyce C# `FindNext` metodu, která najde ve větě, která začíná zadaným podřetězcem následující slovo. Řetězec se vrátí jako odkaz vrátí hodnotu a `Boolean` proměnné, které jsou předány podle odkazu na metodu označuje, zda bylo hledání úspěšné. To znamená, že volající nelze číst pouze vrácené hodnoty; uživatel můžete také upravit jej a této změny se projeví v `Sentence` třídy.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Ve své nejjednodušší podobě můžete upravit slovo nalezené ve větě pomocí kódu, jako je následující. Všimněte si, že jste nejsou přiřazení hodnoty k metodě, ale závisí na výraz, metoda vrátí hodnotu, která je odkaz na návratová hodnota.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Problém s tímto kódem, ale je, že pokud není nalezena shoda, metoda vrátí první slovo. Protože příklad nezkoumá hodnotu `Boolean` argument k určení, zda je nalezena shoda, upraví první slovo. Pokud není nalezena žádná shoda. Následující příklad upravuje to tak, že nahradíte první slovo se sebou samým, pokud není nalezena žádná shoda.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Lepším řešením je použití pomocnou metodu, ke kterému je návratová hodnota odkazu předány podle odkazu. Pomocná metoda poté můžete upravit argument předaný odkazem. Následující příklad činí.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Další informace najdete v tématu [referenční vrátit hodnoty](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[Nameof](../../csharp/language-reference/keywords/nameof.md)

Bez pevného kódování řetězec můžete získat název nekvalifikované řetězce na typ nebo člena pro použití v chybové zprávě.  Díky tomu váš kód zůstane správné refaktoringu.  Tato funkce je také užitečné pro zapojování model-view-controller MVC odkazy a vyvolává události změněné vlastnosti.

[Interpolace řetězců](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)

Výrazy interpolace řetězců můžete použít k vytvoření řetězce.  Interpolovaný řetězcový výraz vypadá jako řetězec šablony, který obsahuje výrazy.  Interpolované řetězce je lze snáze pochopit s ohledem na argumenty než [složené formátování](../../standard/base-types/composite-format.md).

[Přístup ke členu podmíněných Null a indexování](../language-reference/operators/null-conditional-operators.md)

Můžete testovat null velmi malé syntaktické způsobem před provedením přístup ke členu (`?.`) nebo indexu (`?[]`) operace.  Tyto operátory usnadňuje psaní méně kód pro zpracování null kontrol, zejména pro sestupné řazení do datové struktury.  Pokud levý operand nebo objekt odkaz má hodnotu null, operace vrátí hodnotu null.

[Literály víceřádkových řetězců](../../visual-basic/programming-guide/language-features/strings/string-basics.md)

Řetězcové literály můžou obsahovat sekvence znaku nového řádku.  Je již nutné starý obejít použití `<xml><![CDATA[...text with newlines...]]></xml>.Value`

**Komentáře**

Vložit poznámky po řádku implicitní pokračování, uvnitř inicializátoru výrazy a podmínky výrazu LINQ.

**Inteligentnější řešení plně kvalifikovaný název**

Zadaný kód například `Threading.Thread.Sleep(1000)`, používá k vyhledání oboru názvů jazyka Visual Basic "Dělení na vlákna", zjistit bylo nejednoznačné mezi System.Threading a System.Windows.Threading a potom nahlásit chybu.  Visual Basic nyní brány v úvahu oba obory názvů možné dohromady.  Pokud můžete zobrazit seznam dokončení, editoru sady Visual Studio obsahuje členy z obou typů v seznamu dokončení.

**Literály data začínající rokem**

Date – literály může mít ve formátu rrrr mm-dd, `#2015-03-17 16:10 PM#`.

**Vlastnosti rozhraní jen pro čtení**

Můžete implementovat rozhraní vlastnosti jen pro čtení pomocí vlastnosti readwrite.  Rozhraní zaručuje minimální funkční požadavky a nezastaví implementující třída z povolení vlastnost, která má být nastavena.

[TypeOf \<expr > IsNot \<typ >](../../visual-basic/language-reference/operators/typeof-operator.md)

Pro další čitelnost kódu, můžete nyní použít `TypeOf` s `IsNot`.

[Upozornění #Disable \<ID > a upozornění #Enable \<ID >](../../visual-basic/language-reference/directives/index.md)

Můžete zakázat a povolit specifická upozornění pro oblasti v rámci zdrojového souboru.

**Vylepšení komentářů k dokumentu XML**

Při zápisu komentáře, získáte inteligentní editor a podpora pro ověřování názvů parametrů, správné zpracování sestavení `crefs` (obecné typy, operátory, atd.), barevné zvýrazňování a refaktoringu.

[Částečné definice modulu a interface](../../visual-basic/language-reference/modifiers/partial.md)

Kromě tříd a struktur můžete deklarovat dílčí moduly a rozhraní.

[#Region direktivy uvnitř těla metod](../../visual-basic/language-reference/directives/region-directive.md)

Můžete vložit #Region... #End Region oddělovače kdekoli v souboru, do funkcí a dokonce pokrývá funkce těla.

[Přepsání definice jsou implicitně přetížení](../../visual-basic/language-reference/modifiers/overrides.md)

Pokud chcete přidat `Overrides` modifikátor s definicí, kompilátor implicitně přidá `Overloads` tak, aby méně kódu můžete zadat v běžných případů.

**CObj v argumentech atributů povolena**

Kompilátor slouží k pojmenování chybu, CObj(...) nebyl konstantu při použití v atributu konstrukce.

**Deklarace a používání nejednoznačný metody v různá rozhraní**

Dříve vrátil následující kód chyby, které zabránily deklarace `IMock` nebo z volání `GetDetails` (pokud tyto by byl deklarován v jazyce C#):

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

Nyní kompilátor použije normální přetížení rozlišení pravidla k výběru nejvhodnější `GetDetails` volat, a je možné deklarovat vztahy rozhraní v jazyce Visual Basic podobné těm je znázorněno v ukázce.

## <a name="see-also"></a>Viz také:

- [Co je nového v sadě Visual Studio 2017](/visualstudio/ide/whats-new-in-visual-studio)
