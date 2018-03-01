---
title: "My.Response – objekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76d0e701107add0d5bd468ba7a829759739e0cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="myresponse-object"></a><span data-ttu-id="3ee2f-102">My.Response – objekt</span><span class="sxs-lookup"><span data-stu-id="3ee2f-102">My.Response Object</span></span>
<span data-ttu-id="3ee2f-103">Získá <xref:System.Web.HttpResponse> objekt přidružený k <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="3ee2f-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="3ee2f-104">Tento objekt umožňuje odeslat data odpovědi HTTP do klienta a obsahuje informace o této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="3ee2f-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ee2f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ee2f-105">Remarks</span></span>  
 <span data-ttu-id="3ee2f-106">`My.Response` Objekt obsahuje aktuální <xref:System.Web.HttpResponse> objekt přidružený k stránce.</span><span class="sxs-lookup"><span data-stu-id="3ee2f-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="3ee2f-107">`My.Response` Objektu je k dispozici pouze [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="3ee2f-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ee2f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ee2f-108">Example</span></span>  
 <span data-ttu-id="3ee2f-109">Následující příklad získá kolekci hlaviček z `My.Request` objekt a používá `My.Response` objekt zapisovat na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3ee2f-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="3ee2f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ee2f-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="3ee2f-111">My.Request – objekt</span><span class="sxs-lookup"><span data-stu-id="3ee2f-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
