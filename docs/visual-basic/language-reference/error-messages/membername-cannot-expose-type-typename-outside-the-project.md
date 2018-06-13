---
title: '&#39;&lt;MemberName&gt; &#39; nemůže vystavovat typ &#39; &lt;typename&gt; &#39; mimo projekt prostřednictvím &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 36add48ebee2d1804921eeeec0b59cdd4cbafecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588090"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39;&lt;MemberName&gt; &#39; nemůže vystavovat typ &#39; &lt;typename&gt; &#39; mimo projekt prostřednictvím &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;
Proměnnou, parametr procedury nebo funkce návratový je nezveřejní jejímu kontejneru, ale je deklarován jako typ, který nesmí být nezveřejní kontejneru.  
  
 Následující kód kostru ukazuje situaci, který generuje této chybě.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Typ, který je deklarován `Protected`, `Friend`, `Protected Friend`, nebo `Private` má mít omezený přístup mimo kontext jeho deklaraci. Použití jako data typ proměnné s méně omezený přístup by vůbec nemělo tento účel. V předchozím kostru kódu `exposedVar` je `Public` a by vystavit `privateClass` na kód, který by neměl mít přístup k němu.  
  
 **ID chyby:** BC30909  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Změnit úroveň přístupu proměnnou, parametr procedury nebo funkce vrátí omezující jako úroveň přístupu datového typu.  
  
## <a name="see-also"></a>Viz také  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
