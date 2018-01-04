---
title: "Rozšíření WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c84f25dfd5d3066f9c5d0b62bc0b28bc98c283d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="extending-wcf"></a><span data-ttu-id="c4b81-102">Rozšíření WCF</span><span class="sxs-lookup"><span data-stu-id="c4b81-102">Extending WCF</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="c4b81-103">Umožňuje upravit a rozšířit běhu součásti přesněji řídit a rozšířit aplikace založené na služby.</span><span class="sxs-lookup"><span data-stu-id="c4b81-103"> allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="c4b81-104">Témata v této části najdete podrobněji o architektuře rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c4b81-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="c4b81-105">Další informace o základní programování najdete v tématu [základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="c4b81-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4b81-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c4b81-106">In This Section</span></span>  
 [<span data-ttu-id="c4b81-107">Rozšíření ServiceHost a vrstva modelu služby</span><span class="sxs-lookup"><span data-stu-id="c4b81-107">Extending ServiceHost and the Service Model Layer</span></span>](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="c4b81-108">Vrstva modelu služby je zodpovědná za stahování příchozí zprávy mimo základní kanály, převedena do volání metod v kódu aplikace a odesílání výsledky zpět k volajícímu.</span><span class="sxs-lookup"><span data-stu-id="c4b81-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="c4b81-109">Rozšíření modelů služby upravit nebo jsou implementovány provádění nebo komunikace chování a funkce zahrnující dispečera funkce, vlastní chování, zprávu a parametr zachycení a další funkce rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="c4b81-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="c4b81-110">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="c4b81-110">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 <span data-ttu-id="c4b81-111">Vazby jsou objekty, které popisují podrobnosti komunikace požadované pro připojení ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="c4b81-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="c4b81-112">Vazba rozšíření nebo vlastní vazby implementovat vlastní komunikaci funkce potřebné k podpoře funkce aplikací.</span><span class="sxs-lookup"><span data-stu-id="c4b81-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="c4b81-113">Rozšíření vrstvy kanálu</span><span class="sxs-lookup"><span data-stu-id="c4b81-113">Extending the Channel Layer</span></span>](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 <span data-ttu-id="c4b81-114">Vrstvy kanálu je umístěna pod vrstva modelu služby a je odpovědná za výměny zpráv mezi klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="c4b81-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="c4b81-115">Kanál rozšíření můžete implementovat nové funkce protokolu, například zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c4b81-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="c4b81-116">Rozšíření kanál také přenosu funkce, například implementace nový síťový přenos pro přenos protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="c4b81-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="c4b81-117">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c4b81-117">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
 <span data-ttu-id="c4b81-118">Zabezpečení v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se skládá z zabezpečení přenosu (integrity, důvěrnost a ověřování), řízení přístupu (autorizace) a auditování.</span><span class="sxs-lookup"><span data-stu-id="c4b81-118">Security in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="c4b81-119">Třídy v nalezen `IdentityModel` oboru názvů používají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pro řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="c4b81-119">The classes found in the `IdentityModel` namespace are used by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] for access control.</span></span> <span data-ttu-id="c4b81-120">Principy zabezpečení architektura umožňuje vytvořit typy vlastních deklarací identity pro přizpůsobení systémy kontroly vlastní přístup.</span><span class="sxs-lookup"><span data-stu-id="c4b81-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="c4b81-121">Rozšíření systému metadat</span><span class="sxs-lookup"><span data-stu-id="c4b81-121">Extending the Metadata System</span></span>](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 <span data-ttu-id="c4b81-122">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Systém metadat je skupina třídy a rozhraní, které představují metadata potřebnou k implementaci aplikace založené na služby.</span><span class="sxs-lookup"><span data-stu-id="c4b81-122">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="c4b81-123">Upravit nebo rozšíření třídy nebo implementovat a nakonfigurovat rozhraní pro export a import vlastních metadat, jako je například rozšíření webové služby popis Language (WSDL) nebo vlastní WS-PolicyAttachments kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="c4b81-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="c4b81-124">Rozšiřování kodérů a serializátorů</span><span class="sxs-lookup"><span data-stu-id="c4b81-124">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 <span data-ttu-id="c4b81-125">Kodérů a serializátorů převede data z jednoho formátu do jiného.</span><span class="sxs-lookup"><span data-stu-id="c4b81-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="c4b81-126">Témata v této části popisují, jak rozšířit zadané třídy zvláštních požadavků.</span><span class="sxs-lookup"><span data-stu-id="c4b81-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c4b81-127">Odkaz</span><span class="sxs-lookup"><span data-stu-id="c4b81-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="c4b81-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c4b81-128">Related Sections</span></span>  
 [<span data-ttu-id="c4b81-129">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="c4b81-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="c4b81-130">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="c4b81-130">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="c4b81-131">Pokyny a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="c4b81-131">Guidelines and Best Practices</span></span>](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
