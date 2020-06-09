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
ms.openlocfilehash: dc3bbe0ee72ca5583b1e52a61c914ad866a22a05
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596807"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="9fc69-102">Integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="9fc69-102">Integrating with COM Applications</span></span>
<span data-ttu-id="9fc69-103">Služby Windows Communication Foundation (WCF) lze integrovat přímo do stávajícího kódu pomocí monikeru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="9fc69-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="9fc69-104">Moniker služby lze použít z široké škály vývojových prostředí založených na modelu COM, jako je například Office VBA, Visual Basic 6,0 nebo Visual C++ 6,0.</span><span class="sxs-lookup"><span data-stu-id="9fc69-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9fc69-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9fc69-105">In This Section</span></span>  
 [<span data-ttu-id="9fc69-106">Přehled integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="9fc69-106">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)  
 <span data-ttu-id="9fc69-107">Poskytuje přehled o hlavních částech procesu integrace.</span><span class="sxs-lookup"><span data-stu-id="9fc69-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="9fc69-108">Postupy: Registrace a konfigurace monikeru služby</span><span class="sxs-lookup"><span data-stu-id="9fc69-108">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="9fc69-109">Chcete-li použít moniker služby WCF v rámci aplikace modelu COM, zaregistrujte požadované typy s atributy pomocí modelu COM a nakonfigurujte aplikaci COM a moniker s požadovanou konfigurací vazby.</span><span class="sxs-lookup"><span data-stu-id="9fc69-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="9fc69-110">Postupy: Použití monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="9fc69-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="9fc69-111">Vysvětluje, jak získat definici kontraktu ve formě dokumentu WSDL (Web Services Definition Language) nebo z koncového bodu WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="9fc69-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="9fc69-112">Postupy: Použití monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="9fc69-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="9fc69-113">Popisuje způsob volání ukázky WCF pomocí monikeru WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="9fc69-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="9fc69-114">Postupy: Použití monikeru služby u kontraktů výměny metadat</span><span class="sxs-lookup"><span data-stu-id="9fc69-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="9fc69-115">Popisuje způsob volání ukázky WCF pomocí monikeru WCF, který určuje koncový bod mex.</span><span class="sxs-lookup"><span data-stu-id="9fc69-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="9fc69-116">Postupy: Určení přihlašovacích údajů pro zabezpečení kanálu</span><span class="sxs-lookup"><span data-stu-id="9fc69-116">How to: Specify Channel Security Credentials</span></span>](how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="9fc69-117">Moniker služby WCF podporuje `IChannelCredentials` rozhraní, které umožňuje určit rozsah alternativních metod pro zadání přihlašovacích údajů kanálu.</span><span class="sxs-lookup"><span data-stu-id="9fc69-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9fc69-118">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="9fc69-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="9fc69-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fc69-119">See also</span></span>

- [<span data-ttu-id="9fc69-120">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="9fc69-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
