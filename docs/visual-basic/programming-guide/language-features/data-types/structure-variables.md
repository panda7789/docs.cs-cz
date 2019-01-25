---
title: Proměnné struktury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: f9cc6d0165b0eda8358d250c37910b1362473ab1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640599"
---
# <a name="structure-variables-visual-basic"></a>Proměnné struktury (Visual Basic)
Po vytvoření struktury můžete deklarovat proměnné, postup úroveň a úroveň modulu jako tohoto typu. Můžete například vytvořit strukturu tohoto zaznamenává informace o systému počítače. Následující příklad ukazuje to.  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 Nyní můžete deklarovat proměnné tohoto typu. To znázorňuje následující deklarace.  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  Ve třídách a moduly, struktur deklarované pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) výchozí veřejný přístup. Pokud máte v úmyslu struktura bude privátní, ujistěte se, že deklarujete jej s použitím [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo.  
  
## <a name="access-to-structure-values"></a>Přístup k hodnotám struktura  
 Přiřazení a načítat hodnoty z elementů proměnnou struktury, použijete stejnou syntaxi jako použijte k nastavení a načtení vlastností pro objekt. Umístit operátor přístupu členů (`.`) mezi názvem proměnné struktury a název elementu. Následující příklad přistupuje k prvky proměnných dříve deklarovány jako typ `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>Přiřazení proměnné struktury  
 Můžete také přiřadit jednu proměnnou do jiného, pokud jsou obě stejného typu Struktura. To zkopíruje všechny prvky z jedné struktury na odpovídající elementy v jiném. To znázorňuje následující deklarace.  
  
```  
yourSystem = mySystem  
```  
  
 Pokud element struktury, jako je typem odkazu `String`, `Object`, nebo pole, ukazatel na data zkopírována. V předchozím příkladu Pokud `systemInfo` obsahoval proměnné objektu, pak by jste zkopírovali v předchozím příkladu ukazatel z `mySystem` k `yourSystem`, a změna data objektu prostřednictvím jedné struktury by při přístupu nebudou platit prostřednictvím jiné struktury.  
  
## <a name="see-also"></a>Viz také:
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Postupy: Deklarace struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Struktury a ostatní programovací elementy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
