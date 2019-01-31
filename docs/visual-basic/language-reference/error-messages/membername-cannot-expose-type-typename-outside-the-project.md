---
title: "'<membername>' nemůže vystavovat typ '<typename>' mimo projekt prostřednictvím <containertype> '<containertypename>'."
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 03767501488a395073f925e27adea439751c0de6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265061"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>"\<membername >' nemůže vystavovat typ '\<typename >' mimo projekt prostřednictvím \<containertype > '\<containertypename >"
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
