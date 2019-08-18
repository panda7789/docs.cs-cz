---
title: My. Response – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: a50701998011c25c600c2a3763459c1aba3cc59a
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567449"
---
# <a name="myresponse-object"></a><span data-ttu-id="b7e79-102">My.Response – objekt</span><span class="sxs-lookup"><span data-stu-id="b7e79-102">My.Response Object</span></span>
<span data-ttu-id="b7e79-103">Získá objekt přidružený k <xref:System.Web.UI.Page>. <xref:System.Web.HttpResponse></span><span class="sxs-lookup"><span data-stu-id="b7e79-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="b7e79-104">Tento objekt umožňuje odeslat data odpovědi HTTP klientovi a obsahuje informace o této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b7e79-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7e79-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7e79-105">Remarks</span></span>  
 <span data-ttu-id="b7e79-106">Objekt obsahuje aktuální <xref:System.Web.HttpResponse> objekt přidružený k této stránce. `My.Response`</span><span class="sxs-lookup"><span data-stu-id="b7e79-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="b7e79-107">`My.Response` Objekt je k dispozici pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b7e79-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7e79-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7e79-108">Example</span></span>  
 <span data-ttu-id="b7e79-109">Následující příklad získá kolekci hlaviček z `My.Request` objektu a `My.Response` použije objekt k jeho zápisu na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b7e79-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b7e79-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7e79-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="b7e79-111">Objekt My.Request</span><span class="sxs-lookup"><span data-stu-id="b7e79-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
