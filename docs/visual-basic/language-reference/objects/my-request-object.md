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
# <a name="myrequest-object"></a><span data-ttu-id="473db-102">My.Request – objekt</span><span class="sxs-lookup"><span data-stu-id="473db-102">My.Request Object</span></span>
<span data-ttu-id="473db-103">Získá objekt <xref:System.Web.HttpRequest> pro požadovanou stránku.</span><span class="sxs-lookup"><span data-stu-id="473db-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="473db-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="473db-104">Remarks</span></span>  
 <span data-ttu-id="473db-105">Objekt `My.Request` obsahuje informace o aktuálním požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="473db-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="473db-106">Objekt `My.Request` je k dispozici pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="473db-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="473db-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="473db-107">Example</span></span>  
 <span data-ttu-id="473db-108">Následující příklad získá kolekci hlaviček z objektu `My.Request` a pomocí objektu `My.Response` jej zapíše na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="473db-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="473db-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="473db-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="473db-110">Objekt My.Response</span><span class="sxs-lookup"><span data-stu-id="473db-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
