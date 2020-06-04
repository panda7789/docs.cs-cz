---
title: Sub – příkaz
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: e50b79c31c92ac116d6c82bcececba3340894d74
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404171"
---
# <a name="sub-statement-visual-basic"></a>Sub – příkaz (Visual Basic)

Deklaruje název, parametry a kód, které definují `Sub` proceduru.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a>Součásti

- `attributelist`

  Nepovinný parametr. Viz [seznam atributů](attribute-list.md).

- `Partial`

  Nepovinný parametr. Označuje definici částečné metody. Viz [částečné metody](../../programming-guide/language-features/procedures/partial-methods.md).

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

- `name`

  Povinná hodnota. Název procedury. Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md). Chcete-li vytvořit proceduru konstruktoru pro třídu, nastavte název `Sub` procedury na `New` klíčové slovo. Další informace naleznete v tématu [Doba života objektu: vytváření a zničení objektů](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

- `typeparamlist`

  Nepovinný parametr. Seznam parametrů typu pro obecný postup Viz [seznam typů](type-list.md).

- `parameterlist`

  Nepovinný parametr. Seznam názvů místních proměnných, které představují parametry tohoto postupu. Viz [seznam parametrů](parameter-list.md).

- `Implements`

  Nepovinný parametr. Označuje, že tento postup implementuje jeden nebo více `Sub` postupů, každý z nich definovaný v rozhraní implementovaném touto procedurou obsahuje třídu nebo strukturu. Viz [příkaz Implements](implements-statement.md).

- `implementslist`

  Vyžaduje `Implements` se, pokud je zadaný. Seznam `Sub` implementovaných procedur.

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

  Nepovinný parametr. Blok příkazů, které mají být spuštěny v rámci tohoto postupu.

- `End Sub`

  Ukončí definici tohoto postupu.

## <a name="remarks"></a>Poznámky

Veškerý spustitelný kód musí být v rámci procedury. Použijte `Sub` proceduru, pokud nechcete vracet hodnotu volajícímu kódu. Použijte `Function` proceduru, pokud chcete vrátit hodnotu.

## <a name="defining-a-sub-procedure"></a>Definování procedury Sub

Můžete definovat `Sub` proceduru pouze na úrovni modulu. Kontext deklarace pro proceduru Sub musí tedy být třída, struktura, modul nebo rozhraní a nemůže se jednat o zdrojový soubor, obor názvů, proceduru nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

`Sub`postupy jsou výchozí pro veřejný přístup. Úrovně přístupu můžete upravit pomocí modifikátorů přístupu.

Pokud procedura používá `Implements` klíčové slovo, obsahující třídu nebo strukturu musí mít `Implements` příkaz, který následuje hned za `Class` `Structure` příkazem or. `Implements`Příkaz musí zahrnovat každé rozhraní, které je určeno v `implementslist` . Název, pomocí kterého rozhraní definuje `Sub` (in), ale `definedname` nemusí odpovídat názvu této procedury (v `name` ).

## <a name="returning-from-a-sub-procedure"></a>Vrácení z procedury Sub

Když se `Sub` procedura vrátí k volajícímu kódu, provádění pokračuje příkazem po příkazu, který ho volal.

Následující příklad ukazuje návrat z `Sub` procedury.

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

`Exit Sub`Příkazy a `Return` způsobují bezprostřední ukončení `Sub` procedury. Libovolný počet `Exit Sub` příkazů a `Return` se může objevit kdekoli v proceduře a můžete kombinovat `Exit Sub` a `Return` příkazy.

## <a name="calling-a-sub-procedure"></a>Volání procedury Sub

Proceduru zavoláte `Sub` pomocí názvu procedury v příkazu a potom následujícím názvem se seznamem argumentů v závorkách. Závorky můžete vynechat pouze v případě, že nezadáte žádné argumenty. Váš kód je však čitelnější, pokud vždy zahrnete závorky.

`Sub`Procedura a `Function` procedura mohou mít parametry a provádět sérii příkazů. `Function`Procedura však vrátí hodnotu a `Sub` procedura nikoli. Proto nemůžete `Sub` ve výrazu použít proceduru.

Klíčové slovo lze použít `Call` při volání `Sub` procedury, ale toto klíčové slovo se pro většinu použití nedoporučuje. Další informace naleznete v tématu [Call Statement](call-statement.md).

Visual Basic někdy mění uspořádání aritmetických výrazů a zvyšuje tak vnitřní efektivitu. Z tohoto důvodu, pokud seznam argumentů obsahuje výrazy, které volají jiné procedury, neměli byste předpokládat, že tyto výrazy budou volány v určitém pořadí.

## <a name="async-sub-procedures"></a>Asynchronní procedury Sub

Pomocí asynchronní funkce můžete vyvolat asynchronní funkce bez použití explicitního zpětného volání nebo ruční rozdělení kódu napříč více funkcemi nebo lambda výrazy.

Pokud označíte proceduru modifikátorem [Async](../modifiers/async.md) , můžete použít operátor [await](../operators/await-operator.md) v proceduře. Když ovládací prvek dosáhne `Await` výrazu v `Async` proceduře, ovládací prvek se vrátí volajícímu a průběh procedury je pozastaven, dokud se nedokončí očekávaný úkol. Po dokončení úlohy může provádění pokračovat postupem.

> [!NOTE]
> `Async`Procedura se vrátí volajícímu, když buď dojde k prvnímu očekávanému objektu, který ještě nebyl dokončen `Async` , nebo je dosaženo konce procedury, podle toho, co nastane dříve.

[Příkaz funkce](function-statement.md) můžete také označit `Async` modifikátorem. `Async`Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task> . Příklad dále v tomto tématu ukazuje `Async` funkci, která má návratový typ <xref:System.Threading.Tasks.Task%601> .

`Async``Sub`procedury jsou primárně používány pro obslužné rutiny událostí, kde nelze vrátit hodnotu. `Async` `Sub` Procedura nemůže být očekávána a volající `Async` `Sub` procedury nemůže zachytit výjimky, které `Sub` procedura vyvolá.

`Async`Procedura nemůže deklarovat žádné parametry [ByRef](../modifiers/byref.md) .

Další informace o `Async` procedurách naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../programming-guide/concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../../programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Příklad

Následující příklad používá `Sub` příkaz k definování názvu, parametrů a kódu, který tvoří tělo `Sub` procedury.

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>Příklad

V následujícím příkladu je, `DelayAsync` `Async` `Function` který má návratový typ <xref:System.Threading.Tasks.Task%601> . `DelayAsync`obsahuje `Return` příkaz, který vrací celé číslo. Proto deklarace funkce `DelayAsync` musí mít návratový typ `Task(Of Integer)` . Vzhledem k tomu, že návratový typ je `Task(Of Integer)` , vyhodnocení `Await` výrazu v `DoSomethingAsync` vytvoří celé číslo, jak ukazuje následující příkaz: `Dim result As Integer = Await delayTask` .

`startButton_Click`Procedura je příkladem `Async Sub` procedury. Vzhledem k tomu `DoSomethingAsync` `Async` , že je funkce, úloha pro volání `DoSomethingAsync` musí být očekávána, jak ukazuje následující příkaz: `Await DoSomethingAsync()` . `startButton_Click` `Sub` Procedura musí být definována s `Async` modifikátorem, protože má `Await` výraz.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Viz také

- [Implements – Příkaz](implements-statement.md)
- [Function – příkaz](function-statement.md)
- [Seznam parametrů](parameter-list.md)
- [Dim – příkaz](dim-statement.md)
- [Call – příkaz](call-statement.md)
- [Tohoto](of-clause.md)
- [Pole parametrů](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [Postupy: Použití obecné třídy](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Řešení potíží s procedurami](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Částečné metody](../../programming-guide/language-features/procedures/partial-methods.md)
