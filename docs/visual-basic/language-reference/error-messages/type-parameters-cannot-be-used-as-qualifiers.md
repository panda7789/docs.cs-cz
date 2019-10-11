---
title: Parametry typu se nedají použít jako kvalifikátory.
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 3ff4b189539bf119351a94dabadd596c336ac723
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250330"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Parametry typu se nedají použít jako kvalifikátory.

Programovací element je kvalifikován pomocí řetězce kvalifikace, který obsahuje parametr typu.

Parametr typu představuje požadavek pro typ, který se má zadat při sestavení obecného typu. Nepředstavuje konkrétní definovaný typ. Kvalifikační řetězec musí zahrnovat pouze prvky, které jsou definovány v době kompilace.

Následující kód může vygenerovat tuto chybu:

```vb  
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.
End Function  
```  
  
 **ID chyby:** BC32098  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Odeberte parametr typu z řetězce kvalifikace nebo ho nahraďte definovaným typem.  
  
2. Pokud potřebujete použít konstruovaný typ k vyhledání programovacího prvku, který je kvalifikován, je nutné použít další logiku programu.  
  
## <a name="see-also"></a>Související témata

- [Odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Seznam typů](../statements/type-list.md)
