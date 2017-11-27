---
title: Kontrakty
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60835e9d85412aa07958273daa5d9b7a24cfbfeb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="contracts"></a>Kontrakty
V této části se dozvíte, jak definovat a implementovat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]smluv. Smlouvy o poskytování služeb určuje, co koncový bod komunikuje s vnějším světem. Více konkrétní úrovni je prohlášení o sadu zprávy specifické pro uspořádány do základní zpráva exchange vzory (MEPs), jako je například požadavek nebo odpověď, jednosměrné a duplexní. Pokud smlouvy o poskytování služeb je sada logicky spojených výměny zpráv, je operace služby exchange jedné zprávy. Například `Hello` operace musí samozřejmě přijmout jednu zprávu (takže volající může informovat pozdrav) a může nebo nemusí vracet zprávy (v závislosti na provedla operaci).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kontrakty a další základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncepty, najdete v části [základní Windows Communication Foundation koncepty](../../../../docs/framework/wcf/fundamental-concepts.md). Toto téma se zaměřuje na pochopení kontraktů služby. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak sestavit klienty, kteří používají službu měnící se připojit ke službám, najdete v části [klienta WCF – přehled](../../../../docs/framework/wcf/wcf-client-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Klient kanály, architekturu klienta a další problémy s klientem, najdete v části [klienti](../../../../docs/framework/wcf/feature-details/clients.md).  
  
## <a name="overview"></a>Přehled  
 Toto téma obsahuje základní koncepční orientaci k navrhování a implementace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. Související témata poskytují že podrobnější informace o specifika návrhu a implementace. Před navrhování a implementace vašeho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, je doporučeno, které:  
  
-   Pochopit, jaké kontraktu služby je, jak to funguje a jak ji vytvořit.  
  
-   Pochopit, že kontrakty stavu minimální požadavky nemusí podporovat tato konfigurace spuštění nebo hostitelské prostředí.  
  
## <a name="service-contracts"></a>Kontrakty služeb  
 Kontrakt služby je příkaz, který poskytuje informace o:  
  
-   Seskupování operací ve službě.  
  
-   Podpis operace z hlediska zprávy vyměňují.  
  
-   Datové typy tyto zprávy.  
  
-   Umístění operace.  
  
-   Konkrétní protokoly a formáty serializace, které se používají pro podporu úspěšné komunikace se službou.  
  
 Například může mít kontraktu pořadí nákupu `CreateOrder` operace, která přijímá vstup informace o objednávce typy a vrátí informace o úspěchu nebo neúspěchu, včetně identifikátor pořadí. Také může mít `GetOrderStatus` operace, která přijímá identifikátor pořadí a vrátí informace o stavu pořadí. Chcete-li zadejte kontraktu služby toto řazení:  
  
-   Kontrakt nákupu pořadí, které se skládal z `CreateOrder` a `GetOrderStatus` operace.  
  
-   Zda operace zadali zprávy vstup a výstup zprávy.  
  
-   Data, která tyto zprávy mohou přenášet.  
  
-   Kategorizovaná prohlášení o potřeba úspěšně zpracovat zprávy komunikační infrastruktura. Tyto podrobnosti patří například jestli a jaké formuláře zabezpečení jsou požadované k navázání komunikace úspěšná.  
  
 K předání informací o tom tento druh informací do aplikací na jiných platformách (včetně jiných společností než Microsoft platformy), XML kontraktů služby jsou veřejně vyjádřené v standardní formáty XML, jako například [webové služby popis Language (WSDL)](http://go.microsoft.com/fwlink/?LinkId=87004) a [schématu XML (XSD)](http://go.microsoft.com/fwlink/?LinkId=87005), mimo jiné. Vývojáři pro mnoho platformy můžete použít tyto informace veřejného kontraktu k vytvoření aplikace, které mohou komunikovat se službou, protože porozumí jazyk specifikace i vzhledem k tomu, že tyto jazyky jsou navržené tak, aby vzájemná spolupráce prostřednictvím popisu veřejné formuláře, formátů a protokoly podporující službu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] najdete v tomto typu informací, obslužné rutiny [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Kontrakty může být vyjádřený mnoha způsoby, ale a WSDL a XSD jsou vynikající jazyků k popisu služby přístupné způsobem, jsou těžko jazyky používat přímo – v žádném případě jsou jenom popisy kontraktu služby, není služba implementace. Proto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikací pomocí spravovaného atributy, rozhraní a třídy definovat strukturu a implementaci služby.  
  
 Lze převést výsledné kontrakt definovaný ve spravované typy (také nazývané *exportovat*) jako metadata – WSDL a XSD – v případě potřeby klienti nebo jiné služby implementátory, hlavně na jiných platformách. Výsledkem je jednoduchý programovací model, který lze popsat pomocí veřejného metadata pro všechny klientské aplikace. Podrobnosti o základní protokolu SOAP zprávy, jako je například Transport a informace týkající se zabezpečení, může být ponecháno na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], která automaticky provede potřeby převod na a z systému typu kontraktu služby pro systém typů XML.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]navrhování kontraktů, najdete v části [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]implementace kontraktů, najdete v části [implementace kontraktů služby](../../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Kromě toho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] také nabízí možnost vyvíjet kontraktů služby zcela na úrovni zpráv. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Viz vývoj kontraktů služby na úrovni zpráv [pomocí kontrakty zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vývoj služby v nejsou SOAP XML, najdete v části [vzájemná funkční spolupráce s aplikacemi POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Principy hierarchii požadavky  
 Kontrakt služby skupiny operace; Určuje MEP, typy zpráv a datové typy těchto zpráv carry; a označuje kategorie chování implementace musí mít pro podporu kontrakt (například se může vyžadovat, aby se zprávy šifrovaný a podepsaný). Kontrakt služby samostatně, ale neurčuje, přesně jak jsou tyto požadavky splněny, pouze to, že musí být. Jaký typ šifrování nebo jak je podepsaný zprávu závisí na implementaci a konfigurace služby kompatibilní.  
  
 Všimněte si, že kontrakt vyžaduje některé aspekty implementace kontraktu služby a konfiguraci spuštění přidat chování způsob. Sadu požadavků, které musí být splněny vystavit služby pro použití založený na předchozí sadu požadavků. Pokud kontraktu provede požadavky implementace, implementace může ještě vyžadovat další konfigurace a vazby, které umožňují službu spustit. Nakonec hostitelskou aplikaci musí zároveň podporovat všechny požadavky, které konfigurace služby a vazby přidat.  
  
 Tento proces sčítání požadavek je důležité, třeba vzít v úvahu při návrhu, implementaci, konfiguraci a hostování vaší [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace služby. Kontrakt například můžete určit, že tato služba vyžaduje pro podporu relaci. Pokud ano, musíte nakonfigurovat vazby pro podporu tohoto smluvními požadavek nebo implementace služby nebude fungovat. Nebo pokud vaše služba vyžaduje integrované ověřování systému Windows a je hostovaná v Internetové informační služby (IIS), musí mít webovou aplikaci, ve kterém se služba nachází, integrované ověřování systému Windows zapnuté a anonymní podporu vypnutý. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Funkce a dopad typy aplikací hostitele jinou službu, najdete v části [hostitelský](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncové body: Adresy, vazby a kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Implementace kontraktů služeb](../../../../docs/framework/wcf/implementing-service-contracts.md)
