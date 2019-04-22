---
title: My.Request – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 08212dc5fe563ce84be02ab706b56195a0636894
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836620"
---
# <a name="myrequest-object"></a>My.Request – objekt
Získá <xref:System.Web.HttpRequest> objekt pro požadovanou stránku.  
  
## <a name="remarks"></a>Poznámky  
 `My.Request` Objekt obsahuje informace o aktuální žádosti HTTP.  
  
 `My.Request` Objekt je k dispozici pouze pro aplikace ASP.NET.  
  
## <a name="example"></a>Příklad  
 Následující příklad získá kolekci hlaviček z `My.Request` a použije `My.Response` objekt k zápisu na stránku ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Web.HttpRequest>
- [Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
