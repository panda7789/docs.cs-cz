---
title: Řešení potíží s poli
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 3c50c68c2a39aa04cff2dd43b5dfde709aec290f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349069"
---
# <a name="troubleshooting-arrays-visual-basic"></a>Řešení potíží s poli (Visual Basic)
Tato stránka obsahuje některé běžné problémy, které mohou nastat při práci s poli.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Chyby kompilace, které deklaruje a inicializuje pole  
 Chyby kompilace mohou nastat při nepochopení pravidel pro deklarování, vytváření a inicializaci polí. Nejběžnější příčiny chyb jsou následující:  
  
- Zadání nové klauzule [operátoru](../../../../visual-basic/language-reference/operators/new-operator.md) po určení délek dimenzí v deklaraci proměnné pole. Následující řádky kódu ukazují neplatné deklarace tohoto typu.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- Určení délek dimenzí pro více než pole nejvyšší úrovně vícenásobného pole. Následující řádek kódu ukazuje neplatnou deklaraci tohoto typu.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- Vynechává se klíčové slovo `New` při zadávání hodnot elementu. Následující řádek kódu ukazuje neplatnou deklaraci tohoto typu.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- Poskytnutí klauzule `New` bez složených závorek (`{}`). Následující řádky kódu ukazují neplatné deklarace tohoto typu.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Přístup k poli je mimo hranice.  
 Proces inicializace pole přiřadí horní mez a spodní mez na každou dimenzi. Každý přístup k prvku pole musí pro každou dimenzi určovat platný index nebo dolní index. Pokud je některý index pod jeho dolní mezí nebo nad jeho horní mez, <xref:System.IndexOutOfRangeException> výsledek výjimky. Kompilátor nemůže rozpoznat takovou chybu, takže dojde k chybě v době běhu.  
  
### <a name="determining-bounds"></a>Určení hranic  
 Pokud jiná komponenta předá pole do kódu, například jako argument procedury, neznáte velikost tohoto pole nebo délky jeho rozměrů. Před pokusem o přístup k libovolným prvkům byste měli vždy určit horní mez pro každý rozměr pole. Pokud bylo pole Vytvořeno jiným způsobem než Visual Basic `New` klauzule, dolní hranice může být jiná než 0 a je nejbezpečnější, aby bylo možné zjistit, zda je i dolní mez.  
  
### <a name="specifying-the-dimension"></a>Určení dimenze  
 Při určování hranic multidimenzionálního pole se ujistěte, jak zadáte dimenzi. Parametry `dimension` <xref:System.Array.GetLowerBound%2A> a <xref:System.Array.GetUpperBound%2A> metody jsou založené na 0, zatímco parametry `Rank` Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> a <xref:Microsoft.VisualBasic.Information.UBound%2A>ch funkcí jsou založené na 1.  
  
## <a name="see-also"></a>Viz také:

- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Postupy: Inicializace proměnné pole v Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
