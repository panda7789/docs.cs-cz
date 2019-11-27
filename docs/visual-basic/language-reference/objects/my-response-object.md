---
title: My.Response – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 522814ad48fb7548032b8a37779bb3ff6ca62413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350661"
---
# <a name="myresponse-object"></a><span data-ttu-id="49b89-102">My.Response – objekt</span><span class="sxs-lookup"><span data-stu-id="49b89-102">My.Response Object</span></span>
<span data-ttu-id="49b89-103">Získá objekt <xref:System.Web.HttpResponse> přidružený k <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="49b89-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="49b89-104">Tento objekt umožňuje odeslat data odpovědi HTTP klientovi a obsahuje informace o této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="49b89-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49b89-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49b89-105">Remarks</span></span>  
 <span data-ttu-id="49b89-106">Objekt `My.Response` obsahuje aktuální objekt <xref:System.Web.HttpResponse> přidružený k této stránce.</span><span class="sxs-lookup"><span data-stu-id="49b89-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="49b89-107">Objekt `My.Response` je k dispozici pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="49b89-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49b89-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="49b89-108">Example</span></span>  
 <span data-ttu-id="49b89-109">Následující příklad získá kolekci hlaviček z objektu `My.Request` a pomocí objektu `My.Response` jej zapíše na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="49b89-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="49b89-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49b89-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="49b89-111">Objekt My.Request</span><span class="sxs-lookup"><span data-stu-id="49b89-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
