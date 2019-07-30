---
title: 'Postupy: Přesun dat do proměnné a z ní (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: df55f122c4ea029a383196f8d9684295ac8926aa
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631120"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Postupy: Přesun dat do proměnné a z ní (Visual Basic)

Hodnotu v proměnné uložíte tak, že na levou stranu příkazu přiřazení umístíte název proměnné.

## <a name="putting-data-in-a-variable"></a>Vložení dat do proměnné

#### <a name="to-store-a-value-in-a-variable"></a>Uložení hodnoty do proměnné

- Použijte název proměnné na levé straně příkazu přiřazení.

    Následující příklad nastaví hodnotu proměnné `alpha`.

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    Hodnota generovaná na pravé straně příkazu přiřazení je uložena v proměnné.

## <a name="getting-data-from-a-variable"></a>Získávání dat z proměnné

Načtěte hodnotu proměnné zahrnutím názvu proměnné do výrazu.

#### <a name="to-retrieve-a-value-from-a-variable"></a>Načtení hodnoty z proměnné

- Použijte název proměnné ve výrazu. Proměnnou můžete použít všude, kde můžete použít konstantu nebo literál, s výjimkou výrazu, který definuje hodnotu konstanty.

  \-ani

- Použijte název proměnné za znaménkem EQUAL (`=`) v příkazu přiřazení.

  Následující příklad přečte hodnotu proměnné `startValue` a poté použije hodnotu proměnné `counter` ve výrazu.

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  Hodnota proměnné se účastní ve výrazu stejně jako konstanta a pak je uložena v proměnné nebo vlastnosti na levé straně příkazu přiřazení.

## <a name="see-also"></a>Viz také:

- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
