---
title: Yield – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 72a8dafdc5aa834a644e1e70a309cfc0827b5fdf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352716"
---
# <a name="yield-statement-visual-basic"></a>Yield – příkaz (Visual Basic)
Odešle další prvek kolekce do příkazu `For Each...Next`.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>Parametry  
  
|Termín|Definice|  
|---|---|  
|`expression`|Požadováno. Výraz, který je implicitně převoditelné na typ funkce iterátoru nebo přistupující objekt `Get`, který obsahuje příkaz `Yield`.|  
  
## <a name="remarks"></a>Poznámky  
 Příkaz `Yield` vrací jeden prvek kolekce v čase. Příkaz `Yield` je součástí funkce iterátoru nebo přístupového objektu `Get`, který provádí vlastní iterace v kolekci.  
  
 Využijete funkci iterátoru [pro každý z nich... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md) nebo dotaz LINQ. Každá iterace `For Each` smyčky volá funkci iterátoru. Když se ve funkci iterátoru dosáhne `Yield` příkazu, vrátí se `expression` a aktuální umístění v kódu se zachová. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.  
  
 Implicitní převod musí existovat v typu `expression` v příkazu `Yield` na návratový typ iterátoru.  
  
 Chcete-li ukončit iteraci, můžete použít příkaz `Exit Function` nebo `Return`.  
  
 "Yield" není rezervované slovo a má zvláštní význam pouze v případě, že je použit ve funkci `Iterator` nebo přístupovém objektu `Get`.  
  
 Další informace o funkcích iterátoru a přístupových objektů `Get` najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Funkce iterátoru a přistupující objekty get  
 Deklarace funkce iterátoru nebo přístupového objektu `Get` musí splňovat následující požadavky:  
  
- Musí obsahovat modifikátor [iterátoru](../../../visual-basic/language-reference/modifiers/iterator.md) .  
  
- Návratový typ musí být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
- Nemůže mít žádné parametry `ByRef`.  
  
 Funkce iterátoru nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statickém destruktoru.  
  
 Funkce iterátoru může být anonymní funkce. Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Zpracování výjimek  
 Příkaz `Yield` může být uvnitř bloku `Try` [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Blok `Try`, který má příkaz `Yield`, může mít `Catch` bloky a může mít `Finally` blok.  
  
 Příkaz `Yield` nemůže být uvnitř bloku `Catch` nebo bloku `Finally`.  
  
 Pokud `For Each` tělo (mimo funkci iterátoru) vyvolá výjimku, není proveden blok `Catch` ve funkci iterátoru, ale je spuštěn blok `Finally` ve funkci iterátoru. `Catch` blok uvnitř funkce iterátoru zachytává pouze výjimky, ke kterým dojde uvnitř funkce iterátoru.  
  
## <a name="technical-implementation"></a>Technická implementace  
 Následující kód vrátí `IEnumerable (Of String)` z funkce iterátoru a poté provede iteraci prvky `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 Volání `MyIteratorFunction` nespustí tělo funkce. Místo toho volání vrátí `IEnumerable(Of String)` do proměnné `elements`.  
  
 V iteraci `For Each` smyčky je <xref:System.Collections.IEnumerator.MoveNext%2A> metoda volána pro `elements`. Toto volání provede text `MyIteratorFunction` až do chvíle, kdy se dosáhne dalšího příkazu `Yield`. Příkaz `Yield` vrací výraz, který určuje nejen hodnotu `element` proměnné pro spotřebu v těle smyčky, ale také vlastnost <xref:System.Collections.Generic.IEnumerator%601.Current%2A> prvků, což je `IEnumerable (Of String)`.  
  
 Při každé následující iteraci `For Each` smyčky pokračuje v provádění tohoto textu iterátoru, kde se nachází, a znovu se zastaví, až dosáhne příkazu `Yield`. `For Each` cyklus dokončí, když je dosaženo konce funkce iterátoru nebo příkazu `Return` nebo `Exit Function`.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje příkaz `Yield`, který je uvnitř [... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka Každá iterace [pro každý](../../../visual-basic/language-reference/statements/for-each-next-statement.md) text příkazu v `Main` vytvoří volání funkce `Power` iterátoru. Každé volání funkce iterátoru pokračuje na další provedení příkazu `Yield`, ke kterému dojde během další iterace `For…Next` smyčky.  
  
 Návratový typ metody iterátoru je <xref:System.Collections.Generic.IEnumerable%601>, typ rozhraní iterátoru. Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje přistupující objekt `Get`, který je iterátorem. Deklarace vlastnosti obsahuje modifikátor `Iterator`.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Další příklady naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Viz také:

- [Příkazy](../../../visual-basic/language-reference/statements/index.md)
