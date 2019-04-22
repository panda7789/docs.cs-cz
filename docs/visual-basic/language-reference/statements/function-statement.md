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
ms.openlocfilehash: dffe67d1c31b0fe7c037839ba0588793a461f276
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818459"
---
# <a name="function-statement-visual-basic"></a>Function – příkaz (Visual Basic)
Deklaruje název, parametry a kód, které definují `Function` postup.  
  
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
  
     Volitelné. Zobrazit [seznam atributů](attribute-list.md).  
  
-   `accessmodifier`  
  
     Volitelné. Může být jedna z následujících akcí:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [Protected Friend](../../language-reference/modifiers/protected-friend.md)

    - [Private Protected](../../language-reference/modifiers/private-protected.md)  
  
     Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
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
  
     Volitelné. Zobrazit [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Volitelné. Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Async`  
  
     Volitelné. Zobrazit [asynchronní](../../../visual-basic/language-reference/modifiers/async.md).  
  
-   `Iterator`  
  
     Volitelné. Zobrazit [iterátoru](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Povinný parametr. Název procedury. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `typeparamlist`  
  
     Volitelné. Seznam parametrů typu pro obecný postup. Zobrazit [seznamu](type-list.md).  
  
-   `parameterlist`  
  
     Volitelné. Seznam místní názvy proměnných představující parametry tohoto postupu. Zobrazit [seznam parametrů](parameter-list.md).  
  
-   `returntype`  
  
     Požadováno pokud `Option Strict` je `On`. Datový typ hodnoty vrácené tímto postupem.  
  
-   `Implements`  
  
     Volitelné. Označuje, že tento postup implementuje jednu nebo více `Function` postupy, každý z nich definované v rozhraní implementované obsahující třídu nebo strukturu, tento postup. Zobrazit [implementuje příkaz](implements-statement.md).  
  
-   `implementslist`  
  
     Požadováno pokud `Implements` pochází. Seznam `Function` postupy se implementuje.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Každý `implementedprocedure` má následující syntaxi a části:  
  
     `interface.definedname`  
  
    |Část|Popis|  
    |---|---|  
    |`interface`|Povinný parametr. Název rozhraní implementovaných tímto postupem obsahující třídy nebo struktury.|  
    |`definedname`|Povinný parametr. Název, podle kterého postupu je definován v `interface`.|  
  
-   `Handles`  
  
     Volitelné. Označuje, že tento postup může zpracovat jeden nebo více konkrétních událostí. Zobrazit [zpracovává](handles-clause.md).  
  
-   `eventlist`  
  
     Požadováno pokud `Handles` pochází. Seznam událostí, který zpracovává tento postup.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Každý `eventspecifier` má následující syntaxi a části:  
  
     `eventvariable.event`  
  
    |Část|Popis|  
    |---|---|  
    |`eventvariable`|Povinný parametr. Objektová proměnná deklarovaná s datovým typem třídy nebo struktury, která vyvolává událost.|  
    |`event`|Povinný parametr. Název události, které zpracovává tento postup.|  
  
-   `statements`  
  
     Volitelné. Blok příkazů má být spuštěn v rámci tohoto postupu.  
  
-   `End Function`  
  
     Ukončí definici tohoto postupu.  
  
## <a name="remarks"></a>Poznámky  
 Všechny spustitelný kód musí být uvnitř procedury. Každá procedura, pak je deklarována v rámci třídy, struktury nebo modul, který se označuje jako obsahující třídy, struktury nebo modulu.  
  
 Pokud chcete vrátit hodnotu volajícímu kódu, použijte `Function` postupu; jinak použijte `Sub` postup.  
  
## <a name="defining-a-function"></a>Definice funkce  
 Můžete definovat `Function` postup pouze na úrovni modulu. Proto kontextu deklarace funkce musí být třída, struktura, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedura nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](declaration-contexts-and-default-access-levels.md).  
  
 `Function` postupy výchozí veřejný přístup. Můžete nastavit jejich úrovně přístupu modifikátory přístupu.  
  
 A `Function` postupu můžete deklarovat datový typ hodnoty, která vrací postup. Můžete zadat libovolný datový typ nebo název výčtu, strukturu, třídu nebo rozhraní. Pokud nezadáte `returntype` vrátí parametr postupu `Object`.  
  
 Pokud tento postup používá `Implements` – klíčové slovo, obsahuje třídu nebo strukturu, musíte také mít `Implements` příkaz, který bezprostředně následuje po jeho `Class` nebo `Structure` příkazu. `Implements` Příkazu musí obsahovat každé rozhraní, které je zadáno v `implementslist`. Ale název, pomocí kterého rozhraní definuje `Function` (v `definedname`) nemusí odpovídat názvu tohoto postupu (v `name`).  
  
> [!NOTE]
>  Výrazy lambda můžete použít k definování vložené výrazy funkce. Další informace najdete v tématu [výraz funkce](../../../visual-basic/language-reference/operators/function-expression.md) a [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="returning-from-a-function"></a>Vrácení z funkce  
 Když `Function` postup vrátí volajícímu kódu, provádění pokračuje s příkazem, který následuje příkazu, který volá postup.  
  
 Pro navrácení hodnoty z funkce, můžete buď přiřaďte hodnotu k názvu funkce nebo ji v zahrnout `Return` příkazu.  
  
 `Return` Příkaz současně přiřadí návratovou hodnotu a ukončení funkce, jako v následujícím příkladu.  
  
 [!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]  
  
 Následující příklad přiřadí název funkce návratová hodnota `myFunction` a použije je `Exit Function` příkazu vrátit.  
  
 [!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]  
  
 `Exit Function` a `Return` příkazy způsobit okamžité ukončení `Function` postup. Libovolný počet `Exit Function` a `Return` příkazů může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Function` a `Return` příkazy.  
  
 Pokud používáte `Exit Function` bez přiřazení hodnoty k `name`, procedura vrací výchozí hodnota pro datový typ, který je zadán v `returntype`. Pokud `returntype` nezadá, vrátí postup `Nothing`, což je výchozí hodnota pro `Object`.  
  
## <a name="calling-a-function"></a>Volání funkce  
 Volání `Function` postup pomocí název procedury, za nímž následuje seznam argumentů v závorkách, ve výrazu. Závorky můžete vynechat jenom v případě, že nejsou zadávání argumentů. Váš kód je však čitelnější, pokud vždy závorek.  
  
 Volání `Function` postup fungovat stejným způsobem, že můžete volat všechny knihovny, jako `Sqrt`, `Cos`, nebo `ChrW`.  
  
 Můžete také volat funkci pomocí `Call` – klíčové slovo. V takovém případě je vrácená hodnota ignorována. Použití `Call` – klíčové slovo se nedoporučuje ve většině případů. Další informace najdete v tématu [zavolat příkaz](call-statement.md).  
  
 Visual Basic někdy znovu uspořádá aritmetických výrazů ke zvýšení účinnosti interní. Z tohoto důvodu byste neměli používat `Function` postupu na portále aritmetický výraz při změně hodnoty proměnné ve stejném výrazu funkce.  
  
## <a name="async-functions"></a>Asynchronní funkce  
 *Asynchronní* funkce umožňuje vyvolat asynchronní funkce bez použití explicitní zpětná volání nebo Ruční rozdělení kódu mezi více funkcí nebo výrazů lambda.  
  
 Pokud označíte funkce s [asynchronní](../../../visual-basic/language-reference/modifiers/async.md) modifikátor, můžete použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor ve funkci. Když ovládací prvek dosáhne `Await` výrazu v `Async` funkce, ovládací prvek vrátí volajícímu a průběh ve funkci je pozastavený, až do dokončení očekávané úlohy. Po dokončení úlohy se provádění může pokračovat ve funkci.  
  
> [!NOTE]
>  `Async` Postup vrátí řízení volajícímu, pokud buď se setká s první očekávaný objekt, který ještě není dokončeno nebo nabude na konec objektu `Async` postup, podle toho, co nastane dříve.  
  
 `Async` Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>. Příklad `Async` funkci, která má návratový typ <xref:System.Threading.Tasks.Task%601> jsou uvedeny níže.  
  
 `Async` Funkce nemůže deklarovat všechny [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametry.  
  
 A [příkaz Sub](sub-statement.md) může být označena také `Async` modifikátor. To se používá především pro obslužné rutiny událostí, ve kterém nejde vrátit hodnotu. `Async` `Sub` Nemůže být očekávána proceduru a volající `Async` `Sub` procedura nemůže zachytit výjimky, které jsou vyvolány `Sub` postup.  
  
 Další informace o `Async` funkce, najdete v článku [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [tok řízení v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), a [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>Funkce iterátorů  
 *Iterátoru* funkce provádí vlastní iterace nad kolekcí, jako je například seznamu nebo pole. Používá funkce iterátoru [Yield](yield-statement.md) příkaz vrátit vždy jeden prvek v čase. Když [Yield](yield-statement.md) je dosažen příkaz, se uloží aktuální umístění v kódu. Provádění je restartováno z tohoto umístění při příštím je zavolána funkce iterátoru.  
  
 Můžete volat iterátor z klientského kódu s použitím [For Each... Další](for-each-next-statement.md) příkazu.  
  
 Může být návratový typ funkce iterátoru <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Function` příkaz deklarovat název, parametry a kód, který tvoří text `Function` postup. `ParamArray` Modifikátor umožňuje funkci tak, aby přijímal proměnný počet argumentů.  
  
 [!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]  
  
## <a name="example"></a>Příklad  
 Následující příklad popisuje vyvolání funkce deklarovaná v předchozím příkladu.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `DelayAsync` je `Async` `Function` , která má návratový typ <xref:System.Threading.Tasks.Task%601>. `DelayAsync` má `Return` příkaz, který vrátí celé číslo. Proto deklarace funkce z `DelayAsync` musí mít typ vrácené hodnoty `Task(Of Integer)`. Vzhledem k tomu, že je návratový typ `Task(Of Integer)`, vyhodnocení `Await` výrazu v `DoSomethingAsync` vytváří celé číslo. To je ukázáno v tomto prohlášení: `Dim result As Integer = Await delayTask`.  
  
 `startButton_Click` Postup je příkladem `Async Sub` postup. Protože `DoSomethingAsync` je `Async` funkce, úkol pro volání `DoSomethingAsync` musí ní použít operátor await, jak ukazuje následující příkaz: `Await DoSomethingAsync()`. `startButton_Click` `Sub` Postupu musí být definované s `Async` modifikátor vzhledem k tomu, že má `Await` výrazu.  
  
 [!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Sub](sub-statement.md)
- [Procedury funkce](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Seznam parametrů](parameter-list.md)
- [Příkaz Dim](dim-statement.md)
- [Příkaz Call](call-statement.md)
- [z](of-clause.md)
- [Pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Řešení potíží s procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Výraz Function](../../../visual-basic/language-reference/operators/function-expression.md)
