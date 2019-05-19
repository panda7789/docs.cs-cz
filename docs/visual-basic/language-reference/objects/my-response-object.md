---
title: My.Response – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 0e49a3b5732ee1a3626666ce06e366c4940eca05
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881967"
---
# <a name="myresponse-object"></a><span data-ttu-id="e8d1f-102">My.Response – objekt</span><span class="sxs-lookup"><span data-stu-id="e8d1f-102">My.Response Object</span></span>
<span data-ttu-id="e8d1f-103">Získá <xref:System.Web.HttpResponse> objekt přidružený k <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="e8d1f-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="e8d1f-104">Tento objekt umožňuje odeslat data odpovědi HTTP do klienta a obsahuje informace o této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e8d1f-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8d1f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8d1f-105">Remarks</span></span>  
 <span data-ttu-id="e8d1f-106">`My.Response` Objekt obsahuje aktuální <xref:System.Web.HttpResponse> objekt přidružený k stránky.</span><span class="sxs-lookup"><span data-stu-id="e8d1f-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="e8d1f-107">`My.Response` Objektu je dostupná jenom pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e8d1f-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8d1f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8d1f-108">Example</span></span>  
 <span data-ttu-id="e8d1f-109">Následující příklad získá kolekci hlaviček z `My.Request` a použije `My.Response` objekt k zápisu na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e8d1f-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e8d1f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8d1f-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="e8d1f-111">Objekt My.Request</span><span class="sxs-lookup"><span data-stu-id="e8d1f-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
