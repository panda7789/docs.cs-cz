---
title: Proměnné struktury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: a86a60def9ac1b8140194ecb6f5e784c62a0e101
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630967"
---
# <a name="structure-variables-visual-basic"></a>Proměnné struktury (Visual Basic)

Po vytvoření struktury můžete jako typ deklarovat proměnné na úrovni procedury a modulu. Můžete například vytvořit strukturu, která zaznamenává informace o počítačovém systému. Následující příklad ukazuje to.

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

Nyní můžete deklarovat proměnné tohoto typu. Následující deklarace tento příklad ilustruje.

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> Ve třídách a modulech jsou struktury deklarované pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) výchozí pro veřejný přístup. Pokud máte v úmyslu strukturu jako soukromou, ujistěte se, že ji deklarujete pomocí klíčového slova [Private](../../../../visual-basic/language-reference/modifiers/private.md) .

## <a name="access-to-structure-values"></a>Přístup k hodnotám struktury

Chcete-li přiřadit a načíst hodnoty z prvků proměnné struktury, použijte stejnou syntaxi, jako je použit k nastavení a získání vlastností objektu. Umístěte operátor přístupu členů (`.`) mezi název proměnné struktury a název elementu. Následující příklad přistupuje k prvkům proměnných dříve deklarovaných jako typ `systemInfo`.

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a>Přiřazení proměnných struktury

Můžete také přiřadit jednu proměnnou k druhé, pokud jsou obě stejné typu struktury. Tím se zkopírují všechny prvky jedné struktury do odpovídajících prvků v druhé. Následující deklarace tento příklad ilustruje.

```vb
yourSystem = mySystem
```

Pokud prvek struktury je odkazový typ, jako `String`je například, `Object`nebo pole, je zkopírován ukazatel na data. V předchozím příkladu, pokud `systemInfo` obsahoval proměnnou objektu, pak předchozí příklad zkopíroval ukazatel z `mySystem` na `yourSystem`a a změna dat objektu prostřednictvím jedné struktury bude platit při použití prostřednictvím jiné struktury.

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
