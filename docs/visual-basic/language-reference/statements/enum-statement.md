---
title: Enum – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 976cc68d67c69ec86918962ab2dd3406d15aed9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404729"
---
# <a name="enum-statement-visual-basic"></a>Enum – příkaz (Visual Basic)

Deklaruje výčet a definuje hodnoty jeho členů.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a>Součásti

- `attributelist`

  Nepovinný parametr. Seznam atributů, které se vztahují k tomuto výčtu. [Seznam atributů](attribute-list.md) musíte uzavřít do lomených závorek (" `<` " a " `>` ").

  <xref:System.FlagsAttribute>Atribut označuje, že hodnota instance výčtu může zahrnovat více členů výčtu a že každý člen představuje bitové pole v hodnotě výčtu.

- `accessmodifier`

  Nepovinný parametr. Určuje, který kód má k tomuto výčtu přístup. Může to být jedna z následujících:

  - [Republik](../modifiers/public.md)

  - [Proti](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Hlášen](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Soukromé chráněné](../modifiers/private-protected.md)

- `Shadows`

  Nepovinný parametr. Určuje, že tento výčet znovu deklaruje a skryje identicky pojmenovaný prvek programování nebo sadu přetížených prvků v základní třídě. [Stíny](../modifiers/shadows.md) lze zadat pouze pro samotný výčet, nikoli na žádném z jeho členů.

- `enumerationname`

  Povinná hodnota. Název výčtu. Informace o platných názvech naleznete v tématu [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `datatype`

  Nepovinný parametr. Datový typ výčtu a všech jeho členů.

- `memberlist`

  Povinná hodnota. Seznam konstant členů, které jsou deklarovány v tomto příkazu. Na jednotlivých řádcích zdrojového kódu se zobrazí více členů.

  Každá `member` z nich má následující syntaxi a části:`[<attribute list>] member name [ = initializer ]`

  |Část|Description|
  |---|---|
  |`membername`|Povinná hodnota. Název tohoto člena|
  |`initializer`|Nepovinný parametr. Výraz, který se vyhodnocuje v době kompilace a přiřazený k tomuto členovi.|

- `End` `Enum`

  Ukončí `Enum` blok.

## <a name="remarks"></a>Poznámky

Máte-li sadu nezměněných hodnot, které jsou logicky vzájemně propojeny, můžete je definovat společně ve výčtu. To poskytuje smysluplné názvy pro výčet a jeho členy, které je snazší pamatovat než jejich hodnoty. Pak můžete použít členy výčtu na mnoha místech v kódu.

Mezi výhody používání výčtů patří následující:

- Snižuje chyby způsobené přetypováním nebo nesprávným zadáním čísel.

- V budoucnu usnadňuje změnu hodnot.

- Usnadňuje čtení kódu, což znamená, že je méně pravděpodobný, že budou zavedeny chyby.

- Zajišťuje dopředné kompatibility. Pokud použijete výčty, váš kód je méně pravděpodobný, pokud v budoucnu někdo změní hodnoty odpovídající názvům členů.

Výčet má název, základní datový typ a sadu členů. Každý člen představuje konstantu.

Výčet deklarovaný na úrovni třídy, struktury, modulu nebo rozhraní, mimo jakoukoli proceduru, je *výčet členů*. Je členem třídy, struktury, modulu nebo rozhraní, které je deklaruje.

K výčtům členů lze přistupovat odkudkoli v rámci své třídy, struktury, modulu nebo rozhraní. Kód mimo třídu, strukturu nebo modul musí kvalifikovat název výčtu členů s názvem této třídy, struktury nebo modulu. Je možné vyhnout se nutnosti používat plně kvalifikované názvy přidáním příkazu [Imports](imports-statement-net-namespace-and-type.md) do zdrojového souboru.

Výčet deklarovaný na úrovni oboru názvů, mimo jakoukoliv třídu, strukturu, modul nebo rozhraní, je členem oboru názvů, ve kterém se zobrazí.

*Kontext deklarace* pro výčet musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedura. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

Můžete použít atributy na výčet jako celek, ale nikoli na jeho členy jednotlivě. Atribut přispívá informace k metadatům sestavení.

## <a name="data-type"></a>Typ dat

`Enum`Příkaz může deklarovat datový typ výčtu. Každý člen získá datový typ výčtu. Můžete zadat `Byte` , `Integer` , `Long` , `SByte` , `Short` , `UInteger` , `ULong` , nebo `UShort` .

Pokud pro výčet neurčíte `datatype` , každý člen získá datový typ svého `initializer` . Pokud zadáte obojí `datatype` a `initializer` , datový typ `initializer` musí být převoditelné na `datatype` . V případě `datatype` `initializer` , že není k dispozici ani, je výchozím datovým typem `Integer` .

## <a name="initializing-members"></a>Inicializace členů

`Enum`Příkaz může inicializovat obsah vybraných členů v `memberlist` . Použijete `initializer` k poskytnutí výrazu, který má být přiřazen členu.

Pokud pro člena neurčíte `initializer` , Visual Basic inicializuje buď na nulu (Pokud se jedná o první `member` v `memberlist` ), nebo na hodnotu větší od jedné, než je bezprostředně předchozí `member` .

Výraz zadaný v každém z nich `initializer` může být libovolná kombinace literálů, dalších konstant, které jsou již definovány, a členů výčtu, kteří jsou již definováni, včetně předchozího člena tohoto výčtu. K kombinování takových prvků lze použít aritmetické a logické operátory.

V nástroji nelze použít proměnné nebo funkce `initializer` . Můžete však použít klíčová slova převodu, jako je `CByte` a `CShort` . Můžete také použít, `AscW` Pokud je volána s konstantou `String` nebo `Char` argumentem, protože lze vyhodnotit v době kompilace.

Výčty nemůžou mít hodnoty s plovoucí desetinnou čárkou. Pokud je členovi přiřazena hodnota s plovoucí desetinnou čárkou a `Option Strict` je nastavena na hodnotu on, dojde k chybě kompilátoru. Pokud `Option Strict` je hodnota vypnuta, hodnota je automaticky převedena na `Enum` typ.

Pokud hodnota členu překročí povolený rozsah pro základní datový typ, nebo Pokud inicializujete libovolného člena na maximální hodnotu povolenou podkladovým datovým typem, kompilátor ohlásí chybu.

## <a name="modifiers"></a>Modifikátory

Výčet členů třídy, struktury, modulu a rozhraní je ve výchozím nastavení veřejným přístupem. Můžete upravit jejich úrovně přístupu modifikátory přístupu. Výčty členů oboru názvů mají ve výchozím nastavení přístup typu Friend. Úrovně přístupu můžete upravit na veřejné, ale ne na privátní nebo chráněné. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

Všichni členové výčtu mají veřejný přístup a nemůžete použít žádné modifikátory přístupu. Nicméně pokud má výčet vlastní úroveň přístupu s vyšší úrovní oprávnění, má zadaná úroveň přístupu ke výčtu přednost.

Ve výchozím nastavení jsou všechny výčty typy a jejich pole jsou konstanty. `Shared` `Static` `ReadOnly` Klíčová slova, a nelze proto použít při deklaraci výčtu nebo jejích členů.

## <a name="assigning-multiple-values"></a>Přiřazení více hodnot

Výčty typicky znázorňují vzájemně se vylučující hodnoty. Zahrnutím <xref:System.FlagsAttribute> atributu do `Enum` deklarace můžete místo toho přiřadit více hodnot instanci výčtu. <xref:System.FlagsAttribute>Atribut určuje, že výčet bude zpracován jako bitové pole, tedy sada příznaků. Tyto jsou označovány jako *bitové* výčty.

Pokud deklarujete výčet pomocí <xref:System.FlagsAttribute> atributu, doporučujeme pro tyto hodnoty použít mocniny 2, to znamená 1, 2, 4, 8, 16 a tak dále. Doporučujeme také, aby "žádný" byl název členu, jehož hodnota je 0. Další pokyny naleznete v tématech <xref:System.FlagsAttribute> a <xref:System.Enum> .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `Enum` příkaz. Všimněte si, že člen je označován jako `EggSizeEnum.Medium` a nikoli jako `Medium` .

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>Příklad

Metoda v následujícím příkladu je mimo `Egg` třídu. Proto `EggSizeEnum` je plně kvalifikovaný jako `Egg.EggSizeEnum` .

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>Příklad

Následující příklad používá `Enum` příkaz k definování související sady pojmenovaných hodnot konstant. V tomto případě hodnoty jsou barvy, které můžete zvolit pro návrh formulářů pro zadávání dat pro databázi.

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>Příklad

Následující příklad ukazuje hodnoty, které obsahují kladná i záporná čísla.

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>Příklad

V následujícím příkladu `As` je použita klauzule k určení `datatype` výčtu.

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít bitový výčet. K instanci bitového výčtu lze přiřadit více hodnot. `Enum`Deklarace obsahuje <xref:System.FlagsAttribute> atribut, který označuje, že výčet lze považovat za sadu příznaků.

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>Příklad

Následující příklad prochází výčet. Používá <xref:System.Enum.GetNames%2A> metodu k načtení pole názvů členů z výčtu a <xref:System.Enum.GetValues%2A> k načtení pole hodnot členů.

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>Viz také

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const – příkaz](const-statement.md)
- [Dim – příkaz](dim-statement.md)
- [Implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Konstanty a výčty](../constants-and-enumerations.md)
