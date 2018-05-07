---
title: Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cf5d3e16c43920a90b69c815f91601c6d33c845d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání
Výchozí instance třídy se používá v konstruktoru třídy. To může vést k nekonečné rekurzivní volání, také známé jako nekonečné smyčce.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Výchozí instance odeberte z konstruktoru třídy.  
  
## <a name="see-also"></a>Viz také  
 [Konstruktory](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
