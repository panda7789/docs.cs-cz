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
ms.openlocfilehash: bfe452b41c39598e237633490d09cd267fda04ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="69c80-102">Integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="69c80-102">Integrating with COM Applications</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="69c80-103">služby lze integrovat přímo do existujícího kódu pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] monikeru služby.</span><span class="sxs-lookup"><span data-stu-id="69c80-103"> services can be integrated directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="69c80-104">Monikeru služby lze použít z celý na základě rozsahu COM vývojových prostředí, například Office VBA, Visual Basic 6.0 nebo Visual C++ verze 6.0.</span><span class="sxs-lookup"><span data-stu-id="69c80-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69c80-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="69c80-105">In This Section</span></span>  
 [<span data-ttu-id="69c80-106">Integrace s přehled aplikace modelu COM</span><span class="sxs-lookup"><span data-stu-id="69c80-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="69c80-107">Poskytuje přehled hlavních součástí procesu integrace.</span><span class="sxs-lookup"><span data-stu-id="69c80-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="69c80-108">Postupy: registrace a konfigurace Monikeru služby</span><span class="sxs-lookup"><span data-stu-id="69c80-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="69c80-109">Použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby Přezdívka v rámci aplikace modelu COM, požadované s atributy typy zaregistrovat u modelu COM a konfiguraci aplikace modelu COM a Přezdívka s konfigurací požadovaná vazba.</span><span class="sxs-lookup"><span data-stu-id="69c80-109">To use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="69c80-110">Postupy: použití Monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="69c80-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="69c80-111">Vysvětluje, jak získat definici kontraktu ve formě dokumentu definice jazyka WSDL (Web Services) nebo z koncového bodu WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="69c80-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="69c80-112">Postupy: použití Monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="69c80-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="69c80-113">Popisuje, jak volat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázkové pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přezdívka WSDL.</span><span class="sxs-lookup"><span data-stu-id="69c80-113">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL moniker.</span></span>  
  
 [<span data-ttu-id="69c80-114">Postupy: použití Monikeru služby s kontrakty Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="69c80-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="69c80-115">Popisuje, jak volat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázkové pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přezdívka, která určuje koncový bod Mex.</span><span class="sxs-lookup"><span data-stu-id="69c80-115">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="69c80-116">Postupy: Zadejte pověření zabezpečení kanálu</span><span class="sxs-lookup"><span data-stu-id="69c80-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="69c80-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Služby podporuje Přezdívka `IChannelCredentials` rozhraní, které umožňuje řadu alternativní metody pro zadání přihlašovacích údajů kanálu.</span><span class="sxs-lookup"><span data-stu-id="69c80-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="69c80-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="69c80-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="69c80-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="69c80-119">See Also</span></span>  
 [<span data-ttu-id="69c80-120">Integrace s aplikacemi modelu COM +</span><span class="sxs-lookup"><span data-stu-id="69c80-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
