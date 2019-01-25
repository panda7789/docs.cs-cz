---
title: '&#39;#Region&#39; a &#39;#End Region&#39; příkazy nejsou platné uvnitř těla nebo víceřádkových výrazů lambda – metoda'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 55399cd123ce4d67cc833f2eabe3230acdafc0bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737212"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39;#Region&#39; a &#39;#End Region&#39; příkazy nejsou platné uvnitř těla nebo víceřádkových výrazů lambda – metoda
`#Region` Bloku musí být deklarován na úrovni třídy, modulu nebo oboru názvů. Sbalitelná oblast může zahrnovat jeden nebo více postupů, ale nesmí začínat ani končit v rámci procedury.  
  
 **ID chyby:** BC32025  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že je správně ukončují předchozí postup `End Function` nebo `End Sub` příkazu.  
  
2.  Ujistěte se, `#Region` a `#End Region` direktivy jsou ve stejném bloku kódu.  
  
## <a name="see-also"></a>Viz také:
- [Direktiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
