---
title: "& č. 39; #Region & č. 39; a & č. 39; #End Region & č. 39; příkazy nejsou platné uvnitř těla víceřádkových výrazů lambda – metoda"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 614d0c7324bfbf07bc5736c799e8b54937ead081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>& č. 39; #Region & č. 39; a & č. 39; #End Region & č. 39; příkazy nejsou platné uvnitř těla nebo víceřádkových výrazů lambda – metoda
`#Region` Bloku musí být deklarován na úrovni třídy, modul nebo obor názvů. Sbalitelné oblast může obsahovat jednu nebo více procedur, ale nesmí začínat ani končit v rámci procedury.  
  
 **ID chyby:** BC32025  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že předchozí postup je správně byla ukončena s `End Function` nebo `End Sub` příkaz.  
  
2.  Ujistěte se, že `#Region` a `#End Region` direktivy jsou ve stejné blok kódu.  
  
## <a name="see-also"></a>Viz také  
 [#Region – direktiva](../../../visual-basic/language-reference/directives/region-directive.md)
