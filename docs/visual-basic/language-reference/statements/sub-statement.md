---
title: Sub – příkaz (Visual Basic)
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
ms.openlocfilehash: 7baa4e25bc876ebfbe03c316b2020e01aedbc88d
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924492"
---
# <a name="sub-statement-visual-basic"></a>Sub – příkaz (Visual Basic)
Deklaruje název, parametry a kód, které definují `Sub` postup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Součásti  
  
-   `attributelist`  
  
     Volitelné. Zobrazit [seznam atributů](attribute-list.md).  
  
-   `Partial`  
  
     Volitelné. Určuje definici dílčí metody. Zobrazit [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).  
  
-   `accessmodifier`  
  
     Volitelné. Může být jedna z následujících akcí:  
  
    -   [Public](../modifiers/public.md)  
  
    -   [Protected](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Private](../modifiers/private.md)  
  
    - [Chráněné typu Friend](../../language-reference/modifiers/protected-friend.md)

    - [Privátní, chráněné](../../language-reference/modifiers/private-protected.md)
  
     Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Volitelné. Může být jedna z následujících akcí:  
  
    -   [Overloads](../modifiers/overloads.md)  
  
    -   [Overrides](../modifiers/overrides.md)  
  
    -   [Overridable](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Volitelné. Zobrazit [sdílené](../modifiers/shared.md).  
  
-   `Shadows`  
  
     Volitelné. Zobrazit [stíny](../modifiers/shadows.md).  
  
-   `Async`  
  
     Volitelné. Zobrazit [asynchronní](../modifiers/async.md).  
  
-   `name`  
  
     Požadováno. Název procedury. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Chcete-li vytvořit proceduru konstruktor pro třídu, nastavte název `Sub` postup `New` – klíčové slovo. Další informace najdete v tématu [doba života objektu: jak objekty jsou vytvořená a Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
-   `typeparamlist`  
  
     Volitelné. Seznam parametrů typu pro obecný postup. Zobrazit [seznamu](type-list.md).  
  
-   `parameterlist`  
  
     Volitelné. Seznam místní názvy proměnných představující parametry tohoto postupu. Zobrazit [seznam parametrů](parameter-list.md).  
  
-   `Implements`  
  
     Volitelné. Označuje, že tento postup implementuje jednu nebo více `Sub` postupy, každý z nich definované v rozhraní implementované obsahující třídu nebo strukturu, tento postup. Zobrazit [implementuje příkaz](implements-statement.md).  
  
-   `implementslist`  
  
     Požadováno pokud `Implements` pochází. Seznam `Sub` postupy se implementuje.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Každý `implementedprocedure` má následující syntaxi a části:  
  
     `interface.definedname`  
  
    |Část|Popis|  
    |---|---|  
    |`interface`|Požadováno. Název rozhraní implementovaných tímto postupem obsahující třídy nebo struktury.|  
    |`definedname`|Požadováno. Název, podle kterého postupu je definován v `interface`.|  
  
-   `Handles`  
  
     Volitelné. Označuje, že tento postup může zpracovat jeden nebo více konkrétních událostí. Zobrazit [zpracovává](handles-clause.md).  
  
-   `eventlist`  
  
     Požadováno pokud `Handles` pochází. Seznam událostí, který zpracovává tento postup.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Každý `eventspecifier` má následující syntaxi a části:  
  
     `eventvariable.event`  
  
    |Část|Popis|  
    |---|---|  
    |`eventvariable`|Požadováno. Objektová proměnná deklarovaná s datovým typem třídy nebo struktury, která vyvolává událost.|  
    |`event`|Požadováno. Název události, které zpracovává tento postup.|  
  
-   `statements`  
  
     Volitelné. Blok příkazů ke spuštění v rámci tohoto postupu.  
  
-   `End Sub`  
  
     Ukončí definici tohoto postupu.  
  
## <a name="remarks"></a>Poznámky  
 Všechny spustitelný kód musí být uvnitř procedury. Použití `Sub` procedury při nechcete vracet hodnotu volajícímu kódu. Použití `Function` postup, pokud chcete vracet hodnotu.  
  
## <a name="defining-a-sub-procedure"></a>Definuje proceduru Sub  
 Můžete definovat `Sub` postup pouze na úrovni modulu. Kontext deklarace pro proceduru sub, proto musí třída, struktura, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedura nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](declaration-contexts-and-default-access-levels.md).  
  
 `Sub` postupy výchozí veřejný přístup. Můžete nastavit jejich úrovně přístupu pomocí přístupu modifikátory přístupu.  
  
 Pokud postup používá `Implements` – klíčové slovo, obsahuje třídu nebo strukturu, musíte mít `Implements` příkaz, který bezprostředně následuje po jeho `Class` nebo `Structure` příkazu. `Implements` Příkazu musí obsahovat každé rozhraní, které je zadáno v `implementslist`. Ale název, pomocí kterého rozhraní definuje `Sub` (v `definedname`) nemusí odpovídat názvu tohoto postupu (v `name`).  
  
## <a name="returning-from-a-sub-procedure"></a>Návrat z proceduru Sub  
 Když `Sub` postup vrátí volajícímu kódu, provádění pokračuje s příkazu následujícímu po prohlášení, která ji zavolala.  
  
 Následující příklad ukazuje návrat z `Sub` postup.  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 `Exit Sub` a `Return` příkazy způsobit okamžité ukončení `Sub` postup. Libovolný počet `Exit Sub` a `Return` příkazů může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Sub` a `Return` příkazy.  
  
## <a name="calling-a-sub-procedure"></a>Volání procedury Sub  
 Volání `Sub` postup pomocí název procedury v příkazu a budete postupovat tímto názvem s jeho seznamem argumentů v závorkách. Závorky lze vynechat pouze tehdy, pokud nezadáte žádné argumenty. Váš kód je však čitelnější, pokud vždy závorek.  
  
 A `Sub` postup a `Function` procedury mohou mít parametry a provádět řadu příkazů. Ale `Function` postup vrátí hodnotu a s `Sub` není procedura. Proto je nelze použít `Sub` postup ve výrazu.  
  
 Můžete použít `Call` – klíčové slovo při volání `Sub` postup, ale toto klíčové slovo se nedoporučuje pro většinu použití. Další informace najdete v tématu [zavolat příkaz](call-statement.md).  
  
 Visual Basic někdy znovu uspořádá aritmetických výrazů ke zvýšení účinnosti interní. Z tohoto důvodu Pokud váš seznam argumentů obsahuje výrazy, které vyžadují další postupy budete by neměl předpokládat, že tyto výrazy se nazývají v určitém pořadí.  
  
## <a name="async-sub-procedures"></a>Async Sub – procedury  
 Při použití asynchronní funkce, se dají vyvolat asynchronní funkce bez použití explicitní zpětná volání nebo Ruční rozdělení kódu mezi více funkcí nebo výrazů lambda.  
  
 Pokud označíte procedura se [asynchronní](../modifiers/async.md) modifikátor, můžete použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor v postupu. Když ovládací prvek dosáhne `Await` výrazu v `Async` postupu ovládací prvek vrátí volajícímu a průběh v postupu je pozastaveno, dokud očekávaná úloha dokončí. Po dokončení úlohy se provádění může pokračovat v postupu.  
  
> [!NOTE]
>  `Async` Postup vrátí volajícímu vyskytne buď první očekávaný objekt, který ještě není dokončeno nebo konec `Async` postup je dosaženo, podle toho, co nastane dříve.  
  
 Můžete také označit [Function – příkaz](function-statement.md) s `Async` modifikátor. `Async` Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>. Příklad dále v tomto tématu si ukážeme `Async` funkci, která má návratový typ <xref:System.Threading.Tasks.Task%601>.  
  
 `Async` `Sub` postupy jsou primárně určené pro obslužné rutiny událostí, ve kterém nejde vrátit hodnotu. `Async` `Sub` Nemůže být očekávána proceduru a volající `Async` `Sub` postup zaznamenat tak výjimky, která `Sub` postup vyvolá.  
  
 `Async` Procedura nemůže deklarovat všechny [ByRef](../modifiers/byref.md) parametry.  
  
 Další informace o `Async` postupy, najdete v článku [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [tok řízení v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), a [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Sub` příkazu zadat název, parametry a kód, který tvoří text `Sub` postup.  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `DelayAsync` je `Async` `Function` , která má návratový typ <xref:System.Threading.Tasks.Task%601>. `DelayAsync` má `Return` příkaz, který vrátí celé číslo. Proto se funkce deklarace `DelayAsync` musí mít typ vrácené hodnoty `Task(Of Integer)`. Vzhledem k tomu, že je návratový typ `Task(Of Integer)`, vyhodnocení `Await` výrazu v `DoSomethingAsync` vytváří celé číslo, jak ukazuje následující příkaz: `Dim result As Integer = Await delayTask`.  
  
 `startButton_Click` Postup je příkladem `Async Sub` postup. Protože `DoSomethingAsync` je `Async` funkce, úkol pro volání `DoSomethingAsync` musí ní použít operátor await, jak ukazuje následující příkaz: `Await DoSomethingAsync()`. `startButton_Click` `Sub` Postupu musí být definované s `Async` modifikátor vzhledem k tomu, že má `Await` výrazu.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Implements](implements-statement.md)  
 [Příkaz Function](function-statement.md)  
 [Seznam parametrů](parameter-list.md)  
 [Příkaz Dim](dim-statement.md)  
 [Příkaz Call](call-statement.md)  
 [z](of-clause.md)  
 [Pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Řešení potíží s procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
