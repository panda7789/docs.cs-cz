---
title: "Sub – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Sub
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
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02ba9a999db20abce2106269522c9a3221a00cef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sub-statement-visual-basic"></a>Sub – příkaz (Visual Basic)
Deklaruje název, parametry a kód, který definovat `Sub` postupu.  
  
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
  
     Volitelné. V tématu [seznam atributů](attribute-list.md).  
  
-   `Partial`  
  
     Volitelné. Určuje definici částečné metody. V tématu [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).  
  
-   `accessmodifier`  
  
     Volitelné. Může být jedna z následujících akcí:  
  
    -   [Veřejné](../modifiers/public.md)  
  
    -   [Chráněný](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Privátní](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Volitelné. Může být jedna z následujících akcí:  
  
    -   [Přetížení](../modifiers/overloads.md)  
  
    -   [Přepsání](../modifiers/overrides.md)  
  
    -   [Overridable](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Volitelné. V tématu [sdílené](../modifiers/shared.md).  
  
-   `Shadows`  
  
     Volitelné. V tématu [stínů](../modifiers/shadows.md).  
  
-   `Async`  
  
     Volitelné. V tématu [asynchronní](../modifiers/async.md).  
  
-   `name`  
  
     Požadováno. Název procedury. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Chcete-li vytvořit proceduru konstruktor pro třídu, nastavte název `Sub` postup `New` – klíčové slovo. Další informace najdete v tématu [doba života objektu: jak jsou objekty vytvořen a Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
-   `typeparamlist`  
  
     Volitelné. Seznam parametrů typu pro obecný postup. V tématu [zadejte seznam](type-list.md).  
  
-   `parameterlist`  
  
     Volitelné. Seznam místní názvy proměnných představující parametry tohoto postupu. V tématu [seznam parametrů](parameter-list.md).  
  
-   `Implements`  
  
     Volitelné. Označuje, že tento postup implementuje jeden nebo více `Sub` postupy, každé z nich definované v rozhraní implementované obsahující třídu nebo strukturu tento postup. V tématu [implementuje příkaz](implements-statement.md).  
  
-   `implementslist`  
  
     Požadováno pokud `Implements` pochází. Seznam `Sub` postupy se implementuje.  
  
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
  
     Volitelné. Blok příkazů ke spuštění v rámci tohoto postupu.  
  
-   `End Sub`  
  
     Ukončí definici tohoto postupu.  
  
## <a name="remarks"></a>Poznámky  
 Všechny spustitelný kód musí být uvnitř procedury. Použití `Sub` procedury při nechcete vrátit hodnotu volání kódu. Použití `Function` postup, pokud chcete vrátit hodnotu.  
  
## <a name="defining-a-sub-procedure"></a>Definování Sub – procedury  
 Můžete definovat `Sub` postup jenom na úrovni modulu. Kontext deklarace pro proceduru sub proto musí být třídy, struktury, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedury nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](declaration-contexts-and-default-access-levels.md).  
  
 `Sub`Výchozí nastavení postupy veřejný přístup. Jejich úrovně přístupu můžete upravit pomocí modifikátory přístupu.  
  
 Pokud postup používá `Implements` – klíčové slovo, obsahující třídu nebo strukturu, musíte mít `Implements` příkaz, který následuje jeho `Class` nebo `Structure` příkaz. `Implements` Příkaz musí zahrnovat každé rozhraní, který je uveden v `implementslist`. Ale název, podle kterého rozhraní definuje `Sub` (v `definedname`) nemusí odpovídat názvu tohoto postupu (v `name`).  
  
## <a name="returning-from-a-sub-procedure"></a>Vrácení z Sub – procedury  
 Když `Sub` postup vrátí kód volání, pokračuje provádění příkaz po příkazu, která je volána.  
  
 Následující příklad ukazuje vrátit z `Sub` postupu.  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 `Exit Sub` a `Return` příkazy způsobit okamžitou výstupu z `Sub` postupu. Libovolný počet `Exit Sub` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Sub` a `Return` příkazy.  
  
## <a name="calling-a-sub-procedure"></a>Volání metody Sub – procedury  
 Volání `Sub` postup s využitím název procedury v příkazu a potom následující tento název s jeho seznam argumentů v závorkách. Závorky můžete vynechat, pouze v případě, že jste zadali žádné argumenty. Váš kód je však lépe čitelný, pokud vždy zahrnovat závorkách.  
  
 A `Sub` postupu a `Function` postupu můžete mít parametry a provádět řadu příkazů. Ale `Function` postup vrátí hodnotu a `Sub` postup není. Proto nelze použít `Sub` postup ve výrazu.  
  
 Můžete použít `Call` – klíčové slovo při volání `Sub` postup, ale že – klíčové slovo není vhodná pro většinu používá. Další informace najdete v tématu [volání příkazu](call-statement.md).  
  
 Visual Basic někdy Přeuspořádá aritmetických výrazech ke zvýšení efektivity interní. Z tohoto důvodu Pokud váš argument seznam obsahuje výrazy, které volají další postupy, budete by neměl předpokládat, že bude volán tyto výrazy v určitém pořadí.  
  
## <a name="async-sub-procedures"></a>Asynchronní Sub – procedury  
 Pomocí funkce asynchronní můžete vyvolat asynchronní funkce bez použití explicitní zpětná volání nebo Ruční rozdělení kódu napříč více funkcí nebo výrazy lambda.  
  
 Pokud označíte procedura se [asynchronní](../modifiers/async.md) modifikátor, můžete použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor v postupu. Při řízení dosáhnou `Await` výrazu v `Async` postupu řízení vrátí volajícímu a průběh v postupu je pozastaveno, dokud dokončení awaited úlohy. Po dokončení úlohy provádění může pokračovat v postupu.  
  
> [!NOTE]
>  `Async` Postup vrátí volajícího, když je zjištěna buď první awaited objekt, který ještě není dokončena nebo konci `Async` postup je dosaženo, cokoliv nastane dříve.  
  
 Můžete také označit [funkce příkaz](function-statement.md) s `Async` modifikátor. `Async` Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>. Příklad později v tomto tématu je uveden `Async` funkce, která má návratový typ <xref:System.Threading.Tasks.Task%601>.  
  
 `Async``Sub` postupy se primárně používají pro obslužné rutiny událostí, kde nejde vrátit hodnotu. `Async``Sub` Procedury nelze očekáváno a volající `Async``Sub` procedury nelze zachytit výjimky, `Sub` postup vyvolává.  
  
 `Async` Procedury nelze deklarovat všechny [ByRef](../modifiers/byref.md) parametry.  
  
 Další informace o `Async` postupech najdete v [asynchronní programování s Async a Await](../../../visual-basic/programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), a [asynchronní vrátit typy](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Sub` příkaz zadat název, parametry a kód, který vytvoří text `Sub` postupu.  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `DelayAsync` je došlo `Async``Function` s návratovým typem <xref:System.Threading.Tasks.Task%601>. `DelayAsync`má `Return` příkaz, který vrátí celé číslo. Proto funkce deklaraci `DelayAsync` musí mít návratový typ `Task(Of Integer)`. Vzhledem k tomu, že je návratový typ `Task(Of Integer)`, vyhodnocení `Await` výrazu v `DoSomethingAsync` vytváří celé číslo, jak ukazuje následující příkaz: `Dim result As Integer = Await delayTask`.  
  
 `startButton_Click` Postup je příklad `Async Sub` postupu. Protože `DoSomethingAsync` je `Async` funkce, úlohy pro volání `DoSomethingAsync` musí být očekáváno, jak ukazuje následující příkaz: `Await DoSomethingAsync()`. `startButton_Click``Sub` Postupu musí být definovány se `Async` modifikátor vzhledem k tomu, že má `Await` výrazu.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Implements – příkaz](implements-statement.md)  
 [Function – příkaz](function-statement.md)  
 [Seznam parametrů](parameter-list.md)  
 [Dim – příkaz](dim-statement.md)  
 [Call – příkaz](call-statement.md)  
 [Z](of-clause.md)  
 [Pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Postupy: použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Řešení potíží s procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
