---
title: Parametry typů nelze použít jako kvalifikátory.
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592140"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Parametry typů nelze použít jako kvalifikátory.
Programovací element je kvalifikován pomocí řetězce kvalifikace, který obsahuje parametr typu.  
  
 Parametr typu představuje požadavek pro typ, který se má zadat při sestavení obecného typu. Nepředstavuje konkrétní definovaný typ. Kvalifikační řetězec musí zahrnovat pouze prvky, které jsou definovány v době kompilace.  
  
 Následující příkazy mohou vygenerovat tuto chybu.  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **ID chyby:** BC32098  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Odeberte parametr typu z řetězce kvalifikace nebo ho nahraďte definovaným typem.  
  
2. Pokud potřebujete použít konstruovaný typ k vyhledání programovacího prvku, který je kvalifikován, je nutné použít další logiku programu.  
  
## <a name="see-also"></a>Viz také:

- [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)
