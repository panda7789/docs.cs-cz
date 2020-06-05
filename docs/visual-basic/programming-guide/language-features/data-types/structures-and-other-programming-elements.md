---
title: Struktury a ostatní programovací elementy
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: dbd24065a954e5611663963371d5a9f4bbbaea68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393491"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Struktury a ostatní programovací elementy (Visual Basic)
Struktury můžete používat ve spojení s poli, objekty a procedurami a také mezi sebou. Interakce používají stejnou syntaxi, protože tyto prvky používají samostatně.  
  
> [!NOTE]
> V deklaraci struktury nelze inicializovat žádné prvky struktury. Hodnoty lze přiřadit pouze k prvkům proměnné, které byly deklarovány jako typ struktury.  
  
## <a name="structures-and-arrays"></a>Struktury a pole  
 Struktura může obsahovat pole jako jeden nebo více jeho prvků. Toto dokládá následující příklad.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 Přístup k hodnotám pole v rámci struktury je stejný způsob, jakým přistupujete k vlastnosti objektu. Toto dokládá následující příklad.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Můžete také deklarovat pole struktur. Toto dokládá následující příklad.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Pro přístup k součástem této architektury dat se řiďte stejná pravidla. Toto dokládá následující příklad.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Struktury a objekty  
 Struktura může obsahovat objekt jako jeden nebo více jeho prvků. Toto dokládá následující příklad.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 V takové deklaraci byste měli použít konkrétní třídu objektu, nikoli `Object` .  
  
## <a name="structures-and-procedures"></a>Struktury a postupy  
 Strukturu můžete předat jako argument procedury. Toto dokládá následující příklad.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 Předchozí příklad předá strukturu *odkazem*, což umožňuje, aby procedura změnila své prvky tak, aby se změny projevily v volajícím kódu. Pokud chcete chránit strukturu pro takovou úpravu, předejte ji podle hodnoty.  
  
 Můžete také vrátit strukturu z `Function` procedury. Toto dokládá následující příklad.  
  
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
  
## <a name="structures-within-structures"></a>Struktury ve strukturách  
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
  
 Tento postup můžete použít také k zapouzdření struktury definované v jednom modulu v rámci struktury definované v jiném modulu.  
  
 Struktury mohou obsahovat jiné struktury s libovolnou hloubkou.  
  
## <a name="see-also"></a>Viz také

- [Datové typy](index.md)
- [Základní datové typy](elementary-data-types.md)
- [Složené datové typy](composite-data-types.md)
- [Typy hodnot a typy odkazu](value-types-and-reference-types.md)
- [Struktury](structures.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Postupy: Deklarace struktury](how-to-declare-a-structure.md)
- [Proměnné struktury](structure-variables.md)
- [Struktury a třídy](structures-and-classes.md)
- [Structure – příkaz](../../../language-reference/statements/structure-statement.md)
