---
title: My.Request – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 38f510e2a3958761b902f37760069aa8d595ea8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372424"
---
# <a name="myrequest-object"></a><span data-ttu-id="ce20b-102">My.Request – objekt</span><span class="sxs-lookup"><span data-stu-id="ce20b-102">My.Request Object</span></span>
<span data-ttu-id="ce20b-103">Získá <xref:System.Web.HttpRequest> objekt pro požadovanou stránku.</span><span class="sxs-lookup"><span data-stu-id="ce20b-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce20b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce20b-104">Remarks</span></span>  
 <span data-ttu-id="ce20b-105">`My.Request`Objekt obsahuje informace o aktuálním požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce20b-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="ce20b-106">`My.Request`Objekt je k dispozici pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce20b-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce20b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce20b-107">Example</span></span>  
 <span data-ttu-id="ce20b-108">Následující příklad získá kolekci hlaviček z `My.Request` objektu a použije `My.Response` objekt k jeho zápisu na stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce20b-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ce20b-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce20b-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="ce20b-110">My.Response – objekt</span><span class="sxs-lookup"><span data-stu-id="ce20b-110">My.Response Object</span></span>](my-response-object.md)
