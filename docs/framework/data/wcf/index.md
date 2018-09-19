---
title: Datové služby WCF 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 9ece2fe051855d0fd39556f56a4343ead2c437bc
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288128"
---
# <a name="wcf-data-services-45"></a>Datové služby WCF 4.5

Služby WCF Data Services (dříve označované jako "Služby ADO.NET Data Services") je součástí rozhraní .NET Framework, která umožňuje vytvářet služby, které používají [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] k vystavení a zpracování dat prostřednictvím webu nebo intranetu pomocí sémantiky [ (REST) Representational state transfer](https://go.microsoft.com/fwlink/?LinkId=113919). OData zveřejňuje data jako prostředky, které jsou adresovat pomocí identifikátorů URI. Data se získat přístup, změnit pomocí standardní příkazy HTTP z GET, PUT, POST a DELETE. Používá relace entity konvencí OData [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) vystavit prostředky jako sady entit, které se týkají přidružení.

Služby WCF Data Services používá protokol OData pro adresy a aktualizaci prostředků. Tímto způsobem přistupujete k těmto službám z libovolného klienta, který podporuje prostředí OData. OData umožňuje vyžádat a zapisovat data do zdroje s použitím dobře známé přenos formáty: Atom, sada standardů pro výměnu a aktualizace dat ve formátu XML, JavaScript Object Notation (JSON), často používají v AJAX formátu textová data systému exchange aplikace.

Datové služby WCF můžete zpřístupnit data, která pochází z různých zdrojů, jako k datovým kanálům OData. Nástroje sady Visual Studio usnadňují vytvoření služby založených na protokolu OData s použitím datový model ADO.NET Entity Framework. Můžete také vytvořit na základě běžné třídy language runtime (CLR) a dokonce i s pozdní vazbou nebo netypové datové kanály OData.

Služby WCF Data Services obsahuje také sada klientských knihoven, jeden pro obecné klientské aplikace rozhraní .NET Framework a druhý speciálně pro aplikace založené na technologii Silverlight. Tyto klientské knihovny poskytuje programovací model založený na objektu při přístupu z prostředí, jako je rozhraní .NET Framework a Silverlight datového kanálu OData.

## <a name="where-should-i-start"></a>Kde bych měl(a) začít?

V závislosti na vašich zájmech vezměte v úvahu Začínáme se službou WCF Data Services v jednom z následujících témat.

Chci pustit do práce …

-   [Rychlý start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

-   [Silverlight Quickstart](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [Silverlight Quickstart pro vývoj pro Windows Phone](https://go.microsoft.com/fwlink/?LinkID=214535)

Stačí ukázat kódu...

-   [Rychlý start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [Postupy: Provádění dotazů v datové službě](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

-   [Postupy: Vytvoření vazby dat na elementy Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

Chci vědět více o OData...

 -   [Dokument White Paper: Představujeme OData](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [Otevřít web Data protokolu](https://go.microsoft.com/fwlink/?LinkID=184554)

-   [OData: sady SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

-   [OData: Nejčastější dotazy](https://go.microsoft.com/fwlink/?LinkId=185867)

Chci některé videa...

-   [Průvodce pro začátečníky služeb WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=220864)

-   [WCF Data Services – video pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=220861)

-   [OData: Vývojáři webové stránky](https://go.microsoft.com/fwlink/?LinkId=185866)

Chci zobrazit-koncové ukázky...

-   [Dokumentace ke službě vzorky z Galerie ukázek MSDN služeb WCF Data Services](https://go.microsoft.com/fwlink/?LinkID=220865)

-   [Další WCF Data Services – ukázky na Galerie ukázek MSDN](https://go.microsoft.com/fwlink/?LinkId=220866)

-   [OData: sady SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

Jak zajistíte jejich integraci se sadou Visual Studio?

-   [Generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

-   [Vytvoření datové služby](../../../../docs/framework/data/wcf/creating-the-data-service.md)

-   [Zprostředkovatel Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

Co můžu dělat s ním?

-   [Přehled](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

-   [Dokument White Paper: Představujeme OData](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [Scénáře aplikací](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

Chci používat Silverlight...

-   [Silverlight Quickstart](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [Datové služby WCF (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

-   [Začínáme s aplikací Silverlight](https://go.microsoft.com/fwlink/?LinkId=148366)

Chci používat LINQ...

-   [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

-   [Aspekty LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

-   [Postupy: Provádění dotazů v datové službě](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

Potřebuji ještě nějaké další informace...

-   [Blog týmu služby WCF Data](https://go.microsoft.com/fwlink/?LinkID=150511)

-   [Prostředky](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

-   [Středisko pro vývojáře služby WCF Data](https://go.microsoft.com/fwlink/?LinkId=220868)

-   [Otevřít web Data protokolu](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>V tomto oddílu

 [Přehled](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

 Poskytuje přehled funkcí a možností, které jsou k dispozici ve službě WCF Data Services.

 [Co je nového ve službě WCF Data Services](https://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)

 Popisuje nové funkce služeb WCF Data Services a podpora pro nové funkce OData.

 [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

 Popisuje, jak vystavení a spotřebování informační kanály OData s použitím služeb WCF Data Services.

 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

 Popisuje postup vytvoření a konfigurace datové služby, která zveřejňuje informační kanály OData.

 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

 Popisuje, jak pomocí klientských knihoven využívat informačních kanálů OData z klientské aplikace rozhraní .NET Framework.

## <a name="see-also"></a>Viz také

- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
