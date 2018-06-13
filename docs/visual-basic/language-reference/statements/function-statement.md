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
ms.openlocfilehash: 908aa594ecbdd8ae2ec5a06de8181a1b16bb7e40
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234121"
---
# <a name="function-statement-visual-basic"></a>Function – příkaz (Visual Basic)
Deklaruje název, parametry a kód, který definovat `Function` postupu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Součásti  
  
-   `attributelist`  
  
     Volitelné. V tématu [seznam atributů](attribute-list.md).  
  
-   `accessmodifier`  
  
     Volitelné. Může být jedna z následujících akcí:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [Chráněné Friend](../../language-reference/modifiers/protected-friend.md)

    - [Privátní chráněný](../../language-reference/modifiers/private-protected.md)  
  
     V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Volitelné. Může být jedna z následujících akcí:  
  
    -   [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Volitelné. V tématu [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Volitelné. V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Async`  
  
     Volitelné. V tématu [asynchronní](../../../visual-basic/language-reference/modifiers/async.md).  
  
-   `Iterator`  
  
     Volitelné. V tématu [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Požadováno. Název procedury. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `typeparamlist`  
  
     Volitelné. Seznam parametrů typu pro obecný postup. V tématu [zadejte seznam](type-list.md).  
  
-   `parameterlist`  
  
     Volitelné. Seznam místní názvy proměnných představující parametry tohoto postupu. V tématu [seznam parametrů](parameter-list.md).  
  
-   `returntype`  
  
     Požadováno pokud `Option Strict` je `On`. Datový typ hodnoty vrácené tímto postupem.  
  
-   `Implements`  
  
     Volitelné. Označuje, že tento postup implementuje jeden nebo více `Function` postupy, každé z nich definované v rozhraní implementované obsahující třídu nebo strukturu tento postup. V tématu [implementuje příkaz](implements-statement.md).  
  
-   `implementslist`  
  
     Požadováno pokud `Implements` pochází. Seznam `Function` postupy se implementuje.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Každý `implementedprocedure` má následující syntaxe a částí:  
  
     `interface.definedname`  
  
    |Část|Popis|  
    |---|---|  
    |`interface`|Požadováno. Název rozhraní implementované tento postup obsahující třídu nebo strukturu.|  
    |`definedname`|Požadováno. Název, podle kterého postupu je definována v `interface`.|  
  
-   `Handles`  
  
     Volitelné. Označuje, že tento postup může zpracovat jeden nebo více konkrétní události. V tématu [zpracovává](handles-clause.md).  
  
-   `eventlist`  
  
     Požadováno pokud `Handles` pochází. Seznam událostí, který zpracovává tento postup.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Každý `eventspecifier` má následující syntaxe a částí:  
  
     `eventvariable.event`  
  
    |Část|Popis|  
    |---|---|  
    |`eventvariable`|Požadováno. Objektová proměnná deklarovat s datový typ třídu nebo strukturu, která vyvolává událost.|  
    |`event`|Požadováno. Název události, který zpracovává tento postup.|  
  
-   `statements`  
  
     Volitelné. Blok příkazů k provedení v rámci tohoto postupu.  
  
-   `End Function`  
  
     Ukončí definici tohoto postupu.  
  
## <a name="remarks"></a>Poznámky  
 Všechny spustitelný kód musí být uvnitř procedury. Každý postup je pak deklarované v rámci třídy, struktury nebo modul, který se označuje jako obsahující třídy, struktury nebo modul.  
  
 Chcete-li vrátit hodnotu volání kódu, použijte `Function` postupu; jinak použijte `Sub` postup.  
  
## <a name="defining-a-function"></a>Definování funkcí  
 Můžete definovat `Function` postup jenom na úrovni modulu. Kontext deklarace pro funkci proto musí být třídy, struktury, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedury nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](declaration-contexts-and-default-access-levels.md).  
  
 `Function` Výchozí nastavení postupy veřejný přístup. Můžete nastavit jejich úrovně přístupu s modifikátory přístupu.  
  
 A `Function` postupu můžou deklarovat datový typ hodnoty, která vrátí postupu. Můžete zadat jakýkoli datový typ nebo název výčet, struktury, třídu nebo rozhraní. Pokud nezadáte `returntype` vrátí parametr postupu `Object`.  
  
 Pokud tento postup používá `Implements` – klíčové slovo, obsahující třídu nebo strukturu musí také mít `Implements` příkaz, který následuje jeho `Class` nebo `Structure` příkaz. `Implements` Příkaz musí zahrnovat každé rozhraní, který je uveden v `implementslist`. Ale název, podle kterého rozhraní definuje `Function` (v `definedname`) nemusí odpovídat názvu tohoto postupu (v `name`).  
  
> [!NOTE]
>  Lambda – výrazy můžete použít k definování vložené výrazy funkce. Další informace najdete v tématu [výraz funkce](../../../visual-basic/language-reference/operators/function-expression.md) a [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="returning-from-a-function"></a>Vrácení z funkce  
 Když `Function` postup vrátí kód volání, pokračuje provádění příkaz, který následuje příkaz, který volá postup.  
  
 Vrácení hodnoty z funkce, můžete přiřadit hodnotu název funkce nebo ji v zahrnout `Return` příkaz.  
  
 `Return` Příkaz současně přiřadí návratovou hodnotu a ukončí funkce, jako ukazuje následující příklad.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 Následující příklad přiřadí návratovou hodnotu pro název funkce `myFunction` a použije je `Exit Function` příkaz, který má vrátit.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 `Exit Function` a `Return` příkazy způsobit okamžitou výstupu z `Function` postupu. Libovolný počet `Exit Function` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Function` a `Return` příkazy.  
  
 Pokud používáte `Exit Function` bez přiřazení hodnoty k `name`, vrátí výchozí hodnota pro datový typ, který je uveden v postupu `returntype`. Pokud `returntype` není zadán, vrátí postup `Nothing`, což je výchozí hodnota pro `Object`.  
  
## <a name="calling-a-function"></a>Volání funkce  
 Volání `Function` postup pomocí název postupu, za nímž následuje seznam argumentů v závorkách ve výrazu. Závorky můžete vynechat, pouze v případě, že nejsou zadávání žádné argumenty. Váš kód je však lépe čitelný, pokud vždy zahrnovat závorkách.  
  
 Volání `Function` postup volat žádnou knihovnu stejným způsobem jako funkce, jako `Sqrt`, `Cos`, nebo `ChrW`.  
  
 Můžete také zavolat funkci pomocí `Call` – klíčové slovo. V takovém případě se ignoruje návratovou hodnotu. Použití `Call` ve většině případů se nedoporučuje – klíčové slovo. Další informace najdete v tématu [volání příkazu](call-statement.md).  
  
 Visual Basic někdy Přeuspořádá aritmetických výrazech ke zvýšení efektivity interní. Z tohoto důvodu byste neměli používat `Function` postup ve výrazu aritmetické při změně hodnot proměnných ve stejném výrazu funkce.  
  
## <a name="async-functions"></a>Asynchronní funkce  
 *Asynchronní* funkce umožňuje vyvolání asynchronní funkce bez použití explicitní zpětná volání nebo Ruční rozdělení kódu napříč více funkcí nebo výrazy lambda.  
  
 Pokud označíte funkce s [asynchronní](../../../visual-basic/language-reference/modifiers/async.md) modifikátor, můžete použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor ve funkci. Při řízení dosáhnou `Await` výrazu v `Async` funkce, vrátí ovládací prvek volajícímu a průběh ve funkci je pozastaveno, dokud dokončení awaited úlohy. Po dokončení úlohy můžete pokračovat v provádění ve funkci.  
  
> [!NOTE]
>  `Async` Postup vrátí volajícímu při buď zjistí první awaited objekt, který ještě není dokončena nebo získá na konec `Async` postup, cokoliv nastane dříve.  
  
 `Async` Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>. Příklad `Async` funkce, která má návratový typ <xref:System.Threading.Tasks.Task%601> najdete níže.  
  
 `Async` Funkce nelze deklarovat všechny [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametry.  
  
 A [Sub – příkaz](sub-statement.md) může také být označen `Async` modifikátor. Především používá se pro obslužné rutiny událostí, kde nejde vrátit hodnotu. `Async``Sub` Procedury nelze očekáváno a volající `Async``Sub` procedury nelze catch výjimky, které jsou vyvolány `Sub` postupu.  
  
 Další informace o `Async` funkce, najdete v části [asynchronní programování s Async a Await](../../../visual-basic/programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), a [asynchronní vrátit typy](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>Iterator funkce  
 *Iterator* funkce provede vlastní iterace nad kolekcí, jako je například seznam nebo pole. Iterator funkce používá [Yield](yield-statement.md) příkaz vrátit každý element, jeden v čase. Když [Yield](yield-statement.md) příkaz je dosaženo, uloží je aktuální umístění v kódu. Provádění restartování z tohoto umístění při příštím iterator funkce je volána.  
  
 Volání iterovat z kódu klienta pomocí [For Each... Další](for-each-next-statement.md) příkaz.  
  
 Návratový typ funkce iterator může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Function` příkaz deklarovat název, parametry a kód, který vytvoří text `Function` postupu. `ParamArray` Modifikátor umožňuje funkci tak, aby přijímal proměnný počet argumentů.  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad popisuje vyvolání funkce deklarované v předchozím příkladu.  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `DelayAsync` je `Async``Function` s návratovým typem <xref:System.Threading.Tasks.Task%601>. `DelayAsync` má `Return` příkaz, který vrátí celé číslo. Proto funkce deklaraci `DelayAsync` musí mít návratový typ `Task(Of Integer)`. Vzhledem k tomu, že je návratový typ `Task(Of Integer)`, vyhodnocení `Await` výrazu v `DoSomethingAsync` vytváří celé číslo. Tento postup je znázorněn v tomto prohlášení: `Dim result As Integer = Await delayTask`.  
  
 `startButton_Click` Postup je příklad `Async Sub` postupu. Protože `DoSomethingAsync` je `Async` funkce, úlohy pro volání `DoSomethingAsync` musí být očekáváno, jak ukazuje následující příkaz: `Await DoSomethingAsync()`. `startButton_Click``Sub` Postupu musí být definovány se `Async` modifikátor vzhledem k tomu, že má `Await` výrazu.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Sub](sub-statement.md)  
 [Procedury funkce](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [Seznam parametrů](parameter-list.md)  
 [Příkaz Dim](dim-statement.md)  
 [Příkaz Call](call-statement.md)  
 [z](of-clause.md)  
 [Pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Řešení potíží s procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Výraz Function](../../../visual-basic/language-reference/operators/function-expression.md)
