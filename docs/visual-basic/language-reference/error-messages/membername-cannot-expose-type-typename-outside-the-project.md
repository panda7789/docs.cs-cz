---
title: '&#39;&lt;MemberName&gt; &#39; nemůže vystavovat typ &#39; &lt;typename&gt; &#39; mimo projekt prostřednictvím &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 39d316aca5ec306de4b1e43e2eb2d1495f5525d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672341"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39;&lt;MemberName&gt; &#39; nemůže vystavovat typ &#39; &lt;typename&gt; &#39; mimo projekt prostřednictvím &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;
Proměnná, parametr procedury nebo návratová hodnota funkce je vystaven vně svého kontejneru, ale je deklarován jako typ, který nesmí být vystaven vně kontejneru.  
  
 Následující kostrou kód ukazuje situaci, která vygeneruje tuto chybu.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Typ, který je deklarován `Protected`, `Friend`, `Protected Friend`, nebo `Private` má omezený přístup mimo jeho deklarace kontextu. Použití jako data typu proměnné s méně omezený přístup by vůbec nemělo tento účel. V předchozím kódu kostru `exposedVar` je `Public` a by vystavovat `privateClass` kódu, který by neměl mít přístup k němu.  
  
 **ID chyby:** BC30909  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Změna úrovně přístupu proměnná, parametr procedury nebo funkce vrátit se nejméně omezující jako úroveň přístupu jeho datového typu.  
  
## <a name="see-also"></a>Viz také:
- [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
