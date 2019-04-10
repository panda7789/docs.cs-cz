---
title: Parametry typů nelze použít jako kvalifikátory.
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: ba7348ae50965ffcf2719b20934451916c8fa95a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296352"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Parametry typů nelze použít jako kvalifikátory.
Programovací element je kvalifikován s kvalifikací řetězec, který obsahuje parametr typu.  
  
 Parametr typu představuje požadavek pro typ, který se nemusí zadávat, když je vytvořen obecného typu. To nepředstavuje konkrétní typ definovaný. Kvalifikace řetězec musí obsahovat pouze prvky, které jsou definovány v době kompilace.  
  
 Tato chyba může generovat následující příkazy.  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **ID chyby:** BC32098  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Odeberte parametr typu z řetězce kvalifikaci, nebo nahraďte určitého typu.  
  
2. Pokud budete muset použít konstruovaný typ najít programovací element je kvalifikován, musíte použít další logiku programu.  
  
## <a name="see-also"></a>Viz také:

- [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)
