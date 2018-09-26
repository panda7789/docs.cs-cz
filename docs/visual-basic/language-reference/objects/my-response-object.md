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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071631"
---
# <a name="myresponse-object"></a><span data-ttu-id="a6716-102">My.Response – objekt</span><span class="sxs-lookup"><span data-stu-id="a6716-102">My.Response Object</span></span>
<span data-ttu-id="a6716-103">Získá <xref:System.Web.HttpResponse> objekt přidružený k <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="a6716-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="a6716-104">Tento objekt umožňuje odeslat data odpovědi HTTP do klienta a obsahuje informace o této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a6716-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6716-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6716-105">Remarks</span></span>  
 <span data-ttu-id="a6716-106">`My.Response` Objekt obsahuje aktuální <xref:System.Web.HttpResponse> objekt přidružený k stránky.</span><span class="sxs-lookup"><span data-stu-id="a6716-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="a6716-107">`My.Response` Objektu je dostupná jenom pro [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="a6716-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6716-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6716-108">Example</span></span>  
 <span data-ttu-id="a6716-109">Následující příklad získá kolekci hlaviček z `My.Request` a použije `My.Response` objekt k zápisu na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a6716-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="a6716-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6716-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="a6716-111">Objekt My.Request</span><span class="sxs-lookup"><span data-stu-id="a6716-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
