---
title: My.Request – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 22329bc501c9bb75b1336dd5384ab5b23a98ac21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350680"
---
# <a name="myrequest-object"></a>My.Request – objekt
Získá objekt <xref:System.Web.HttpRequest> pro požadovanou stránku.  
  
## <a name="remarks"></a>Poznámky  
 Objekt `My.Request` obsahuje informace o aktuálním požadavku HTTP.  
  
 Objekt `My.Request` je k dispozici pouze pro aplikace ASP.NET.  
  
## <a name="example"></a>Příklad  
 Následující příklad získá kolekci hlaviček z objektu `My.Request` a pomocí objektu `My.Response` jej zapíše na stránku ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Web.HttpRequest>
- [Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
