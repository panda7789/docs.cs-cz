---
title: '&#39;&lt;TypeName&gt; &#39; nemůže Zdědit z &lt;typ&gt; &#39; &lt;basetypename&gt; &#39; protože rozšiřuje přístup základní &lt;typ&gt; mimo sestavení'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: f747b2b24f5fecc22b9e1fbc6ba26b634e9ead2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39;&lt;TypeName&gt; &#39; nemůže Zdědit z &lt;typ&gt; &#39; &lt;basetypename&gt; &#39; protože rozšiřuje přístup základní &lt;typ&gt; mimo sestavení
Třídy nebo rozhraní dědí vlastnosti ze základní třídy nebo rozhraní ale je méně omezující úroveň přístupu.  
  
 Například `Public` rozhraní dědí z `Friend` rozhraní, nebo `Protected` třída dědí z `Private` třídy. To zpřístupňuje základní třídy nebo rozhraní pro přístup k mimo určený úroveň.  
  
 **ID chyby:** BC30910  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Změníte úroveň přístupu tohoto odvozené třídy nebo rozhraní na omezující jako základní třídy nebo rozhraní.  
  
     -nebo-  
  
-   Pokud budete potřebovat méně omezující úroveň přístupu, odeberte `Inherits` příkaz. Nelze zdědit omezenější základní třídy nebo rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
