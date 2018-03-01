---
title: "& č. 39; &lt;membername&gt;& č. 39; nelze vystavit typ & č. 39;&lt; TypeName&gt;& č. 39; mimo projekt prostřednictvím &lt;containertype&gt; & č. 39;&lt; containertypename&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd64c815286a5ffec111bcf1f68674a8e3558403
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>& č. 39; &lt;membername&gt;& č. 39; nelze vystavit typ & č. 39;&lt; TypeName&gt;& č. 39; mimo projekt prostřednictvím &lt;containertype&gt; & č. 39;&lt; containertypename&gt;& č. 39;
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
