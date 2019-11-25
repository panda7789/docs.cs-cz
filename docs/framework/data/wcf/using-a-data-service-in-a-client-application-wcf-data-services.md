---
title: Použití datové služby v klientské aplikaci (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: ccf003b915876a30eeb27b39066168fb22950292
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975098"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Použití datové služby v klientské aplikaci (WCF Data Services)
Ke službě, která zpřístupňuje informační kanál protokolu OData (Open Data Protocol), můžete přistupovat zadáním identifikátoru URI do webového prohlížeče. Identifikátor URI poskytuje adresu prostředku a žádosti se odesílají na tyto adresy pro přístup k datům, která tento prostředek představuje, nebo jejich změnu. Prohlížeč vydá příkaz HTTP GET a vrátí požadovaný prostředek jako kanál OData. Další informace najdete v tématu [přístup ke službě z webového prohlížeče](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 I když může být webový prohlížeč užitečný při testování, že služba OData vrátí očekávaná data, produkční služby OData, které umožňují také vytvářet, aktualizovat a odstraňovat data, jsou obecně dostupné pomocí kódu aplikace nebo skriptovacích jazyků na webové stránce. Toto téma poskytuje přehled o tom, jak přistupovat k kanálům OData z klientské aplikace.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Přístup k datům a jejich změna pomocí sémantiky REST  
 OData pomáhá zajistit vzájemnou spolupráci mezi službami, které zveřejňují kanály OData a aplikace, které využívají kanály OData. Aplikace přistupují a mění data ve službě založené na protokolu OData odesláním zpráv požadavku na konkrétní akci HTTP a s identifikátorem URI, který řeší prostředek entity, vůči kterému by měla být akce provedena. Když je nutné zadat data entity, je zadána jako přímo kódovaná datová část v těle zprávy.  
  
### <a name="http-actions"></a>Akce HTTP  
 Služba OData podporuje následující akce HTTP k provádění operací vytvoření, čtení, aktualizace a odstranění u dat entity, která je předmětem odkazovaného prostředku:  
  
- **HTTP GET** – jedná se o výchozí akci, když je prostředek přístupný z prohlížeče. Ve zprávě požadavku není zadána žádná datová část a je vrácena metoda odpovědi s datovou částí, která obsahuje požadovaná data.  
  
- **Http post** – vloží data nové entity do poskytnutého prostředku. Data, která mají být vložena, jsou uvedena v datové části zprávy požadavku. Datová část zprávy s odpovědí obsahuje data pro nově vytvořenou entitu. To zahrnuje všechny automaticky vygenerované hodnoty klíčů. Záhlaví obsahuje také identifikátor URI, který řeší nový prostředek entity.  
  
- **Http Delete** – odstraní data entity, která zadaný prostředek představuje. V žádostech a odpovědích není přítomna datová část.  
  
- **HTTP PUT** – nahradí existující data entity požadovaným prostředkem novými daty, která jsou uvedena v datové části zprávy požadavku.  
  
- **Sloučení http** – kvůli neefektivitám při provádění odstranění, po kterém následuje vložení ve zdroji dat, a to jenom pro změnu dat entity, Služba OData zavádí novou akci sloučení http. Datová část zprávy požadavku obsahuje vlastnosti, které se musí změnit u prostředku s adresovánou entitou. Protože sloučení HTTP není ve specifikaci HTTP definované, může vyžadovat další zpracování pro směrování požadavku HTTP MERGE přes servery, které nepodporují OData.  
  
 Další informace najdete v tématu [OData: Operations](https://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Formáty datové části  
 V případě požadavku HTTP PUT, HTTP POST nebo HTTP MERGE datová část zprávy požadavku obsahuje data entity, která odešlete do datové služby. Obsah datové části závisí na formátu dat zprávy. Odpovědi HTTP na všechny akce kromě možnosti odstranit také obsahují takovou datovou část. Služba OData podporuje pro přístup k datům a jejich změně pomocí následujících formátů datové části:  
  
- **Atom** – kódování zpráv založené na jazyce XML definované službou OData jako rozšíření protokolu AtomPub (Atom Publishing Protocol), které umožňuje výměnu dat přes protokol HTTP pro webové informační kanály, podcasty, wiki a internetové funkce založené na jazyce XML. Další informace najdete v tématu [Formát OData: Atom](https://go.microsoft.com/fwlink/?LinkId=185794).  
  
- **JSON** -JavaScript Object Notation (JSON) je odlehčený formát pro výměnu dat, který je založen na podmnožině programovacího jazyka JavaScript. Další informace najdete v tématu [Formát OData: JSON](https://go.microsoft.com/fwlink/?LinkId=185795).  
  
 Formát zprávy datové části je požadován v hlavičce zprávy s požadavkem protokolu HTTP. Další informace najdete v tématu [OData: Operations](https://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Přístup k datům a jejich změna pomocí klientských knihoven  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsahuje klientské knihovny, které vám umožní snadněji využívat informační kanál OData z .NET Framework klientské aplikace založené na technologii Silverlight. Tyto knihovny zjednodušují posílání a přijímání zpráv HTTP. Také přeloží datovou část zprávy na objekty CLR, které představují data entity. Klientské knihovny nástroje jsou dvě základní třídy <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601>. Tyto třídy vám umožní dotazovat se na datovou službu a pak pracovat s vrácenými daty entity jako s objekty CLR. Další informace najdete v tématu [WCF Data Services Klientská knihovna](wcf-data-services-client-library.md) a [WCF Data Services (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 Pomocí dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio můžete přidat odkaz na datovou službu. Tento nástroj požaduje metadata služby z odkazované datové služby a generuje <xref:System.Data.Services.Client.DataServiceContext> reprezentující datovou službu, a generuje také třídy služby data klienta, které představují entity. Další informace najdete v tématu [generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md).  
  
 K dispozici jsou programové knihovny, které můžete použít ke využívání kanálu OData v jiných typech klientských aplikací. Další informace najdete v tématu [sada OData SDK](https://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Viz také:

- [Přístup k prostředkům datové služby](accessing-data-service-resources-wcf-data-services.md)
- [Rychlý start](quickstart-wcf-data-services.md)
