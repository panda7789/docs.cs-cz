---
title: Kontrakty
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
ms.openlocfilehash: 839f7790a5dd300313931672c60e7826af39aeea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651091"
---
# <a name="contracts"></a>Kontrakty
Tato část ukazuje, jak definovat a implementovat kontrakty Windows Communication Foundation (WCF). Kontrakt služby specifikuje, koncový bod komunikuje s vnějším světem. Konkrétnější úrovni je příkaz o sadě určitých zpráv, které jsou uspořádány do základní zprávy exchange vzory (MEPs), jako je například požadavek/odpověď jednosměrného a duplexní. Pokud kontrakt služby je sada logicky spojených výměny zpráv, je operace služby exchange jedné zprávy. Například `Hello` operace musíte samozřejmě přijmout jednu zprávu (aby volající může oznamujeme pozdrav) a může nebo nemusí vrátit zprávu (v závislosti na provedla operaci).  
  
 Další informace o kontraktech a další základní pojmy WCF najdete v tématu [základní koncepty Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md). Toto téma se zaměřuje na pochopení kontraktů služby. Další informace o tom, jak vytvářet klienty, kteří používají kontraktů služby pro připojení ke službám, naleznete v tématu [přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md). Další informace o klientské kanály, architekturu klienta a další problémy s klientem najdete v tématu [klienti](../../../../docs/framework/wcf/feature-details/clients.md).  
  
## <a name="overview"></a>Přehled  
 Toto téma obsahuje podrobný koncepční orientace k navrhování a implementace služeb WCF. Související témata poskytují že podrobnější informace o specifika návrhu a implementace. Doporučujeme před navrhování a implementace aplikace WCF, který jste:  
  
- Pochopit, jaký kontrakt služby je, jak to funguje a jak ji vytvořit.  
  
- Vysvětlení, že kontrakty stavu minimální požadavky na tuto konfiguraci za běhu nebo hostitelské prostředí nemusí podporovat.  
  
## <a name="service-contracts"></a>Kontrakty služeb  
 Kontrakt služby je příkaz, který poskytuje informace o:  
  
- Seskupování operací ve službě.  
  
- Podpis operace z hlediska si vyměňují zprávy.  
  
- Datové typy z následujících zpráv.  
  
- Umístění operací.  
  
- Konkrétní protokoly a formáty serializace, které slouží k podpoře úspěšné komunikaci se službou.  
  
 Například může mít kontrakt nákupní objednávky `CreateOrder` operace, která přijímá vstup z informací o objednávkách typů a vrátí informace o úspěchu nebo neúspěchu, včetně identifikátor objednávky. Také může mít `GetOrderStatus` operace, která přijímá identifikátor objednávky a vrátí informace o stavu objednávky. Kontrakt služby toto řazení zadáte:  
  
- Kontrakt nákupní objednávky, které se skládal z `CreateOrder` a `GetOrderStatus` operace.  
  
- Zda operace zadali zprávy vstupní a výstupní zprávy.  
  
- Data, která může obsahovat tyto zprávy.  
  
- Zařazené do kategorií příkazy týkající se komunikace infrastrukturu nezbytnou k úspěšné zpracování zprávy. Například tyto podrobnosti patří, jestli a jaké formuláře zabezpečení požadované k navázání komunikace úspěšná.  
  
 K předání tento druh informací do aplikací na jiných platformách (včetně jiné platformy než Microsoft), kontrakty služeb XML jsou veřejně vyjádřené v standardní formáty XML, jako například [webové služby WSDL (Description Language)](https://go.microsoft.com/fwlink/?LinkId=87004) a [schématu XML (XSD)](https://go.microsoft.com/fwlink/?LinkId=87005), mimo jiné. Pro mnoho platforem mohou vývojáři tyto informace veřejného kontraktu vytvářet aplikace, které mohou komunikovat se službou, protože porozumí jazykové specifikaci a protože tyto jazyky jsou navržené tak, aby vzájemná spolupráce grafického subsystému Zadáním popisu vašeho nového veřejného formuláře, formátů a protokoly, které služba podporuje. Další informace o zpracování tento druh informací WCF najdete v tématu [metadat](../../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Kontrakty lze vyjádřit mnoha způsoby, ale a WSDL a XSD jsou vynikající jazyků k popisu služby přístupné způsobem, ale jsou obtížné jazycích používat přímo – v každém případě jsou pouze popisy kontraktu service, ne služba implementace. Aplikace WCF proto používat spravované atributy, rozhraní a třídy definovat strukturu a implementace služby.  
  
 Výsledný kontrakt definovaný ve spravovaných typů lze převést (také nazývané *exportovat*) jako metadata – WSDL a XSD – v případě potřeby klienty nebo jiné služby implementátory, zvláště na jiných platformách. Výsledkem je jednoduchý programovací model, který lze popsat pomocí veřejného metadata pro všechny klientské aplikace. Podrobnosti o podkladové zprávy protokolu SOAP, jako je například doprava a informace týkající se zabezpečení, můžou zůstat na WCF, která automaticky provádí potřebné převody do a z systém typů kontraktu služby do systému typů XML.  
  
 Další informace o navrhování kontraktů, naleznete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md). Další informace o implementaci kontrakty, naleznete v tématu [implementace kontraktů služeb](../../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Kromě toho WCF také umožňuje vyvíjet kontrakty služeb výhradně na úrovni zprávy. Další informace o vývoji kontraktů služby na úrovni zpráv najdete v tématu [použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Další informace o vývoji služeb v protokolu SOAP XML, naleznete v tématu [vzájemná funkční spolupráce s aplikacemi POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Principy hierarchie požadavky  
 Kontrakt služby skupiny operace; Určuje MEP typy zpráv a datové typy těchto zpráv carry; a určuje kategorie pro podporu kontrakt musí mít implementaci chování za běhu (například může vyžadovat, že zprávy zašifrovaná a podepsaná). Kontrakt služby samostatně, ale neurčuje, přesně jak jsou tyto požadavky splněny, pouze to, že musí být. Jaký typ šifrování nebo jak podepsanou zprávu je až po implementaci a konfiguraci kompatibilní služby.  
  
 Všimněte si, že tak, že kontrakt vyžaduje některé aspekty implementace kontraktu služby a konfiguraci spuštění pro přidání chování. Sadu požadavků, které musí být splněny zpřístupnit služby pro použití se navazuje na předchozí sadu požadavků. Pokud kontrakt odešle požadavky na provádění, implementace může ještě vyžadovat další konfiguraci a vazby, které povolí službu spustit. Hostitelská aplikace nakonec musí podporovat všechny požadavky, které aplikacím dodávají konfigurace služby a vazby.  
  
 Tento proces sčítání požadavek je potřeba vzít v úvahu při navrhování, implementaci, konfiguraci a hostování aplikace služby Windows Communication Foundation (WCF). Kontrakt například můžete určit, že je nutné podporují relace. Pokud ano, musíte nakonfigurovat vazby ke splnění tohoto požadavku smluvní nebo implementace služby nebudou fungovat. Nebo pokud vaše služba vyžaduje ověření integrované Windows a je hostovaná v Internetové informační služby (IIS), webové aplikace, ve kterém se služba nachází musí mít ověření integrované Windows zapnutý a anonymní podporu vypnuté. Další informace o funkcích a vliv těchto typů hostitele jinou službu, naleznete v tématu [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
## <a name="see-also"></a>Viz také:

- [Koncové body: Adresy, vazby a kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Implementace kontraktů služeb](../../../../docs/framework/wcf/implementing-service-contracts.md)
