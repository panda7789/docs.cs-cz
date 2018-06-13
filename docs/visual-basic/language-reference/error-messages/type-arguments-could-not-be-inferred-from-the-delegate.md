---
title: Argumenty typu nelze odvodit z delegáta.
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 757483f1e88276dd9db82de1c2a7e47b5c975b0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598238"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Argumenty typu nelze odvodit z delegáta.
Pomocí příkazu přiřazení `AddressOf` přiřadit adresu obecný postup delegáta, ale neposkytuje žádné argumenty Typ na obecný postup.  
  
 Za normálních okolností při vyvolání obecného typu, můžete zadat typ argumentu pro každý typ parametr, který definuje obecného typu. Pokud nezadáte žádné argumenty typu, pokusí se kompilátor odvození typy, které mají být předána do parametrů. Pokud kontext nenabízí dostatek informací pro kompilátor odvození typů, je generována chyba.  
  
 **ID chyby:** BC36564  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte argumenty typu pro obecný postup v `AddressOf` výraz.  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Obecné procedury v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)  
 [Rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
