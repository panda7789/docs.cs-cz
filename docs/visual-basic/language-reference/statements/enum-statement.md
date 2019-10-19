---
title: Enum – příkaz (Visual Basic)
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
ms.openlocfilehash: be1780b00b4d58964e1de5ec199cb80dc0f9dba5
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583397"
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

  Volitelné. Seznam atributů, které se vztahují k tomuto výčtu. [Seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) je nutné uzavřít do lomených závorek ("`<`" a "`>`").

  Atribut <xref:System.FlagsAttribute> označuje, že hodnota instance výčtu může zahrnovat více členů výčtu a že každý člen představuje bitové pole v hodnotě výčtu.

- `accessmodifier`

  Volitelné. Určuje, který kód má k tomuto výčtu přístup. Může to být jedna z následujících:

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  Volitelné. Určuje, že tento výčet znovu deklaruje a skryje identicky pojmenovaný prvek programování nebo sadu přetížených prvků v základní třídě. [Stíny](../../../visual-basic/language-reference/modifiers/shadows.md) lze zadat pouze pro samotný výčet, nikoli na žádném z jeho členů.

- `enumerationname`

  Požadováno. Název výčtu. Informace o platných názvech naleznete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `datatype`

  Volitelné. Datový typ výčtu a všech jeho členů.

- `memberlist`

  Požadováno. Seznam konstant členů, které jsou deklarovány v tomto příkazu. Na jednotlivých řádcích zdrojového kódu se zobrazí více členů.

  Každý `member` má následující syntaxi a části: `[<attribute list>] member name [ = initializer ]`

  |Částí|Popis|
  |---|---|
  |`membername`|Požadováno. Název tohoto člena|
  |`initializer`|Volitelné. Výraz, který se vyhodnocuje v době kompilace a přiřazený k tomuto členovi.|

- `End``Enum`

  Ukončí blok `Enum`.

## <a name="remarks"></a>Poznámky

Máte-li sadu nezměněných hodnot, které jsou logicky vzájemně propojeny, můžete je definovat společně ve výčtu. To poskytuje smysluplné názvy pro výčet a jeho členy, které je snazší pamatovat než jejich hodnoty. Pak můžete použít členy výčtu na mnoha místech v kódu.

Mezi výhody používání výčtů patří následující:

- Snižuje chyby způsobené přetypováním nebo nesprávným zadáním čísel.

- V budoucnu usnadňuje změnu hodnot.

- Usnadňuje čtení kódu, což znamená, že je méně pravděpodobný, že budou zavedeny chyby.

- Zajišťuje dopředné kompatibility. Pokud použijete výčty, váš kód je méně pravděpodobný, pokud v budoucnu někdo změní hodnoty odpovídající názvům členů.

Výčet má název, základní datový typ a sadu členů. Každý člen představuje konstantu.

Výčet deklarovaný na úrovni třídy, struktury, modulu nebo rozhraní, mimo jakoukoli proceduru, je *výčet členů*. Je členem třídy, struktury, modulu nebo rozhraní, které je deklaruje.

K výčtům členů lze přistupovat odkudkoli v rámci své třídy, struktury, modulu nebo rozhraní. Kód mimo třídu, strukturu nebo modul musí kvalifikovat název výčtu členů s názvem této třídy, struktury nebo modulu. Je možné vyhnout se nutnosti používat plně kvalifikované názvy přidáním příkazu [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do zdrojového souboru.

Výčet deklarovaný na úrovni oboru názvů, mimo jakoukoliv třídu, strukturu, modul nebo rozhraní, je členem oboru názvů, ve kterém se zobrazí.

*Kontext deklarace* pro výčet musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedura. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Můžete použít atributy na výčet jako celek, ale nikoli na jeho členy jednotlivě. Atribut přispívá informace k metadatům sestavení.

## <a name="data-type"></a>Datový typ

Příkaz `Enum` může deklarovat datový typ výčtu. Každý člen získá datový typ výčtu. Můžete zadat `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong` nebo `UShort`.

Pokud neurčíte `datatype` pro výčet, každý člen získá datový typ jeho `initializer`. Pokud zadáte obě `datatype` i `initializer`, datový typ `initializer` musí být převeden na `datatype`. Pokud není k dispozici žádná `datatype` ani `initializer`, je výchozím nastavením datový typ `Integer`.

## <a name="initializing-members"></a>Inicializace členů

Příkaz `Enum` může inicializovat obsah vybraných členů v `memberlist`. Pomocí `initializer` můžete zadat výraz, který má být přiřazen členu.

Pokud neurčíte `initializer` pro člena, Visual Basic inicializuje buď na hodnotu nula (Pokud se jedná o první `member` v `memberlist`), nebo na hodnotu větší od jedné, než je hodnota bezprostředně předcházejícího `member`.

Výraz zadaný v každém `initializer` může být libovolná kombinace literálů, dalších konstant, které jsou již definovány, a členů výčtu, kteří jsou již definováni, včetně předchozího člena tohoto výčtu. K kombinování takových prvků lze použít aritmetické a logické operátory.

V `initializer` nemůžete použít proměnné ani funkce. Můžete však použít klíčová slova převodu, například `CByte` a `CShort`. @No__t_0 můžete použít také v případě, že ho voláte s konstantním `String` nebo argumentem `Char`, protože lze vyhodnotit v době kompilace.

Výčty nemůžou mít hodnoty s plovoucí desetinnou čárkou. Pokud je členovi přiřazena hodnota s plovoucí desetinnou čárkou a `Option Strict` je nastavena na hodnotu on, dojde k chybě kompilátoru. Pokud je `Option Strict` vypnuto, hodnota je automaticky převedena na typ `Enum`.

Pokud hodnota členu překročí povolený rozsah pro základní datový typ, nebo Pokud inicializujete libovolného člena na maximální hodnotu povolenou podkladovým datovým typem, kompilátor ohlásí chybu.

## <a name="modifiers"></a>Modifikátory

Výčet členů třídy, struktury, modulu a rozhraní je ve výchozím nastavení veřejným přístupem. Můžete upravit jejich úrovně přístupu modifikátory přístupu. Výčty členů oboru názvů mají ve výchozím nastavení přístup typu Friend. Úrovně přístupu můžete upravit na veřejné, ale ne na privátní nebo chráněné. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Všichni členové výčtu mají veřejný přístup a nemůžete použít žádné modifikátory přístupu. Nicméně pokud má výčet vlastní úroveň přístupu s vyšší úrovní oprávnění, má zadaná úroveň přístupu ke výčtu přednost.

Ve výchozím nastavení jsou všechny výčty typy a jejich pole jsou konstanty. Proto klíčová slova `Shared`, `Static` a `ReadOnly` nelze použít při deklaraci výčtu nebo jeho členů.

## <a name="assigning-multiple-values"></a>Přiřazení více hodnot

Výčty typicky znázorňují vzájemně se vylučující hodnoty. Zahrnutím atributu <xref:System.FlagsAttribute> v deklaraci `Enum` můžete místo toho přiřadit více hodnot do instance výčtu. Atribut <xref:System.FlagsAttribute> určuje, že výčet bude zpracován jako bitové pole, tedy sada příznaků. Tyto jsou označovány jako *bitové* výčty.

Pokud deklarujete výčet pomocí atributu <xref:System.FlagsAttribute>, doporučujeme pro hodnoty použít mocniny 2, to znamená 1, 2, 4, 8, 16 a tak dále. Doporučujeme také, aby "žádný" byl název členu, jehož hodnota je 0. Další pokyny najdete v tématu <xref:System.FlagsAttribute> a <xref:System.Enum>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít příkaz `Enum`. Všimněte si, že člen je označován jako `EggSizeEnum.Medium`, a ne jako `Medium`.

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>Příklad

Metoda v následujícím příkladu je mimo třídu `Egg`. Proto je `EggSizeEnum` plně kvalifikovaný jako `Egg.EggSizeEnum`.

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>Příklad

Následující příklad používá příkaz `Enum` k definování související sady pojmenovaných hodnot konstant. V tomto případě hodnoty jsou barvy, které můžete zvolit pro návrh formulářů pro zadávání dat pro databázi.

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>Příklad

Následující příklad ukazuje hodnoty, které obsahují kladná i záporná čísla.

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>Příklad

V následujícím příkladu je použita klauzule `As` k určení `datatype` výčtu.

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít bitový výčet. K instanci bitového výčtu lze přiřadit více hodnot. Deklarace `Enum` obsahuje atribut <xref:System.FlagsAttribute>, který označuje, že výčet lze považovat za sadu příznaků.

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>Příklad

Následující příklad prochází výčet. Používá metodu <xref:System.Enum.GetNames%2A> k načtení pole názvů členů z výčtu a <xref:System.Enum.GetValues%2A> k načtení pole hodnot členů.

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>Viz také:

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konstanty a výčty](../../../visual-basic/language-reference/constants-and-enumerations.md)
