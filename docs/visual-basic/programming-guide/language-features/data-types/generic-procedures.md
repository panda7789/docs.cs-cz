---
title: Obecné procedury v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 686087e4520ea5e6e69e5906c628af3ad54749da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="generic-procedures-in-visual-basic"></a>Obecné procedury v jazyce Visual Basic
A *obecný postup*, také zavolat *obecná metoda*, je procedura definovaný s alespoň jeden typ parametru. To umožňuje přizpůsobit typy dat, které mají požadavky na jeho pokaždé, když se volá proceduru volajícího kódu.  
  
 Postup není obecné jednoduše na základě definovaný v obecné třídy nebo obecná struktura. Chcete-li být obecný, musí trvat minimálně jeden parametr typu, kromě všech normální parametrů, může to trvat. Obecné třídu nebo strukturu může obsahovat neobecné procedury a neobecná třída, struktura, nebo modul může obsahovat obecné procedury.  
  
 Obecný postup můžete použít jeho parametry typu ve svém seznamu normální parametr, v její návratový typ, pokud má jeden a v jeho postupu kódu.  
  
## <a name="type-inference"></a>Odvození typu  
 Obecný postup můžete volat bez nutnosti zadávat žádné argumenty typu vůbec. Pokud jste ji volat tímto způsobem, kompilátor se pokusí určit příslušné datové typy předat argumenty procedury typu. To se označuje jako *odvození typu*. Následující kód ukazuje volání v které kompilátor odvodí, že by měl předat typ `String` pro parametr typu `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 Pokud kompilátor nelze odvodit typ argumentů v kontextu volání, nahlásí chybu. Možnou příčinou takové chyby neshodě rozhraní pole rank. Předpokládejme například, že definujete normální parametr jako pole parametr typu. Když zavoláte obecný postup poskytuje řadu různých pořadí (počet dimenzí), je neshoda způsobí, že odvození typu selhání. Následující kód ukazuje volání v který předat do procedury, která očekává jednorozměrné pole dvourozměrná pole.  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 Odvození typu můžete vyvolat jenom vynecháním všechny argumenty typu. Pokud zadáte jeden argument typu, je nutné zadat všechny.  
  
 Odvození typu je podporována pouze pro obecné procedury. Odvození typu obecné třídy, struktury, rozhraní nebo delegáti nelze vyvolat.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu definuje obecný `Function` postup najít konkrétní prvek v poli. Definuje jeden parametr typu a použije ji k vytvoření dva parametry v seznamu parametrů.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>Komentáře  
 V předchozím příkladu vyžaduje možnost k porovnání `searchValue` proti každý element `searchArray`. Pokud chcete zajistit tuto možnost, omezuje parametr typu `T` implementovat <xref:System.IComparable%601> rozhraní. Kód používá <xref:System.IComparable%601.CompareTo%2A> metoda místo `=` operátor, protože není zaručeno, že pro zadaný argument typu `T` podporuje `=` operátor.  
  
 Můžete otestovat `findElement` postup následujícím kódem.  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 Podle předchozích volání `MsgBox` zobrazit "0", "1" a "-1" v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [Postupy: Použití obecné třídy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Procedury](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametry a argumenty procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Seznam typů](../../../../visual-basic/language-reference/statements/type-list.md)  
 [Seznam parametrů](../../../../visual-basic/language-reference/statements/parameter-list.md)
