---
title: My. Request – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: da17872acb839cdcdfa7f80c3f58f26dc25d0ab5
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567472"
---
# <a name="myrequest-object"></a>My.Request – objekt
<xref:System.Web.HttpRequest> Získá objekt pro požadovanou stránku.  
  
## <a name="remarks"></a>Poznámky  
 `My.Request` Objekt obsahuje informace o aktuálním požadavku HTTP.  
  
 `My.Request` Objekt je k dispozici pouze pro aplikace ASP.NET.  
  
## <a name="example"></a>Příklad  
 Následující příklad získá kolekci hlaviček z `My.Request` objektu a `My.Response` použije objekt k jeho zápisu na stránku ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Web.HttpRequest>
- [Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
