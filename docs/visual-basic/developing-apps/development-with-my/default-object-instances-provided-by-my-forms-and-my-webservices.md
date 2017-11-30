---
title: "Výchozí instance objektů poskytované třídami My.Forms a My.WebServices (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44265c3f6f38a001192a8d92f2fbb6edeaca21cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Výchozí instance objektů poskytované třídami My.Forms a My.WebServices (Visual Basic)
[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) a [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objekty poskytují přístup k formulářů, zdroje dat a webové služby XML používá vaše aplikace. Je to tím, že poskytuje kolekce *výchozí instance* každé z těchto objektů.  
  
## <a name="default-instances"></a>Výchozí instance  
 Výchozí instance je instance třídy, která je k dispozici modulem runtime a nemusí být deklarována a vytvořena pomocí `Dim` a `New` příkazy. Následující příklad ukazuje, jak vám může deklarovat a vytvořili instanci <xref:System.Windows.Forms.Form> třídu s názvem `Form1`, a jak je nyní možné získat výchozí instanci tohoto <xref:System.Windows.Forms.Form> třídy prostřednictvím `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 `My.Forms` Objekt vrátí kolekci výchozí instance pro každý `Form` třídu, která existuje v projektu. Podobně `My.WebServices` poskytuje výchozí instanci třídy proxy pro každou webovou službu, že jste vytvořili odkaz na ve vaší aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [My.Forms – objekt](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.WebServices – objekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [Jak Moje závisí na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
