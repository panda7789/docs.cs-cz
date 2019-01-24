---
title: Struktury a ostatní programovací elementy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: ed406254435602dcd98bc97716cc88710a470ed1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679588"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Struktury a ostatní programovací elementy (Visual Basic)
Struktury můžete použít ve spojení s pole objektů a postupy, stejně jako mezi sebou. Interakce používají stejnou syntaxi jako tyto prvky použít jednotlivě.  
  
> [!NOTE]
>  Nelze inicializovat prvky struktury v deklaraci struktury. Pouze na prvky, které jsou deklarované se strukturovaným typem proměnné můžete přiřadit hodnoty.  
  
## <a name="structures-and-arrays"></a>Struktury a pole  
 Struktura může obsahovat pole jako jeden nebo více z jeho prvků. Toto dokládá následující příklad.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 Máte přístup k hodnoty pole v rámci struktury stejným způsobem, přístup k vlastnosti pro objekt. Toto dokládá následující příklad.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Můžete také deklarovat pole struktur. Toto dokládá následující příklad.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Můžete řídit stejnými pravidly pro přístup k součástem tato architektura data. Toto dokládá následující příklad.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Struktury a objekty  
 Struktura může obsahovat objekt jako jeden nebo více z jeho prvků. Toto dokládá následující příklad.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Používejte konkrétní objekt třídy v deklaraci, spíše než `Object`.  
  
## <a name="structures-and-procedures"></a>Struktury a postupy  
 Struktury lze předat jako argument procedury. Toto dokládá následující příklad.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 Předchozí příklad předává struktury *odkazem*, což umožňuje postupu upravte jeho prvky tak, aby se změny projevily ve volajícím kódu. Pokud chcete chránit proti takové změny struktury, předejte hodnotou.  
  
 Můžete se taky vrátit struktury z `Function` postup. Toto dokládá následující příklad.  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a>Struktury v rámci struktury  
 Struktury mohou obsahovat jiné struktury. Toto dokládá následující příklad.  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 Tento postup lze také použít k zapouzdření struktuře definované v jeden modul v rámci struktury definované v jiný modul.  
  
 Struktury mohou obsahovat další struktury do libovolné hloubky.  
  
## <a name="see-also"></a>Viz také:
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Postupy: Deklarace struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Proměnné struktury](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
