---
title: Použití datové služby v klientské aplikaci (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: 092f073a138a09fc25b96fbddde5b73992056981
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732245"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Použití datové služby v klientské aplikaci (WCF Data Services)
Můžete přístup ke službě, která zveřejňuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu zadáním identifikátor URI pro webový prohlížeč. Identifikátor URI poskytuje adresu prostředku a zpráv žádostí se odesílají na tyto adresy k přístupu nebo změnám podkladová data, která představuje prostředek. Prohlížeč vydá příkaz HTTP GET a vrátí jako požadovaný prostředek [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu. Další informace najdete v tématu [přístupu ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 I když může být užitečné pro testování, které webový prohlížeč [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služba vrací očekávaná data produkční [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby, které můžete také vytvářet, aktualizovat a odstraňovat data jsou obecně dostupné přes kód aplikace nebo skriptovacích jazyků na webové stránce. Toto téma obsahuje přehled o tom, jak přistupovat k [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály z klientské aplikace.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Přístup k a se měnícími daty pomocí sémantiky REST  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pomáhá zajistit interoperabilitu mezi službami, které zveřejňují [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály a aplikací, které využívají [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály. Aplikace získávat přístup a měnit data v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-odesláním zprávy s požadavkem na konkrétní akci HTTP a s identifikátorem URI, který adresuje prostředek entity, proti kterému by provádět akce na základě služby. Když je nutné zadat entity data, je předána jako datové části je konkrétně kódovaný v textu zprávy.  
  
### <a name="http-actions"></a>Akce HTTP  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] podporuje následující akce HTTP k provedení vytvořit, číst, aktualizovat a odstraňovat operace s daty entit, který představuje adresovaný prostředků:  
  
-   **HTTP GET** – jedná se o výchozí akci, když prostředek přistupuje z prohlížeče. Žádné datové části není zadána ve zprávy s požadavkem, a vrátí odpověď metody s datovou částí, která obsahuje požadovaná data.  
  
-   **HTTP POST** – vloží nový data entity do zadaného prostředku. Dat má být vložen je zadána v datové části zprávy s požadavkem. Datová část zprávy s odpovědí obsahuje data pro nově vytvořené entity. To zahrnuje všechny automaticky generované hodnoty klíče. Hlavička také obsahuje identifikátor URI, který adresuje nový prostředek entity.  
  
-   **HTTP DELETE** -odstraní data entity, který představuje zadaný prostředek. Datovou část, která není součástí zprávy požadavku nebo odpovědi.  
  
-   **HTTP PUT** – nahradí stávající data entity na požadovaný prostředek s novými daty, která je zadaná v datové části zprávy s požadavkem.  
  
-   **Sloučit HTTP** – z důvodu nedostatečné efektivity při provádění delete, za nímž následuje vložení ve zdroji dat stejně, chcete-li změnit entity data [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zavádí novou akci HTTP SLOUČENÍ. Datová část požadavku obsahuje vlastnosti, které musí být změněny na prostředek adresovaný entity. Protože sloučit HTTP není definováno ve specifikaci protokolu HTTP, může vyžadovat další zpracování směrovat žádost HTTP sloučit prostřednictvím jinou hodnotu než[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] clustery serverů.  
  
 Další informace najdete v tématu [OData: operace](https://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Formáty datových částí  
 Pro HTTP PUT, POST protokolu HTTP nebo HTTP SLOUČENÍ žádosti datovou část zprávy požadavku obsahuje data entity, která odesíláte do datové služby. Obsah datové části závisí na formát dat zprávy. Odpovědí HTTP na všechny akce s výjimkou odstranění, také obsahovat tyto datové části. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] podporuje následující formáty datové části pro přístup k a změna dat uložených ve službě:  
  
-   **Atom** – kódování zpráv na základě jazyka XML, který je definován [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jako rozšíření Atom publikování protokol (AtomPub) umožňující výměny dat prostřednictvím protokolu HTTP webové informační kanály, podcasty, wikiweby a založený na formátu XML internetové funkce. Další informace najdete v tématu [OData: formát Atom](https://go.microsoft.com/fwlink/?LinkId=185794).  
  
-   **JSON** – zápis JSON (JavaScript Object) je formát pro výměnu zjednodušené data, která je založena na podmnožinu programovací jazyk JavaScript. Další informace najdete v tématu [OData: formát JSON](https://go.microsoft.com/fwlink/?LinkId=185795).  
  
 Formát zprávy datové části je požadováno v záhlaví zprávy s požadavkem HTTP. Další informace najdete v tématu [OData: operace](https://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Přístup a změnu dat s využitím klientské knihovny  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsahuje klientské knihovny, které vám umožní snadněji využívat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] obálek rozhraní .NET Framework a klienta založeného na technologii Silverlight aplikace. Tyto knihovny zjednodušují posílat a přijímat zprávy HTTP. Převede uzel se také datovou část zprávy do CLR objektů, které představují entity data. Tyto klientské knihovny funkce dvě základní třídy <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601>. Tyto třídy umožňují dotazování datové služby a poté pracovat s daty vrácenou entitu jako objekty CLR. Další informace najdete v tématu [klientské knihovny WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) a [služeb WCF Data Services (Silverlight)](https://msdn.microsoft.com/library/c0cd9f4b-1372-48e4-9935-c8421239da30).  
  
 Můžete použít **přidat odkaz na službu** dialogového okna v sadě Visual Studio se přidat odkaz na datovou službu. Tento nástroj požaduje metadata služby ze služby využívaných dat a vygeneruje <xref:System.Data.Services.Client.DataServiceContext> , která představuje datové služby a také vygeneruje tříd klientské datové služby, které představují entity. Další informace najdete v tématu [generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
 Nejsou k dispozici, můžete využívat programovací knihovny [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu do jiných typů klientských aplikací. Další informace najdete v tématu [OData SDK](https://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Viz také  
 [Přístup k prostředkům datové služby](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [Rychlý start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
