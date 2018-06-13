---
title: '&#39;#Region&#39; a &#39;#End Region&#39; příkazy nejsou platné uvnitř těla víceřádkových výrazů lambda – metoda'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: bf3843e0ec3009f3dc7d60e91c340a7f20543231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593230"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39;#Region&#39; a &#39;#End Region&#39; příkazy nejsou platné uvnitř těla nebo víceřádkových výrazů lambda – metoda
`#Region` Bloku musí být deklarován na úrovni třídy, modul nebo obor názvů. Sbalitelné oblast může obsahovat jednu nebo více procedur, ale nesmí začínat ani končit v rámci procedury.  
  
 **ID chyby:** BC32025  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že předchozí postup je správně byla ukončena s `End Function` nebo `End Sub` příkaz.  
  
2.  Ujistěte se, že `#Region` a `#End Region` direktivy jsou ve stejné blok kódu.  
  
## <a name="see-also"></a>Viz také  
 [Direktiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
