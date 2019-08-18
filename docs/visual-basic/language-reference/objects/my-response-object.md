---
title: My. Response – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: a50701998011c25c600c2a3763459c1aba3cc59a
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567449"
---
# <a name="myresponse-object"></a>My.Response – objekt
Získá objekt přidružený k <xref:System.Web.UI.Page>. <xref:System.Web.HttpResponse> Tento objekt umožňuje odeslat data odpovědi HTTP klientovi a obsahuje informace o této odpovědi.  
  
## <a name="remarks"></a>Poznámky  
 Objekt obsahuje aktuální <xref:System.Web.HttpResponse> objekt přidružený k této stránce. `My.Response`  
  
 `My.Response` Objekt je k dispozici pouze pro aplikace ASP.NET.  
  
## <a name="example"></a>Příklad  
 Následující příklad získá kolekci hlaviček z `My.Request` objektu a `My.Response` použije objekt k jeho zápisu na stránku ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Web.HttpResponse>
- [Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
