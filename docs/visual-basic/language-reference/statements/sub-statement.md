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
ms.openlocfilehash: da498a5e0a3633eb98882aaed145fcd21ab169fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346443"
---
# <a name="sub-statement-visual-basic"></a>Sub – příkaz (Visual Basic)

Deklaruje název, parametry a kód, které definují proceduru `Sub`.

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

  Volitelná. Viz [seznam atributů](attribute-list.md).

- `Partial`

  Volitelná. Označuje definici částečné metody. Viz [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).

- `accessmodifier`

  Volitelná. Může být jedna z následujících akcí:

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Volitelná. Může být jedna z následujících akcí:

  - [Overloads](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Volitelná. Viz [Shared](../modifiers/shared.md).

- `Shadows`

  Volitelná. Viz [Shadows](../modifiers/shadows.md).

- `Async`

  Volitelná. Viz [Async](../modifiers/async.md).

- `name`

  Požadováno. Název procedury. Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Chcete-li vytvořit proceduru konstruktoru pro třídu, nastavte název `Sub` procedury na klíčové slovo `New`. Další informace naleznete v tématu [Doba života objektu: vytváření a zničení objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

- `typeparamlist`

  Volitelná. Seznam parametrů typu pro obecný postup Viz [seznam typů](type-list.md).

- `parameterlist`

  Volitelná. Seznam názvů místních proměnných, které představují parametry tohoto postupu. Viz [seznam parametrů](parameter-list.md).

- `Implements`

  Volitelná. Označuje, že tento postup implementuje jeden nebo více `Sub` procedur, každý z nich definovaný v rozhraní implementovaném touto procedurou obsahuje třídu nebo strukturu. Viz [příkaz Implements](implements-statement.md).

- `implementslist`

  Vyžaduje se, pokud je dodána `Implements`. Seznam `Sub`ch procedur, které jsou implementovány.

  `implementedprocedure [ , implementedprocedure ... ]`

  Každý `implementedprocedure` má následující syntaxi a části:

  `interface.definedname`

  |Částí|Popis|
  |---|---|
  |`interface`|Požadováno. Název rozhraní implementovaného touto procedurou obsahuje třídu nebo strukturu.|
  |`definedname`|Požadováno. Název, podle kterého je procedura definovaná v `interface`.|

- `Handles`

  Volitelná. Označuje, že tento postup může zpracovávat jednu nebo více konkrétních událostí. Viz [Handles](handles-clause.md).

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

  Volitelná. Blok příkazů, které mají být spuštěny v rámci tohoto postupu.

- `End Sub`

  Ukončí definici tohoto postupu.

## <a name="remarks"></a>Poznámky

Veškerý spustitelný kód musí být v rámci procedury. Pokud nechcete vracet hodnotu volajícímu kódu, použijte `Sub` proceduru. Pokud chcete vrátit hodnotu, použijte `Function` proceduru.

## <a name="defining-a-sub-procedure"></a>Definování procedury Sub

Můžete definovat `Sub` proceduru pouze na úrovni modulu. Kontext deklarace pro proceduru Sub musí tedy být třída, struktura, modul nebo rozhraní a nemůže se jednat o zdrojový soubor, obor názvů, proceduru nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

výchozími postupy `Sub` jsou veřejné přístupy. Úrovně přístupu můžete upravit pomocí modifikátorů přístupu.

Pokud procedura používá klíčové slovo `Implements`, obsahující třídu nebo strukturu musí mít příkaz `Implements`, který následuje bezprostředně za `Class` nebo `Structure` příkaz. Příkaz `Implements` musí zahrnovat každé rozhraní, které je určeno v `implementslist`. Název, kterým rozhraní definuje `Sub` (v `definedname`), ale nemusí odpovídat názvu tohoto postupu (v `name`).

## <a name="returning-from-a-sub-procedure"></a>Vrácení z procedury Sub

Když se `Sub` procedura vrátí k volajícímu kódu, provádění pokračuje příkazem po příkazu, který ho volal.

Následující příklad ukazuje návrat z `Sub` proceduře.

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

Příkazy `Exit Sub` a `Return` způsobují bezprostřední ukončení `Sub`ho postupu. Libovolný počet `Exit Sub` a `Return` příkazů se může objevit kdekoli v proceduře a můžete kombinovat `Exit Sub` a `Return` příkazy.

## <a name="calling-a-sub-procedure"></a>Volání procedury Sub

Proceduru `Sub` zavoláte pomocí názvu procedury v příkazu a potom následujícím názvem se seznamem argumentů v závorkách. Závorky můžete vynechat pouze v případě, že nezadáte žádné argumenty. Váš kód je však čitelnější, pokud vždy zahrnete závorky.

Procedura `Sub` a procedura `Function` mohou mít parametry a provádět sérii příkazů. Nicméně procedura `Function` vrátí hodnotu a `Sub` procedura ne. Proto nemůžete ve výrazu použít `Sub` proceduru.

Klíčové slovo `Call` můžete použít při volání `Sub` procedury, ale toto klíčové slovo se pro většinu použití nedoporučuje. Další informace naleznete v tématu [Call Statement](call-statement.md).

Visual Basic někdy mění uspořádání aritmetických výrazů a zvyšuje tak vnitřní efektivitu. Z tohoto důvodu, pokud seznam argumentů obsahuje výrazy, které volají jiné procedury, neměli byste předpokládat, že tyto výrazy budou volány v určitém pořadí.

## <a name="async-sub-procedures"></a>Asynchronní procedury Sub

Pomocí asynchronní funkce můžete vyvolat asynchronní funkce bez použití explicitního zpětného volání nebo ruční rozdělení kódu napříč více funkcemi nebo lambda výrazy.

Pokud označíte proceduru modifikátorem [Async](../modifiers/async.md) , můžete použít operátor [await](../../../visual-basic/language-reference/operators/await-operator.md) v proceduře. Když ovládací prvek dosáhne `Await` výraz v proceduře `Async`, ovládací prvek se vrátí volajícímu a průběh procedury je pozastaven, dokud se nedokončí očekávaný úkol. Po dokončení úlohy může provádění pokračovat postupem.

> [!NOTE]
> `Async` procedura se vrátí volajícímu, když buď dojde k prvnímu očekávanému objektu, který ještě nebyl dokončen, nebo je dosaženo konce `Async` postupu, podle toho, co nastane dříve.

Můžete také označit [příkaz funkce](function-statement.md) pomocí modifikátoru `Async`. `Async` funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>. Příklad dále v tomto tématu ukazuje funkci `Async`, která má návratový typ <xref:System.Threading.Tasks.Task%601>.

procedury `Async` `Sub` jsou primárně používány pro obslužné rutiny událostí, kde nelze vrátit hodnotu. Procedura `Async` `Sub` nemůže být očekávána a volající procedury `Async` `Sub` nemůže zachytit výjimky, které vyvolá procedura `Sub`.

Procedura `Async` nemůže deklarovat žádné parametry [ByRef](../modifiers/byref.md) .

Další informace o `Async` postupy naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../../visual-basic/programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Příklad

Následující příklad používá příkaz `Sub` k definování názvu, parametrů a kódu, který tvoří tělo `Sub`ho postupu.

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>Příklad

V následujícím příkladu je `DelayAsync` `Async` `Function`, který má návratový typ <xref:System.Threading.Tasks.Task%601>. `DelayAsync` má příkaz `Return`, který vrací celé číslo. Proto deklarace funkce `DelayAsync` musí mít návratový typ `Task(Of Integer)`. Vzhledem k tomu, že návratový typ je `Task(Of Integer)`, vyhodnocení výrazu `Await` v `DoSomethingAsync` vytvoří celé číslo, jak ukazuje následující příkaz: `Dim result As Integer = Await delayTask`.

Procedura `startButton_Click` je příkladem `Async Sub` postupu. Vzhledem k tomu, že `DoSomethingAsync` je `Async` funkce, musí být úkol pro volání `DoSomethingAsync` očekáván, jak ukazuje následující příkaz: `Await DoSomethingAsync()`. Procedura `startButton_Click` `Sub` musí být definována s modifikátorem `Async`, protože obsahuje výraz `Await`.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Viz také:

- [Příkaz Implements](implements-statement.md)
- [Příkaz Function](function-statement.md)
- [Seznam parametrů](parameter-list.md)
- [Příkaz Dim](dim-statement.md)
- [Příkaz Call](call-statement.md)
- [Tohoto](of-clause.md)
- [Pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Řešení potíží s procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
