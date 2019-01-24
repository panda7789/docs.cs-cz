---
title: Řešení potíží s poli (Visual basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 81817af230298528a766aa6494899538c35da7bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707619"
---
# <a name="troubleshooting-arrays-visual-basic"></a>Řešení potíží s poli (Visual basic)
Tato stránka obsahuje některé běžné problémy, které se mohou vyskytnout při práci s poli.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Chyby při kompilaci deklarace a inicializace pole  
 Chyby při kompilaci mohou vyplývat z neporozumění pravidla pro deklarování, vytváření a inicializaci polí. Nejběžnější příčiny chyby jsou následující:  
  
-   Zadávání [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) klauzule po zadání délky dimenzí v deklaraci proměnné pole. Následující řádky kódu zobrazit neplatná deklarace tohoto typu.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Určení délky dimenzí pro více než pole nejvyšší úrovně vícenásobného pole. Následující řádek kódu obsahuje neplatnou deklarací tohoto typu.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   Vynechání `New` – klíčové slovo při zadávání hodnot prvků. Následující řádek kódu obsahuje neplatnou deklarací tohoto typu.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   Zadávání `New` klauzule bez složených závorek (`{}`). Následující řádky kódu zobrazit neplatná deklarace tohoto typu.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Přístup k poli mimo rozsah  
 Proces inicializace pole přiřadí horní a dolní mez každé dimenze. Každý přístup k elementu pole musíte zadat platný index nebo dolní index pro každou dimenzi. Pokud je jakýkoli index pod její dolní mez nebo nad horní mez <xref:System.IndexOutOfRangeException> dojde k výjimce. Kompilátor nemůže rozpoznat takové chyby, takže dojde k chybě za běhu.  
  
### <a name="determining-bounds"></a>Určení hranic  
 Pokud jiná komponenta předává pole do kódu, například jako argumentu procedury si nejste jisti velikost pole nebo délky jeho rozměrů. Vždy byste měli určit horní mez pro každou dimenzi pole před pokusem o přístup k žádné prvky. Pokud byl vytvořen pole některé prostředky než v jazyce Visual Basic `New` klauzule dolní mez může být něco jiného než 0 a je nejbezpečnější určit, že dolní mez.  
  
### <a name="specifying-the-dimension"></a>Určení dimenze  
 Při určování hranice vícerozměrného pole, zajistíme, jak specifikujete dimenze. `dimension` Parametry <xref:System.Array.GetLowerBound%2A> a <xref:System.Array.GetUpperBound%2A> metody jsou založeny na 0 při `Rank` parametrů jazyka Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> a <xref:Microsoft.VisualBasic.Information.UBound%2A> funkce jsou založené na 1.  
  
## <a name="see-also"></a>Viz také:
- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Postupy: Inicializace proměnné pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
