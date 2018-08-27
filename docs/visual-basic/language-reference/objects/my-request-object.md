---
title: My.Request – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: f2c43afb723944293907d0efbb4cf3cc66a40e1e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932547"
---
# <a name="myrequest-object"></a><span data-ttu-id="f1896-102">My.Request – objekt</span><span class="sxs-lookup"><span data-stu-id="f1896-102">My.Request Object</span></span>
<span data-ttu-id="f1896-103">Získá <xref:System.Web.HttpRequest> objekt pro požadovanou stránku.</span><span class="sxs-lookup"><span data-stu-id="f1896-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1896-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1896-104">Remarks</span></span>  
 <span data-ttu-id="f1896-105">`My.Request` Objekt obsahuje informace o aktuální žádosti HTTP.</span><span class="sxs-lookup"><span data-stu-id="f1896-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="f1896-106">`My.Request` Objekt je k dispozici pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f1896-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1896-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1896-107">Example</span></span>  
 <span data-ttu-id="f1896-108">Následující příklad získá kolekci hlaviček z `My.Request` a použije `My.Response` objekt k zápisu na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f1896-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="f1896-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1896-109">See Also</span></span>  
 <xref:System.Web.HttpRequest>  
 [<span data-ttu-id="f1896-110">Objekt My.Response</span><span class="sxs-lookup"><span data-stu-id="f1896-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
