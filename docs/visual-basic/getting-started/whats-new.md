---
title: "Co je nového v jazyce Visual Basic"
ms.date: 04/27/2017
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
caps.latest.revision: "145"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d26eb23aae6e5baec98e27a246d06af6b78e0802
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-for-visual-basic"></a>Co je nového v jazyce Visual Basic

Toto téma obsahuje seznam názvů klíčových funkcí pro každou verzi jazyka Visual Basic s podrobný popis nových a vylepšených funkcí v nejnovější verzi jazyka.
  
## <a name="current-version"></a>Aktuální verze

Visual Basic / Visual Studio .NET 2017   
Nové funkce, najdete v části [2017 Visual Basic](#visual-basic-2017)

## <a name="previous-versions"></a>Předchozí verze

Visual Basic / Visual Studio 2015 rozhraní .NET   
Nové funkce, najdete v části [14 Visual Basic](#visual-basic-14)

Visual Basic / Visual Studio 2013 rozhraní .NET  
Verze Preview technologie kompilátoru platformy .NET ("Roslyn")

Visual Basic / Visual Studio 2012 rozhraní .NET   
`Async`a `await` klíčová slova, iterátory, volající – atributy s informacemi

Visual Basic, Visual Studio 2010 rozhraní .NET   
Automaticky implementované vlastnosti, Inicializátory kolekcí, implicitní pokračování řádku, dynamické, obecný co/opravné položky k odchylky, přístupu globální obor názvů

Visual Basic / Visual Studio 2008 rozhraní .NET   
Jazyk integrovaného dotazu (LINQ), XML – literály, odvození místního typu objektu inicializátory, anonymní typy, rozšiřující metody, místní `var` odvození výrazy lambda typu `if` operátor, částečné metody, typy hodnot s povolenou hodnotou Null  

Visual Basic / Visual Studio 2005 rozhraní .NET   
`My` Typy typu a pomocné rutiny (přístup k aplikaci, počítače, systém souborů, sítě)

Visual Basic / Visual Studio .NET 2003   
Bitové posunutí – operátory, smyčky deklarace proměnné

Visual Basic / Visual Studio .NET 2002   
První verze součásti Visual Basic .NET

## <a name="visual-basic-2017"></a>2017 Visual Basic

[Řazené kolekce členů](../programming-guide/language-features/data-types/tuples.md)

Řazené kolekce členů jsou jednoduché datové struktury, které se nejčastěji používá k vrácení více hodnot z volání jedné metody. Normálně vrátit více hodnot z metody, je nutné provést jednu z těchto možností:

- Definování vlastních typů ( `Class` nebo `Structure`). Toto je těžké řešení.

- Zadejte jednu nebo více `ByRef` parametry, kromě vrací hodnotu z metody.
 
Podpora jazyka Visual Basic pro řazené kolekce členů umožňuje rychle definovat řazené kolekce členů, volitelně přiřadit jeho hodnoty sémantického názvy a rychle načíst jeho hodnoty. Následující příklad zabalí volání <xref:System.Int32.TryParse%2A> metodu a vrátí řazené kolekce členů.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Potom můžete volat metodu a zpracování vrácená řazené kolekce členů s kódem podobně jako tento.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)] 

**Binární literály a oddělovačů číslice**

Binární literálu můžete definovat pomocí předponu `&B` nebo `&b`. Kromě toho můžete použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti. Následující příklad používá obě přiřadit `Byte` hodnotu a pro zobrazení jako decimal, hexadecimální a binární číslo.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Další informace najdete v části "Přiřazení literálu" [bajtů](../language-reference/data-types/byte-data-type.md#literal-assignments), [celé číslo](../language-reference/data-types/integer-data-type.md#literal-assignments), [dlouho](../language-reference/data-types/long-data-type.md#literal-assignments), [krátké](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte – ](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [Uinteger –](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments), a [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) datové typy.

**Podpora pro C# odkaz návratové hodnoty**

Od verze jazyka C# 7, podporuje referenční dokumentace jazyka C# návratové hodnoty. To znamená při volání metody obdrží hodnotu vrácený odkaz, můžete změnit hodnotu odkazu. Metody s odkazem na vytváření obsahu návratové hodnoty, ale možné využívat a upravit vrácené hodnoty referenční dokumentace jazyka Visual Basic není povoleno.

Například následující `Sentence` zahrnuje třídy, které jsou napsané v C# `FindNext` metoda, která vyhledá další aplikace word ve větě, která začíná je určený dílčí řetězec. Řetězec se vrátí jako odkaz vrátí hodnotu a `Boolean` předaná odkazu na metodu proměnná Určuje, zda byla hledání úspěšné. To znamená, že volající nelze číst jenom vrácená hodnota; potvrdí také ho upravit, a že změna se odrazí v `Sentence` třídy.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

V nejjednodušší podobě můžete upravit slovo nalezené ve větě pomocí kódu podobně jako tento. Všimněte si, že jste nejsou přiřazení hodnoty metodě, ale spíše výraz, metoda vrátí, které je odkaz na vrátit hodnotu.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Problém s tímto kódem, ale je, pokud není nalezena shoda, vrátí metoda první slovo. Vzhledem k tomu, že v příkladu není zkontrolujte hodnotu `Boolean` argument k určení, zda je nalezena shoda, upraví první slovo Pokud není nalezena žádná shoda. Následující příklad opraví to nahrazením první slovo sama se sebou, pokud není nalezena žádná shoda.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Lepším řešením je použití Pomocná metoda, ke kterému je předán odkaz návratovou hodnotu odkazem. Pomocná metoda pak můžete upravovat argument předaný odkazem. Následující příklad nemá který.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Další informace najdete v tématu [hodnoty vrátí odkaz na](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[Nameof](../../csharp/language-reference/keywords/nameof.md)  
 Pro použití v chybovou zprávu můžete získat název nekvalifikované řetězce na typ nebo člen bez pevné kódování řetězec.  To umožňuje kód a dál správné refaktoring.  Tato funkce je také užitečné pro zapojování model-view-controller MVC odkazy a ohlásí události změněné vlastnosti.  
  
[Řetězec interpolace](../../csharp/language-reference/keywords/interpolated-strings.md)  
 Řetězec interpolace výrazy můžete vytvářet řetězce.  Interpolované řetězce výrazu vypadá jako šablona řetězec, který obsahuje výrazy.  Interpolované řetězce je jednodušší zjistit, s ohledem na argumenty než [složené formátování](../../standard/base-types/composite-format.md).  
  
[Člen NULL podmíněného přístupu a indexování](../../csharp/language-reference/operators/null-conditional-operators.md)  
Můžete otestovat pro null velmi malé syntaktické způsobem před provedením přístup ke členu (`?.`) nebo index (`?[]`) operaci.  Tyto operátory usnadňuje psaní, méně kód pro zpracování null kontroly, zejména pro sestupné řazení do datové struktury.  Pokud levý operand nebo objekt odkaz má hodnotu null, vrátí hodnotu null operace.  
  
[Víceřádkový textové literály](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 Textové literály může obsahovat pořadí nový řádek.  Je již nebude nutné starý obejít použití`<xml><![CDATA[...text with newlines...]]></xml>.Value`  
  
Komentáře  
Komentáře můžete vložit po implicitní řádku pokračování, uvnitř inicializátoru výrazy a mezi podmínky výrazu LINQ.  
  
 Chytřejší plně kvalifikovaný název řešení  
 Zadaný kód například `Threading.Thread.Sleep(1000)`, Visual Basic použita k vyhledání oboru názvů "Dělení na vlákna", zjistit byl nejednoznačný mezi System.Threading – a System.Windows.Threading a potom nahlásit chybu.  Visual Basic nyní brány v úvahu oba obory názvů možné společně.  Pokud můžete zobrazit seznam dokončení, editoru Visual Studio uvádí členy z obou typů v seznamu dokončení.  
  
 Datum prvního roku literály  
 Máte literály data ve formátu rrrr mm-dd `#2015-03-17 16:10 PM#`.  
  
 Vlastnosti rozhraní určené jen pro čtení  
 Můžete implementovat pomocí vlastnosti readwrite vlastností rozhraní určené jen pro čtení.  Rozhraní zaručuje minimální funkční a nezastaví implementující třídu z povolení vlastnosti, která má být nastavena.  
  
 [TypeOf \<expr > IsNot \<typ >](../../visual-basic/language-reference/operators/typeof-operator.md)  
 Pro další čitelnost kódu, teď můžete použít `TypeOf` s `IsNot`.  
  
 [Upozornění #Disable \<ID > a upozornění #Enable \<ID >](../../visual-basic/language-reference/directives/directives.md)  
 Můžete zakázat a povolit konkrétní varování pro oblasti v rámci zdrojového souboru.  
  
 Vylepšení komentáře Doc XML  
 Při zápisu komentáře doc, můžete získat inteligentní editoru a podpora pro ověření názvy parametrů, správné zpracování sestavení `crefs` (obecné typy, operátory, atd.), barevné a refaktoring.  
  
 [Částečné modulu a definic rozhraní](../../visual-basic/language-reference/modifiers/partial.md)  
 Kromě třídy a struktury můžou deklarovat částečné moduly a rozhraní.  
  
 [#Region direktivy uvnitř těla – metoda](../../visual-basic/language-reference/directives/region-directive.md)  
 Můžete vložit #Region... #End Region oddělovače kdekoli v souboru uvnitř funkce a to i v pokrývání uzlů napříč funkce subjektů.  
  
 [Definice přepsání jsou implicitně přetížení](../../visual-basic/language-reference/modifiers/overrides.md)  
 Pokud přidáte `Overrides` modifikátor k definici kompilátor implicitně přidá `Overloads` tak, aby méně kódu můžete zadat společné případů.  
  
 CObj povolené v argumentech atributy  
 Kompilátor dávat chybu CObj(...) nebyla při použití v konstrukce atribut konstantní.  
  
 Deklarování a použití nejednoznačný metody z různých rozhraní  
 Dříve poskytuje následující kód chyby, které zabránily deklarace `IMock` nebo z volání `GetDetails` (pokud tyto byly přihlášeny v jazyce C#):  
  
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
  
 Teď kompilátor použije pravidel řešení normální přetížení zvolit nejvhodnější `GetDetails` volat, a vztahy rozhraní v jazyce Visual Basic jako ty, můžou deklarovat uvedené v ukázce.  
  
## <a name="see-also"></a>Viz také  
 [Co je nového ve Visual Studio 2017](/visualstudio/ide/whats-new-in-visual-studio)
