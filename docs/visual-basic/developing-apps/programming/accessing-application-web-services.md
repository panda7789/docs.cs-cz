---
title: Přístup k aplikačním webovým službám
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: ad616bd46f92261ec5ad6ae81d0db48138631ed1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349228"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="a6a59-102">Přístup k aplikačním webovým službám (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6a59-102">Accessing Application Web Services (Visual Basic)</span></span>

<span data-ttu-id="a6a59-103">Objekt `My.WebServices` poskytuje instanci každé webové služby, na kterou odkazuje aktuální projekt.</span><span class="sxs-lookup"><span data-stu-id="a6a59-103">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="a6a59-104">Každá instance je vytvořena na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="a6a59-104">Each instance is instantiated on demand.</span></span> <span data-ttu-id="a6a59-105">K těmto webovým službám můžete přistupovat prostřednictvím vlastností objektu `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="a6a59-105">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="a6a59-106">Název vlastnosti je stejný jako název webové služby, ke které vlastnost přistupuje.</span><span class="sxs-lookup"><span data-stu-id="a6a59-106">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="a6a59-107">Libovolná třída, která dědí z <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> je webová služba.</span><span class="sxs-lookup"><span data-stu-id="a6a59-107">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>

## <a name="tasks"></a><span data-ttu-id="a6a59-108">Tasks</span><span class="sxs-lookup"><span data-stu-id="a6a59-108">Tasks</span></span>

<span data-ttu-id="a6a59-109">V následující tabulce jsou uvedeny možné způsoby přístupu k webovým službám, na které odkazuje aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6a59-109">The following table lists possible ways to access Web services referenced by an application.</span></span>

|<span data-ttu-id="a6a59-110">Pro</span><span class="sxs-lookup"><span data-stu-id="a6a59-110">To</span></span>|<span data-ttu-id="a6a59-111">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="a6a59-111">See</span></span>|
|---|---|
|<span data-ttu-id="a6a59-112">Volání webové služby</span><span class="sxs-lookup"><span data-stu-id="a6a59-112">Call a Web service</span></span>|[<span data-ttu-id="a6a59-113">Objekt My.WebServices</span><span class="sxs-lookup"><span data-stu-id="a6a59-113">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)|
|<span data-ttu-id="a6a59-114">Asynchronní volání webové služby a zpracování události při jejím dokončení</span><span class="sxs-lookup"><span data-stu-id="a6a59-114">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="a6a59-115">Postupy: Asynchronní volání webové služby</span><span class="sxs-lookup"><span data-stu-id="a6a59-115">How to: Call a Web Service Asynchronously</span></span>](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|

## <a name="see-also"></a><span data-ttu-id="a6a59-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6a59-116">See also</span></span>

- [<span data-ttu-id="a6a59-117">Objekt My.WebServices</span><span class="sxs-lookup"><span data-stu-id="a6a59-117">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
