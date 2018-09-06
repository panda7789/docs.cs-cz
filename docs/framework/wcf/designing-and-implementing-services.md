---
title: Navrhování a implementace služeb
ms.date: 03/30/2017
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
ms.openlocfilehash: 673712912b674c48dee094859364df9b22c51c82
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877291"
---
# <a name="designing-and-implementing-services"></a>Navrhování a implementace služeb
Tato část ukazuje, jak definovat a implementovat kontrakty WCF. Kontrakt služby specifikuje, koncový bod komunikuje s vnějším světem. Konkrétnější úrovni je příkaz o sadě určitých zpráv, které jsou uspořádány do základní zprávy exchange vzory (MEPs), jako je například požadavek/odpověď jednosměrného a duplexní. Pokud kontrakt služby je sada logicky spojených výměny zpráv, je operace služby exchange jedné zprávy. Například `Hello` operace musíte samozřejmě přijmout jednu zprávu (aby volající může oznamujeme pozdrav) a může nebo nemusí vrátit zprávu (v závislosti na provedla operaci).  
  
 Další informace o kontraktech a jiné základní koncepty Windows Communication Foundation (WCF), najdete v části [základní koncepty Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md). Toto téma se zaměřuje na pochopení kontraktů služby. Další informace o tom, jak vytvářet klienty, kteří používají kontraktů služby pro připojení ke službám, naleznete v tématu [přehled klientů WCF](../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Přehled  
 Toto téma obsahuje základní koncepční orientace k navrhování a implementace služeb WCF. Související témata poskytují podrobnější informace o specifika návrhu a implementace. Doporučujeme před navrhování a implementace aplikace WCF, který jste:  
  
-   Pochopit, jaký kontrakt služby je, jak to funguje a jak ji vytvořit.  
  
-   Vysvětlení, že kontrakty stavu minimální požadavky na tuto konfiguraci modulu runtime nebo hostitelské prostředí nemusí podporovat.  
  
## <a name="service-contracts"></a>Kontrakty služeb  
 Kontrakt služby specifikuje, následující:  
  
-   Operace kontraktu a zpřístupňuje.  
  
-   Podpis operace z hlediska si vyměňují zprávy.  
  
-   Datové typy z následujících zpráv.  
  
-   Umístění operací.  
  
-   Konkrétní protokoly a formáty serializace, které slouží k podpoře úspěšné komunikaci se službou.  
  
 Například může mít kontrakt nákupní objednávky `CreateOrder` operace, která přijímá vstup z informací o objednávkách typů a vrátí informace o úspěchu nebo neúspěchu, včetně identifikátor objednávky. Také může mít `GetOrderStatus` operace, která přijímá identifikátor objednávky a vrátí informace o stavu objednávky. Kontrakt služby toto řazení zadáte:  
  
1.  Kontrakt nákupní objednávky, které se skládal z `CreateOrder` a `GetOrderStatus` operace.  
  
2.  Zda operace zadali zprávy vstupní a výstupní zprávy.  
  
3.  Data, která může obsahovat tyto zprávy.  
  
4.  Zařazené do kategorií příkazy týkající se komunikace infrastrukturu nezbytnou k úspěšné zpracování zprávy. Například tyto podrobnosti patří, jestli a jaké formuláře zabezpečení požadované k navázání komunikace úspěšná.  
  
 K předání tento druh informací do jiných aplikací na mnoha platformách (včetně jiné platformy než Microsoft), kontrakty služeb XML jsou veřejně vyjádřené v standardní formáty XML, jako například [Web Services Description Language](https://go.microsoft.com/fwlink/?LinkId=94952) () WSDL) a [schématu XML](https://go.microsoft.com/fwlink/?LinkId=94953) (XSD), mimo jiné. Pro mnoho platforem mohou vývojáři tyto informace veřejného kontraktu vytvářet aplikace, které mohou komunikovat se službou, protože porozumí jazykové specifikaci a protože tyto jazyky jsou navržené tak, aby vzájemná spolupráce grafického subsystému Zadáním popisu vašeho nového veřejného formuláře, formátů a protokoly, které služba podporuje. Další informace o zpracování tento druh informací WCF najdete v tématu [metadat](../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Kontrakty lze vyjádřit mnoha způsoby a WSDL a XSD jsou vynikající jazyků k popisu služby přístupné způsobem, jejich obtížné jazycích používat přímo a jsou pouze popis služby, ne implementací kontraktu služby. Aplikace WCF proto použít spravované atributy, rozhraní a třídy pro definici struktury služba i na jeho implementaci.  
  
 Výsledný kontrakt definovaný ve spravovaných typů může být *exportovat* jako metadata – WSDL a XSD – v případě potřeby klienty nebo jiné služby implementátory. Výsledkem je jednoduchý programovací model, který lze popsat (s použitím veřejné metadat) na všechny klientské aplikace. Podrobnosti o podkladové zprávy protokolu SOAP, dopravy a informace týkající se zabezpečení a tak dále, může být ponecháno na WCF, která automaticky provádí potřebné převody do a z systém typů kontraktu služby do systému typů XML.  
  
 Další informace o navrhování kontraktů, naleznete v tématu [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md). Další informace o implementaci kontrakty, naleznete v tématu [implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Zprávy Front a System Center  
 Použití spravovaného rozhraní, třídy a metody k operacím služby modelu je jednoduché, když jste zvyklí. vzdálené volání procedur (RPC)-stylu podpisy metod, v které předání parametrů do metody a přijímání návratové hodnoty je běžné formě žádost o funkci z objektu nebo jiný typ kódu. Například programátoři, kteří používají spravované jazyky, jako je například Visual Basic a C++ COM můžete použít svých znalostí v oblasti přístup stylu RPC (ať už s použitím objektů nebo rozhraní) k vytvoření kontrakty služeb WCF bez dochází k problémům vyplývajících z Styl RPC distribuovaných systémů objektu. Orientaci na služby poskytuje výhody volně propojených, objektově orientovaného programování při zachování jednoduchosti a vzdáleného volání Procedur známý programovací prostředí.  
  
 Mnoho programátorů se lépe seznámíte s objektově orientovaný aplikačního programovacího rozhraní, jako jsou fronty zpráv, jako je Microsoft MSMQ <xref:System.Messaging> obory názvů v rozhraní .NET Framework nebo odesílání nestrukturovaných XML v požadavcích HTTP, na další. Další informace o programování na úrovni zpráv najdete v tématu [použití kontraktů zpráv](../../../docs/framework/wcf/feature-details/using-message-contracts.md), [programování na úrovni kanálu služby](../../../docs/framework/wcf/extending/service-channel-level-programming.md), a [vzájemná funkční spolupráce s aplikacemi POX](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Principy hierarchie požadavky  
 Kontrakt služby skupiny operace; Určuje vzorce výměny zpráv, typy zpráv a datové typy těchto zpráv carry; a určuje kategorie pro podporu kontrakt musí mít implementaci chování za běhu (například může vyžadovat, že zprávy zašifrovaná a podepsaná). Kontrakt služby samotný neurčuje přesně jak jsou tyto požadavky splněny, pouze to, že musí být. Typ šifrování nebo způsobem, ve kterém je zpráva podepsaný je až po implementaci a konfiguraci kompatibilní služby.  
  
 Všimněte si, že tak, že kontrakt vyžaduje některé aspekty implementace kontraktu služby a konfiguraci spuštění pro přidání chování. Sadu požadavků, které musí být splněny zpřístupnit služby pro použití se navazuje na předchozí sadu požadavků. Pokud kontrakt odešle požadavky na provádění, implementace může ještě vyžadovat další konfiguraci a vazby, které povolí službu spustit. Hostitelská aplikace nakonec musí podporovat všechny požadavky, které aplikacím dodávají konfigurace služby a vazby.  
  
 Tento proces sčítání požadavek je potřeba vzít v úvahu při navrhování, implementaci, konfiguraci a hostování aplikace služby Windows Communication Foundation (WCF). Kontrakt například můžete určit, že je nutné podporují relace. Pokud ano, musíte nakonfigurovat vazby ke splnění tohoto požadavku smluvní nebo implementace služby nebudou fungovat. Nebo pokud vaše služba vyžaduje integrované ověřování Windows a je hostovaná v Internetové informační služby (IIS), webové aplikace, ve kterém se služba nachází musí mít povoleno integrované ověřování Windows a anonymní podporu vypnuté. Další informace o funkcích a vliv těchto typů hostitele jinou službu, naleznete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
