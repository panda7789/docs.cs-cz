---
title: Proměnné struktury
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 270e8ca26185e4a68def3b95f4ce6ab4c57a629c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393582"
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
> Ve třídách a modulech jsou struktury deklarované pomocí [příkazu Dim](../../../language-reference/statements/dim-statement.md) výchozí pro veřejný přístup. Pokud máte v úmyslu strukturu jako soukromou, ujistěte se, že ji deklarujete pomocí klíčového slova [Private](../../../language-reference/modifiers/private.md) .

## <a name="access-to-structure-values"></a>Přístup k hodnotám struktury

Chcete-li přiřadit a načíst hodnoty z prvků proměnné struktury, použijte stejnou syntaxi, jako je použit k nastavení a získání vlastností objektu. Umístěte operátor přístupu členů ( `.` ) mezi název proměnné struktury a název elementu. Následující příklad přistupuje k prvkům proměnných dříve deklarovaných jako typ `systemInfo` .

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

Pokud prvek struktury je odkazový typ, jako je například `String` , `Object` nebo pole, je zkopírován ukazatel na data. V předchozím příkladu, pokud `systemInfo` obsahoval proměnnou objektu, pak předchozí příklad zkopíroval ukazatel z `mySystem` na a `yourSystem` a změna dat objektu prostřednictvím jedné struktury bude platit při otevření prostřednictvím jiné struktury.

## <a name="see-also"></a>Viz také

- [Datové typy](index.md)
- [Základní datové typy](elementary-data-types.md)
- [Složené datové typy](composite-data-types.md)
- [Typy hodnot a typy odkazu](value-types-and-reference-types.md)
- [Struktury](structures.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Postupy: Deklarace struktury](how-to-declare-a-structure.md)
- [Struktury a ostatní programovací elementy](structures-and-other-programming-elements.md)
- [Struktury a třídy](structures-and-classes.md)
- [Structure – příkaz](../../../language-reference/statements/structure-statement.md)
