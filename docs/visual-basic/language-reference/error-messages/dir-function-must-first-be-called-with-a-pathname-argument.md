---
title: '&#39;Dir&#39; funkce musí být nejdříve volána s &#39;PathName&#39; argument'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 3a271d7c2c2f7b98bae8f3f6fa9b67b65e3548f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39;Dir&#39; funkce musí být nejdříve volána s &#39;PathName&#39; argument
Počáteční volání `Dir` funkce nezahrnuje `PathName` argument. První volání `Dir` musí obsahovat `PathName`, ale následující volání `Dir` nemusí obsahovat parametry pro načtení další položky.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zadejte `PathName` argument ve volání funkce.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
