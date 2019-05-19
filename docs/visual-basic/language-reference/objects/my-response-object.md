---
title: My.Response – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 0e49a3b5732ee1a3626666ce06e366c4940eca05
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881967"
---
# <a name="myresponse-object"></a>My.Response – objekt
Získá <xref:System.Web.HttpResponse> objekt přidružený k <xref:System.Web.UI.Page>. Tento objekt umožňuje odeslat data odpovědi HTTP do klienta a obsahuje informace o této odpovědi.  
  
## <a name="remarks"></a>Poznámky  
 `My.Response` Objekt obsahuje aktuální <xref:System.Web.HttpResponse> objekt přidružený k stránky.  
  
 `My.Response` Objektu je dostupná jenom pro aplikace ASP.NET.  
  
## <a name="example"></a>Příklad  
 Následující příklad získá kolekci hlaviček z `My.Request` a použije `My.Response` objekt k zápisu na stránku ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Web.HttpResponse>
- [Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
