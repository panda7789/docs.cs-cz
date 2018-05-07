---
title: '&#39;&lt;– klíčové slovo&gt; &#39; je platná pouze v rámci metody instance'
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 2d9e26aa7dccf1b9c6390a20a59b10a0d248969d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a>&#39;&lt;– klíčové slovo&gt; &#39; je platná pouze v rámci metody instance
`Me`, `MyClass`, A `MyBase` klíčová slova odkazovat na instancí určité třídy. Proto je nelze použít uvnitř sdílenou `Function` nebo `Sub` postupu.  
  
 **ID chyby:** BC30043  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Postup odebrání klíčové slovo nebo odebrat `Shared` – klíčové slovo z deklarace procedury.  
  
## <a name="see-also"></a>Viz také  
 [Přiřazení objektové proměnné](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
