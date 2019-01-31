---
title: Příkazy '#Region' a '#End Region' nejsou platné uvnitř těla nebo víceřádkových výrazů lambda – metoda
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 2a2f5692518c6784dfc6e3be6302f1e8dcf2aaa7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265568"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>Příkazy '#Region' a '#End Region' nejsou platné uvnitř těla metody nebo víceřádkových výrazů lambda.
`#Region` Bloku musí být deklarován na úrovni třídy, modulu nebo oboru názvů. Sbalitelná oblast může zahrnovat jeden nebo více postupů, ale nesmí začínat ani končit v rámci procedury.  
  
 **ID chyby:** BC32025  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že je správně ukončují předchozí postup `End Function` nebo `End Sub` příkazu.  
  
2.  Ujistěte se, `#Region` a `#End Region` direktivy jsou ve stejném bloku kódu.  
  
## <a name="see-also"></a>Viz také:
- [Direktiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
