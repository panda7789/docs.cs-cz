---
title: Správa verzí datové služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: f82ab4c98e724bbed658a6c77de9c5a5d5c3390f
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121526"
---
# <a name="data-service-versioning-wcf-data-services"></a>Správa verzí datové služby (WCF Data Services)
Protokol OData (Open Data Protocol) umožňuje vytvářet datové služby tak, aby klienti měli přístup k datům jako k prostředkům pomocí identifikátorů URI založených na datovém modelu. OData také podporuje definici operací služby. Po počátečním nasazení a potenciálně několikrát během jejich životnosti může být nutné tyto datové služby změnit z různých důvodů, jako je například změna obchodních potřeb, požadavky na informační technologie nebo řešení dalších problémů. Při provádění změn v existující datové službě je třeba zvážit, zda definovat novou verzi datové služby a jak nejlépe minimalizovat dopad na existující klientské aplikace. Toto téma obsahuje pokyny, kdy a jak vytvořit novou verzi datové služby. Popisuje také, jak WCF Data Services zpracovává výměnu mezi klienty a datových služeb, které podporují různé verze protokolu OData.

## <a name="versioning-a-wcf-data-service"></a>Správa verzí datové služby WCF
 Jakmile je datová služba nasazena a data jsou spotřebována, změny datové služby mohou způsobit problémy s kompatibilitou s existujícími klientskými aplikacemi. Protože však změny jsou často vyžadovány celkovými obchodními potřebami služby, je třeba zvážit, kdy a jak vytvořit novou verzi datové služby s nejmenším dopadem na klientské aplikace.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Změny datového modelu, které doporučují novou verzi datové služby
 Při zvažování, zda chcete publikovat novou verzi datové služby, je důležité pochopit, jak různé druhy změn mohou ovlivnit klientské aplikace. Změny datové služby, které mohou vyžadovat vytvoření nové verze datové služby, lze rozdělit do následujících dvou kategorií:

- Změny servisní smlouvy , které zahrnují aktualizace servisních operací, změny přístupnosti sad entit (informačníkanály), změny verzí a další změny chování služby.

- Změny smlouvy o datech, které zahrnují změny datového modelu, formátů informačních kanálů nebo vlastního nastavení informačního kanálu.

 V následující tabulce jsou uvedeny podrobnosti o typech změn, které byste měli zvážit publikování nové verze datové služby:

|Typ změny|Vyžaduje novou verzi|Nová verze není potřeba|
|--------------------|----------------------------|----------------------------|
|Servisní operace|- Přidat nový parametr<br />- Změna návratového typu<br />- Odebrání servisního provozu|- Odstranit existující parametr<br />- Přidat novou službu|
|Chování služby|- Zakázat počet požadavků<br />- Zakázat podporu projekce<br />- Zvýšit požadovanou verzi datové služby|- Povolit požadavky na počet<br />- Povolit podporu projekce<br />- Snížení požadované verze datové služby|
|Oprávnění sady entit|- Omezit oprávnění k nastavení entity<br />- Změna kódu odpovědi (nová hodnota první číslice) <sup>1</sup>|- Oprávnění k nastavení relaxentity<br />- Změna kódu odpovědi (stejná hodnota první číslice)|
|Vlastnosti entity|- Odebrání existující vlastnosti nebo vztahu<br />- Přidat vlastnost, která by neuplatnovala hodnotu neplatné<br />- Změna existující vlastnosti|- Přidat vlastnost, která může být null<sup>2</sup>|
|Sady entit|- Odebrat sadu entit|- Přidat odvozený typ<br />- Změna základního typu<br />- Přidat sadu entit|
|Přizpůsobení informačního kanálu|- Změna mapování entity-vlastnosti||

 <sup>1</sup> To může záviset na tom, jak přísně klientská aplikace závisí na přijetí konkrétního kódu chyby.

 <sup>2</sup> Vlastnost můžete <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> nastavit `true` tak, aby klient ignoroval všechny nové vlastnosti odeslané datovou službou, které nejsou v klientovi definovány. Však při vložení, vlastnosti, které nejsou zahrnuty klientem v požadavku POST jsou nastaveny na jejich výchozí hodnoty. Pro aktualizace mohou být všechna existující data ve vlastnosti, kterou klient klient neznal, přepsána výchozími hodnotami. V takovém případě byste měli odeslat aktualizaci jako požadavek MERGE, což je výchozí. Další informace naleznete [v tématu Správa kontextu datové služby](managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Jak na verzi datové služby
 V případě potřeby je nová verze datové služby definována vytvořením nové instance služby s aktualizovanou smlouvou o poskytování služeb nebo datovým modelem. Tato nová služba je pak vystavena pomocí nového koncového bodu URI, který ji odlišuje od předchozí verze. Příklad:

- Stará verze:`http://services.odata.org/Northwind/v1/Northwind.svc/`

- Nová verze:`http://services.odata.org/Northwind/v2/Northwind.svc/`

 Při inovaci datové služby bude nutné klienty také aktualizovat na základě nových metadat datové služby a použít nový kořenový identifikátor URI. Pokud je to možné, měli byste udržovat předchozí verzi datové služby pro podporu klientů, kteří ještě nebyli upgradováni na použití nové verze. Starší verze datové služby lze odebrat, pokud již nejsou potřeba. Měli byste zvážit zachování identifikátoru URI koncového bodu datové služby v externím konfiguračním souboru.

## <a name="odata-protocol-versions"></a>Verze protokolu OData
 Při vydání nových verzí OData nemusí klientské aplikace používat stejnou verzi protokolu OData, kterou datová služba podporuje. Starší klientská aplikace může přistupovat k datové službě, která podporuje novější verzi OData. Klientská aplikace může také používat novější verzi klientské knihovny WCF Data Services, která podporuje novější verzi OData než datová služba, která je přístupná.

 WCF Data Services využívá podporu poskytovanou OData ke zpracování těchto scénářů správy verzí. K dispozici je také podpora pro generování a používání metadat datového modelu k vytvoření tříd klientské datové služby, když klient používá jinou verzi OData, než používá datová služba. Další informace naleznete v části Protocol Versioning v článku [OData: Přehled.](https://www.odata.org/documentation/odata-version-2-0/overview/)

### <a name="version-negotiation"></a>Vyjednávání verze
 Datovou službu lze nakonfigurovat tak, aby definovala nejvyšší verzi protokolu OData, kterou bude služba používat, bez ohledu na verzi požadovanou klientem. Můžete to provést zadáním <xref:System.Data.Services.Common.DataServiceProtocolVersion> hodnoty <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> pro vlastnost <xref:System.Data.Services.DataServiceBehavior> používané datovou službou. Další informace naleznete [v tématu Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).

 Pokud aplikace používá klientské knihovny WCF Data Services pro přístup k datové službě, knihovny automaticky nastaví tyto hlavičky na správné hodnoty v závislosti na verzi OData a funkcích, které se používají ve vaší aplikaci. Ve výchozím nastavení používá služba WCF Data Services nejnižší verzi protokolu, která podporuje požadovanou operaci.

 V následující tabulce jsou uvedeny podrobnosti o verzích rozhraní .NET Framework a Silverlight, které zahrnují podporu wcf datových služeb pro konkrétní verze protokolu OData.

|Verze protokolu OData|Podpora zavedena v...|
|-----------------------------------------------------------------------------------|----------------------------|
|Verze 1|- Rozhraní .NET Framework 3.5 Service Pack 1 (SP1)<br />- Silverlight verze 3|
|Verze 2|- Rozhraní .NET Framework 4<br />- Silverlight verze 4|

### <a name="metadata-versions"></a>Verze metadat
 Ve výchozím nastavení wcf datové služby používá verzi 1.1 CSDL představují datový model. To je vždy případ pro datové modely, které jsou založeny na zprostředkovatele odrazu nebo vlastní poskytovatele datových služeb. Pokud je však datový model definován pomocí entity Framework, verze vrácené CSDL je stejná jako verze, která je používána entity framework. Verze CSDL je určena oborem názvů [elementu Schema (CSDL).](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl)

 Prvek `DataServices` vrácených metadat také obsahuje `DataServiceVersion` atribut, což je stejná hodnota jako `DataServiceVersion` záhlaví ve zprávě odpovědi. Klientské aplikace, jako je například dialogové okno **Přidat odkaz na službu** v sadě Visual Studio, používají tyto informace ke generování tříd klientských datových služeb, které správně fungují s verzí datové služby WCF, která je hostitelem datové služby. Další informace naleznete v části Protocol Versioning v článku [OData: Přehled.](https://www.odata.org/documentation/odata-version-2-0/overview/)

## <a name="see-also"></a>Viz také

- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
