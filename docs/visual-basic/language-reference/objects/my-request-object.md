---
title: My.Request – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 38f510e2a3958761b902f37760069aa8d595ea8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372424"
---
# <a name="myrequest-object"></a>My.Request – objekt
Získá <xref:System.Web.HttpRequest> objekt pro požadovanou stránku.  
  
## <a name="remarks"></a>Poznámky  
 `My.Request`Objekt obsahuje informace o aktuálním požadavku HTTP.  
  
 `My.Request`Objekt je k dispozici pouze pro aplikace ASP.NET.  
  
## <a name="example"></a>Příklad  
 Následující příklad získá kolekci hlaviček z `My.Request` objektu a použije `My.Response` objekt k jeho zápisu na stránku ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Web.HttpRequest>
- [My.Response – objekt](my-response-object.md)
