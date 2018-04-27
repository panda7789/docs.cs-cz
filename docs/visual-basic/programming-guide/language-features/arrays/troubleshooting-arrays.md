---
title: Řešení potíží s poli (Visual basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e5c00c2b531dd019a207b16ffcac95424bfe450
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-arrays-visual-basic"></a>Řešení potíží s poli (Visual basic)
Tato stránka obsahuje některé běžné problémy, ke kterým dochází při práci s poli.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Chyby při kompilaci deklarace a inicializace pole  
 Chyby při kompilaci mohou vyplývat z neporozumění pravidla pro deklarování, vytváření a inicializace polí. Nejčastější příčinou chyb jsou následující:  
  
-   Poskytnutí [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) klauzule po zadání dimenze délky v deklarace proměnné pole. Následující řádky kódu ukazují neplatná deklarace tohoto typu.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Určení délky dimenze pro více než pole nejvyšší úrovně Vícenásobná pole. Následující řádek kódu ukazuje neplatný deklaraci tohoto typu.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   Vynechání `New` – klíčové slovo při zadávání hodnot prvků. Následující řádek kódu ukazuje neplatný deklaraci tohoto typu.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   Poskytnutí `New` klauzule bez složené závorky (`{}`). Následující řádky kódu ukazují neplatná deklarace tohoto typu.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Přístup k pole mimo rozsah  
 Proces inicializace pole přiřadí horní mez a dolní hranice Každá dimenze. Každý přístup k elementu pole musíte zadat platný index nebo dolní index pro každé dimenze. Pokud žádný index je menší než její dolní mez nebo vyšší než horní mez, <xref:System.IndexOutOfRangeException> dojde k výjimce. Kompilátor nerozpozná takové chyby, takže dojde k chybě za běhu.  
  
### <a name="determining-bounds"></a>Určení hranice  
 Pokud jiný součást předá pole do kódu, například jako argumentu procedury neznáte velikost tohoto pole nebo délky jeho dimenzí. Vždy byste měli zjistit horní mez pro každé dimenze pole před dalším pokusem o přístup k žádné elementy. Pokud byla vytvořena pole některé prostředky než jazyka Visual Basic `New` klauzuli dolní mez může být něco jiného než 0 a je nejbezpečnější určit, že dolní mez.  
  
### <a name="specifying-the-dimension"></a>Určení dimenze  
 Při určování hranice multidimenzionálního pole, vezměte v potaz, jak určit dimenzi. `dimension` Parametry <xref:System.Array.GetLowerBound%2A> a <xref:System.Array.GetUpperBound%2A> metody jsou založené na 0 při `Rank` parametry Visual Basicu <xref:Microsoft.VisualBasic.Information.LBound%2A> a <xref:Microsoft.VisualBasic.Information.UBound%2A> funkce jsou založené na 1.  
  
## <a name="see-also"></a>Viz také  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Postupy: Inicializace proměnné pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
