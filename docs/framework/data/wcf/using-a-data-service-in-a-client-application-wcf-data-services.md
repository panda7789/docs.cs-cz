---
title: Použití datové služby v klientské aplikaci (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: 050c1a67a367a6dd5175c535fe89fb0010ae8cbc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790292"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Použití datové služby v klientské aplikaci (WCF Data Services)
Ke službě, která zpřístupňuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informační kanál, můžete přistupovat zadáním identifikátoru URI do webového prohlížeče. Identifikátor URI poskytuje adresu prostředku a žádosti se odesílají na tyto adresy pro přístup k datům, která tento prostředek představuje, nebo jejich změnu. Prohlížeč vydá příkaz HTTP GET a vrátí požadovaný prostředek jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanál. Další informace najdete v tématu [přístup ke službě z webového prohlížeče](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 I když může být webový prohlížeč užitečný pro testování, že [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služba vrátí očekávaná data, provozní [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby, které umožňují také vytvářet, aktualizovat a odstraňovat data, jsou obecně dostupné pomocí kódu aplikace nebo skriptovacích jazyků. na webové stránce. Toto téma poskytuje přehled o tom, jak získat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] přístup k informačním kanálům z klientské aplikace.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Přístup k datům a jejich změna pomocí sémantiky REST  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]pomáhá zajistit interoperabilitu mezi službami, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] které zveřejňují informační kanály [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a aplikace, které využívají informační kanály. Aplikace přistupují a mění data v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]rámci služby odesláním zpráv požadavku na konkrétní akci HTTP a s identifikátorem URI, který řeší prostředek entity, vůči kterému by měla být akce provedena. Když je nutné zadat data entity, je zadána jako přímo kódovaná datová část v těle zprávy.  
  
### <a name="http-actions"></a>Akce HTTP  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]aplikace podporuje následující akce protokolu HTTP k provádění operací vytvoření, čtení, aktualizace a odstranění u dat entity, která je předmětem odkazovaného prostředku:  
  
- **HTTP GET** – jedná se o výchozí akci, když je prostředek přístupný z prohlížeče. Ve zprávě požadavku není zadána žádná datová část a je vrácena metoda odpovědi s datovou částí, která obsahuje požadovaná data.  
  
- **Http post** – vloží data nové entity do poskytnutého prostředku. Data, která mají být vložena, jsou uvedena v datové části zprávy požadavku. Datová část zprávy s odpovědí obsahuje data pro nově vytvořenou entitu. To zahrnuje všechny automaticky vygenerované hodnoty klíčů. Záhlaví obsahuje také identifikátor URI, který řeší nový prostředek entity.  
  
- **Http Delete** – odstraní data entity, která zadaný prostředek představuje. V žádostech a odpovědích není přítomna datová část.  
  
- **HTTP PUT** – nahradí existující data entity požadovaným prostředkem novými daty, která jsou uvedena v datové části zprávy požadavku.  
  
- **Sloučení http** – kvůli neefektivitám při provádění odstranění, po kterém následuje vložení ve zdroji dat, aby se změnila data entity [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] , zavádí novou akci sloučení http. Datová část zprávy požadavku obsahuje vlastnosti, které se musí změnit u prostředku s adresovánou entitou. Protože sloučení http není ve specifikaci http definované, může vyžadovat další zpracování pro směrování požadavku HTTP Merge přes[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] nepodporující servery.  
  
 Další informace najdete v tématu [OData: Operace](https://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Formáty datové části  
 V případě požadavku HTTP PUT, HTTP POST nebo HTTP MERGE datová část zprávy požadavku obsahuje data entity, která odešlete do datové služby. Obsah datové části závisí na formátu dat zprávy. Odpovědi HTTP na všechny akce kromě možnosti odstranit také obsahují takovou datovou část. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]podporuje následující formáty datové části pro přístup k datům a jejich změnu pomocí služby:  
  
- **Atom** – kódování zpráv založené na jazyce XML, které je definováno [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jako rozšíření protokolu AtomPub (Atom Publishing Protocol) pro povolení výměny dat přes protokol HTTP pro webové informační kanály, podcasty, wiki a internetové funkce založené na jazyce XML. Další informace najdete v tématu [OData: Formát](https://go.microsoft.com/fwlink/?LinkId=185794)Atom.  
  
- **JSON** -JavaScript Object Notation (JSON) je odlehčený formát pro výměnu dat, který je založen na podmnožině programovacího jazyka JavaScript. Další informace najdete v tématu [OData: Formát](https://go.microsoft.com/fwlink/?LinkId=185795)JSON.  
  
 Formát zprávy datové části je požadován v hlavičce zprávy s požadavkem protokolu HTTP. Další informace najdete v tématu [OData: Operace](https://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Přístup k datům a jejich změna pomocí klientských knihoven  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsahuje klientské knihovny, které vám umožní snadněji využívat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanál z .NET Framework a klientské aplikace založené na technologii Silverlight. Tyto knihovny zjednodušují posílání a přijímání zpráv HTTP. Také přeloží datovou část zprávy na objekty CLR, které představují data entity. Klientské knihovny funkce jsou dvě základní třídy <xref:System.Data.Services.Client.DataServiceContext> a. <xref:System.Data.Services.Client.DataServiceQuery%601> Tyto třídy vám umožní dotazovat se na datovou službu a pak pracovat s vrácenými daty entity jako s objekty CLR. Další informace najdete v tématu [WCF Data Services Klientská knihovna](wcf-data-services-client-library.md) a [WCF Data Services (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 Pomocí dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio můžete přidat odkaz na datovou službu. Tento nástroj požaduje metadata služby z odkazované datové služby a generuje <xref:System.Data.Services.Client.DataServiceContext> , který představuje datovou službu, a generuje také třídy služby data klienta, které představují entity. Další informace najdete v tématu [generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md).  
  
 K dispozici jsou programové knihovny, které můžete použít k využívání [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu v jiných typech klientských aplikací. Další informace najdete v tématu [sada OData SDK](https://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Viz také:

- [Přístup k prostředkům datové služby](accessing-data-service-resources-wcf-data-services.md)
- [Rychlý start](quickstart-wcf-data-services.md)
