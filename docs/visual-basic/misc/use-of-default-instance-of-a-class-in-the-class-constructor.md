---
title: "Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a0c54c6e62f9bdc7fe510500a486461d26636d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Použití výchozí Instance třídy v konstruktoru třídy může vést k nekonečné rekurzivní volání
Výchozí instance třídy se používá v konstruktoru třídy. To může vést k nekonečné rekurzivní volání, také známé jako nekonečné smyčce.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Výchozí instance odeberte z konstruktoru třídy.  
  
## <a name="see-also"></a>Viz také  
 [Konstruktory](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
