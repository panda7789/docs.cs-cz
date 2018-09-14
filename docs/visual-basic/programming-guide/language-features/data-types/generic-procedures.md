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
ms.openlocfilehash: 9a88a979a6b46f897e5f04f4481d4a23e245b165
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569460"
---
# <a name="generic-procedures-in-visual-basic"></a>Obecné procedury v jazyce Visual Basic
A *obecný postup*, označované také jako *obecnou metodu*, postup definované s alespoň jedním parametrem typu. To umožňuje volajícímu kódu pro datové typy na své požadavky na přizpůsobení pokaždé, když volá proceduru.  
  
 Postup není obecná jednoduše tím, že je definována uvnitř obecnou třídu nebo o obecnou strukturu. Je obecný, musí trvat aspoň jeden parametr typu, kromě jakékoliv běžné parametry, které může trvat. Obecná třída nebo struktura může obsahovat neobecné postupy a neobecná třída, struktura, nebo modul může obsahovat obecné procedury.  
  
 Obecný postup můžete použít jeho parametry typu jejího seznamu parametrů normální, v jejím návratovém typu, pokud má kód z nich a v její postup.  
  
## <a name="type-inference"></a>Odvození typu  
 Obecný postup lze volat bez poskytnutí vůbec žádné argumenty typu. Při volání tímto způsobem, kompilátor se pokusí určit příslušné datové typy k předávání argumentů podle postupu. Tento postup se nazývá *odvození typu*. Následující kód ukazuje volání ve kterém kompilátor odvodí, že by měla předat typ `String` na parametr typu `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 Pokud kompilátor nemůže odvodit argumenty typu z kontextu volání, hlásí chybu. Jednou z možných příčin takové chyby je řadit nesoulad pole. Předpokládejme například, že definovat normální parametr jako pole parametru typu. Při volání obecný postup poskytuje celou řadu jiné hodnosti (počet rozměrů), neshoda způsobí, že odvození typu selhání. Následující kód ukazuje volání v které dvourozměrné pole se předává procedury, která očekává, že jednorozměrné pole.  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 Odvození typu proměnné lze vyvolat pouze vynecháním všechny argumenty typu. Pokud zadáte jeden argument typu, je třeba zadat všechny.  
  
 Odvození typu je podporován pouze pro obecné procedury. Nejde vyvolat odvození typu na obecné třídy, struktury, rozhraní nebo delegátů.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad definuje obecný `Function` procedury k nalezení konkrétní element v poli. Definuje jeden parametr typu a použije je k vytvoření dva parametry v seznamu parametrů.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>Komentáře  
 V předchozím příkladu vyžaduje schopnost porovnávat `searchValue` proti každý prvek `searchArray`. Pokud chcete zajistit tuto možnost, omezuje parametr typu `T` k implementaci <xref:System.IComparable%601> rozhraní. Tento kód použije <xref:System.IComparable%601.CompareTo%2A> metoda místo `=` operátoru, protože není k dispozici žádná záruka, že argument typu zadaný pro `T` podporuje `=` operátor.  
  
 Můžete testovat `findElement` procedury s následujícím kódem.  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 Předchozí volání `MsgBox` zobrazení "0", "1" a "-1" v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [Postupy: Použití obecné třídy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Procedury](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametry a argumenty procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Seznam typů](../../../../visual-basic/language-reference/statements/type-list.md)  
 [Seznam parametrů](../../../../visual-basic/language-reference/statements/parameter-list.md)
