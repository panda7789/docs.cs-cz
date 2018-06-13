---
title: Výchozí instance objektů poskytované třídami My.Forms a My.WebServices (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 421995684201ec48d5e8aff9b0ed7640efd1e4b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582659"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Výchozí instance objektů poskytované třídami My.Forms a My.WebServices (Visual Basic)
[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) a [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objekty poskytují přístup k formulářů, zdroje dat a webové služby XML používá vaše aplikace. Je to tím, že poskytuje kolekce *výchozí instance* každé z těchto objektů.  
  
## <a name="default-instances"></a>Výchozí instance  
 Výchozí instance je instance třídy, která je k dispozici modulem runtime a nemusí být deklarována a vytvořena pomocí `Dim` a `New` příkazy. Následující příklad ukazuje, jak vám může deklarovat a vytvořili instanci <xref:System.Windows.Forms.Form> třídu s názvem `Form1`, a jak je nyní možné získat výchozí instanci tohoto <xref:System.Windows.Forms.Form> třídy prostřednictvím `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 `My.Forms` Objekt vrátí kolekci výchozí instance pro každý `Form` třídu, která existuje v projektu. Podobně `My.WebServices` poskytuje výchozí instanci třídy proxy pro každou webovou službu, že jste vytvořili odkaz na ve vaší aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [Závislost oboru názvů My na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
