---
title: Zabezpečení součásti WCF Data Services
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45cb1dc7223181bcbd093664380f24d04c5a92d4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="securing-wcf-data-services"></a>Zabezpečení součásti WCF Data Services
Toto téma popisuje aspekty zabezpečení, které jsou specifické pro vývoj, nasazování a spouštění [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] a aplikace, které přístup ke službám, které podporují [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Také postupujte podle doporučení pro vytvoření zabezpečeného [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace.  
  
 Při plánování zabezpečení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]– na základě [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby, musíte vyřešit, ověřování, proces zjišťování a ověřování identity objektu zabezpečení a autorizace, proces pro určení toho, zda je ověření objekt zabezpečení je povolen přístup k požadované prostředky. Dále je vhodné zvážit, zda chcete zprávy šifrovat pomocí protokolu SSL.  
  
## <a name="authenticating-client-requests"></a>Ověřování požadavků klientů  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] neimplementuje žádný typ ověřování své vlastní, ale spíše se spoléhá na ověřování ustanovení hostitele služby data. To znamená, že služba předpokládá, že každá žádost, kterou přijme již byl ověřen pro sítě hostitele a správně má hostitel identifikovat zásadu pro žádosti o správně prostřednictvím rozhraní poskytované [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Tyto možnosti ověřování a přístupy jsou podrobně popsané na [OData a ověřování řady](http://go.microsoft.com/fwlink/?LinkId=200381).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Možnosti ověřování ve službě WCF Data  
 Následující tabulka shrnuje některé mechanismy, které jsou k dispozici pro ověřování požadavků na službu WCF Data Service.  
  
|Možnosti ověřování|Popis|  
|----------------------------|-----------------|  
|Anonymní ověření|Pokud je aktivováno anonymní ověřování HTTP, může se k datové službě připojit libovolný objekt zabezpečení. U anonymního přístupu nejsou požadována pověření. Tuto možnost použijte pouze v případě, že chcete přístup k datové službě povolit všem uživatelům.|  
|Základní ověřování a ověřování algoritmem Digest|Pro ověření jsou vyžadována pověření, která sestávají z uživatelského jména a hesla. Podporuje ověřování klientů jiných platforem než Windows. **Poznámka k zabezpečení:** základní ověřovací pověření (uživatelské jméno a heslo) se odesílají v nešifrované a mohou být zachyceny. Ověřování algoritmem Digest odešle hodnotu hash vycházející ze zadaných pověření. Je tedy bezpečnější než základní ověřování. Oba zmíněné typy ověřování jsou však náchylné k útoku prostředníkem (man-in-the-middle). Při použití těchto metod ověřování je vhodné zvážit šifrování komunikace mezi klientem a datovou službou pomocí protokolu SSL (Secure Sockets Layer). <br /><br /> Microsoft Internetové informační služby (IIS) poskytuje implementaci pro obě basic a ověřování algoritmem digest pro protokol HTTP požadavků ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace. Tato implementace poskytovatele ověřování systému Windows umožňuje klientské aplikaci rozhraní .NET Framework vložit pověření do hlavičky HTTP požadavku na datovou službu. Dovoluje tak bez problémů vyjednat ověření uživatele systému Windows. Další informace najdete v tématu [technické informace o ověřování hodnotou hash](http://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Pokud chcete mít data služby použijte základní ověřování na základě některé vlastní ověřovací služby a nejsou přihlašovací údaje systému Windows, je nutné implementovat vlastní [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modulu HTTP pro ověřování.<br /><br /> Příklad použití vlastní základní ověřování schéma s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], najdete v příspěvku na [vlastní základní ověřování](http://go.microsoft.com/fwlink/?LinkID=200388) v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a ověřování řady.|  
|Ověřování systému Windows|Pověření systému Windows se vyměňují pomocí protokolu NTLM nebo Kerberos. Tento mechanismus je bezpečnější než základní ověřování nebo ověřování algoritmem Digest, vyžaduje však, aby klientská aplikace byla založena na systému Windows. Služba IIS také poskytuje implementaci pro ověřování systému Windows pro požadavky HTTP v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace. Další informace najdete v tématu [Přehled ověřování formulářů ASP.NET](http://msdn.microsoft.com/library/099c1587-6934-476e-ac95-28f534bc9708).<br /><br /> Příklad použití ověřování systému Windows s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], najdete v příspěvku na [ověřování systému Windows](http://go.microsoft.com/fwlink/?LinkID=200384) v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a ověřování řady.|  
|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ověřování pomocí formulářů|Ověřování pomocí formulářů umožňuje ověřovat uživatele pomocí vlastního kódu a poté uchovat ověřovací token v souboru cookie nebo v adrese URL stránky. Uživatelská jména a hesla uživatelů se ověřují pomocí přihlašovacího formuláře, který vytvoříte. Neověřené požadavky jsou přesměrovány na přihlašovací stránku, kde uživatel poskytne své údaje a formulář odešle. Pokud aplikace požadavek ověří, systém vydá ověřovací lístek obsahující klíč k ověření identity následných požadavků. Další informace najdete v tématu [zprostředkovatele ověřování formulářů](http://msdn.microsoft.com/library/77e21ba2-bad1-4967-a8ec-74942dea7e47). **Poznámka k zabezpečení:** ve výchozím nastavení, není při použití ověřování pomocí formulářů v zabezpečené souboru cookie, který obsahuje lístek pro ověřování pomocí formulářů [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové aplikace. Je vhodné zvážit, že budete vyžadovat protokol SSL, což zajistí ochranu ověřovacího lístku i počátečních přihlašovacích pověření. <br /><br /> Pro příklad použití ověřování pomocí formulářů [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], najdete v příspěvku na [ověřování pomocí formulářů](http://go.microsoft.com/fwlink/?LinkID=200389) v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a ověřování řady.|  
|Ověřování na základě deklarací|Ověřování založené na deklaracích identity na službu data spoléhá na důvěryhodné identity "jiného výrobce" poskytovatele služby k ověření uživatele. Tento poskytovatel identit pozitivně ověřuje uživatele, který žádá o přístup k prostředkům datové služby, a vydá token zajišťující přístup k požadovaným prostředkům. Tento token se pak předává datové službě, která udělí uživateli přístup na základě vztahu důvěry se službou identit, jež přístupový token vydala.<br /><br /> Výhodou poskytovatele ověřování na základě deklarací je, že ho lze použít k ověřování různých typů klientů napříč důvěryhodnými doménami. Díky použití takového poskytovatele třetí strany může datová služba předat požadavky na údržbu a ověřování uživatelů. OAuth 2.0 je ověřovací protokol založený na deklaracích podporovaný službou AppFabric Access Control na platformě Microsoft Azure, který je určen pro federované ověřování poskytované jako služba. Tento protokol podporuje služby založené na technologii REST. Příklad použití OAuth 2.0 s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], najdete v příspěvku na [OData a OAuth](http://go.microsoft.com/fwlink/?LinkId=200514) v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a ověřování řady.|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Ověřování v knihovně klienta  
 Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny neposkytuje při vytváření požadavku na přihlašovací údaje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby. Pokud přihlašovací údaje jsou vyžadované službou data k ověření uživatele, můžete je nutné zadat tyto přihlašovací údaje v <xref:System.Net.NetworkCredential> k němu přistupovat z <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> vlastnost <xref:System.Data.Services.Client.DataServiceContext>, jako v následujícím příkladu:  
  
```csharp  
// Set the client authentication credentials.  
context.Credentials =  
    new NetworkCredential(userName, password, domain);  
```  
  
```vb  
' Set the client authentication credentials.  
context.Credentials = _  
    New NetworkCredential(userName, password, domain)  
```  
  
 Další informace najdete v tématu [postup: Zadejte pověření klienta služby Data žádosti o](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Když služba dat vyžaduje přihlašovací údaje, které nelze zadat pomocí <xref:System.Net.NetworkCredential> objektu, například token založené na deklaracích nebo soubor cookie, musíte ručně nastavit hlavičky v požadavku HTTP, obvykle `Authorization` a `Cookie` hlavičky. Další informace o tento druh ověřovacím scénáři, najdete v příspěvku [OData a ověřování: Client-Side zachytí](http://go.microsoft.com/fwlink/?LinkID=200385). Příklad, jak nastavit hlavičky HTTP ve zprávě požadavku, naleznete v části [postup: nastavit hlavičky v požadavku klienta](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Zosobnění  
 Obecně platí, že datová služba přistupuje k požadovaným prostředkům, například k souborům na serveru nebo v databázi, pomocí pověření pracovního procesu, který je hostitelem datové služby. Při použití zosobnění, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikací může spustit s identitou systému Windows (uživatelský účet) uživatele, který vytvořil požadavek. Zosobnění se běžně používá v aplikacích, které k ověření uživatele využívají službu IIS, a pro přístup k požadovaným prostředkům se používají pověření tohoto typu. Další informace najdete v tématu [zosobnění technologie ASP.NET](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d).  
  
## <a name="configuring-data-service-authorization"></a>Konfigurace autorizace datové služby  
 Autorizace představuje udělení přístupu k prostředkům aplikace pro objekt zabezpečení nebo proces, který je identifikován na základě dřívějšího úspěšného ověření. Obecně platí, že uživatelům datové služby je vhodné udělit pouze práva dostatečná k provedení operací vyžadovaných klientskými aplikacemi.  
  
### <a name="restrict-access-to-data-service-resources"></a>Omezení přístupu k prostředkům datové služby  
 Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vám umožní udělit běžné oprávnění ke čtení a zápisu pro prostředky služby data (entitu nastavit a služby operations) s žádným uživatelem, který se bude moct přístup ke službě data. Pravidla určující přístup pro čtení a zápis lze definovat samostatně pro každou sadu entit, která je datovou službou vystavena, a pro jakékoli operace služby. Doporučujeme omezit přístup pro čtení a zápis pouze na prostředky vyžadované klientskou aplikací. Další informace najdete v tématu [požadavky na přístup k prostředku minimální](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Implementace zachycovacích dotazů založených na rolích  
 Zachycovací dotazy umožňují zachytit požadavky na prostředky datové služby předtím, než je datová služba vykoná. Další informace najdete v tématu [sběrače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Zachycovací dotazy dovolují přijímat rozhodnutí o autorizaci na základě ověřeného uživatele, který požadavek zadává. Příklad toho, jak omezit přístup k prostředkům služby dat podle identity ověřeného uživatele, naleznete v části [postupy: zachycení datových služba zpráv](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Omezení přístupu k trvalému úložišti dat a místním prostředkům  
 Účtům používaným pro přístup k trvalému úložišti je vhodné poskytnout pouze dostatečná práva pro databázi nebo systém souborů tak, aby byly podporovány požadavky datové služby. Pokud se používá anonymní ověřování, slouží právě tento účet ke spouštění hostitelské aplikace. Další informace najdete v tématu [postup: vývoj WCF Data Service spuštěna ve službě IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Při použití zosobnění musí být k těmto prostředkům udělen přístup ověřeným uživatelům, obvykle v rámci skupiny systému Windows.  
  
## <a name="other-security-considerations"></a>Další informace o zabezpečení  
  
### <a name="secure-the-data-in-the-payload"></a>Zabezpečení dat v datové části  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] je založen na protokolu HTTP. Hlavička zprávy HTTP může v závislosti na typu ověřování implementovaného datovou službou obsahovat důležitá uživatelská pověření. Cenná zákaznická data, která je třeba ochránit, mohou být obsažena také v textu zprávy. V obou těchto případech doporučujeme k ochraně informací přenášených v síti používat protokol SSL.  
  
### <a name="ignored-message-headers-and-cookies"></a>Ignorované hlavičky zpráv a soubory cookie  
 Hlavičky požadavků HTTP s výjimkou těch, které deklarují typy obsahu a umístění prostředků, se ignorují a datová služba je nenastavuje.  
  
 Soubory cookie slouží jako součást schématu ověřování, například s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ověřování pomocí formulářů. Však nejsou žádné soubory cookie HTTP, který je nastaven na příchozí žádosti Ignorovat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Hostitel služby dat může zpracovat soubor cookie, ale [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] runtime nikdy analyzuje nebo vrátí soubory cookie. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientské knihovny také nezpracovává souborů cookie zaslaných v odpovědi.  
  
### <a name="custom-hosting-requirements"></a>Vlastní požadavky na hostování  
 Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] je vytvořen jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace hostované ve službě IIS. To datové službě dovoluje těžit z bezpečného chování této platformy. Můžete definovat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] který jsou hostitelem vlastního hostitele. Další informace najdete v tématu [hostující službu Data](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Součásti a platforma hostující datovou službu musí jako prevenci proti útokům na datovou službu zajistit následující bezpečnostní chování:  
  
-   Omezení délky identifikátoru URI přijímaného v požadavku na datovou službu pro všechny možné operace.  
  
-   Omezení velikosti příchozí a odchozí zprávy HTTP.  
  
-   Omezení celkového počtu nevyřízených požadavků v kterémkoli okamžiku.  
  
-   Omezení velikosti hlavičky protokolu HTTP a jejich hodnot a zadejte [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] přístup k datům záhlaví.  
  
-   Rozpoznání a odvracení známých útoků, jako jsou útoky TCP SYN a útoky pomocí opakovaného přehrávání zprávy.  
  
### <a name="values-are-not-further-encoded"></a>Hodnoty se dále nešifrují  
 Hodnoty vlastností, odešle do služby data nejsou další kódovaný pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] modulu runtime. Pokud například řetězcová vlastnost entity obsahuje formátovaný obsah ve formátu HTML, jeho značky nejsou datovou službou zašifrovány do jazyka HTML. Datová služby zároveň dále nešifruje hodnoty vlastností v odezvě. Další šifrování neprovádí ani knihovna klienta.  
  
### <a name="considerations-for-client-applications"></a>Důležité informace o klientských aplikacích  
 Pro aplikace, které používají, platí následující aspekty zabezpečení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientovi přístup k [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby:  
  
-   Knihovna klienta předpokládá, že protokoly použité k přístupu k datové službě poskytují odpovídající úroveň zabezpečení.  
  
-   Knihovna klienta používá veškeré výchozí hodnoty pro časové limity a možnosti analýzy transportních zásobníků poskytovaných podkladovou platformou.  
  
-   Knihovna klienta nenačítá žádná nastavení z konfiguračních souborů aplikace.  
  
-   Knihovna klienta neimplementuje žádné mechanismy přístupu napříč doménami. Místo toho využívá mechanismy poskytované podkladovým zásobníkem HTTP.  
  
-   Knihovna klienta neobsahuje žádné prvky uživatelského rozhraní a nikdy se nepokouší zobrazit ani vykreslit data, která přijímá nebo odesílá.  
  
-   Doporučujeme, aby klientské aplikace vždy ověřovaly uživatelské vstupy i údaje přijímané z nedůvěryhodných služeb.  
  
## <a name="see-also"></a>Viz také  
 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
