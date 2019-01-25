---
title: My.Request – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: a9af211df358b8c87cc9735f05d18c191b49500e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716192"
---
# <a name="myrequest-object"></a>My.Request – objekt
Získá <xref:System.Web.HttpRequest> objekt pro požadovanou stránku.  
  
## <a name="remarks"></a>Poznámky  
 `My.Request` Objekt obsahuje informace o aktuální žádosti HTTP.  
  
 `My.Request` Objekt je k dispozici pouze pro aplikace ASP.NET.  
  
## <a name="example"></a>Příklad  
 Následující příklad získá kolekci hlaviček z `My.Request` a použije `My.Response` objekt k zápisu na stránku ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Web.HttpRequest>
- [Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
