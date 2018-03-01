---
title: "& č. 39; &lt;– klíčové slovo&gt;& č. 39; je platná pouze v rámci metody instance"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a61314c036cec0fd1412a9c844a610fbd1401add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a>& č. 39; &lt;– klíčové slovo&gt;& č. 39; je platná pouze v rámci metody instance
`Me`, `MyClass`, A `MyBase` klíčová slova odkazovat na instancí určité třídy. Proto je nelze použít uvnitř sdílenou `Function` nebo `Sub` postupu.  
  
 **ID chyby:** BC30043  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Postup odebrání klíčové slovo nebo odebrat `Shared` – klíčové slovo z deklarace procedury.  
  
## <a name="see-also"></a>Viz také  
 [Přiřazení objektové proměnné](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [ME, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
