---
title: "& č. 39; &lt;typename&gt;& č. 39; je typem delegáta"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords: BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>& č. 39; &lt;typename&gt;& č. 39; je typem delegáta
'\<typename >' je typ delegáta. Delegát konstrukce umožňuje jenom jeden výraz AddressOf jako seznam argumentů. Často Výraz AddressOf lze namísto vytváření delegáta.  
  
 A `New` klauzule vytvoření instance třídy delegáta poskytuje seznam neplatný argumentů pro konstruktor delegáta.  
  
 Můžete zadat jenom jeden `AddressOf` výraz při vytvoření nové instance delegáta.  
  
 K této chybě může dojít, pokud neproběhne úspěšně všechny argumenty pro konstruktor delegáta, pokud předáte více než jeden argument, nebo Pokud předáte jeden argument, který není platným `AddressOf` výraz.  
  
 **ID chyby:** BC32008  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použití jedné `AddressOf` výraz v seznamu argumentů pro třídu delegáta v `New` klauzule.  
  
## <a name="see-also"></a>Viz také  
 [New – operátor](../../../visual-basic/language-reference/operators/new-operator.md)  
 [AddressOf – operátor](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Postupy: volání metody delegáta](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
