---
title: Výchozí instance objektů poskytované třídami My.Forms a My.WebServices
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 847724450ee2bc8bc591371f71171e8ba4ed9337
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411737"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Výchozí instance objektů poskytované třídami My.Forms a My.WebServices (Visual Basic)

Objekty [My. Forms](../../language-reference/objects/my-forms-object.md) a [My.](../../language-reference/objects/my-webservices-object.md) WebServices poskytují přístup k formulářům, zdrojům dat a webovým službám XML, které vaše aplikace používá. Poskytují kolekce *výchozích instancí* každého z těchto objektů.  
  
## <a name="default-instances"></a>Výchozí instance  

 Výchozí instance je instance třídy, která je poskytována modulem runtime a není nutné ji deklarovat a vytvořit pomocí `Dim` `New` příkazů a. Následující příklad ukazuje, jak je možné deklarovat a vytvořit instanci <xref:System.Windows.Forms.Form> třídy s názvem a `Form1` jak teď lze získat výchozí instanci této <xref:System.Windows.Forms.Form> třídy prostřednictvím `My.Forms` .  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms`Objekt vrátí kolekci výchozích instancí pro každou `Form` třídu, která existuje ve vašem projektu. Podobně `My.WebServices` poskytuje výchozí instanci třídy proxy pro každou webovou službu, na kterou jste vytvořili odkaz na aplikaci.  
  
## <a name="see-also"></a>Viz také

- [My.Forms – objekt](../../language-reference/objects/my-forms-object.md)
- [My.WebServices – objekt](../../language-reference/objects/my-webservices-object.md)
- [Závislost oboru názvů My na typu projektu](how-my-depends-on-project-type.md)
