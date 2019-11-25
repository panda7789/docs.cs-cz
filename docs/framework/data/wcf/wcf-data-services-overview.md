---
title: Přehled WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: 21c09608bcf5d9f0b7bfc05b703d1ebe846a77bd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975053"
---
# <a name="wcf-data-services-overview"></a>Přehled WCF Data Services
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umožňuje vytvořit a spotřebovat datové služby pro web nebo intranet pomocí protokolu OData (Open Data Protocol). OData umožňuje vystavit data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI. To vám umožní přístup k datům a jejich změny pomocí sémantiky representational state transfer (REST), konkrétně standardní příkazy HTTP pro GET, PUT, POST a DELETE. V tomto tématu najdete Přehled vzorů a postupů definovaných v rámci služby OData a také o zařízeních poskytovaných [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], které využívají OData v aplikacích založených na .NET Framework.  
  
## <a name="address-data-as-resources"></a>Adresovat data jako prostředky  
 OData zpřístupňuje data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI. Cesty k prostředkům se vytvářejí na základě konvencí vztahů mezi entitami model EDM (Entity Data Model). V tomto modelu entity reprezentují provozní jednotky dat v doméně aplikace, jako jsou například zákazníci, objednávky, položky a produkty. Další informace najdete v tématu [model EDM (Entity Data Model)](../adonet/entity-data-model.md).  
  
 V rámci OData adresujte prostředky entit jako sadu entit, která obsahuje instance typů entit. Například identifikátor URI <https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders> vrátí všechny objednávky z datové služby `Northwind`, které se vztahují k zákazníkovi s hodnotou `CustomerID` `ALFKI.`  
  
 Výrazy dotazů umožňují provádět tradiční operace dotazů na prostředky, jako je filtrování, řazení a stránkování. Například identifikátor URI <https://services.odata.org/Northwind/Northwind.svc/Customers( ' ALFKI ')/Orders? $filter = dopravení gt 50 > filtruje prostředky, aby vracely pouze objednávky s náklady na dopravné na více než $50. Další informace najdete v tématu [přístup k prostředkům datové služby](accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Přístup k datům vzájemně ovladatelného  
 OData staví na standardních internetových protokolech, aby byly datové služby vzájemně ovladatelné s aplikacemi, které .NET Framework nepoužívají. Vzhledem k tomu, že je možné použít standardní identifikátory URI k adresování dat, může vaše aplikace přistupovat k datům a měnit je pomocí sémantiky representational state transfer (REST), konkrétně standardní příkazy HTTP GET, PUT, POST a DELETE. To vám umožní přístup k těmto službám z libovolného klienta, který může analyzovat a přistupovat k datům přenášeným přes standardní protokoly HTTP.  
  
 OData definuje sadu rozšíření protokolu AtomPub (Atom Publishing Protocol). Podporuje požadavky HTTP a odpovědi ve více než jednom formátu dat, aby se vešly na různé klientské aplikace a platformy. Datový kanál OData může představovat data ve atomech, JavaScript Object Notation (JSON) a jako prostý kód XML. I když je výchozí formát Atom, je formát informačního kanálu určen v hlavičce požadavku HTTP. Další informace najdete v tématu formát [OData: Atom](https://go.microsoft.com/fwlink/?LinkID=185794) a [Formát OData: JSON](https://go.microsoft.com/fwlink/?LinkID=185795).  
  
 Při publikování dat jako datového kanálu OData [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] spoléhá na další existující Internetová zařízení pro takové operace jako ukládání do mezipaměti a ověřování. K tomu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integrovat s existujícími hostujícími aplikacemi a službami, jako je ASP.NET, Windows Communication Foundation (WCF) a Internetová informační služba (IIS).  
  
## <a name="storage-independence"></a>Nezávislost úložiště  
 I když se prostředky řeší na základě modelu vztahů mezi entitami, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vystavovat kanály OData bez ohledu na podkladové zdroje dat. Po [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] přijme požadavek HTTP na prostředek, který identifikátor URI identifikuje, je žádost deserializovat a reprezentace tohoto požadavku se předává poskytovateli [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Tento zprostředkovatel přeloží požadavek do formátu specifického pro zdroj dat a provede požadavek na podkladovém zdroji dat. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dosahuje nezávislosti úložiště oddělením koncepčního modelu, který řeší prostředky předepsané službou OData z konkrétního schématu podkladového zdroje dat.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] se integruje s Entity Framework ADO.NET, které vám umožní vytvářet datové služby, které zpřístupňují relační data. Pomocí nástrojů model EDM (Entity Data Model) můžete vytvořit datový model, který obsahuje adresovatelné prostředky jako entity a zároveň definovat mapování mezi tímto modelem a tabulkami v podkladové databázi. Další informace najdete v tématu [poskytovatel Entity Framework](entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] také umožňuje vytvářet datové služby, které zveřejňují datové struktury, které vracejí implementaci rozhraní <xref:System.Linq.IQueryable%601>. Díky tomu můžete vytvářet datové služby, které zveřejňují data z .NET Frameworkch typů. Operace CREATE, Update a DELETE jsou podporovány při implementaci rozhraní <xref:System.Data.Services.IUpdatable>. Další informace najdete v tématu [Zprostředkovatel reflexe](reflection-provider-wcf-data-services.md).  
  
 Ilustraci, jak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integrovat s těmito poskytovateli dat, najdete v diagramu architektury dále v tomto tématu.  
  
## <a name="custom-business-logic"></a>Vlastní obchodní logika  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umožňuje snadno přidat vlastní obchodní logiku k datové službě prostřednictvím operací a zachycení služby. Operace služby jsou metody definované na serveru, které jsou adresovatelné identifikátory URI ve stejném tvaru jako datové prostředky. Operace služby mohou také pomocí syntaxe výrazu dotazu filtrovat, seřadit a stránková data vrácená operací. Identifikátor URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` například představuje volání operace služby s názvem `GetOrdersByCity` ve službě Northwind data Service, která vrací objednávky pro zákazníky z Londýna a stránkované výsledky seřazené podle `OrderDate`. Další informace najdete v tématu [provozní operace](service-operations-wcf-data-services.md).  
  
 Zachycení umožňují integrovat vlastní logiku aplikace do zpracování zpráv požadavku nebo odpovědí datovou službou. Zachycení jsou volána, když dojde k akci dotazování, vložení, aktualizace nebo odstranění v zadané sadě entit. Zachytávací pak může data změnit, vymáhat zásady autorizace nebo dokonce ukončit operaci. Metody pro zachycování musí být explicitně registrovány pro danou sadu entit, která je vystavena datovou službou. Další informace naleznete v tématu [zachycení](interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Klientské knihovny  
 OData definuje sadu jednotných vzorů pro interakci s datovými službami. To vám umožní vytvořit opakovaně použitelné komponenty, které jsou založeny na těchto službách, jako jsou například knihovny na straně klienta, které usnadňují využívání datových služeb.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsahuje klientské knihovny pro klientské aplikace založené na .NET Framework a Silverlight. Tyto klientské knihovny umožňují pracovat s datovými službami pomocí .NET Framework objektů. Podporují taky dotazy založené na objektech a dotazy LINQ, načítají se související objekty, sledování změn a rozlišení identity. Další informace najdete v tématu [WCF Data Services Klientská knihovna](wcf-data-services-client-library.md).  
  
 Kromě klientských knihoven OData obsažených v .NET Framework a s programem Silverlight jsou k dispozici další klientské knihovny, které vám umožní využívat v klientských aplikacích kanál OData, jako jsou například aplikace PHP, AJAX a Java. Další informace najdete v tématu [sada OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Přehled architektury  
 Následující diagram znázorňuje architekturu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pro vystavení kanálů OData a používání těchto informačních kanálů v knihovnách klienta s povolenou OData:  
  
 ![Snímek obrazovky znázorňující diagram architektury WCF Data Services](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Viz také:

- [WCF Data Services 4.5](index.md)
- [Začínáme](getting-started-with-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Přístup k prostředkům datové služby (WCF Data Services)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Převádění stavu reprezentace (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
