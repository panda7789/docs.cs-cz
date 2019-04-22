---
title: "'<membername>' nemůže vystavovat typ '<typename>' mimo projekt prostřednictvím <containertype> '<containertypename>'."
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 16f579a05236ba8977a071cb08068be8e98799f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818333"
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
