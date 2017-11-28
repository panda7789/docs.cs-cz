---
title: "Parametry typů nelze použít jako kvalifikátory."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords: BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58be51e0c05750ee044f0287cde8db037718b4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Parametry typů nelze použít jako kvalifikátory.
Programovací element je kvalifikovaný s kvalifikací řetězec, který obsahuje parametr typu.  
  
 Parametr typu představuje požadavek pro typ, který je nutné zadat, když se obecného typu. Nereprezentuje konkrétního typu definované. Kvalifikace řetězec musí obsahovat pouze elementy, které jsou definovány v době kompilace.  
  
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
  
1.  Odeberte parametr typu z řetězce kvalifikaci, nebo nahraďte určitého typu.  
  
2.  Pokud potřebujete použít vytvořený typ najít programovací element jako kvalifikované, je nutné použít další logiku programu.  
  
## <a name="see-also"></a>Viz také  
 [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)
