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
ms.openlocfilehash: cc89e6f9bc2ccb4fff9a9fe12cd190a6b2d212dc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401365"
---
# <a name="yield-statement-visual-basic"></a>Yield – příkaz (Visual Basic)
Odešle další prvek kolekce do `For Each...Next` příkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>Parametry  
  
|Pojem|Definice|  
|---|---|  
|`expression`|Povinná hodnota. Výraz, který lze implicitně převést na typ funkce iterátoru nebo `Get` přistupující objekt, který obsahuje `Yield` příkaz.|  
  
## <a name="remarks"></a>Poznámky  
 `Yield`Příkaz vrátí jeden prvek kolekce v čase. `Yield`Příkaz je obsažen ve funkci iterátoru nebo `Get` přistupující objekt, který provádí vlastní iterace v kolekci.  
  
 Využijete funkci iterátoru [pro každý z nich... Další příkaz](for-each-next-statement.md) nebo dotaz LINQ. Každá iterace `For Each` smyčky volá funkci iterátoru. Je-li `Yield` ve funkci iterátoru dosaženo příkazu, `expression` je vráceno a aktuální umístění v kódu je uchováno. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.  
  
 Implicitní převod musí existovat `expression` v typu v `Yield` příkazu na návratový typ iterátoru.  
  
 `Exit Function` `Return` K ukončení iterace můžete použít příkaz or.  
  
 "Yield" není rezervované slovo a má zvláštní význam pouze v případě, že je použit ve `Iterator` funkci nebo `Get` přistupující objekt.  
  
 Další informace o funkcích iterátoru a `Get` přístupových objektů naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Funkce iterátoru a přistupující objekty get  
 Deklarace funkce iterátoru nebo `Get` přístupového objektu musí splňovat následující požadavky:  
  
- Musí obsahovat modifikátor [iterátoru](../modifiers/iterator.md) .  
  
- Návratový typ musí být <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> .  
  
- Nemůže mít žádné `ByRef` parametry.  
  
 Funkce iterátoru nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statickém destruktoru.  
  
 Funkce iterátoru může být anonymní funkce. Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Zpracování výjimek  
 `Yield`Příkaz může být uvnitř `Try` bloku [Try... Zachytit... Finally – příkaz](try-catch-finally-statement.md). `Try`Blok, který má `Yield` příkaz, může mít `Catch` bloky a může mít `Finally` blok.  
  
 `Yield`Příkaz nemůže být uvnitř `Catch` bloku nebo `Finally` bloku.  
  
 Pokud `For Each` tělo (mimo funkci iterátoru) vyvolá výjimku, není `Catch` proveden blok ve funkci iterátoru, ale `Finally` je proveden blok ve funkci iterátoru. `Catch`Blok uvnitř funkce iterátoru zachytává pouze výjimky, ke kterým dojde uvnitř funkce iterátoru.  
  
## <a name="technical-implementation"></a>Technická implementace  
 Následující kód vrátí `IEnumerable (Of String)` z funkce iterátoru a poté provede iteraci prvky objektu `IEnumerable (Of String)` .  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 Volání `MyIteratorFunction` nespustí tělo funkce. Místo toho volání vrátí `IEnumerable(Of String)` do `elements` proměnné.  
  
 V iteraci `For Each` smyčky <xref:System.Collections.IEnumerator.MoveNext%2A> je metoda volána pro `elements` . Toto volání provede tělo `MyIteratorFunction` až do `Yield` dosažení dalšího příkazu. `Yield`Příkaz vrátí výraz, který určuje nejen hodnotu `element` proměnné pro spotřebu v těle smyčky, ale také <xref:System.Collections.Generic.IEnumerator%601.Current%2A> vlastnost prvků, což je `IEnumerable (Of String)` .  
  
 Při každém následném opakování `For Each` smyčky pokračuje provádění textu iterátoru z místa, kde bylo ponecháno, opětovné zastavení při dosažení `Yield` příkazu. `For Each`Smyčka skončí po dosažení konce funkce iterátoru nebo `Return` `Exit Function` příkazu or.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje `Yield` příkaz, který je uvnitř [... Další](for-next-statement.md) smyčka Každá iterace [pro každý](for-each-next-statement.md) text příkazu v `Main` vytvoří volání `Power` funkce iterátoru. Každé volání funkce iterátoru pokračuje k dalšímu provedení `Yield` příkazu, ke kterému dojde během další iterace `For…Next` smyčky.  
  
 Návratový typ metody iterátoru je <xref:System.Collections.Generic.IEnumerable%601> , typ rozhraní iterátoru. Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `Get` přistupující objekt, který je iterátorem. Deklarace vlastnosti obsahuje `Iterator` modifikátor.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Další příklady naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Viz také

- [Příkazy](index.md)
