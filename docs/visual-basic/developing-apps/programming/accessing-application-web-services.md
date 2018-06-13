---
title: Přístup k aplikačním webovým službám (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: b1d5a2166ace2ea16e1764139133457439675876
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583731"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="bb8be-102">Přístup k aplikačním webovým službám (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb8be-102">Accessing Application Web Services (Visual Basic)</span></span>
<span data-ttu-id="bb8be-103">`My.WebServices` Objekt poskytuje instanci každé webové služby odkazuje v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="bb8be-103">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="bb8be-104">Každá instance je vytvořena na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="bb8be-104">Each instance is instantiated on demand.</span></span> <span data-ttu-id="bb8be-105">Tyto webové služby můžete přistupovat prostřednictvím vlastnosti `My.WebServices` objektu.</span><span class="sxs-lookup"><span data-stu-id="bb8be-105">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="bb8be-106">Název vlastnosti je stejný jako název webové služby, který má přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bb8be-106">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="bb8be-107">Všechny třídy, která dědí z <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> je webová služba.</span><span class="sxs-lookup"><span data-stu-id="bb8be-107">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="bb8be-108">Úlohy</span><span class="sxs-lookup"><span data-stu-id="bb8be-108">Tasks</span></span>  
 <span data-ttu-id="bb8be-109">Následující tabulka uvádí možné způsoby, jak pro přístup k webovým službám odkazuje aplikace.</span><span class="sxs-lookup"><span data-stu-id="bb8be-109">The following table lists possible ways to access Web services referenced by an application.</span></span>  
  
|<span data-ttu-id="bb8be-110">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="bb8be-110">To</span></span>|<span data-ttu-id="bb8be-111">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="bb8be-111">See</span></span>|  
|---|---|   
|<span data-ttu-id="bb8be-112">Volání webové služby</span><span class="sxs-lookup"><span data-stu-id="bb8be-112">Call a Web service</span></span>|[<span data-ttu-id="bb8be-113">Objekt My.WebServices</span><span class="sxs-lookup"><span data-stu-id="bb8be-113">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)|  
|<span data-ttu-id="bb8be-114">Asynchronní volání webové služby a zpracování události po dokončení</span><span class="sxs-lookup"><span data-stu-id="bb8be-114">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="bb8be-115">Postupy: Asynchronní volání webové služby</span><span class="sxs-lookup"><span data-stu-id="bb8be-115">How to: Call a Web Service Asynchronously</span></span>](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|  
  
## <a name="see-also"></a><span data-ttu-id="bb8be-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb8be-116">See Also</span></span>  
 [<span data-ttu-id="bb8be-117">Objekt My.WebServices</span><span class="sxs-lookup"><span data-stu-id="bb8be-117">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
