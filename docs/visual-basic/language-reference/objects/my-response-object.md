---
title: My.Response – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 522814ad48fb7548032b8a37779bb3ff6ca62413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350661"
---
# <a name="myresponse-object"></a>My.Response – objekt
Získá objekt <xref:System.Web.HttpResponse> přidružený k <xref:System.Web.UI.Page>. Tento objekt umožňuje odeslat data odpovědi HTTP klientovi a obsahuje informace o této odpovědi.  
  
## <a name="remarks"></a>Poznámky  
 Objekt `My.Response` obsahuje aktuální objekt <xref:System.Web.HttpResponse> přidružený k této stránce.  
  
 Objekt `My.Response` je k dispozici pouze pro aplikace ASP.NET.  
  
## <a name="example"></a>Příklad  
 Následující příklad získá kolekci hlaviček z objektu `My.Request` a pomocí objektu `My.Response` jej zapíše na stránku ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Web.HttpResponse>
- [Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
