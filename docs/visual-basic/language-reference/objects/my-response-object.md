---
title: My.Response – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 962108264563c5e0b2894c5c856a5f23a3c1a8b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372454"
---
# <a name="myresponse-object"></a>My.Response – objekt
Získá <xref:System.Web.HttpResponse> objekt přidružený k <xref:System.Web.UI.Page> . Tento objekt umožňuje odeslat data odpovědi HTTP klientovi a obsahuje informace o této odpovědi.  
  
## <a name="remarks"></a>Poznámky  
 `My.Response`Objekt obsahuje aktuální <xref:System.Web.HttpResponse> objekt přidružený k této stránce.  
  
 `My.Response`Objekt je k dispozici pouze pro aplikace ASP.NET.  
  
## <a name="example"></a>Příklad  
 Následující příklad získá kolekci hlaviček z `My.Request` objektu a použije `My.Response` objekt k jeho zápisu na stránku ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Web.HttpResponse>
- [My.Request – objekt](my-request-object.md)
