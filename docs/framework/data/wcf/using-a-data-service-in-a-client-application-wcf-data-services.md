---
title: Pomocí služby dat v aplikaci klienta (služby WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: b25489de9a64ba4f1938e4d52c1cc677a218495b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Pomocí služby dat v aplikaci klienta (služby WCF Data Services)
Službě, která zveřejňuje se můžete dostat [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu zadáním identifikátor URI pro webový prohlížeč. Identifikátor URI poskytuje adresu prostředku a tyto adresy přístup, nebo změňte základní data, která představuje prostředek se posílají zprávy požadavku. Prohlížeč vydá příkaz HTTP GET a vrátí jako požadovaný prostředek [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu. Další informace najdete v tématu [přístupu ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 I když může být užitečné pro testování, které webový prohlížeč [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služba vrací očekávaná data produkční [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby, které vám umožní také vytvářet, aktualizovat a odstraňovat data jsou obecně dostupné přes kód aplikace nebo skriptovací jazyky na webové stránce. Toto téma obsahuje přehled o přístup k [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály z klientské aplikace.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Přístup k a změna dat pomocí sémantiky REST.  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pomáhá zajistit interoperabilitu mezi službami, které zveřejňují [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačních kanálů a aplikace, které využívají [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály. Aplikace přístup a změnit data [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby odesláním zprávy žádosti konkrétní akce HTTP a s identifikátorem URI, která řeší prostředek entity, pro kterou akce je třeba provést. Když je nutné zadat entity data, je zadána jako konkrétně kódovaného datovou část v textu zprávy.  
  
### <a name="http-actions"></a>Akce HTTP  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] podporuje následující akce HTTP lze provádět vytvářet, číst, aktualizovat a odstraňovat operací na data entity, která představuje adresovaný prostředků:  
  
-   **HTTP GET** -Toto je výchozí akci při přístupu k prostředku z prohlížeče. Žádné datové části je zadaný ve zprávě požadavku a odpovědi metodu s datovou část, která obsahuje požadovaná data se vrátí.  
  
-   **HTTP POST** -vloží nová data entity do zadaný prostředek. Poskytuje data, která má být vložen v datové části zprávy požadavku. Datová část zprávy s odpovědí obsahuje data pro nově vytvořené entity. To zahrnuje všechny klíčové hodnoty generován automaticky. Záhlaví obsahuje také identifikátor URI, která řeší nový prostředek entity.  
  
-   **HTTP DELETE** -odstraní data entity, který představuje zadaný prostředek. Datové části není součástí zprávy požadavku nebo odpovědi.  
  
-   **HTTP PUT** – nahradí existující data entity na požadovaný prostředek se nová data, která se dodává v datové části zprávy požadavku.  
  
-   **SLOUČENÍ HTTP** – kvůli nedostatky při provádění odstranění následuje příkaz insert ve zdroji dat. Chcete-li změnit entity data, stejně [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zavádí novou akci HTTP SLOUČENÍ. Datová část zprávy požadavku obsahuje vlastnosti, které je třeba změnit na prostředek adresovaný entity. Protože SLOUČENÍ HTTP není definován v specifikace protokolu HTTP, že může vyžadovat další zpracování směrovat požadavek HTTP SLOUČENÍ prostřednictvím jinou hodnotu než[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] clustery serverů.  
  
 Další informace najdete v tématu [OData: operace](http://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Datová část formáty  
 Datová část zprávu požadavku HTTP PUT, POST protokolu HTTP, nebo požadavku HTTP SLOUČENÍ, obsahuje data entity, který odešlete do služby data. Obsah datové části závisí na formát dat zprávy. Odpovědí HTTP na všechny akce s výjimkou odstranit také obsahovat takové datové části. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] podporuje následující formáty datové části pro přístup k a změny dat ve službě:  
  
-   **Atom** – to znamená kódování zpráv na základě jazyka XML definované [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jako rozšíření pro publikování protokol Atom (AtomPub) přes protokol HTTP pro webové informační kanály, podcasty, wikiweby povolit výměny dat a funkce na základě XML Internetu. Další informace najdete v tématu [OData: formát Atom](http://go.microsoft.com/fwlink/?LinkId=185794).  
  
-   **JSON** -JavaScript Object Notation (JSON) je formát pro výměnu lightweight dat, který je založen na podmnožinu programovací jazyk JavaScript. Další informace najdete v tématu [OData: formát JSON](http://go.microsoft.com/fwlink/?LinkId=185795).  
  
 Formát zprávy datové části je požadována v záhlaví zprávy požadavku HTTP. Další informace najdete v tématu [OData: operace](http://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Přístup k a změna dat pomocí klientské knihovny  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zahrnuje knihovny klienta, které vám umožní snadno využívat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu z rozhraní .NET Framework a založená na technologii Silverlight klientské aplikace. Tyto knihovny zjednodušují odesílání a přijímání zpráv protokolu HTTP. Také se převede datové části zprávy do CLR objektů, které představují entity data. Knihovny klienta funkce dvě základní třídy <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601>. Tyto třídy umožňují dotazování datové služby a pak pracovat s daty vrácenou entitu jako objekty CLR. Další informace najdete v tématu [WCF Data Services klientské knihovny](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) a [datové služby WCF (Silverlight)](http://msdn.microsoft.com/library/c0cd9f4b-1372-48e4-9935-c8421239da30).  
  
 Můžete použít **přidat odkaz na službu** dialogové okno v sadě Visual Studio se přidat odkaz na datové služby. Tento nástroj požaduje metadata služby z odkazovaného datové služby a vygeneruje <xref:System.Data.Services.Client.DataServiceContext> která představuje datové služby, a také vygeneruje třídy klienta dat služby, které představují entity. Další informace najdete v tématu [generování dat služby klientské knihovny](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
 Nejsou k dispozici, můžete využívat programovací knihovny [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu v jiné druhy klientské aplikace. Další informace najdete v tématu [OData SDK](http://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Viz také  
 [Přístup k prostředkům datové služby](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [Rychlý start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
