---
title: WCF Data Services 4.5
description: Přečtěte si o WCF Data Services, .NET Framework komponentě, která podporuje služby pro vystavení a využití dat pomocí sémantiky REST.
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: ca6b196e8c910f97ead6d1df5b6c0dd6c49c68a4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247750"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

WCF Data Services (dříve označované jako "ADO.NET Data Services") je součástí .NET Framework, která umožňuje vytvářet služby, které používají protokol OData (Open Data Protocol) k vystavování a využívání dat prostřednictvím webu nebo intranetu, a to pomocí sémantiky opětovného [přenosu stavu (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm). OData zpřístupňuje data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI. Data se získávají a mění pomocí standardních příkazů HTTP GET, PUT, POST a DELETE. OData používá konvence vztahů mezi entitami [model EDM (Entity Data Model)](../adonet/entity-data-model.md) k vystavení prostředků jako sady entit, které souvisejí s přidruženími.

WCF Data Services používá protokol OData k adresování a aktualizaci prostředků. Tímto způsobem můžete získat přístup k těmto službám z libovolného klienta, který podporuje OData. OData umožňuje vyžádat a zapsat data do prostředků pomocí známých formátů přenosu: Atom, sady standardů pro výměnu a aktualizaci dat ve formátu XML a JavaScript Object Notation (JSON), textový formát výměny dat založený na rozsáhlých aplikacích v AJAX.

WCF Data Services můžou vystavovat data, která pocházejí z různých zdrojů, jako kanály OData. Nástroje sady Visual Studio usnadňují vytvoření služby založené na protokolu OData pomocí Entity Framework datového modelu ADO.NET. Můžete také vytvořit kanály OData na základě tříd modulu CLR (Common Language Runtime) a dokonce i pozdě vázaných nebo netypových dat.

WCF Data Services taky obsahuje sadu klientských knihoven, jednu pro obecné .NET Framework klientské aplikace a další specificky pro aplikace založené na programu Silverlight. Tyto klientské knihovny poskytují model programování založený na objektech při přístupu k datovému kanálu OData z prostředí, jako jsou .NET Framework a Silverlight.

## <a name="where-should-i-start"></a>Kde mám začít?

V závislosti na vašich zájmech zvažte, jak začít s WCF Data Services v jednom z následujících témat.

Chci se pustit přímo v...

- [Rychlé zprovoznění](quickstart-wcf-data-services.md)

- [Začínáme](getting-started-with-wcf-data-services.md)

Pouze zobrazit kód...

- [Rychlé zprovoznění](quickstart-wcf-data-services.md)

- [Postupy: Provádění dotazů v datové službě](how-to-execute-data-service-queries-wcf-data-services.md)

- [Postupy: Vytvoření vazby dat na elementy Windows Presentation Foundation](bind-data-to-wpf-elements-wcf-data-services.md)

Chci se dozvědět víc o OData...

- [Dokument White Paper: představení OData](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [Web s otevřeným datovým protokolem](https://www.odata.org/)
- [OData: SDK](https://www.odata.org/ecosystem/)

Chci se podívat na ucelené ukázky...

- [Rychlý Start WCF Data Services](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))
- [OData SDK – ukázkový kód](https://www.odata.org/ecosystem/#sdk)

Jak se integruje se sadou Visual Studio?

- [Generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md)

- [Vytvoření datové služby](creating-the-data-service.md)

- [Zprostředkovatel Entity Framework](entity-framework-provider-wcf-data-services.md)

Co s tím můžu dělat?

- [Přehled](wcf-data-services-overview.md)

- [Scénáře aplikací](application-scenarios-wcf-data-services.md)

Chci použít LINQ...

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)

- [Aspekty LINQ](linq-considerations-wcf-data-services.md)

- [Postupy: Provádění dotazů v datové službě](how-to-execute-data-service-queries-wcf-data-services.md)

Pořád ještě potřebuji nějaké další informace...

- [Blog týmu WCF Data Services](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [Zdroje informací](wcf-data-services-resources.md)

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

## <a name="see-also"></a>Viz také

- [Převádění stavu reprezentace (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
