---
title: Obecné procedury
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
ms.openlocfilehash: 16a629e07cf711778b3d8d1863958ec7a6300649
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350086"
---
# <a name="generic-procedures-in-visual-basic"></a>Obecné procedury v jazyce Visual Basic
*Obecný postup*, označovaný také jako *Obecná metoda*, je procedura definovaná s alespoň jedním parametrem typu. To umožňuje volajícímu kódu přizpůsobit datové typy na požadavky pokaždé, když volá proceduru.  
  
 Procedura není obecná pouhým definováním v obecné třídě nebo obecné struktuře. Aby bylo možné obecné, procedura musí kromě všech normálních parametrů, které může trvat, obsahovat alespoň jeden parametr typu. Obecná třída nebo struktura může obsahovat neobecné postupy a neobecnou třídu, strukturu nebo modul může obsahovat obecné procedury.  
  
 Obecný postup může použít jeho parametry typu v seznamu normálních parametrů, v jeho návratovém typu, pokud má jednu, a v kódu procedury.  
  
## <a name="type-inference"></a>Odvození typu  
 Můžete zavolat obecný postup bez nutnosti zadávat žádné argumenty typu vůbec. Pokud je zavoláte tímto způsobem, kompilátor se pokusí určit vhodné datové typy, které mají být předávány do argumentů typu procedury. Tato metoda se nazývá *odvození typu*. Následující kód ukazuje volání, ve kterém kompilátor odvodí, že by měl předat typ `String` parametru typu `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 Pokud kompilátor nemůže odvodit argumenty typu z kontextu volání, ohlásí chybu. Jednou z možných příčin této chyby je neshoda pořadí polí. Předpokládejme například, že definujete normální parametr jako pole parametru typu. Pokud voláte obecný postup poskytnutí pole odlišného pořadí (počet dimenzí), neshoda způsobuje neúspěch typu odvození typu. Následující kód ukazuje volání, ve kterém je dvojrozměrné pole předáno proceduře, který očekává jednorozměrné pole.  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 Odvození typu lze vyvolat pouze vynecháním všech argumentů typu. Pokud zadáte jeden argument typu, je nutné je zadat.  
  
 Odvození typu je podporováno pouze pro obecné procedury. Nemůžete vyvolat odvození typu u obecných tříd, struktur, rozhraní a delegátů.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad definuje obecný `Function` postup pro nalezení konkrétního prvku v poli. Definuje jeden parametr typu a používá ho k sestavení dvou parametrů v seznamu parametrů.  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>Komentáře  
 Předchozí příklad vyžaduje možnost porovnat `searchValue` s každým prvkem `searchArray`. Chcete-li zaručit tuto schopnost, omezuje parametr typu `T` k implementaci rozhraní <xref:System.IComparable%601>. Kód používá metodu <xref:System.IComparable%601.CompareTo%2A> namísto operátoru `=`, protože není nijak zaručeno, že argumentu typu, který je zadán pro `T`, podporuje operátor `=`.  
  
 `findElement`ovou proceduru můžete otestovat pomocí následujícího kódu.  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 Předchozí volání pro `MsgBox` zobrazují "0", "1" a "-1" v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Obecné typy v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Postupy: Použití obecné třídy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Procedury](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Parametry a argumenty procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Seznam typů](../../../../visual-basic/language-reference/statements/type-list.md)
- [Seznam parametrů](../../../../visual-basic/language-reference/statements/parameter-list.md)
