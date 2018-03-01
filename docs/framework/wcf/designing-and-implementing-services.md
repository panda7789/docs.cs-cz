---
title: "Navrhování a implementace služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b6d5a2dfb4db1d57f60e4c7f8cf3300b766402e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="designing-and-implementing-services"></a>Navrhování a implementace služeb
V této části se dozvíte, jak definovat a implementovat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] smluv. Smlouvy o poskytování služeb určuje, co koncový bod komunikuje s vnějším světem. Více konkrétní úrovni je prohlášení o sadu zprávy specifické pro uspořádány do základní zpráva exchange vzory (MEPs), jako je například požadavek nebo odpověď, jednosměrné a duplexní. Pokud smlouvy o poskytování služeb je sada logicky spojených výměny zpráv, je operace služby exchange jedné zprávy. Například `Hello` operace musí samozřejmě přijmout jednu zprávu (takže volající může informovat pozdrav) a může nebo nemusí vracet zprávy (v závislosti na provedla operaci).  
  
 Další informace o kontraktech a další základní [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] koncepty, najdete v části [základní Windows Communication Foundation koncepty](../../../docs/framework/wcf/fundamental-concepts.md). Toto téma se zaměřuje na pochopení kontraktů služby. Další informace o tom, jak sestavit klienty, kteří používají k připojení ke službám kontraktů služby najdete v tématu [klienta WCF – přehled](../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Přehled  
 Toto téma obsahuje základní úrovni koncepční orientaci k navrhování a implementace [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Související témata poskytují podrobnější informace o specifika návrhu a implementace. Před navrhování a implementace vašeho [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace, je doporučeno, které:  
  
-   Pochopit, jaké kontraktu služby je, jak to funguje a jak ji vytvořit.  
  
-   Pochopit, že kontrakty stavu minimální požadavky nemusí podporovat této konfigurace modulu runtime nebo hostitelské prostředí.  
  
## <a name="service-contracts"></a>Kontrakty služeb  
 Kontrakt služby určuje následující:  
  
-   Operace zpřístupní kontraktu.  
  
-   Podpis operace z hlediska zprávy vyměňují.  
  
-   Datové typy tyto zprávy.  
  
-   Umístění operace.  
  
-   Konkrétní protokoly a formáty serializace, které se používají pro podporu úspěšné komunikace se službou.  
  
 Například může mít kontraktu pořadí nákupu `CreateOrder` operace, která přijímá vstup informace o objednávce typy a vrátí informace o úspěchu nebo neúspěchu, včetně identifikátor pořadí. Také může mít `GetOrderStatus` operace, která přijímá identifikátor pořadí a vrátí informace o stavu pořadí. Chcete-li zadejte kontraktu služby toto řazení:  
  
1.  Kontrakt nákupu pořadí, které se skládal z `CreateOrder` a `GetOrderStatus` operace.  
  
2.  Zda operace zadali zprávy vstup a výstup zprávy.  
  
3.  Data, která tyto zprávy mohou přenášet.  
  
4.  Kategorizovaná prohlášení o potřeba úspěšně zpracovat zprávy komunikační infrastruktura. Tyto podrobnosti patří například jestli a jaké formuláře zabezpečení jsou požadované k navázání komunikace úspěšná.  
  
 K předání informací o tom tento druh informací k ostatním aplikacím na spoustě platforem (včetně jiných společností než Microsoft platformy), XML kontraktů služby jsou veřejně vyjádřené v standardní formáty XML, jako například [Web Services Description Language](http://go.microsoft.com/fwlink/?LinkId=94952) () WSDL) a [schématu XML](http://go.microsoft.com/fwlink/?LinkId=94953) (XSD), mimo jiné. Vývojáři pro mnoho platformy můžete použít tyto informace veřejného kontraktu k vytvoření aplikace, které mohou komunikovat se službou, protože porozumí jazyk specifikace i vzhledem k tomu, že tyto jazyky jsou navržené tak, aby vzájemná spolupráce prostřednictvím popisu veřejné formuláře, formátů a protokoly podporující službu. Další informace o tom, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] najdete v tomto typu informací, obslužné rutiny [Metadata](../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Kontrakty může být vyjádřený mnoha způsoby a WSDL a XSD jsou vynikající jazyků k popisu služby přístupné způsobem, jejich obtížné jazyky používat přímo a jsou jenom popisy služby, není implementace kontraktu služby. Proto [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikací pomocí spravovaného atributy, rozhraní a třídy definovat strukturu služby a k jejímu.  
  
 Může být výsledný kontrakt definovaný ve spravované typy *exportovat* jako metadata – WSDL a XSD – v případě potřeby klienti nebo jiné služby implementátory. Výsledkem je jednoduchý programovací model, který lze popsat (pomocí veřejného metadata) na všechny klientské aplikace. Podrobnosti o základní protokolu SOAP zprávy, Transport a informace týkající se zabezpečení a tak dále, může být ponecháno na [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], která provede nezbytné převody do a z typu kontraktu služby systému do souboru XML systém typů automaticky.  
  
 Další informace o návrhu kontrakty najdete v tématu [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md). Další informace o implementace kontraktů najdete v tématu [implementace kontraktů služby](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Zprávy se vepředu a uprostřed  
 Použití spravovaného rozhraní, třídy a metody k operacím služby modelu je jasné, pokud se používají k vzdáleného volání procedur (RPC)-styl metoda podpisy, při které předávání parametrů do metody a příjmu návratové hodnoty je normální formu požaduje funkce z objektu nebo jiný typ kódu. Například programátory pomocí spravované jazyky, jako [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] a C++ COM můžete použít jejich znalostí přístup stylu RPC (jestli se používá rozhraní nebo objekty) k vytvoření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby kontrakty bez při setkávají s problémy vyplývajících z RPC-style distribuovaných systémů objektu. Orientaci na služby poskytuje výhody volně párované, zpráva orientované programování při zachování jednoduchosti a znalosti vzdálené volání Procedur programovací prostředí.  
  
 Mnoho programátorů je pohodlnější programovací rozhraní, například fronty zpráv Microsoft MSMQ, jako je aplikace orientované na zprávu <xref:System.Messaging> obory názvů v rozhraní .NET Framework nebo odeslání nestrukturovaných XML v požadavcích HTTP, a další. Další informace o programování na úrovni zpráv najdete v tématu [pomocí kontrakty zpráv](../../../docs/framework/wcf/feature-details/using-message-contracts.md), [programování na úrovni služby kanálů](../../../docs/framework/wcf/extending/service-channel-level-programming.md), a [vzájemná funkční spolupráce s aplikacemi POX](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Principy hierarchii požadavky  
 Kontrakt služby skupiny operace; Určuje vzorce výměny zpráv, typy zpráv a datové typy těchto zpráv carry; a označuje kategorie chování implementace musí mít pro podporu kontrakt (například se může vyžadovat, aby se zprávy šifrovaný a podepsaný). Kontrakt služby samotné neurčuje přesně jak jsou tyto požadavky splněny, pouze to, že musí být. Typ šifrování nebo způsobem, ve kterém je podepsaný zprávu závisí na implementaci a konfigurace služby kompatibilní.  
  
 Všimněte si, že kontrakt vyžaduje některé aspekty implementace kontraktu služby a konfiguraci spuštění přidat chování způsob. Sadu požadavků, které musí být splněny vystavit služby pro použití založený na předchozí sadu požadavků. Pokud kontraktu provede požadavky implementace, implementace může ještě vyžadovat další konfigurace a vazby, které umožňují službu spustit. Nakonec hostitelskou aplikaci musí zároveň podporovat všechny požadavky, které konfigurace služby a vazby přidat.  
  
 Tento proces sčítání požadavek je třeba vzít v úvahu při návrhu, implementaci, konfiguraci a hostování důležité [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace služby. Kontrakt například můžete určit, že tato služba vyžaduje pro podporu relaci. Pokud ano, musíte nakonfigurovat vazby pro podporu tohoto smluvními požadavek nebo implementace služby nebude fungovat. Nebo pokud vaše služba vyžaduje integrované ověřování systému Windows a je hostovaná v Internetové informační služby (IIS), musí mít webovou aplikaci, ve kterém se služba nachází, integrované ověřování systému Windows zapnuté a anonymní podporu vypnutý. Další informace o funkcích a dopad typy jinou službu, pro hostitele aplikací najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
