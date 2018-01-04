---
title: Integrace s aplikacemi modelu COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 130a7cda170721f34a5b44f3361bd591d6375267
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="9c1a5-102">Integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="9c1a5-102">Integrating with COM Applications</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="9c1a5-103">služby lze integrovat přímo do existujícího kódu pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] monikeru služby.</span><span class="sxs-lookup"><span data-stu-id="9c1a5-103"> services can be integrated directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="9c1a5-104">Monikeru služby lze použít z celý na základě rozsahu COM vývojových prostředí, například Office VBA, Visual Basic 6.0 nebo Visual C++ verze 6.0.</span><span class="sxs-lookup"><span data-stu-id="9c1a5-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c1a5-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9c1a5-105">In This Section</span></span>  
 [<span data-ttu-id="9c1a5-106">Přehled integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="9c1a5-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="9c1a5-107">Poskytuje přehled hlavních součástí procesu integrace.</span><span class="sxs-lookup"><span data-stu-id="9c1a5-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="9c1a5-108">Postupy: Registrace a konfigurace monikeru služby</span><span class="sxs-lookup"><span data-stu-id="9c1a5-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="9c1a5-109">Použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby Přezdívka v rámci aplikace modelu COM, požadované s atributy typy zaregistrovat u modelu COM a konfiguraci aplikace modelu COM a Přezdívka s konfigurací požadovaná vazba.</span><span class="sxs-lookup"><span data-stu-id="9c1a5-109">To use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="9c1a5-110">Postupy: Použití monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="9c1a5-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="9c1a5-111">Vysvětluje, jak získat definici kontraktu ve formě dokumentu definice jazyka WSDL (Web Services) nebo z koncového bodu WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="9c1a5-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="9c1a5-112">Postupy: Použití monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="9c1a5-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="9c1a5-113">Popisuje, jak volat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázkové pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přezdívka WSDL.</span><span class="sxs-lookup"><span data-stu-id="9c1a5-113">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL moniker.</span></span>  
  
 [<span data-ttu-id="9c1a5-114">Postupy: Použití monikeru služby u kontraktů výměny metadat</span><span class="sxs-lookup"><span data-stu-id="9c1a5-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="9c1a5-115">Popisuje, jak volat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázkové pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přezdívka, která určuje koncový bod Mex.</span><span class="sxs-lookup"><span data-stu-id="9c1a5-115">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="9c1a5-116">Postupy: Určení přihlašovacích údajů pro zabezpečení kanálu</span><span class="sxs-lookup"><span data-stu-id="9c1a5-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="9c1a5-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Služby podporuje Přezdívka `IChannelCredentials` rozhraní, které umožňuje řadu alternativní metody pro zadání přihlašovacích údajů kanálu.</span><span class="sxs-lookup"><span data-stu-id="9c1a5-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9c1a5-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="9c1a5-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="9c1a5-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c1a5-119">See Also</span></span>  
 [<span data-ttu-id="9c1a5-120">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="9c1a5-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
