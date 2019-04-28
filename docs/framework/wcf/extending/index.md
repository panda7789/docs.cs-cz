---
title: Rozšíření WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 24ad74f04a3ac31d0b0d0d87f0d74f88c0521f50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768716"
---
# <a name="extending-wcf"></a><span data-ttu-id="d43a8-102">Rozšíření WCF</span><span class="sxs-lookup"><span data-stu-id="d43a8-102">Extending WCF</span></span>
<span data-ttu-id="d43a8-103">Windows Communication Foundation (WCF) umožňuje upravit a rozšířit komponenty běhu lze přesně řídit a rozšířit aplikace založené na službách.</span><span class="sxs-lookup"><span data-stu-id="d43a8-103">Windows Communication Foundation (WCF) allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="d43a8-104">Témata v této části přejděte do hloubky o architektuře rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="d43a8-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="d43a8-105">Další informace o základní programování naleznete v tématu [základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="d43a8-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d43a8-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d43a8-106">In This Section</span></span>  
 [<span data-ttu-id="d43a8-107">Rozšíření ServiceHost a vrstva modelu služby</span><span class="sxs-lookup"><span data-stu-id="d43a8-107">Extending ServiceHost and the Service Model Layer</span></span>](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="d43a8-108">Vrstva modelu služby je zodpovědná za přesun příchozí zprávy z podkladové kanály, překládá na volání metod v kódu aplikace a odesílá výsledky zpět do volajícího.</span><span class="sxs-lookup"><span data-stu-id="d43a8-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="d43a8-109">Rozšíření modelů služeb změnit nebo implementovat provádění nebo chování komunikace a funkce zahrnující dispečer funkce, vlastní chování, zpráv a parametr zachycení a další funkce rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d43a8-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="d43a8-110">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="d43a8-110">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 <span data-ttu-id="d43a8-111">Vazby jsou objekty, které popisují podrobnosti o komunikaci požadované pro připojení na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d43a8-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="d43a8-112">Rozšíření vazby nebo vlastních vazeb implementovat vlastní komunikační funkce potřebné k podpoře funkce aplikace.</span><span class="sxs-lookup"><span data-stu-id="d43a8-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="d43a8-113">Rozšíření vrstvy kanálu</span><span class="sxs-lookup"><span data-stu-id="d43a8-113">Extending the Channel Layer</span></span>](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 <span data-ttu-id="d43a8-114">Vrstvy kanálu umístěná pod vrstva modelu služby a je zodpovědný za výměnu zpráv mezi klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="d43a8-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="d43a8-115">Rozšíření kanálu můžete implementovat nové funkce protokolu, jako je zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d43a8-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="d43a8-116">Rozšíření kanál přenosu také funkce, jako je například implementace nového síťového přenosu přenášet zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d43a8-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="d43a8-117">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d43a8-117">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
 <span data-ttu-id="d43a8-118">Zabezpečení ve službě WCF se skládá z přenosu zabezpečení (integrity, utajení a ověřování), řízení přístupu (autorizace) a auditování.</span><span class="sxs-lookup"><span data-stu-id="d43a8-118">Security in WCF consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="d43a8-119">Třídy součástí `IdentityModel` oboru názvů používají WCF pro řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="d43a8-119">The classes found in the `IdentityModel` namespace are used by WCF for access control.</span></span> <span data-ttu-id="d43a8-120">Pochopení architektury zabezpečení umožňuje vytvoření vlastní deklarace typů tak, aby vyhovovaly systémy řízení přístupu vlastní.</span><span class="sxs-lookup"><span data-stu-id="d43a8-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="d43a8-121">Rozšíření systému metadat</span><span class="sxs-lookup"><span data-stu-id="d43a8-121">Extending the Metadata System</span></span>](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 <span data-ttu-id="d43a8-122">Metadata systému WCF je skupina třídy a rozhraní, které představují metadata jsou požadovaná k implementaci aplikací založené na službách.</span><span class="sxs-lookup"><span data-stu-id="d43a8-122">The WCF metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="d43a8-123">Upravit nebo rozšířit třídy nebo implementovat a nakonfigurovat rozhraní pro export a import vlastních metadat – například rozšíření webové služby WSDL (Description Language) nebo vlastní WS-PolicyAttachments kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="d43a8-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="d43a8-124">Rozšiřování kodérů a serializátorů</span><span class="sxs-lookup"><span data-stu-id="d43a8-124">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 <span data-ttu-id="d43a8-125">Kodérů a serializátorů přeložit data z jednoho formuláře.</span><span class="sxs-lookup"><span data-stu-id="d43a8-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="d43a8-126">Témata v této části popíšeme, jak rozšířit zadané třídy zvláštní požadavky.</span><span class="sxs-lookup"><span data-stu-id="d43a8-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d43a8-127">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d43a8-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="d43a8-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d43a8-128">Related Sections</span></span>  
 [<span data-ttu-id="d43a8-129">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="d43a8-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="d43a8-130">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="d43a8-130">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="d43a8-131">Pokyny a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="d43a8-131">Guidelines and Best Practices</span></span>](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
