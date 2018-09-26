---
title: Správa verzí datové služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 9a92346267012d3651d04648b357bbf530097e34
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204071"
---
# <a name="data-service-versioning-wcf-data-services"></a>Správa verzí datové služby (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Umožňuje vytvoření datové služby tak, aby klienti můžou přistupovat k datům jako prostředky pomocí identifikátorů URI, které jsou založeny na datovém modelu. OData podporuje také definice operace služby. Po počátečním nasazení a potenciálně několikrát během jejich životního cyklu mohou tyto datové služby musí změnit pro celou řadu důvodů, jako je například změna obchodních potřeb, požadavků informačních technologií, nebo jiných problémů. Pokud provedete změny do existující služby data, musíte zvážit, jestli se má definovat novou verzi vaše data služby a jak nejlepší k minimalizaci vlivu na existující klientské aplikace. Toto téma obsahuje pokyny pro kdy a jak vytvořit novou verzi datové služby. Také popisuje, jak služeb WCF Data Services zpracovává výměny mezi klienty a datových služeb, které podporují různé verze protokolu OData.

## <a name="versioning-a-wcf-data-service"></a>Správa verzí datové služby WCF
 Po nasazení dat. služby a spotřebovává data, změny ve službě data mohou mít potenciálně způsobit problémy s kompatibilitou s existujícím klientským aplikacím. Ale vzhledem k tomu, že změny jsou často vyžadované celkové obchodní potřeby služby, musíte zvážit, kdy a jak vytvořit novou verzi datové služby s nejmenší dopad na klientské aplikace.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Změn datových modelů, které doporučujeme nové verze datové služby
 Když zvažujete, jestli se má publikovat nové verze datové služby, je důležité pochopit, jak různé druhy změny mohou ovlivnit klientské aplikace. Změny dat službě, která může být nutné vytvořit novou verzi datové služby je možné rozdělit do těchto dvou kategorií:

-   Změny v kontraktu služby, mezi které patří aktualizace operace služby, změny přístupnost sady entit (kanály), verze změn a další změny chování služby.

-   Změny v kontraktu dat, které zahrnují změny do datového modelu, informační kanál formáty nebo informačního kanálu vlastní nastavení.

 Následující podrobnosti tabulky, pro jaké typy změn byste měli zvážit publikování nové verze datové služby:

|Typ změny|Vyžaduje nová verze|Není potřeba nové verze|
|--------------------|----------------------------|----------------------------|
|Operace služby|– Přidat nový parametr<br />– Změnit typ návratové hodnoty<br />-Odebrat operace služby|-Odstranit existující parametr<br />-Přidat nové operace služby|
|Chování služby|– Zakažte počet požadavků<br />-Zakázat podporu projekce<br />-Zvýšení verze požadované datové služby|-Aktivovat počet požadavků<br />-Povolit podporu projekce<br />-Snížit verze požadované datové služby|
|Sada entit oprávnění|-Omezení entity sady oprávnění<br />-Změna kódu odpovědi (nová hodnota první) <sup>1</sup>|-Zmírnit entity sady oprávnění<br />-Změna kódu odpovědi (stejné první hodnota)|
|Vlastnosti entity|-Odebrat existující vlastnost nebo vztahu<br />-Přidat vlastnost se zakázanou<br />– Změnit existující vlastnosti|-Přidat vlastnost nullable<sup>2</sup>|
|Sady entit|-Odebrat sady entit|-Přidat odvozený typ.<br />-Změna základního typu<br />– Přidání sady entit|
|Přizpůsobení informačního kanálu|– Změnit vlastnost entity mapování||

 <sup>1</sup> to může záviset na tom, jak přísně klientská aplikace spoléhá na příjem určitý kód chyby.

 <sup>2</sup> můžete nastavit <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> vlastnost `true` na váš klient bude ignorovat nových vlastností odesílané datové služby, které nejsou definovány v klientském počítači. Ale při vkládání si vlastnosti nejsou zahrnuty klientem v požadavku POST jsou nastaveny na výchozí hodnoty. V případě aktualizací může přepíšou všechna existující data ve vlastnosti Neznámý pro klienta s výchozími hodnotami. V takovém případě by měl odeslat aktualizace jako požadavek SLOUČENÍ, což je výchozí hodnota. Další informace najdete v tématu [Správa kontextu datové služby](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Jak verze datové služby
 V případě potřeby, nová verze datové služby je definován tak, že vytvoříte novou instanci služby s modelem aktualizovanou smlouvy nebo data. Tato nová služba je pak vystavena s použitím nového identifikátoru URI koncového bodu, který by jej odlišovala z předchozí verze. Příklad:

-   Starší verze: `http://services.odata.org/Northwind/v1/Northwind.svc/`

-   Nová verze: `http://services.odata.org/Northwind/v2/Northwind.svc/`

 Při upgradu datové služby, klientům bude nutné také aktualizovat založené na nové metadat datové služby a použití nového kořenového identifikátoru URI. Pokud je to možné, je vhodné ponechat předchozí verzi datové služby na podporu klientů, které ještě nebyly upgradovány na použití nové verze. Starší verze datové služby lze odebrat, pokud už nepotřebujete. Měli byste zvážit zachování koncový bod datové služby identifikátory URI v externí konfigurační soubor.

## <a name="odata-protocol-versions"></a>Verze protokolu OData
 Jak se vydávají nové verze protokolu OData, nemusí klientské aplikace používat stejné verze protokolu OData, který podporuje datové služby. Starší klientská aplikace může přístup ke službě data, která podporuje novější verze protokolu OData. Klientská aplikace může také používat novější verzi klientské knihovny služby WCF Data Services, která podporuje novější verze protokolu OData, než datové služby, která se právě využívají.

 Služby WCF Data Services využívá podpora poskytovaná OData ke zpracování scénářů správy verzí. Je také podpora pro vytvoření a používání metadat modelu dat k vytvoření klienta datové služby třídy, pokud klient používá jinou verzi protokolu OData, než data služba používá. Další informace najdete v tématu [OData: Správa verzí protokolu](https://go.microsoft.com/fwlink/?LinkId=186071).

### <a name="version-negotiation"></a>Vyjednávání verze
 Datové služby lze nastavit k definování nejvyšší verze protokolu OData, který bude používán službou, bez ohledu na verzi požadovaným klientem. Můžete to provést tak, že zadáte <xref:System.Data.Services.Common.DataServiceProtocolVersion> hodnota <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> vlastnost <xref:System.Data.Services.DataServiceBehavior> využívané ve službě data. Další informace najdete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

 Pokud aplikace používá tyto klientské knihovny služby WCF Data Services pro přístup k datové služby, knihovny automaticky nastaví tato záhlaví na správné hodnoty, podle verze protokolu OData a funkce, které se používají ve vaší aplikaci. Ve výchozím nastavení používá služeb WCF Data Services nejnižší verze protokolu, které podporuje požadovanou operaci.

 Následující tabulka obsahuje podrobnosti o verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] a [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] , které zahrnují podporu služeb WCF Data Services pro konkrétní verze protokolu OData.

|Verze protokolu OData|Podpora zavedený...|
|-----------------------------------------------------------------------------------|----------------------------|
|Verze 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Aktualizace Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] verze 3|
|Verze 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-Aktualizaci [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] SP1. Můžete stáhnout a nainstalovat aktualizaci z [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=158125).<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] verze 4|
|verze 3|-Můžete stáhnout a nainstalovat verzi předběžné verze, která podporuje OData verze 3 z [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=203885).|

### <a name="metadata-versions"></a>Verze metadat
 Ve výchozím nastavení používá služeb WCF Data Services verze 1.1 CSDL k reprezentaci datový model. To platí vždy pro datové modely, které jsou založeny na zprostředkovatel reflexe nebo poskytovatel služeb vlastní data. Pokud je však datového modelu definován pomocí [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)], verze CSDL vrátil, je shodná s verzí, který je používán [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. Verze CSDL je určeno obor názvů [element schématu](https://msdn.microsoft.com/library/396074d8-f99c-4f50-a073-68bce848224f). Další informace najdete v tématu specifikace [ \[MC CSDL\]: koncepční formátu definičního souboru schématu](https://go.microsoft.com/fwlink/?LinkId=159072).

 `DataServices` Také obsahuje element vrácených metadat `DataServiceVersion` atribut, který má stejnou hodnotu jako `DataServiceVersion` záhlaví ve zprávě s odpovědí. Klientské aplikace, jako **přidat odkaz na službu** dialogové okno v sadě Visual Studio, tyto informace slouží ke generování tříd klientské datové služby, které fungují správně s verzí datové služby WCF, který hostitelem datové služby. Další informace najdete v tématu [OData: Správa verzí protokolu](https://go.microsoft.com/fwlink/?LinkId=186071).

## <a name="see-also"></a>Viz také

- [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
