---
title: Implementace proxy zjišťování
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 382df95fef2108d338e4ea327da9185c856eca5a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579238"
---
# <a name="implementing-a-discovery-proxy"></a>Implementace proxy zjišťování
Tato část popisuje kroky potřebné k implementaci proxy zjišťování. Proxy zjišťování je samostatná služba, která obsahuje úložiště služeb. Klienti mohou zadat dotaz na proxy zjišťování a vyhledat tak zjistitelné služby, na kterých je daný proxy vědět. Způsob naplnění proxy služeb službami je až implementátor. Například proxy zjišťování se může připojit k existujícímu úložišti služeb a učinit tyto informace zjistitelným správcem může pomocí rozhraní API pro správu přidat zjistitelné služby na proxy server nebo proxy zjišťování může pomocí funkce oznámení aktualizovat svou interní mezipaměť.  
  
 Implementace WCF poskytuje základní třídy, které umožňují snadno vytvořit proxy server. Tato rozhraní API můžete využít k vytvoření proxy serveru zjišťování nad stávajícím úložištěm.  
  
 Proxy zjišťování implementované tady je stejně jako jakékoli jiné služby WCF. v takovém případě můžete také nastavit, aby byl proxy zjišťování zjistitelný a aby klienti našli své koncové body.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Implementace zjišťování proxy](how-to-implement-a-discovery-proxy.md)  
 Popisuje, jak implementovat proxy zjišťování.  
  
 [Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování](discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Popisuje, jak implementovat zjistitelnou službu WCF, která se registruje pomocí proxy zjišťování.  
  
 [Postupy: Implementace klientské aplikace používající proxy zjišťování k vyhledání služby](client-app-discovery-proxy-to-find-a-service.md)  
 Popisuje implementaci klientské aplikace WCF, která používá proxy zjišťování k hledání služby.  
  
 [Postupy: Test proxy zjišťování](how-to-test-the-discovery-proxy.md)  
 Popisuje, jak otestovat kód napsaný v předchozích třech tématech.  
  
## <a name="see-also"></a>Viz také

- [Zjišťování WCF](wcf-discovery.md)
- [Postupy: Programové přidání zjistitelnosti do klienta a služby WCF](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
