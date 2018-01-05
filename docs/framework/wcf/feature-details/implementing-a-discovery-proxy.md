---
title: "Implementace proxy zjišťování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2996eb07c883947210c48471a2c60ba49495566d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-a-discovery-proxy"></a>Implementace proxy zjišťování
Tato část popisuje kroky potřebné k implementace zjišťování proxy. Zjišťování proxy je samostatné služby, který obsahuje úložiště služby. Klienti mohou odesílat dotazy na zjišťování proxy k vyhledání zjistitelný služby, které má informace o proxy serveru. Jak je proxy server naplněný služby závisí implementátor. Například zjišťování proxy můžete připojit k existující úložiště služby a zjistitelnost těchto informací, Správce může pomocí rozhraní API pro správu na přidání služeb zjistitelný na proxy server nebo proxy zjišťování můžete použít funkci oznámení na Aktualizujte vnitřní mezipaměti.  
  
 Implementace WCF poskytuje základní třídy, které vám umožní snadno vytvářet proxy server. Tato rozhraní API k vytvoření zjišťování Proxy na existující úložiště, můžete využít.  
  
 Zjišťování proxy zde implementováno je jako ostatní služby WCF, můžete také zjistitelnost zjišťování proxy a klienti najít své koncové body.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Implementace proxy zjišťování](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 Popisuje způsob implementace zjišťování proxy.  
  
 [Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Popisuje, jak implementovat zjistitelný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba, která registruje s proxy serverem zjišťování.  
  
 [Postupy: Implementace klientské aplikace používající proxy zjišťování k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 Popisuje, jak implementovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientské aplikace používající zjišťování proxy k vyhledání pro službu.  
  
 [Postupy: Test proxy zjišťování](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Popisuje, jak otestovat kód napsaný v předchozí tři témata.  
  
## <a name="see-also"></a>Viz také  
 [Zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [Postupy: Programové přidání zjistitelnosti do klienta a služby WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
