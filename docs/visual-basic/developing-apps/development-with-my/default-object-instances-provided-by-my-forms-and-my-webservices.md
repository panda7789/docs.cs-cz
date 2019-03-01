---
title: Výchozí instance objektů poskytované třídami My.Forms a My.WebServices (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 5a81cde63de258f0996c3ddbc99e0102d58d79b8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973909"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Výchozí instance objektů poskytované třídami My.Forms a My.WebServices (Visual Basic)
[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) a [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objekty poskytují přístup k formulářům, zdroje dat a webové služby XML používaný vaší aplikací. Je to tím, že poskytuje kolekce *výchozí instance* každého z těchto objektů.  
  
## <a name="default-instances"></a>Výchozí instance  
 Výchozí instance je instancí třídy, která poskytuje modul runtime a nemusí být deklarována a vytvořena pomocí `Dim` a `New` příkazy. Následující příklad ukazuje, jak vám může deklarovat a vytvořili instanci <xref:System.Windows.Forms.Form> třídu s názvem `Form1`, a jak je teď možné získat výchozí instanci tohoto <xref:System.Windows.Forms.Form> třídy prostřednictvím `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms` Objekt vrátí kolekci výchozí instance pro každý `Form` třídy, které existují ve vašem projektu. Obdobně `My.WebServices` poskytuje výchozí instanci třídy proxy pro každou webovou službu, že jste vytvořili odkaz na ve vaší aplikaci.  
  
## <a name="see-also"></a>Viz také:
- [Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [Závislost oboru názvů My na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
