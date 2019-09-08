---
title: Přehled WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: 66dd61210e36210f5444eb05355612eeb75c155a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790236"
---
# <a name="wcf-data-services-overview"></a>Přehled WCF Data Services
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje vytvořit a spotřebovat datové služby pro web nebo intranet pomocí [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]umožňuje vystavit data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI. To vám umožní přístup k datům a jejich změny pomocí sémantiky representational state transfer (REST), konkrétně standardní příkazy HTTP pro GET, PUT, POST a DELETE. V tomto tématu najdete Přehled vzorů a postupů definovaných nástrojem [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a také o zařízeních poskytovaných nástrojem, pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kterých můžete využívat aplikace založené na .NET Framework. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]  
  
## <a name="address-data-as-resources"></a>Adresovat data jako prostředky  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]zpřístupňuje data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI. Cesty k prostředkům se vytvářejí na základě konvencí vztahů mezi entitami model EDM (Entity Data Model). V tomto modelu entity reprezentují provozní jednotky dat v doméně aplikace, jako jsou například zákazníci, objednávky, položky a produkty. Další informace najdete v tématu [model EDM (Entity Data Model)](../adonet/entity-data-model.md).  
  
 V [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]nástroji je třeba adresovat prostředky entit jako sadu entit, která obsahuje instance typů entit. Identifikátor URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` například vrátí všechny objednávky `Northwind` z datové služby, které se vztahují `CustomerID` k zákazníkovi s hodnotou.`ALFKI.`  
  
 Výrazy dotazů umožňují provádět tradiční operace dotazů na prostředky, jako je filtrování, řazení a stránkování. Identifikátor URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` například filtruje prostředky tak, aby vracely pouze objednávky s náklady na přepravné na více než $50. Další informace najdete v tématu [přístup k prostředkům datové služby](accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Přístup k datům vzájemně ovladatelného  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Vytvoří na standardních internetových protokolech, aby byly datové služby vzájemně ovladatelné s aplikacemi, které .NET Framework nepoužívají. Vzhledem k tomu, že je možné použít standardní identifikátory URI k adresování dat, může vaše aplikace přistupovat k datům a měnit je pomocí sémantiky representational state transfer (REST), konkrétně standardní příkazy HTTP GET, PUT, POST a DELETE. To vám umožní přístup k těmto službám z libovolného klienta, který může analyzovat a přistupovat k datům přenášeným přes standardní protokoly HTTP.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definuje sadu rozšíření protokolu AtomPub (Atom Publishing Protocol). Podporuje požadavky HTTP a odpovědi ve více než jednom formátu dat, aby se vešly na různé klientské aplikace a platformy. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Informační kanál může představovat data ve atomech, JavaScript Object Notation (JSON) a jako prostý kód XML. I když je výchozí formát Atom, je formát informačního kanálu určen v hlavičce požadavku HTTP. Další informace najdete v tématu [OData: Formát](https://go.microsoft.com/fwlink/?LinkID=185794) Atom a [OData: Formát](https://go.microsoft.com/fwlink/?LinkID=185795)JSON.  
  
 Při publikování dat jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] informačního kanálu spoléhá na další existující Internetová zařízení pro takové operace jako ukládání do mezipaměti a ověřování. K tomuto [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] účelu se integruje s existujícími hostujícími aplikacemi a službami, jako jsou ASP.NET, Windows Communication Foundation (WCF) a Internetová informační služba (IIS).  
  
## <a name="storage-independence"></a>Nezávislost úložiště  
 I když se prostředky řeší na základě modelu vztahů mezi entitami [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zveřejňujte kanály bez ohledu na podkladové zdroje dat. Poté [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , co přijme požadavek HTTP na prostředek, který identifikátor URI identifikuje, je žádost deserializovat a reprezentace tohoto požadavku se předává [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] poskytovateli. Tento zprostředkovatel přeloží požadavek do formátu specifického pro zdroj dat a provede požadavek na podkladovém zdroji dat. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]dosahuje nezávislost úložiště oddělením koncepčního modelu, který řeší prostředky předepsané [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] z konkrétního schématu podkladového zdroje dat.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]integruje se s Entity Framework ADO.NET, aby bylo možné vytvářet datové služby, které zpřístupňují relační data. Pomocí nástrojů model EDM (Entity Data Model) můžete vytvořit datový model, který obsahuje adresovatelné prostředky jako entity a zároveň definovat mapování mezi tímto modelem a tabulkami v podkladové databázi. Další informace najdete v tématu [poskytovatel Entity Framework](entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]také umožňuje vytvářet datové služby, které zveřejňují datové struktury, které vracejí implementaci <xref:System.Linq.IQueryable%601> rozhraní. Díky tomu můžete vytvářet datové služby, které zveřejňují data z .NET Frameworkch typů. Operace CREATE, Update a DELETE jsou podporovány, Pokud implementujete <xref:System.Data.Services.IUpdatable> i rozhraní. Další informace najdete v tématu [Zprostředkovatel reflexe](reflection-provider-wcf-data-services.md).  
  
 Ilustraci, jak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integrovat s těmito poskytovateli dat, najdete v diagramu architektury dále v tomto tématu.  
  
## <a name="custom-business-logic"></a>Vlastní obchodní logika  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje snadno přidat vlastní obchodní logiku k datové službě prostřednictvím operací a zachycení služby. Operace služby jsou metody definované na serveru, které jsou adresovatelné identifikátory URI ve stejném tvaru jako datové prostředky. Operace služby mohou také pomocí syntaxe výrazu dotazu filtrovat, seřadit a stránková data vrácená operací. Identifikátor URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` například představuje volání operace služby s názvem `GetOrdersByCity` ve službě Northwind data Service, která vrací objednávky pro zákazníky z Londýna s stránkovanými výsledky seřazenými podle `OrderDate`. Další informace najdete v tématu [provozní operace](service-operations-wcf-data-services.md).  
  
 Zachycení umožňují integrovat vlastní logiku aplikace do zpracování zpráv požadavku nebo odpovědí datovou službou. Zachycení jsou volána, když dojde k akci dotazování, vložení, aktualizace nebo odstranění v zadané sadě entit. Zachytávací pak může data změnit, vymáhat zásady autorizace nebo dokonce ukončit operaci. Metody pro zachycování musí být explicitně registrovány pro danou sadu entit, která je vystavena datovou službou. Další informace naleznete v tématu [zachycení](interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Klientské knihovny  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definuje sadu jednotných vzorů pro interakci s datovými službami. To vám umožní vytvořit opakovaně použitelné komponenty, které jsou založeny na těchto službách, jako jsou například knihovny na straně klienta, které usnadňují využívání datových služeb.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsahuje klientské knihovny pro klientské aplikace založené na .NET Framework i na technologii Silverlight. Tyto klientské knihovny umožňují pracovat s datovými službami pomocí .NET Framework objektů. Podporují taky dotazy založené na objektech a dotazy LINQ, načítají se související objekty, sledování změn a rozlišení identity. Další informace najdete v tématu [WCF Data Services Klientská knihovna](wcf-data-services-client-library.md).  
  
 Kromě [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] klientských knihoven, které jsou součástí .NET Framework a s programem Silverlight, existují další klientské knihovny, které umožňují [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] využívat informační kanál v klientských aplikacích, například php, AJAX a aplikace Java. Další informace najdete v tématu [sada OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Přehled architektury  
 Následující diagram znázorňuje [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] architekturu pro [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] vystavení kanálů a používání těchto informačních kanálů [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]v povolených klientských knihovnách:  
  
 ![Snímek obrazovky znázorňující diagram architektury WCF Data Services](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Viz také:

- [WCF Data Services 4.5](index.md)
- [Začínáme](getting-started-with-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Přístup k prostředkům datové služby (WCF Data Services)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Převádění stavu reprezentace (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
