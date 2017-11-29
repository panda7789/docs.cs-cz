---
title: "Vnořené funkce neobsahuje podpis, který je kompatibilní s delegáta & č. 39; &lt;vlastnost delegatename&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords: BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60cf15343023110561da3e3fcf202bd00394127a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>Vnořené funkce neobsahuje podpis, který je kompatibilní s delegáta & č. 39; &lt;vlastnost delegatename&gt;& č. 39;
Výraz lambda byl přiřazen delegáta, který má nekompatibilní podpis. Například následující kód, delegovat `Del` má dva parametry celé číslo.  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 Chyba se vyvolá, pokud výraz lambda s jedním argumentem je deklarován jako typ `Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **ID chyby:** BC36532  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Upravte definici delegáta nebo výrazu lambda přiřazené tak, aby byly kompatibilní podpisů.  
  
## <a name="see-also"></a>Viz také  
 [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Lambda – výrazy](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
