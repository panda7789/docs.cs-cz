---
title: "Správa verzí služby dat (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 545096292f34566b4bb6c3c44bb20ddac426af26
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="data-service-versioning-wcf-data-services"></a>Správa verzí služby dat (služby WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Můžete vytvořit datové služby tak, aby klienti přístup k datům jako prostředky pomocí identifikátory URI, které jsou založeny na datový model. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]podporuje také definice operací služby. Po počátečním nasazení a potenciálně několikrát během své životnosti, tato data services bude pravděpodobně nutné změnit z různých důvodů, jako je například změna obchodních potřeb, požadavků informačních technologií, nebo jiných problémů. Pokud provedete změny do existující služby data, musí se zvážit, zda chcete definovat novou verzi dat služby a jak nejlepší minimalizaci dopadů na existující klientské aplikace. Toto téma obsahuje pokyny k kdy a jak vytvořit novou verzi datové služby. Také popisuje, jak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zpracovává exchange mezi klienty a datové služby, které podporují různé verze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu.  
  
## <a name="versioning-a-wcf-data-service"></a>Správa verzí služby WCF Data Service  
 Jakmile je nasazená služba dat a dat spotřebovává, změny dat služby by mohly způsobit problémy s kompatibilitou se stávajícími aplikacemi klienta. Ale protože změny jsou často vyžadované celkové obchodním potřebám služby, musíte zvážit kdy a jak vytvořit novou verzi služby data s nejmenší dopad na klientovi aplikace.  
  
### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Změn datových modelů, které doporučujeme nové verze datové služby  
 Při určování, zda publikovat novou verzi datové služby, je důležité pochopit, jak různé druhy změny mohou ovlivnit klientské aplikace. Změny ke službě data, která může vyžadovat, abyste vytvořili novou verzi datové služby je možné rozdělit do těchto dvou kategorií:  
  
-   Změny kontrakt služby, mezi které patří aktualizace operace služby, změny usnadnění sad entit (kanály), verze změny a jiné změny chování služby.  
  
-   Změny kontrakt dat, které zahrnují změny do datového modelu, kanálu formáty nebo informačního kanálu vlastní nastavení.  
  
 Následující podrobnosti tabulky, pro jaké typy změn, měli byste zvážit publikování nové verze datové služby:  
  
|Typ změny|Vyžaduje nová verze|Nová verze není potřeba.|  
|--------------------|----------------------------|----------------------------|  
|Operace služby|-Přidat nový parametr<br />-Změna návratový typ<br />-Odebrání operaci služby|-Odstranit existující parametr<br />-Přidat nové operaci služby|  
|Chování služby|-Zakázání počet požadavků<br />-Zakažte podporu projekce<br />-Zvýšit verze požadované datové služby|-Povolit počet požadavků<br />-Povolit podporu projekce<br />-Snížit verze požadované datové služby|  
|Sada entit oprávnění|-Omezit oprávnění sady entit<br />-Změnit kód odpovědi (nové první hodnota číslice) <sup>1</sup>|-Uvolnění entity nastavte oprávnění.<br />-Změnit kód odpovědi (stejné první hodnota číslice)|  
|Vlastnosti entity|-Odebrat existující vlastnosti nebo relaci<br />-Přidat vlastnost neumožňující hodnotu Null<br />-Změna existující vlastnosti|-Přidat vlastnost nullable<sup>2</sup>|  
|Sad entit|-Odebrání sady entit|-Přidat odvozený typ<br />-Změňte základní typ<br />-Přidat sadu entit|  
|Přizpůsobení informačního kanálu|-Změnit vlastnost entity mapování||  
  
 <sup>1</sup> to může záviset na jak výhradně klientskou aplikaci spoléhá na příjem určitý kód chyby.  
  
 <sup>2</sup> můžete nastavit <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> vlastnost `true` váš klient bude ignorovat všechny nové vlastnosti odeslaných službou dat, které nejsou definovány na straně klienta. Ale při vložení, vlastnosti neobsažených klientem v požadavku POST jsou nastaveny na výchozí hodnoty. Aktualizace může být jakákoli stávající data v klientovi Neznámá vlastnost přepsána s výchozími hodnotami. V takovém případě byste měli odeslat aktualizace jako požadavek SLOUČENÍ, což je výchozí hodnota. Další informace najdete v tématu [Správa služby kontextu dat](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
### <a name="how-to-version-a-data-service"></a>Postup verze datové služby  
 Pokud jsou povinné, nové verze datové služby je definována vytvoření nové instance služby s aktualizovanou kontrakt nebo dat modelu. Toto nové služby je pak zpřístupněná pomocí nového identifikátoru URI koncového bodu, která odlišuje jej od předchozí verze. Příklad:  
  
-   Stará verze:`http://services.odata.org/Northwind/v1/Northwind.svc/`  
  
-   Nová verze:`http://services.odata.org/Northwind/v2/Northwind.svc/`  
  
 Při upgradování datové služby, klienti se musí taky aktualizovat založenou na nové metadata služby data a použití nového kořenového identifikátoru URI. Pokud je to možné, je vhodné ponechat předchozí verze datové služby pro podporu klientů, které dosud nebyly upgradovány na použití nové verze. Starší verze datové služby můžete odebrat, pokud už nejsou potřeba. Měli byste zvážit, udržování koncový bod služby data URI v externí konfigurační soubor.  
  
## <a name="odata-protocol-versions"></a>Verze protokolu OData  
 Jako nové verze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jsou vydání, klientské aplikace nemusí používat stejnou verzi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol, který je podporován službou data. Starší klientské aplikace mohou přistupovat k služba dat, která podporuje novější verzi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Klientská aplikace může také používat na novější verzi [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny, která podporuje novější verzi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] než službu data, která se právě využívají.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]využívá podpora poskytovaná [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pro zpracování takových scénářů správy verzí. Je také podpora pro vytváření a používání metadat modelu dat k vytvoření klienta datových služba tříd, když klient používá jinou verzi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] než služba data používá. Další informace najdete v tématu [OData: Správa verzí protokolu](http://go.microsoft.com/fwlink/?LinkId=186071).  
  
### <a name="version-negotiation"></a>Verze vyjednávání  
 Služba data lze nakonfigurovat pro definování nejvyšší verzi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol, který budou používat služby, bez ohledu na verzi, kterou klient požaduje. To provedete tak, že zadáte <xref:System.Data.Services.Common.DataServiceProtocolVersion> hodnota <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> vlastnost <xref:System.Data.Services.DataServiceBehavior> používá službu data. Další informace najdete v tématu [konfigurace službu Data](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Pokud aplikace používá [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny pro přístup k datové služby, knihovny automaticky nastavit tyto hlavičky správné hodnoty, v závislosti na verzi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a funkce, které se používají ve vaší aplikaci. Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] používá nejnižší verze protokolu, který podporuje požadovanou operaci.  
  
 V následující tabulce jsou verze [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] a [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] , zahrnout [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporu pro určité verze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu.  
  
|[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Verze protokolu|Podpora byla zavedená v...|  
|-----------------------------------------------------------------------------------|----------------------------|  
|Verze 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]Aktualizace Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)]verze 3|  
|Verze 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-Aktualizace [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] SP1. Můžete stáhnout a nainstalovat aktualizaci z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=158125).<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)]verze 4|  
|Verze 3|-Stáhněte a nainstalujte na předprodejní verzi, která podporuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] verze 3 z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=203885).|  
  
### <a name="metadata-versions"></a>Verze metadat  
 Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] verze 1.1 CSDL používá k reprezentaci datový model. Toto je vždy případ datové modely, které jsou založeny na zprostředkovatele reflexe nebo poskytovatele služeb vlastní data. Pokud je však datového modelu definované za použití [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)], verzi CSDL vrátil, je stejná jako verze, který je používán [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. Verze CSDL je dáno obor názvů [Schema element](http://msdn.microsoft.com/en-us/396074d8-f99c-4f50-a073-68bce848224f). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]specifikace [ \[MC CSDL\]: koncepční formátu definičního souboru schématu](http://go.microsoft.com/fwlink/?LinkId=159072).  
  
 `DataServices` Také obsahuje element vrácený metadat `DataServiceVersion` atribut, který má stejnou hodnotu jako `DataServiceVersion` záhlaví ve zprávě s odpovědí. Klientské aplikace, jako **přidat odkaz na službu** dialogovém okně [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], tyto informace slouží k vytvoření klienta data služby tříd, které fungují správně s verzí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] který hostovat službu data. Další informace najdete v tématu [OData: Správa verzí protokolu](http://go.microsoft.com/fwlink/?LinkId=186071).  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Definování datových služeb WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
