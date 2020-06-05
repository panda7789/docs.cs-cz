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
# <a name="myresponse-object"></a><span data-ttu-id="c38f5-102">My.Response – objekt</span><span class="sxs-lookup"><span data-stu-id="c38f5-102">My.Response Object</span></span>
<span data-ttu-id="c38f5-103">Získá <xref:System.Web.HttpResponse> objekt přidružený k <xref:System.Web.UI.Page> .</span><span class="sxs-lookup"><span data-stu-id="c38f5-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="c38f5-104">Tento objekt umožňuje odeslat data odpovědi HTTP klientovi a obsahuje informace o této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="c38f5-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c38f5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c38f5-105">Remarks</span></span>  
 <span data-ttu-id="c38f5-106">`My.Response`Objekt obsahuje aktuální <xref:System.Web.HttpResponse> objekt přidružený k této stránce.</span><span class="sxs-lookup"><span data-stu-id="c38f5-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="c38f5-107">`My.Response`Objekt je k dispozici pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c38f5-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c38f5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c38f5-108">Example</span></span>  
 <span data-ttu-id="c38f5-109">Následující příklad získá kolekci hlaviček z `My.Request` objektu a použije `My.Response` objekt k jeho zápisu na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c38f5-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c38f5-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c38f5-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="c38f5-111">My.Request – objekt</span><span class="sxs-lookup"><span data-stu-id="c38f5-111">My.Request Object</span></span>](my-request-object.md)
