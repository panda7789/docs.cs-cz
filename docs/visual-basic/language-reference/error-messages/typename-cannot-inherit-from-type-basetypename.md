---
title: '&#39;&lt;TypeName&gt; &#39; nemůže dědit od třídy &lt;typ&gt; &#39; &lt;basetypename&gt; &#39; protože rozšiřuje přístup základní třídy &lt;typ&gt; mimo sestavení'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 108025132bdd0fa86df5ed142aaa39c7b7e18062
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556480"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39;&lt;TypeName&gt; &#39; nemůže dědit od třídy &lt;typ&gt; &#39; &lt;basetypename&gt; &#39; protože rozšiřuje přístup základní třídy &lt;typ&gt; mimo sestavení
Třídy nebo rozhraní dědí ze základní třídy nebo rozhraní, ale má míň omezující úroveň přístupu.  
  
 Například `Public` rozhraní zdědí `Friend` rozhraní, nebo `Protected` třída dědí z `Private` třídy. Tato třída zveřejňuje základní třídu nebo rozhraní pro přístup k mimo určené úroveň.  
  
 **ID chyby:** BC30910  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Změníte úroveň přístupu odvozené třídy nebo rozhraní, které má být omezující jako základní třídu nebo rozhraní.  
  
     -nebo-  
  
-   Pokud požadujete méně omezující úroveň přístupu, odeberte `Inherits` příkazu. Nemůže dědit z více omezený základní třídu nebo rozhraní.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
