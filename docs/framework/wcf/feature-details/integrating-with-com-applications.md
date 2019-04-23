---
title: Integrace s aplikacemi modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: 51626da6e97e346f43cfe606a5164024580a2ac7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155321"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="5a8bb-102">Integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="5a8bb-102">Integrating with COM Applications</span></span>
<span data-ttu-id="5a8bb-103">Služby Windows Communication Foundation (WCF) je možné integrovat přímo do vašeho existujícího kódu pomocí monikeru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5a8bb-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="5a8bb-104">Moniker služby je možné z široký rozsah COM vývoj prostředí, jako je například Office VBA, Visual Basic 6.0 nebo Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="5a8bb-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a8bb-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5a8bb-105">In This Section</span></span>  
 [<span data-ttu-id="5a8bb-106">Přehled integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="5a8bb-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="5a8bb-107">Poskytuje přehled hlavních částí procesu integrace.</span><span class="sxs-lookup"><span data-stu-id="5a8bb-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="5a8bb-108">Postupy: Registrace a konfigurace Monikeru služby</span><span class="sxs-lookup"><span data-stu-id="5a8bb-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="5a8bb-109">Použití monikeru služby WCF v rámci aplikace modelu COM, zaregistrujte požadované typy s atributy s modelem COM a konfigurace aplikace COM i Přezdívka pomocí konfigurace požadované vazby.</span><span class="sxs-lookup"><span data-stu-id="5a8bb-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="5a8bb-110">Postupy: Použití Monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="5a8bb-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="5a8bb-111">Vysvětluje, jak získat definici kontraktu ve formě souboru definice jazyka WSDL (Web Services) nebo z koncového bodu WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="5a8bb-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="5a8bb-112">Postupy: Použití Monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="5a8bb-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="5a8bb-113">Popisuje, jak volat Ukázky WCF pomocí monikeru WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="5a8bb-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="5a8bb-114">Postupy: Použití Monikeru služby u kontraktů Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="5a8bb-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="5a8bb-115">Popisuje, jak volat WCF ukázku použití monikeru služby WCF, který určuje koncový bod Mex.</span><span class="sxs-lookup"><span data-stu-id="5a8bb-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="5a8bb-116">Postupy: Určení zabezpečovacích pověření kanálu</span><span class="sxs-lookup"><span data-stu-id="5a8bb-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="5a8bb-117">Podporuje monikeru služby WCF `IChannelCredentials` rozhraní, které umožňuje širokou škálou alternativní metody pro zadání pověření kanálu.</span><span class="sxs-lookup"><span data-stu-id="5a8bb-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5a8bb-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="5a8bb-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="5a8bb-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a8bb-119">See also</span></span>

- [<span data-ttu-id="5a8bb-120">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="5a8bb-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
