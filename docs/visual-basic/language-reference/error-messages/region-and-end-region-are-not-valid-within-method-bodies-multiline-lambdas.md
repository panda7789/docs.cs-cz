---
title: Příkazy '#Region' a '#End Region' nejsou platné uvnitř těla nebo víceřádkových výrazů lambda – metoda
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c41b95da7e3565ae7aaf332fe49361336e79f7c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303905"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>Příkazy '#Region' a '#End Region' nejsou platné uvnitř těla metody nebo víceřádkových výrazů lambda.
`#Region` Bloku musí být deklarován na úrovni třídy, modulu nebo oboru názvů. Sbalitelná oblast může zahrnovat jeden nebo více postupů, ale nesmí začínat ani končit v rámci procedury.  
  
 **ID chyby:** BC32025  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že je správně ukončují předchozí postup `End Function` nebo `End Sub` příkazu.  
  
2. Ujistěte se, `#Region` a `#End Region` direktivy jsou ve stejném bloku kódu.  
  
## <a name="see-also"></a>Viz také:

- [Direktiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
