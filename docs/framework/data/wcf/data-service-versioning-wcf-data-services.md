---
title: Správa verzí datových služeb (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: f2007e5c2fa638d64c5c1e0d6879e12c7bcc901d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854097"
---
# <a name="data-service-versioning-wcf-data-services"></a>Správa verzí datových služeb (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Umožňuje vytvořit datové služby, aby klienti měli přístup k datům jako k prostředkům pomocí identifikátorů URI, které jsou založeny na datovém modelu. OData podporuje taky definici operací služby. Po počátečním nasazení a potenciálně během své životnosti může být potřeba tyto datové služby změnit z nejrůznějších důvodů, jako jsou třeba změny obchodních potřeb, požadavky na informace o technologii nebo řešení dalších problémů. Pokud provedete změny v existující datové službě, je nutné zvážit, zda chcete definovat novou verzi datové služby a jak nejlépe minimalizovat dopad na existující klientské aplikace. V tomto tématu najdete pokyny, kdy a jak vytvořit novou verzi datové služby. Popisuje také, jak WCF Data Services zpracovává výměnu mezi klienty a datovými službami, které podporují různé verze protokolu OData.

## <a name="versioning-a-wcf-data-service"></a>Správa verzí datové služby WCF
 Jakmile je datová služba nasazená a data se spotřebovávají, můžou změny v datové službě způsobovat problémy s kompatibilitou se stávajícími klientskými aplikacemi. Vzhledem k tomu, že změny jsou často vyžadovány celkovými obchodními požadavky služby, je nutné vzít v úvahu, kdy a jak vytvořit novou verzi datové služby s nejmenším dopadem na klientské aplikace.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Změny datového modelu, které doporučují novou verzi datové služby
 Při zvažování, zda publikovat novou verzi datové služby, je důležité pochopit, jakým způsobem mohou mít různé druhy změn vliv na klientské aplikace. Změny datové služby, které mohou vyžadovat vytvoření nové verze datové služby, lze rozdělit do následujících dvou kategorií:

- Změny kontraktu služby – což zahrnuje aktualizace operací služby, změny dostupnosti sad entit (informační kanály), změny verzí a další změny chování služby.

- Změny kontraktu dat, které zahrnují změny v datovém modelu, formátech informačního kanálu nebo přizpůsobení informačního kanálu.

 V následující tabulce najdete podrobné informace o tom, jaké druhy změn byste měli zvážit při publikování nové verze datové služby:

|Typ změny|Vyžaduje novou verzi.|Nová verze není nutná.|
|--------------------|----------------------------|----------------------------|
|Operace služby|-Přidat nový parametr<br />-Změnit návratový typ<br />-Odebrat operaci služby|-Odstranit existující parametr<br />-Přidat novou operaci služby|
|Chování služby|-Zakázat požadavky na počet<br />-Zakázat podporu projekce<br />-Zvětšit požadovanou verzi datové služby|-Povolit požadavky na počet<br />-Povolit podporu projekce<br />-Snížit požadovanou verzi datové služby|
|Oprávnění sady entit|– Omezit oprávnění sady entit<br />-Změnit kód odpovědi (nová první hodnota číslice) <sup>1</sup>|– Zmírnit oprávnění sady entit<br />-Změnit kód odpovědi (stejná první hodnota číslice)|
|Vlastnosti entity|-Odebrat existující vlastnost nebo relaci<br />-Přidat vlastnost, která není null<br />-Změnit existující vlastnost|-Přidat vlastnost Nullable<sup>2</sup>|
|Sady entit|-Odebrat sadu entit|-Přidat odvozený typ<br />-Změnit základní typ<br />-Přidat sadu entit|
|Přizpůsobení informačního kanálu|-Změnit mapování vlastností entity||

 <sup>1</sup> Tato funkce může záviset na tom, jak čistě klientská aplikace spoléhá na přijetí konkrétního kódu chyby.

 <sup>2</sup> <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> vlastnost můžete nastavit tak `true` , aby klienta ignorovala všechny nové vlastnosti odesílané datovou službou, které nejsou definované v klientovi. Pokud jsou však vložena vložení, vlastnosti nezahrnuté klientem v požadavku POST jsou nastaveny na výchozí hodnoty. U aktualizací se můžou všechna existující data ve vlastnosti, která je pro klienta neznámá, přepsat výchozími hodnotami. V takovém případě byste měli aktualizaci odeslat jako požadavek sloučení, což je výchozí nastavení. Další informace najdete v tématu [Správa kontextu datové služby](managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Postup verze datové služby
 V případě potřeby je nová verze datové služby definovaná vytvořením nové instance služby s aktualizovaným servisním kontraktem nebo datovým modelem. Tato nová služba se pak zveřejní pomocí nového koncového bodu URI, který ho odlišuje od předchozí verze. Příklad:

- Stará verze:`http://services.odata.org/Northwind/v1/Northwind.svc/`

- Nová verze:`http://services.odata.org/Northwind/v2/Northwind.svc/`

 Při upgradu datové služby bude potřeba, aby se klienti aktualizovali taky na základě nových metadat datové služby a nového kořenového identifikátoru URI. Pokud je to možné, měli byste zachovat předchozí verzi datové služby, aby podporovala klienty, kteří se ještě neupgradovali na použití nové verze. Starší verze datové služby se dají odebrat, když už je nepotřebujete. Měli byste zvážit zachování identifikátoru URI koncového bodu datové služby v externím konfiguračním souboru.

## <a name="odata-protocol-versions"></a>Verze protokolu OData
 Při vydání nových verzí OData nemusí klientské aplikace používat stejnou verzi protokolu OData, jakou podporuje datová služba. Starší klientská aplikace může získat přístup k datové službě, která podporuje novější verzi OData. Klientská aplikace může také používat novější verzi knihovny WCF Data Services klienta, která podporuje novější verzi OData, než je služba, ke které se přistupovalo.

 WCF Data Services využívá podporu poskytovanou službou OData ke zpracování takových scénářů správy verzí. Existuje také podpora pro generování a používání metadat datového modelu k vytváření tříd klientských datových služeb, když klient používá jinou verzi OData než datová služba používá. Další informace najdete v tématu [OData: Správa verzí](https://go.microsoft.com/fwlink/?LinkId=186071)protokolu.

### <a name="version-negotiation"></a>Vyjednávání verze
 Datovou službu lze nakonfigurovat tak, aby definovala nejvyšší verzi protokolu OData, kterou bude služba používat, bez ohledu na verzi, kterou klient požaduje. To lze provést zadáním <xref:System.Data.Services.Common.DataServiceProtocolVersion> hodnoty <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> vlastnosti <xref:System.Data.Services.DataServiceBehavior> používané datovou službou. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).

 Když aplikace používá klientské knihovny WCF Data Services pro přístup k datové službě, knihovny automaticky nastaví tyto hlavičky na správné hodnoty v závislosti na verzi OData a funkcích, které jsou používány ve vaší aplikaci. Ve výchozím nastavení používá WCF Data Services nejnižší verzi protokolu, která podporuje požadovanou operaci.

 Následující tabulka obsahuje podrobnosti o verzích .NET Framework a Silverlightu, které zahrnují podporu WCF Data Services pro konkrétní verze protokolu OData.

|Verze protokolu OData|Podpora zavedená v...|
|-----------------------------------------------------------------------------------|----------------------------|
|Verze 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]Service Pack 1 (SP1)<br />– Silverlight verze 3|
|Verze 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />– Aktualizace [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] SP1. Aktualizaci můžete stáhnout a nainstalovat z webu [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=158125).<br />– Silverlight verze 4|
|Verze 3|– Můžete si stáhnout a nainstalovat předběžnou verzi, která podporuje OData verze 3 z webu [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=203885).|

### <a name="metadata-versions"></a>Verze metadat
 Ve výchozím nastavení WCF Data Services používá ke znázornění datového modelu verzi 1,1 CSDL. To je vždy případ datových modelů, které jsou založeny na poskytovateli reflexe nebo vlastním poskytovateli datových služeb. Pokud je však datový model definován pomocí Entity Framework, bude verze CSDL vrácena stejná jako verze, kterou používá Entity Framework. Verze CSDL je určena oborem názvů [elementu Schema (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl).

 Element vrácených metadat `DataServiceVersion` obsahuje také atribut, což je stejná hodnota jako `DataServiceVersion` záhlaví ve zprávě odpovědi. `DataServices` Klientské aplikace, jako je například dialogové okno **Přidat odkaz na službu** v aplikaci Visual Studio, používají tyto informace k vygenerování tříd klientských datových služeb, které fungují správně s verzí WCF Data Services, která je hostitelem datové služby. Další informace najdete v tématu [OData: Správa verzí](https://go.microsoft.com/fwlink/?LinkId=186071)protokolu.

## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
