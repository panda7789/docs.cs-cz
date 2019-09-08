---
title: Rozšíření WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 037182a3cb105f544e15a05f955c142ba57f62f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795535"
---
# <a name="extending-wcf"></a><span data-ttu-id="8a36c-102">Rozšíření WCF</span><span class="sxs-lookup"><span data-stu-id="8a36c-102">Extending WCF</span></span>
<span data-ttu-id="8a36c-103">Windows Communication Foundation (WCF) umožňuje upravit a roztáhnout komponenty doby běhu pro přesné řízení a rozšiřování aplikací založených na službách.</span><span class="sxs-lookup"><span data-stu-id="8a36c-103">Windows Communication Foundation (WCF) allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="8a36c-104">Témata v této části se podrobněji týkají architektury rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="8a36c-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="8a36c-105">Další informace o základním programování naleznete v tématu [Základní programování WCF](../basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="8a36c-105">For more information about basic programming, see [Basic WCF Programming](../basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a36c-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8a36c-106">In This Section</span></span>  
 [<span data-ttu-id="8a36c-107">Rozšíření ServiceHost a vrstva modelu služby</span><span class="sxs-lookup"><span data-stu-id="8a36c-107">Extending ServiceHost and the Service Model Layer</span></span>](extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="8a36c-108">Vrstva modelu služby zodpovídá za příjem příchozích zpráv ze základních kanálů, jejich překlad na vyvolání metod v kódu aplikace a odesílání výsledků zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="8a36c-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="8a36c-109">Rozšíření modelu služby mění nebo implementují chování a funkce pro komunikaci, včetně funkcí dispečerů, vlastního chování, zachycení zpráv a parametrů a dalších funkcí rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="8a36c-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="8a36c-110">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="8a36c-110">Extending Bindings</span></span>](extending-bindings.md)  
 <span data-ttu-id="8a36c-111">Vazby jsou objekty, které popisují údaje o komunikaci požadované pro připojení ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="8a36c-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="8a36c-112">Rozšíření vazby nebo vlastní vazby implementují vlastní komunikační funkce vyžadované pro podporu funkcí aplikace.</span><span class="sxs-lookup"><span data-stu-id="8a36c-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="8a36c-113">Rozšíření vrstvy kanálu</span><span class="sxs-lookup"><span data-stu-id="8a36c-113">Extending the Channel Layer</span></span>](extending-the-channel-layer.md)  
 <span data-ttu-id="8a36c-114">Vrstva kanálu je umístěná pod vrstvou modelu služby a zodpovídá za výměnu zpráv mezi klienty a službami.</span><span class="sxs-lookup"><span data-stu-id="8a36c-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="8a36c-115">Rozšíření kanálů můžou implementovat nové funkce protokolu, jako je zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8a36c-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="8a36c-116">Rozšíření kanálů také přenosové funkce, jako je například implementace nového síťového přenosu, který bude obsahovat zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8a36c-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="8a36c-117">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8a36c-117">Extending Security</span></span>](extending-security.md)  
 <span data-ttu-id="8a36c-118">Zabezpečení ve službě WCF se skládá z bezpečnostních přenosů (integrity, důvěrnosti a ověřování), řízení přístupu (autorizace) a auditování.</span><span class="sxs-lookup"><span data-stu-id="8a36c-118">Security in WCF consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="8a36c-119">Třídy nalezené v `IdentityModel` oboru názvů jsou používány WCF pro řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="8a36c-119">The classes found in the `IdentityModel` namespace are used by WCF for access control.</span></span> <span data-ttu-id="8a36c-120">Princip architektury zabezpečení vám umožní vytvořit vlastní typy deklarací identity, které budou vyhovovat vlastním systémům řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="8a36c-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="8a36c-121">Rozšíření systému metadat</span><span class="sxs-lookup"><span data-stu-id="8a36c-121">Extending the Metadata System</span></span>](extending-the-metadata-system.md)  
 <span data-ttu-id="8a36c-122">Systém metadat WCF je skupina tříd a rozhraní, která reprezentují metadata potřebná k implementaci aplikací založených na službách.</span><span class="sxs-lookup"><span data-stu-id="8a36c-122">The WCF metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="8a36c-123">Upravte nebo rozšíříte třídy nebo implementujte a konfigurujte rozhraní pro export a import vlastních metadat, jako jsou rozšíření jazyka WSDL (Web Services Description Language) nebo vlastní kontrolní výrazy WS-PolicyAttachments.</span><span class="sxs-lookup"><span data-stu-id="8a36c-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="8a36c-124">Rozšiřování kodérů a serializátorů</span><span class="sxs-lookup"><span data-stu-id="8a36c-124">Extending Encoders and Serializers</span></span>](extending-encoders-and-serializers.md)  
 <span data-ttu-id="8a36c-125">Kodéry a serializátory převádějí data z jednoho formuláře do druhého.</span><span class="sxs-lookup"><span data-stu-id="8a36c-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="8a36c-126">Témata v této části popisují, jak tyto třídy rozšíříte tak, aby splňovaly speciální požadavky.</span><span class="sxs-lookup"><span data-stu-id="8a36c-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8a36c-127">Reference</span><span class="sxs-lookup"><span data-stu-id="8a36c-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="8a36c-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8a36c-128">Related Sections</span></span>  
 [<span data-ttu-id="8a36c-129">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="8a36c-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="8a36c-130">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="8a36c-130">WCF Feature Details</span></span>](../feature-details/index.md)  
  
 [<span data-ttu-id="8a36c-131">Pokyny a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="8a36c-131">Guidelines and Best Practices</span></span>](../guidelines-and-best-practices.md)
