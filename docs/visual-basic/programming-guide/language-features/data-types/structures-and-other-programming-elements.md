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
ms.openlocfilehash: 73d3f999e95c484dff3f5409f2cdb9032b64fe38
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266856"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Struktury a ostatní programovací elementy (Visual Basic)
Můžete použít struktury ve spojení s matice, objekty a postupy, stejně jako mezi sebou navzájem. Interakce používají stejnou syntaxi jako tyto prvky samostatně.  
  
> [!NOTE]
> Nelze inicializovat žádný z prvků struktury v deklaraci struktury. Hodnoty lze přiřadit pouze prvkům proměnné, která byla deklarována jako typ struktury.  
  
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
  
 Přístup k hodnotám pole v rámci struktury stejným způsobem, jakým přistupujete k vlastnosti na objektu. Toto dokládá následující příklad.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Můžete také deklarovat pole struktur. Toto dokládá následující příklad.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Postupujte podle stejných pravidel pro přístup k součástem této architektury dat. Toto dokládá následující příklad.  
  
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
  
 Měli byste použít konkrétní třídu objektu `Object`v takové deklaraci, nikoli .  
  
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
  
 Předchozí příklad předá strukturu *odkazem*, který umožňuje postup upravit jeho prvky tak, aby změny projeví v volajícíkód. Pokud chcete chránit strukturu proti takové úpravě, předat ji podle hodnoty.  
  
 Můžete také vrátit strukturu `Function` z postupu. Toto dokládá následující příklad.  
  
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
  
## <a name="structures-within-structures"></a>Struktury v rámci struktur  
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
  
 Tuto techniku můžete také použít k zapouzdření struktury definované v jednom modulu v rámci struktury definované v jiném modulu.  
  
 Struktury mohou obsahovat jiné struktury do libovolné hloubky.  
  
## <a name="see-also"></a>Viz také

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Postupy: Definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Proměnné struktury](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md)
