---
title: Výchozí instance objektů poskytované třídami My.Forms a My.WebServices
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: d06df4bd023892429b2aaefdd624398a6546d06d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330209"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Výchozí instance objektů poskytované třídami My.Forms a My.WebServices (Visual Basic)

Objekty [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) a [My.](../../../visual-basic/language-reference/objects/my-webservices-object.md) WebServices poskytují přístup k formulářům, zdrojům dat a webovým službám XML, které vaše aplikace používá. Poskytují kolekce *výchozích instancí* každého z těchto objektů.  
  
## <a name="default-instances"></a>Výchozí instance  

 Výchozí instance je instance třídy, která je poskytována modulem runtime a není nutné ji deklarovat a vytvořit pomocí příkazů `Dim` a `New`. Následující příklad ukazuje, jak je možné deklarovat a vytvořit instanci <xref:System.Windows.Forms.Form> třídy s názvem `Form1`a jakým způsobem je nyní možné získat výchozí instanci této <xref:System.Windows.Forms.Form> třídy prostřednictvím `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 Objekt `My.Forms` vrátí kolekci výchozích instancí pro každou třídu `Form`, která existuje ve vašem projektu. Podobně `My.WebServices` poskytuje výchozí instanci třídy proxy pro každou webovou službu, na kterou jste vytvořili odkaz na aplikaci.  
  
## <a name="see-also"></a>Viz také:

- [Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [Závislost oboru názvů My na typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
