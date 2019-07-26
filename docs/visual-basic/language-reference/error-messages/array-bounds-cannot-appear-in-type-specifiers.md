---
title: Indexy pole nemohou být použity ve specifikátorech typu.
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 951f710160ae1023671773c21c73946f5ae94c2b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512765"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Indexy pole nemohou být použity ve specifikátorech typu.

Velikosti pole nelze deklarovat jako součást specifikátoru datového typu.

**ID chyby:** BC30638

## <a name="to-correct-this-error"></a>Oprava této chyby

- Určete velikost pole bezprostředně za názvem proměnné namísto umístění velikosti pole za typ, jak je znázorněno v následujícím příkladu.

  ```vb
  Dim Array(8) As Integer
  ```

- Definujte pole a inicializujte ho s požadovaným počtem prvků, jak je znázorněno v následujícím příkladu.

  ```vb
  Dim Array2() As Integer = New Integer(8) {}
  ```

## <a name="see-also"></a>Viz také:

- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
