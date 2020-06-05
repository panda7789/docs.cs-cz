---
title: Function – příkaz
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
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404625"
---
# <a name="function-statement-visual-basic"></a>Function – příkaz (Visual Basic)

Deklaruje název, parametry a kód, které definují `Function` proceduru.

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

  Nepovinný parametr. Viz [seznam atributů](attribute-list.md).

- `accessmodifier`

  Nepovinný parametr. Může to být jedna z následujících:

  - [Republik](../modifiers/public.md)

  - [Proti](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Hlášen](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Soukromé chráněné](../modifiers/private-protected.md)

  Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Nepovinný parametr. Může to být jedna z následujících:

  - [Přetížení](../modifiers/overloads.md)

  - [Přepsání](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Nepovinný parametr. Viz [Shared](../modifiers/shared.md).

- `Shadows`

  Nepovinný parametr. Viz [Shadows](../modifiers/shadows.md).

- `Async`

  Nepovinný parametr. Viz [Async](../modifiers/async.md).

- `Iterator`

  Nepovinný parametr. Podívejte se na [iterátor](../modifiers/iterator.md).

- `name`

  Povinná hodnota. Název procedury. Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `typeparamlist`

  Nepovinný parametr. Seznam parametrů typu pro obecný postup Viz [seznam typů](type-list.md).

- `parameterlist`

  Nepovinný parametr. Seznam názvů místních proměnných, které představují parametry tohoto postupu. Viz [seznam parametrů](parameter-list.md).

- `returntype`

  Požadováno v `Option Strict` případě `On` , že je. Datový typ hodnoty vrácené tímto postupem.

- `Implements`

  Nepovinný parametr. Označuje, že tento postup implementuje jeden nebo více `Function` postupů, každý z nich definovaný v rozhraní implementovaném touto procedurou obsahuje třídu nebo strukturu. Viz [příkaz Implements](implements-statement.md).

- `implementslist`

  Vyžaduje `Implements` se, pokud je zadaný. Seznam `Function` implementovaných procedur.

  `implementedprocedure [ , implementedprocedure ... ]`

  Každá `implementedprocedure` z nich má následující syntaxi a části:

  `interface.definedname`

  |Část|Description|
  |---|---|
  |`interface`|Povinná hodnota. Název rozhraní implementovaného touto procedurou obsahuje třídu nebo strukturu.|
  |`definedname`|Povinná hodnota. Název, podle kterého je procedura definovaná `interface` .|

- `Handles`

  Nepovinný parametr. Označuje, že tento postup může zpracovávat jednu nebo více konkrétních událostí. Viz [Handles](handles-clause.md).

- `eventlist`

  Vyžaduje `Handles` se, pokud je zadaný. Seznam událostí, které tato procedura zpracovává

  `eventspecifier [ , eventspecifier ... ]`

  Každá `eventspecifier` z nich má následující syntaxi a části:

  `eventvariable.event`

  |Část|Description|
  |---|---|
  |`eventvariable`|Povinná hodnota. Objektová proměnná deklarovaná s datovým typem třídy nebo struktury, která vyvolává událost.|
  |`event`|Povinná hodnota. Název události, kterou tato procedura zpracovává|

- `statements`

  Nepovinný parametr. Blok příkazů, které mají být provedeny v rámci tohoto postupu.

- `End Function`

  Ukončí definici tohoto postupu.

## <a name="remarks"></a>Poznámky

Veškerý spustitelný kód musí být v rámci procedury. Každý postup je deklarován v rámci třídy, struktury nebo modulu, který je označován jako obsahující třídu, strukturu nebo modul.

Chcete-li vrátit hodnotu volajícímu kódu, použijte `Function` proceduru. v opačném případě použijte `Sub` proceduru.

## <a name="defining-a-function"></a>Definování funkce

Můžete definovat `Function` proceduru pouze na úrovni modulu. Proto kontext deklarace pro funkci musí být třída, struktura, modul nebo rozhraní a nemůže se jednat o zdrojový soubor, obor názvů, proceduru nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

`Function`postupy jsou výchozí pro veřejný přístup. Můžete upravit jejich úrovně přístupu modifikátory přístupu.

`Function`Procedura může deklarovat datový typ hodnoty, kterou procedura vrátí. Můžete zadat libovolný datový typ nebo název výčtu, strukturu, třídu nebo rozhraní. Pokud parametr nezadáte `returntype` , procedura se vrátí `Object` .

Pokud tento postup používá `Implements` klíčové slovo, obsahující třídu nebo strukturu musí mít také `Implements` příkaz, který následuje hned za `Class` příkazem or `Structure` . `Implements`Příkaz musí zahrnovat každé rozhraní, které je určeno v `implementslist` . Název, pomocí kterého rozhraní definuje `Function` (in), ale `definedname` nemusí odpovídat názvu této procedury (v `name` ).

> [!NOTE]
> Lambda výrazy můžete použít k definování vložených výrazů funkcí. Další informace naleznete v tématu [výraz Function](../operators/function-expression.md) a [lambda výrazy](../../programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="returning-from-a-function"></a>Vrácení z funkce

Když se `Function` procedura vrátí na volající kód, vykonání pokračuje příkazem, který následuje za příkazem, který se nazývá procedura.

Chcete-li vrátit hodnotu z funkce, můžete buď přiřadit hodnotu k názvu funkce nebo ji zahrnout do `Return` příkazu.

`Return`Příkaz současně přiřadí návratovou hodnotu a ukončí funkci, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

Následující příklad přiřadí návratovou hodnotu k názvu funkce `myFunction` a potom použije příkaz, `Exit Function` který se má vrátit.

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

`Exit Function`Příkazy a `Return` způsobují bezprostřední ukončení `Function` procedury. Libovolný počet `Exit Function` příkazů a `Return` se může objevit kdekoli v proceduře a můžete kombinovat `Exit Function` a `Return` příkazy.

Použijete `Exit Function` -li bez přiřazení hodnoty k `name` , procedura vrátí výchozí hodnotu datového typu, který je určen v `returntype` . Pokud `returntype` není zadán, procedura vrátí `Nothing` , což je výchozí hodnota pro `Object` .

## <a name="calling-a-function"></a>Volání funkce

Proceduru zavoláte `Function` pomocí názvu procedury následovaný seznamem argumentů v závorkách ve výrazu. Závorky můžete vynechat pouze v případě, že neposkytujete žádné argumenty. Váš kód je však čitelnější, pokud vždy zahrnete závorky.

Proceduru zavoláte `Function` stejným způsobem jako u libovolné funkce knihovny `Sqrt` , jako je například, `Cos` nebo `ChrW` .

Funkci můžete také volat pomocí `Call` klíčového slova. V takovém případě se návratová hodnota ignoruje. `Call`Ve většině případů se použití klíčového slova nedoporučuje. Další informace naleznete v tématu [Call Statement](call-statement.md).

Visual Basic někdy mění uspořádání aritmetických výrazů a zvyšuje tak vnitřní efektivitu. Z tohoto důvodu byste neměli použít `Function` proceduru v aritmetickém výrazu, pokud funkce změní hodnotu proměnných ve stejném výrazu.

## <a name="async-functions"></a>Asynchronní funkce

*Asynchronní* funkce umožňuje vyvolat asynchronní funkce bez použití explicitního zpětného volání nebo ručního rozdělení kódu napříč více funkcemi nebo lambda výrazy.

Pokud označíte funkci s modifikátorem [Async](../modifiers/async.md) , můžete použít operátor [await](../operators/await-operator.md) ve funkci. Když ovládací prvek dosáhne `Await` výrazu ve `Async` funkci, ovládací prvek se vrátí volajícímu a průběh funkce je pozastaven, dokud se nedokončí očekávaný úkol. Po dokončení úlohy může provádění pokračovat ve funkci.

> [!NOTE]
> `Async`Procedura se vrátí volajícímu, když dojde k prvnímu očekávanému objektu, který ještě nebyl dokončen, nebo se dostane na konec `Async` procedury, podle toho, co nastane dříve.

`Async`Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task> . Příklad `Async` funkce, která má návratový typ, <xref:System.Threading.Tasks.Task%601> je uveden níže.

`Async`Funkce nemůže deklarovat žádné parametry [ByRef](../modifiers/byref.md) .

[Dílčí příkaz](sub-statement.md) lze také označit `Async` modifikátorem. Používá se hlavně pro obslužné rutiny událostí, kde nelze vracet hodnotu. `Async` `Sub` Procedura nemůže být očekávána a volající `Async` `Sub` procedury nemůže zachytit výjimky, které jsou vyvolány `Sub` procedurou.

Další informace o `Async` funkcích naleznete v tématu [asynchronní programování s Async a await](../../programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../programming-guide/concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../../programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>Funkce iterátoru

Funkce *iterátoru* provádí vlastní iteraci v kolekci, jako je například list nebo Array. Funkce iterátoru používá příkaz [yield](yield-statement.md) k vrácení jednotlivých prvků po jednom. Při dosažení příkazu [yield](yield-statement.md) se aktuální umístění v kódu pamatuje. Spuštění je restartováno z tohoto umístění při příštím volání funkce iterátoru.

Můžete zavolat iterátor z klientského kódu s použitím [pro každý... Další](for-each-next-statement.md) příkaz.

Návratový typ funkce iterátoru může být <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> .

Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).

## <a name="example"></a>Příklad

Následující příklad používá `Function` příkaz k deklaraci názvu, parametrů a kódu, který tvoří tělo `Function` procedury. `ParamArray`Modifikátor umožňuje funkci přijmout proměnlivý počet argumentů.

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>Příklad

Následující příklad vyvolá funkci deklarovanou v předchozím příkladu.

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>Příklad

V následujícím příkladu je, `DelayAsync` `Async` `Function` který má návratový typ <xref:System.Threading.Tasks.Task%601> . `DelayAsync`obsahuje `Return` příkaz, který vrací celé číslo. Proto deklarace funkce `DelayAsync` musí mít návratový typ `Task(Of Integer)` . Vzhledem k tomu, že návratový typ je `Task(Of Integer)` , vyhodnocení `Await` výrazu v `DoSomethingAsync` vytvoří celé číslo. To je znázorněno v tomto prohlášení: `Dim result As Integer = Await delayTask` .

`startButton_Click`Procedura je příkladem `Async Sub` procedury. Vzhledem k tomu `DoSomethingAsync` `Async` , že je funkce, úloha pro volání `DoSomethingAsync` musí být očekávána, jak ukazuje následující příkaz: `Await DoSomethingAsync()` . `startButton_Click` `Sub` Procedura musí být definována s `Async` modifikátorem, protože má `Await` výraz.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Viz také

- [Sub – příkaz](sub-statement.md)
- [Procedury funkcí](../../programming-guide/language-features/procedures/function-procedures.md)
- [Seznam parametrů](parameter-list.md)
- [Dim – příkaz](dim-statement.md)
- [Call – příkaz](call-statement.md)
- [Tohoto](of-clause.md)
- [Pole parametrů](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [Postupy: Použití obecné třídy](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Řešení potíží s procedurami](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Výrazy lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Výraz funkce](../operators/function-expression.md)
