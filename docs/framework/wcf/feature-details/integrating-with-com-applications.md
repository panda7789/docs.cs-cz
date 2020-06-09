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
# <a name="integrating-with-com-applications"></a>Integrace s aplikacemi modelu COM
Služby Windows Communication Foundation (WCF) lze integrovat přímo do stávajícího kódu pomocí monikeru služby WCF. Moniker služby lze použít z široké škály vývojových prostředí založených na modelu COM, jako je například Office VBA, Visual Basic 6,0 nebo Visual C++ 6,0.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled integrace s aplikacemi modelu COM](integrating-with-com-applications-overview.md)  
 Poskytuje přehled o hlavních částech procesu integrace.  
  
 [Postupy: Registrace a konfigurace monikeru služby](how-to-register-and-configure-a-service-moniker.md)  
 Chcete-li použít moniker služby WCF v rámci aplikace modelu COM, zaregistrujte požadované typy s atributy pomocí modelu COM a nakonfigurujte aplikaci COM a moniker s požadovanou konfigurací vazby.  
  
 [Postupy: Použití monikeru služby Windows Communication Foundation bez registrace](use-the-wcf-service-moniker-without-registration.md)  
 Vysvětluje, jak získat definici kontraktu ve formě dokumentu WSDL (Web Services Definition Language) nebo z koncového bodu WS-MetadataExchange.  
  
 [Postupy: Použití monikeru služby u kontraktů WSDL](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 Popisuje způsob volání ukázky WCF pomocí monikeru WCF WSDL.  
  
 [Postupy: Použití monikeru služby u kontraktů výměny metadat](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 Popisuje způsob volání ukázky WCF pomocí monikeru WCF, který určuje koncový bod mex.  
  
 [Postupy: Určení přihlašovacích údajů pro zabezpečení kanálu](how-to-specify-channel-security-credentials.md)  
 Moniker služby WCF podporuje `IChannelCredentials` rozhraní, které umožňuje určit rozsah alternativních metod pro zadání přihlašovacích údajů kanálu.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a>Viz také

- [Integrace s aplikacemi modelu COM+](integrating-with-com-plus-applications.md)
