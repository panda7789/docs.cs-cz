---
title: My.Response – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: d5f49529a2593093a234babc22f64b591ea3cc61
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45513986"
---
# <a name="myresponse-object"></a><span data-ttu-id="d2793-102">My.Response – objekt</span><span class="sxs-lookup"><span data-stu-id="d2793-102">My.Response Object</span></span>
<span data-ttu-id="d2793-103">Získá <xref:System.Web.HttpResponse> objekt přidružený k <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="d2793-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="d2793-104">Tento objekt umožňuje odeslat data odpovědi HTTP do klienta a obsahuje informace o této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d2793-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2793-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2793-105">Remarks</span></span>  
 <span data-ttu-id="d2793-106">`My.Response` Objekt obsahuje aktuální <xref:System.Web.HttpResponse> objekt přidružený k stránky.</span><span class="sxs-lookup"><span data-stu-id="d2793-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="d2793-107">`My.Response` Objektu je dostupná jenom pro [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="d2793-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2793-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2793-108">Example</span></span>  
 <span data-ttu-id="d2793-109">Následující příklad získá kolekci hlaviček z `My.Request` a použije `My.Response` objekt k zápisu na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d2793-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="d2793-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2793-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="d2793-111">Objekt My.Request</span><span class="sxs-lookup"><span data-stu-id="d2793-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
