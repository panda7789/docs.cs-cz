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
ms.openlocfilehash: 7b375c5a45998fc0bd06f7c075f23a30dd377295
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Struktury a ostatní programovací elementy (Visual Basic)
Struktury můžete použít ve spojení se pole, objekty a postupů, a také mezi sebou. Interakce používají stejnou syntaxi jako tyto prvky použijte jednotlivě.  
  
> [!NOTE]
>  Nelze inicializovat všechny elementy struktury v deklarace struktury. Hodnoty můžete přiřadit pouze na elementy proměnné, která byla deklarována jako struktura typu.  
  
## <a name="structures-and-arrays"></a>Struktury a pole  
 Struktury může obsahovat pole jako jeden nebo více jeho elementy. Toto dokládá následující příklad.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 Hodnoty pole v rámci struktury přístup stejným způsobem jako přístup k vlastnosti objektu. Toto dokládá následující příklad.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Můžete také deklarovat pole struktury. Toto dokládá následující příklad.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Provedením stejná pravidla pro přístup k součástem této architektury data. Toto dokládá následující příklad.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Struktury a objekty  
 Struktury může obsahovat objekt jako jeden nebo více jeho elementy. Toto dokládá následující příklad.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Ve deklarace, byste měli používat konkrétní objekt třídy místo `Object`.  
  
## <a name="structures-and-procedures"></a>Struktury a postupy  
 Můžete předat do struktury jako argumentu procedury. Toto dokládá následující příklad.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 V předchozím příkladu předá strukturu *odkazem*, což umožňuje postupu upravte jeho elementy, aby byl změny se projeví ve volání kódu. Pokud chcete chránit struktura proti takové úpravy, předejte jej hodnotou.  
  
 Můžete se taky vrátit do struktury z `Function` postupu. Toto dokládá následující příklad.  
  
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
 Struktury může obsahovat jiné struktury. Toto dokládá následující příklad.  
  
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
  
 Tento postup můžete taky zapouzdření struktuře definované v jeden modul v rámci struktuře definované v různých modulu.  
  
 Struktury může obsahovat jiné struktur pro libovolný hloubka.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Postupy: Definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Proměnné struktury](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [Struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
