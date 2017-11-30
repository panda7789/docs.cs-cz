---
title: "Přístup k aplikačním webovým službám (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f15c0fd761f08f41abc05f7019ce27bc8cf8dff3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="5de56-102">Přístup k aplikačním webovým službám (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5de56-102">Accessing Application Web Services (Visual Basic)</span></span>
<span data-ttu-id="5de56-103">`My.WebServices` Objekt poskytuje instanci každé webové služby odkazuje v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="5de56-103">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="5de56-104">Každá instance je vytvořena na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="5de56-104">Each instance is instantiated on demand.</span></span> <span data-ttu-id="5de56-105">Tyto webové služby můžete přistupovat prostřednictvím vlastnosti `My.WebServices` objektu.</span><span class="sxs-lookup"><span data-stu-id="5de56-105">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="5de56-106">Název vlastnosti je stejný jako název webové služby, který má přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5de56-106">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="5de56-107">Všechny třídy, která dědí z <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> je webová služba.</span><span class="sxs-lookup"><span data-stu-id="5de56-107">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="5de56-108">Úlohy</span><span class="sxs-lookup"><span data-stu-id="5de56-108">Tasks</span></span>  
 <span data-ttu-id="5de56-109">Následující tabulka uvádí možné způsoby, jak pro přístup k webovým službám odkazuje aplikace.</span><span class="sxs-lookup"><span data-stu-id="5de56-109">The following table lists possible ways to access Web services referenced by an application.</span></span>  
  
|<span data-ttu-id="5de56-110">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="5de56-110">To</span></span>|<span data-ttu-id="5de56-111">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="5de56-111">See</span></span>|  
|---|---|   
|<span data-ttu-id="5de56-112">Volání webové služby</span><span class="sxs-lookup"><span data-stu-id="5de56-112">Call a Web service</span></span>|[<span data-ttu-id="5de56-113">My.WebServices – objekt</span><span class="sxs-lookup"><span data-stu-id="5de56-113">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)|  
|<span data-ttu-id="5de56-114">Asynchronní volání webové služby a zpracování události po dokončení</span><span class="sxs-lookup"><span data-stu-id="5de56-114">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="5de56-115">Postupy: asynchronní volání webové služby</span><span class="sxs-lookup"><span data-stu-id="5de56-115">How to: Call a Web Service Asynchronously</span></span>](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|  
  
## <a name="see-also"></a><span data-ttu-id="5de56-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5de56-116">See Also</span></span>  
 [<span data-ttu-id="5de56-117">My.WebServices – objekt</span><span class="sxs-lookup"><span data-stu-id="5de56-117">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
