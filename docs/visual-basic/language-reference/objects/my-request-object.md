---
title: "My.Request – objekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0e67c8fd85860eacc57bcc7dd7f15f97097efe3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="myrequest-object"></a><span data-ttu-id="51c5c-102">My.Request – objekt</span><span class="sxs-lookup"><span data-stu-id="51c5c-102">My.Request Object</span></span>
<span data-ttu-id="51c5c-103">Získá <xref:System.Web.HttpRequest> objekt pro požadovanou stránku.</span><span class="sxs-lookup"><span data-stu-id="51c5c-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51c5c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51c5c-104">Remarks</span></span>  
 <span data-ttu-id="51c5c-105">`My.Request` Objekt obsahuje informace o aktuální žádosti HTTP.</span><span class="sxs-lookup"><span data-stu-id="51c5c-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="51c5c-106">`My.Request` Objekt je k dispozici pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="51c5c-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51c5c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="51c5c-107">Example</span></span>  
 <span data-ttu-id="51c5c-108">Následující příklad získá kolekci hlaviček z `My.Request` objekt a používá `My.Response` objekt zapisovat na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="51c5c-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="51c5c-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="51c5c-109">See Also</span></span>  
 <xref:System.Web.HttpRequest>  
 [<span data-ttu-id="51c5c-110">My.Response – objekt</span><span class="sxs-lookup"><span data-stu-id="51c5c-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
