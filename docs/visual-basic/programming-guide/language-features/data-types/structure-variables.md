---
title: Proměnné struktury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 0dad7bdcac5428753e252f3b26ca0a127c293a7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="structure-variables-visual-basic"></a>Proměnné struktury (Visual Basic)
Jakmile vytvoříte strukturu, můžou deklarovat proměnné úroveň procedury a úroveň modulu jako typu. Můžete například vytvořit strukturu aby zaznamenávalo informace o systému počítače. Následující příklad ukazuje to.  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 Nyní je možné deklarovat proměnné daného typu. To ukazuje následující prohlášení.  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  Třídy a moduly, struktury deklarováno s použitím [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) výchozí nastavení veřejný přístup. Pokud máte v úmyslu struktura důvěrné, ujistěte se, je pomocí deklarovat [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo.  
  
## <a name="access-to-structure-values"></a>Přístup k hodnotám struktura  
 Pokud chcete přiřadit a načtení hodnoty z elementů struktura proměnné, použijte stejnou syntaxi jako použijte k nastavení a získat vlastnosti objektu. Umístěte operátor přístupu členů (`.`) mezi názvu proměnné struktura a název elementu. Následující příklad používá elementy proměnných dříve deklarované jako typ `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>Přiřazení proměnné struktury  
 Můžete také přiřadit jednu proměnnou do jiného, pokud jsou obě stejného typu Struktura. Zkopíruje všechny elementy struktury jeden odpovídající elementům ve druhé. To ukazuje následující prohlášení.  
  
```  
yourSystem = mySystem  
```  
  
 Pokud element struktura, jako je typu odkazu `String`, `Object`, nebo se zkopíruje pole, které má ukazatel na data. V předchozím příkladu Pokud `systemInfo` měl zahrnuté proměnné objektu, pak by ukazatel z zkopírovali v předchozím příkladu `mySystem` k `yourSystem`, a ke změně dat objektu prostřednictvím jedné struktury by platný při přístupu k prostřednictvím jiné struktury.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Postupy: Definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Struktury a ostatní programovací elementy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
