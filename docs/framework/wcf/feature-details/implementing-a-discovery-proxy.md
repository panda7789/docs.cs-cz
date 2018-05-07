---
title: Implementace proxy zjišťování
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 0c7086e0eecea6cc2d7494d6afda0abf056ba758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-a-discovery-proxy"></a>Implementace proxy zjišťování
Tato část popisuje kroky potřebné k implementace zjišťování proxy. Zjišťování proxy je samostatné služby, který obsahuje úložiště služby. Klienti mohou odesílat dotazy na zjišťování proxy k vyhledání zjistitelný služby, které má informace o proxy serveru. Jak je proxy server naplněný služby závisí implementátor. Například zjišťování proxy můžete připojit k existující úložiště služby a zjistitelnost těchto informací, Správce může pomocí rozhraní API pro správu na přidání služeb zjistitelný na proxy server nebo proxy zjišťování můžete použít funkci oznámení na Aktualizujte vnitřní mezipaměti.  
  
 Implementace WCF poskytuje základní třídy, které vám umožní snadno vytvářet proxy server. Tato rozhraní API k vytvoření zjišťování Proxy na existující úložiště, můžete využít.  
  
 Zjišťování proxy zde implementováno je jako ostatní služby WCF, můžete také zjistitelnost zjišťování proxy a klienti najít své koncové body.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Implementace proxy zjišťování](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 Popisuje způsob implementace zjišťování proxy.  
  
 [Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Popisuje, jak implementovat zjistitelný služby WCF, který se zaregistruje zjišťování proxy.  
  
 [Postupy: Implementace klientské aplikace používající proxy zjišťování k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 Popisuje způsob implementace WCF klientské aplikace používající zjišťování proxy k vyhledání pro službu.  
  
 [Postupy: Test proxy zjišťování](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Popisuje, jak otestovat kód napsaný v předchozí tři témata.  
  
## <a name="see-also"></a>Viz také  
 [Zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [Postupy: Programové přidání zjistitelnosti do klienta a služby WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
