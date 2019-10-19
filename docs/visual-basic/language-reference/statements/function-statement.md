---
title: Function – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 046a3a7d50d15cd3e59205998554a4c330d4552c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581839"
---
# <a name="function-statement-visual-basic"></a>Function – příkaz (Visual Basic)

Deklaruje název, parametry a kód, které definují proceduru `Function`.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a>Součásti

- `attributelist`

  Volitelné. Viz [seznam atributů](attribute-list.md).

- `accessmodifier`

  Volitelné. Může to být jedna z následujících:

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Volitelné. Může to být jedna z následujících:

  - [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Volitelné. Viz [Shared](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  Volitelné. Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Async`

  Volitelné. Viz [Async](../../../visual-basic/language-reference/modifiers/async.md).

- `Iterator`

  Volitelné. Podívejte se na [iterátor](../../../visual-basic/language-reference/modifiers/iterator.md).

- `name`

  Požadováno. Název procedury. Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `typeparamlist`

  Volitelné. Seznam parametrů typu pro obecný postup Viz [seznam typů](type-list.md).

- `parameterlist`

  Volitelné. Seznam názvů místních proměnných, které představují parametry tohoto postupu. Viz [seznam parametrů](parameter-list.md).

- `returntype`

  Vyžaduje se, pokud je `Option Strict` `On`. Datový typ hodnoty vrácené tímto postupem.

- `Implements`

  Volitelné. Označuje, že tento postup implementuje jeden nebo více `Function` procedur, každý z nich definovaný v rozhraní implementovaném touto procedurou obsahuje třídu nebo strukturu. Viz [příkaz Implements](implements-statement.md).

- `implementslist`

  Vyžaduje se, pokud je dodána `Implements`. Seznam `Function`ch procedur, které jsou implementovány.

  `implementedprocedure [ , implementedprocedure ... ]`

  Každý `implementedprocedure` má následující syntaxi a části:

  `interface.definedname`

  |Částí|Popis|
  |---|---|
  |`interface`|Požadováno. Název rozhraní implementovaného touto procedurou obsahuje třídu nebo strukturu.|
  |`definedname`|Požadováno. Název, podle kterého je procedura definovaná v `interface`.|

- `Handles`

  Volitelné. Označuje, že tento postup může zpracovávat jednu nebo více konkrétních událostí. Viz [Handles](handles-clause.md).

- `eventlist`

  Vyžaduje se, pokud je dodána `Handles`. Seznam událostí, které tato procedura zpracovává

  `eventspecifier [ , eventspecifier ... ]`

  Každý `eventspecifier` má následující syntaxi a části:

  `eventvariable.event`

  |Částí|Popis|
  |---|---|
  |`eventvariable`|Požadováno. Objektová proměnná deklarovaná s datovým typem třídy nebo struktury, která vyvolává událost.|
  |`event`|Požadováno. Název události, kterou tato procedura zpracovává|

- `statements`

  Volitelné. Blok příkazů, které mají být provedeny v rámci tohoto postupu.

- `End Function`

  Ukončí definici tohoto postupu.

## <a name="remarks"></a>Poznámky

Veškerý spustitelný kód musí být v rámci procedury. Každý postup je deklarován v rámci třídy, struktury nebo modulu, který je označován jako obsahující třídu, strukturu nebo modul.

Chcete-li vrátit hodnotu volajícímu kódu, použijte `Function` proceduru; v opačném případě použijte `Sub` proceduru.

## <a name="defining-a-function"></a>Definování funkce

Můžete definovat `Function` proceduru pouze na úrovni modulu. Proto kontext deklarace pro funkci musí být třída, struktura, modul nebo rozhraní a nemůže se jednat o zdrojový soubor, obor názvů, proceduru nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

výchozími postupy `Function` jsou veřejné přístupy. Můžete upravit jejich úrovně přístupu modifikátory přístupu.

@No__t_0 procedura může deklarovat datový typ hodnoty, kterou procedura vrátí. Můžete zadat libovolný datový typ nebo název výčtu, strukturu, třídu nebo rozhraní. Pokud nezadáte parametr `returntype`, procedura vrátí `Object`.

Pokud tento postup používá klíčové slovo `Implements`, obsahující třídu nebo strukturu musí mít také příkaz `Implements`, který následuje bezprostředně za `Class` nebo `Structure` příkaz. Příkaz `Implements` musí zahrnovat každé rozhraní, které je určeno v `implementslist`. Název, kterým rozhraní definuje `Function` (v `definedname`), ale nemusí odpovídat názvu tohoto postupu (v `name`).

> [!NOTE]
> Lambda výrazy můžete použít k definování vložených výrazů funkcí. Další informace naleznete v tématu [výraz Function](../../../visual-basic/language-reference/operators/function-expression.md) a [lambda výrazy](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="returning-from-a-function"></a>Vrácení z funkce

Když se `Function` procedura vrátí k volajícímu kódu, provádění pokračuje pomocí příkazu, který následuje za příkazem, který se nazývá procedura.

Chcete-li vrátit hodnotu z funkce, můžete buď přiřadit hodnotu k názvu funkce nebo ji zahrnout do příkazu `Return`.

Příkaz `Return` současně přiřadí návratovou hodnotu a ukončí funkci, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

Následující příklad přiřadí návratovou hodnotu k názvu funkce `myFunction` a poté pomocí příkazu `Exit Function` vrátí.

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

Příkazy `Exit Function` a `Return` způsobují bezprostřední ukončení `Function`ho postupu. Libovolný počet `Exit Function` a `Return` příkazů se může objevit kdekoli v proceduře a můžete kombinovat `Exit Function` a `Return` příkazy.

Použijete-li `Exit Function` bez přiřazení hodnoty k `name`, procedura vrátí výchozí hodnotu datového typu, který je zadán v `returntype`. Pokud není zadán `returntype`, procedura vrátí `Nothing`, což je výchozí hodnota pro `Object`.

## <a name="calling-a-function"></a>Volání funkce

Proceduru `Function` zavoláte pomocí názvu procedury následovaný seznamem argumentů v závorkách ve výrazu. Závorky můžete vynechat pouze v případě, že neposkytujete žádné argumenty. Váš kód je však čitelnější, pokud vždy zahrnete závorky.

Proceduru `Function` zavoláte stejným způsobem jako u libovolné funkce knihovny, jako je například `Sqrt`, `Cos` nebo `ChrW`.

Funkci můžete také volat pomocí klíčového slova `Call`. V takovém případě se návratová hodnota ignoruje. Ve většině případů se použití klíčového slova `Call` nedoporučuje. Další informace naleznete v tématu [Call Statement](call-statement.md).

Visual Basic někdy mění uspořádání aritmetických výrazů a zvyšuje tak vnitřní efektivitu. Z tohoto důvodu byste neměli použít `Function` proceduru v aritmetickém výrazu, pokud funkce změní hodnotu proměnných ve stejném výrazu.

## <a name="async-functions"></a>Asynchronní funkce

*Asynchronní* funkce umožňuje vyvolat asynchronní funkce bez použití explicitního zpětného volání nebo ručního rozdělení kódu napříč více funkcemi nebo lambda výrazy.

Pokud označíte funkci s modifikátorem [Async](../../../visual-basic/language-reference/modifiers/async.md) , můžete použít operátor [await](../../../visual-basic/language-reference/operators/await-operator.md) ve funkci. Když ovládací prvek dosáhne `Await` výraz ve funkci `Async`, ovládací prvek se vrátí volajícímu a průběh funkce je pozastaven až do dokončení očekávané úlohy. Po dokončení úlohy může provádění pokračovat ve funkci.

> [!NOTE]
> @No__t_0 procedura se vrátí volajícímu, když dojde buď k prvnímu očekávanému objektu, který ještě nebyl dokončen, nebo se dostane na konec `Async` postupu, podle toho, co nastane dříve.

@No__t_0 funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>. Příklad funkce `Async`, která má návratový typ <xref:System.Threading.Tasks.Task%601>, je uveden níže.

Funkce `Async` nemůže deklarovat žádné parametry [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .

[Dílčí příkaz](sub-statement.md) lze také označit modifikátorem `Async`. Používá se hlavně pro obslužné rutiny událostí, kde nelze vracet hodnotu. Procedura `Async` `Sub` nemůže být očekávána a volající procedury `Async` `Sub` nemůže zachytit výjimky, které jsou vyvolány postupem `Sub`.

Další informace o funkcích `Async` naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../../visual-basic/programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>Funkce iterátoru

Funkce *iterátoru* provádí vlastní iteraci v kolekci, jako je například list nebo Array. Funkce iterátoru používá příkaz [yield](yield-statement.md) k vrácení jednotlivých prvků po jednom. Při dosažení příkazu [yield](yield-statement.md) se aktuální umístění v kódu pamatuje. Spuštění je restartováno z tohoto umístění při příštím volání funkce iterátoru.

Můžete zavolat iterátor z klientského kódu s použitím [pro každý... Další](for-each-next-statement.md) příkaz.

Návratový typ funkce iterátoru může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601>.

Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).

## <a name="example"></a>Příklad

Následující příklad používá příkaz `Function` k deklaraci názvu, parametrů a kódu, který tvoří tělo `Function`ho postupu. Modifikátor `ParamArray` umožňuje funkci přijmout proměnlivý počet argumentů.

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>Příklad

Následující příklad vyvolá funkci deklarovanou v předchozím příkladu.

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>Příklad

V následujícím příkladu je `DelayAsync` `Async` `Function`, který má návratový typ <xref:System.Threading.Tasks.Task%601>. `DelayAsync` má příkaz `Return`, který vrací celé číslo. Proto musí deklarace funkce `DelayAsync` mít návratový typ `Task(Of Integer)`. Vzhledem k tomu, že návratový typ je `Task(Of Integer)`, vyhodnocení výrazu `Await` v `DoSomethingAsync` vytvoří celé číslo. To je znázorněno v tomto prohlášení: `Dim result As Integer = Await delayTask`.

Procedura `startButton_Click` je příkladem `Async Sub` postupu. Vzhledem k tomu, že `DoSomethingAsync` je `Async` funkce, musí být úkol pro volání `DoSomethingAsync` očekáván, jak ukazuje následující příkaz: `Await DoSomethingAsync()`. Procedura `startButton_Click` `Sub` musí být definována s modifikátorem `Async`, protože obsahuje výraz `Await`.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Viz také:

- [Příkaz Sub](sub-statement.md)
- [Procedury funkce](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Seznam parametrů](parameter-list.md)
- [Příkaz Dim](dim-statement.md)
- [Příkaz Call](call-statement.md)
- [Tohoto](of-clause.md)
- [Pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Řešení potíží s procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Výraz Function](../../../visual-basic/language-reference/operators/function-expression.md)
