---
title: "'<membername>' nemůže vystavovat typ '<typename>' mimo projekt prostřednictvím <containertype> '<containertypename>'."
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 729a9f385d94412469d318cb804d216827eeb0fd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397282"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>'\<membername>' nemůže vystavovat typ '\<typename>' mimo projekt prostřednictvím \<containertype> '\<containertypename>'.
Proměnná, parametr procedury nebo návrat funkce jsou vystaveny mimo svůj kontejner, ale jsou deklarovány jako typ, který nesmí být vystaven mimo kontejner.  
  
 Následující kostrový kód zobrazuje situaci, která tuto chybu generuje.  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Typ deklarovaný `Protected` ,, `Friend` `Protected Friend` nebo `Private` má mít omezený přístup mimo svůj kontext deklarace. Použije se jako datový typ proměnné s omezeným přístupem bez omezení. V předchozí kostrě kódu `exposedVar` je `Public` a vystavuje `privateClass` kód, který by k němu neměl mít přístup.  
  
 **ID chyby:** BC30909  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Změňte úroveň přístupu proměnné, parametru procedury nebo vraťte funkci tak, aby byla alespoň omezující jako úroveň přístupu jeho datového typu.  
  
## <a name="see-also"></a>Viz také

- [Úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
