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
ms.openlocfilehash: 292892ef572bd63fff055aeed88073573fadb934
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491839"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="3399f-102">Integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="3399f-102">Integrating with COM Applications</span></span>
<span data-ttu-id="3399f-103">Služby Windows Communication Foundation (WCF) lze integrovat přímo do váš stávající kód za použití monikeru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="3399f-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="3399f-104">Monikeru služby lze použít z celý na základě rozsahu COM vývojových prostředí, například Office VBA, Visual Basic 6.0 nebo Visual C++ verze 6.0.</span><span class="sxs-lookup"><span data-stu-id="3399f-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3399f-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3399f-105">In This Section</span></span>  
 [<span data-ttu-id="3399f-106">Přehled integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="3399f-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="3399f-107">Poskytuje přehled hlavních součástí procesu integrace.</span><span class="sxs-lookup"><span data-stu-id="3399f-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="3399f-108">Postupy: Registrace a konfigurace monikeru služby</span><span class="sxs-lookup"><span data-stu-id="3399f-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="3399f-109">Použití monikeru služby WCF v rámci aplikace modelu COM, zaregistrujte požadované s atributy typy v modelu COM a nakonfigurujte aplikaci COM a moniker s konfigurací požadovaná vazba.</span><span class="sxs-lookup"><span data-stu-id="3399f-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="3399f-110">Postupy: Použití monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="3399f-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="3399f-111">Vysvětluje, jak získat definici kontraktu ve formě dokumentu definice jazyka WSDL (Web Services) nebo z koncového bodu WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="3399f-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="3399f-112">Postupy: Použití monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="3399f-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="3399f-113">Popisuje, jak volat ukázku WCF pomocí Přezdívka WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="3399f-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="3399f-114">Postupy: Použití monikeru služby u kontraktů výměny metadat</span><span class="sxs-lookup"><span data-stu-id="3399f-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="3399f-115">Popisuje, jak volat ukázku WCF pomocí Přezdívka WCF, který určuje koncový bod Mex.</span><span class="sxs-lookup"><span data-stu-id="3399f-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="3399f-116">Postupy: Určení přihlašovacích údajů pro zabezpečení kanálu</span><span class="sxs-lookup"><span data-stu-id="3399f-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="3399f-117">Podporuje monikeru služby WCF `IChannelCredentials` rozhraní, které umožňuje řadu alternativní metody pro zadání přihlašovacích údajů kanálu.</span><span class="sxs-lookup"><span data-stu-id="3399f-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3399f-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="3399f-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="3399f-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3399f-119">See Also</span></span>  
 [<span data-ttu-id="3399f-120">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="3399f-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
