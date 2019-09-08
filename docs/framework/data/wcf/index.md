---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 017fe2177cf824d461b4c51ea805f75b6ddbe064
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779987"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

WCF Data Services (dříve označované jako "ADO.NET Data Services") je součástí .NET Framework, která umožňuje vytvářet služby, které používají [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] k vystavení a využívání dat prostřednictvím webu nebo intranetu, a to pomocí sémantiky opětovného [stavu prezentace. přenos (REST)](https://go.microsoft.com/fwlink/?LinkId=113919). OData zpřístupňuje data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI. Data se získávají a mění pomocí standardních příkazů HTTP GET, PUT, POST a DELETE. OData používá konvence vztahů mezi entitami [model EDM (Entity Data Model)](../adonet/entity-data-model.md) k vystavení prostředků jako sady entit, které souvisejí s přidruženími.

WCF Data Services používá protokol OData k adresování a aktualizaci prostředků. Tímto způsobem můžete získat přístup k těmto službám z libovolného klienta, který podporuje OData. OData umožňuje vyžádat a zapsat data do prostředků pomocí známých formátů přenosu: Atom, sada standardů pro výměnu a aktualizaci dat ve formátu XML a JavaScript Object Notation (JSON), textový formát výměny dat založený na rozsáhlých aplikacích v AJAX.

WCF Data Services můžou vystavovat data, která pocházejí z různých zdrojů, jako kanály OData. Nástroje sady Visual Studio usnadňují vytvoření služby založené na protokolu OData pomocí Entity Framework datového modelu ADO.NET. Můžete také vytvořit kanály OData na základě tříd modulu CLR (Common Language Runtime) a dokonce i pozdě vázaných nebo netypových dat.

WCF Data Services taky obsahuje sadu klientských knihoven, jednu pro obecné .NET Framework klientské aplikace a další specificky pro aplikace založené na programu Silverlight. Tyto klientské knihovny poskytují model programování založený na objektech při přístupu k datovému kanálu OData z prostředí, jako jsou .NET Framework a Silverlight.

## <a name="where-should-i-start"></a>Kde mám začít?

V závislosti na vašich zájmech zvažte, jak začít s WCF Data Services v jednom z následujících témat.

Chci se pustit přímo v...

- [Rychlý start](quickstart-wcf-data-services.md)

- [Začínáme](getting-started-with-wcf-data-services.md)

- [Rychlý Start pro Silverlight](https://go.microsoft.com/fwlink/?LinkID=192782)

- [Rychlý Start k programu Silverlight pro Windows Phone vývoj](https://go.microsoft.com/fwlink/?LinkID=214535)

Pouze zobrazit kód...

- [Rychlý start](quickstart-wcf-data-services.md)

- [Postupy: Spouštění dotazů datové služby](how-to-execute-data-service-queries-wcf-data-services.md)

- [Postupy: Vázání dat na prvky Windows Presentation Foundation](bind-data-to-wpf-elements-wcf-data-services.md)

Chci se dozvědět víc o OData...

- [Dokument White Paper Představujeme OData](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Otevřít web datového protokolu](https://go.microsoft.com/fwlink/?LinkID=184554)

- [OData: SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

- [OData: Nejčastější dotazy](https://go.microsoft.com/fwlink/?LinkId=185867)

Chci sledovat některá videa...

- [Příručka pro začátečníky k WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=220864)

- [Videa pro vývojáře WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=220861)

- [OData: Web pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=185866)

Chci se podívat na ucelené ukázky...

- [Ukázka dokumentace WCF Data Services v galerii ukázek na webu MSDN](https://go.microsoft.com/fwlink/?LinkID=220865)

- [Další ukázky WCF Data Services v galerii ukázek na webu MSDN](https://go.microsoft.com/fwlink/?LinkId=220866)

- [OData: SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

Jak se integruje se sadou Visual Studio?

- [Generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md)

- [Vytvoření datové služby](creating-the-data-service.md)

- [Zprostředkovatel Entity Framework](entity-framework-provider-wcf-data-services.md)

Co s tím můžu dělat?

- [Přehled](wcf-data-services-overview.md)

- [Dokument White Paper Představujeme OData](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Scénáře aplikací](application-scenarios-wcf-data-services.md)

Chci použít Silverlight...

- [Rychlý Start pro Silverlight](https://go.microsoft.com/fwlink/?LinkID=192782)

- [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

- [Začínáme s Silverlightem](https://go.microsoft.com/fwlink/?LinkId=148366)

Chci použít LINQ...

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)

- [Aspekty LINQ](linq-considerations-wcf-data-services.md)

- [Postupy: Spouštění dotazů datové služby](how-to-execute-data-service-queries-wcf-data-services.md)

Pořád ještě potřebuji nějaké další informace...

- [Blog týmu WCF Data Services](https://go.microsoft.com/fwlink/?LinkID=150511)

- [Prostředky](wcf-data-services-resources.md)

- [Centrum pro vývojáře WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=220868)

- [Otevřít web datového protokolu](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>V tomto oddílu

[Přehled](wcf-data-services-overview.md)

Poskytuje přehled funkcí a funkcí, které jsou k dispozici v WCF Data Services.

[Co je nového v WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

Popisuje nové funkce v WCF Data Services a podporu pro nové funkce OData.

[Začínáme](getting-started-with-wcf-data-services.md)

Popisuje, jak vystavit a využívat kanály OData pomocí WCF Data Services.

[Definování datových služeb WCF Data Services](defining-wcf-data-services.md)

Popisuje, jak vytvořit a nakonfigurovat datovou službu, která zveřejňuje kanály OData.

[Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)

Popisuje použití klientských knihoven ke využívání kanálů OData z klientské aplikace .NET Framework.

## <a name="see-also"></a>Viz také:

- [Převádění stavu reprezentace (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
