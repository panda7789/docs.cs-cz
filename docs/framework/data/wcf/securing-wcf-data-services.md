---
title: Zabezpečení služeb WCF Data Services
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: 56ece9c2c81f05047e85ab681e7cfe0da65f35b9
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324068"
---
# <a name="securing-wcf-data-services"></a>Zabezpečení služeb WCF Data Services
Toto téma popisuje důležité informace o zabezpečení, které jsou specifické pro vývoj, nasazování a spouštění [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] a aplikací přistupujících ke službám, které podporují [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Měli postupovat také podle doporučení pro vytváření zabezpečených [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikací.  
  
 Při plánování zabezpečení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]– na základě [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby, musíte vyřešit, ověřování, tedy procesu zjišťování a ověření identity objektu zabezpečení a autorizaci, tedy procesu určování, zda ověřeného objekt zabezpečení povolen přístup k požadovaným prostředkům. Dále je vhodné zvážit, zda chcete zprávy šifrovat pomocí protokolu SSL.  
  
## <a name="authenticating-client-requests"></a>Ověřování požadavků klientů  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] neimplementuje jakýkoli druh vlastní ověřování, ale využívá ověřování poskytované hostitele datové služby. To znamená, že služba předpokládá, že všechny požadavky, které obdrží, již byly ověřeny síťovým hostitelem a že hostitel správně vyhodnotil objekt zabezpečení požadavku prostřednictvím rozhraní poskytovaných službou [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Tyto možnosti ověřování a přístupy jsou podrobně popsány v [OData a ověřovací série](https://go.microsoft.com/fwlink/?LinkId=200381).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Možnosti ověřování ve službě WCF Data  
 Následující tabulka shrnuje některé mechanismy, které jsou k dispozici pro ověřování požadavků na službu WCF Data Service.  
  
|Možnosti ověřování|Popis|  
|----------------------------|-----------------|  
|Anonymní ověření|Pokud je aktivováno anonymní ověřování HTTP, může se k datové službě připojit libovolný objekt zabezpečení. U anonymního přístupu nejsou požadována pověření. Tuto možnost použijte pouze v případě, že chcete přístup k datové službě povolit všem uživatelům.|  
|Základní ověřování a ověřování algoritmem Digest|Pro ověření jsou vyžadována pověření, která sestávají z uživatelského jména a hesla. Podporuje ověřování klientů jiných platforem než Windows. **Poznámka k zabezpečení:** pověření základního ověřování (uživatelské jméno a heslo) se odesílají v nešifrované podobě a může být zachycena. Ověřování algoritmem Digest odešle hodnotu hash vycházející ze zadaných pověření. Je tedy bezpečnější než základní ověřování. Oba zmíněné typy ověřování jsou však náchylné k útoku prostředníkem (man-in-the-middle). Při použití těchto metod ověřování je vhodné zvážit šifrování komunikace mezi klientem a datovou službou pomocí protokolu SSL (Secure Sockets Layer). <br /><br /> Implementace obou basic poskytuje Microsoft Internetové informační služby (IIS) a ověřování algoritmem digest pro protokol HTTP žádosti v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace. Tato implementace poskytovatele ověřování systému Windows umožňuje klientské aplikaci rozhraní .NET Framework vložit pověření do hlavičky HTTP požadavku na datovou službu. Dovoluje tak bez problémů vyjednat ověření uživatele systému Windows. Další informace najdete v tématu [technické informace o ověřování algoritmem Digest](https://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Pokud chcete, aby vaše data služba používala základní ověřování založené na některé vlastní ověřovací službě, nikoli přihlašovací údaje Windows, musíte implementovat vlastní [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modulu HTTP pro ověřování.<br /><br /> Příklad použití vlastní základní ověřování schématu s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], najdete v příspěvku [vlastní základní ověřování](https://go.microsoft.com/fwlink/?LinkID=200388) v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a ověřování řady.|  
|Ověřování systému Windows|Pověření systému Windows se vyměňují pomocí protokolu NTLM nebo Kerberos. Tento mechanismus je bezpečnější než základní ověřování nebo ověřování algoritmem Digest, vyžaduje však, aby klientská aplikace byla založena na systému Windows. Služba IIS zároveň poskytuje implementaci ověřování Windows pro požadavky HTTP v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace. Další informace najdete v tématu [Přehled ověřování formulářů ASP.NET](https://msdn.microsoft.com/library/099c1587-6934-476e-ac95-28f534bc9708).<br /><br /> Příklad toho, jak používat ověřování Windows s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], najdete v příspěvku [ověřování Windows](https://go.microsoft.com/fwlink/?LinkID=200384) v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a ověřování řady.|  
|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ověřování pomocí formulářů|Ověřování pomocí formulářů umožňuje ověřovat uživatele pomocí vlastního kódu a poté uchovat ověřovací token v souboru cookie nebo v adrese URL stránky. Uživatelská jména a hesla uživatelů se ověřují pomocí přihlašovacího formuláře, který vytvoříte. Neověřené požadavky jsou přesměrovány na přihlašovací stránku, kde uživatel poskytne své údaje a formulář odešle. Pokud aplikace požadavek ověří, systém vydá ověřovací lístek obsahující klíč k ověření identity následných požadavků. Další informace najdete v tématu [zprostředkovatele ověřování formulářů](https://msdn.microsoft.com/library/77e21ba2-bad1-4967-a8ec-74942dea7e47). **Poznámka k zabezpečení:** ve výchozím nastavení, není při použití ověřování pomocí formulářů v zabezpečené souboru cookie, který obsahuje ověřovací lístek [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webovou aplikaci. Je vhodné zvážit, že budete vyžadovat protokol SSL, což zajistí ochranu ověřovacího lístku i počátečních přihlašovacích pověření. <br /><br /> Pro příklad, jak používat ověřování pomocí formulářů [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], najdete v příspěvku [ověřování pomocí formulářů](https://go.microsoft.com/fwlink/?LinkID=200389) v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a ověřování řady.|  
|Ověřování na základě deklarací|Při ověřování nezaloženého na deklaracích datové služby spoléhá na důvěryhodné identit "třetí strany" poskytovatele služby k ověření uživatele. Tento poskytovatel identit pozitivně ověřuje uživatele, který žádá o přístup k prostředkům datové služby, a vydá token zajišťující přístup k požadovaným prostředkům. Tento token se pak předává datové službě, která udělí uživateli přístup na základě vztahu důvěry se službou identit, jež přístupový token vydala.<br /><br /> Výhodou poskytovatele ověřování na základě deklarací je, že ho lze použít k ověřování různých typů klientů napříč důvěryhodnými doménami. Díky použití takového poskytovatele třetí strany může datová služba předat požadavky na údržbu a ověřování uživatelů. OAuth 2.0 je ověřovací protokol založený na deklaracích podporovaný službou AppFabric Access Control na platformě Microsoft Azure, který je určen pro federované ověřování poskytované jako služba. Tento protokol podporuje služby založené na technologii REST. Příklad použití OAuth 2.0 s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], najdete v příspěvku [OData a OAuth](https://go.microsoft.com/fwlink/?LinkId=200514) v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] a ověřování řady.|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Ověřování v knihovně klienta  
 Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna neposkytuje při požadavku na přihlašovací údaje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby. Pokud jsou přihlašovací údaje jsou povinné datová služba k ověření uživatele, lze je zadat tyto přihlašovací údaje v <xref:System.Net.NetworkCredential> k němu přistupovat z <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> vlastnost <xref:System.Data.Services.Client.DataServiceContext>, jako v následujícím příkladu:  
  
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
  
 Další informace najdete v tématu [postupy: určení přihlašovacích údajů klienta Data žádosti o služby](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Pokud datová služba vyžaduje přihlašovací pověření, která nelze zadat s použitím <xref:System.Net.NetworkCredential> objektu, jako jsou založené na deklaracích token nebo soubor cookie, je nutné ručně nastavit hlavičky v požadavku HTTP, obvykle `Authorization` a `Cookie` záhlaví. Další informace o tomto typu scénáře ověřování najdete v příspěvku [OData a ověřování: háčky na straně klienta](https://go.microsoft.com/fwlink/?LinkID=200385). Příklad nastavení hlaviček HTTP ve zprávě požadavku naleznete v tématu [jak: nastavit hlavičky v požadavku klienta](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Zosobnění  
 Obecně platí, že datová služba přistupuje k požadovaným prostředkům, například k souborům na serveru nebo v databázi, pomocí pověření pracovního procesu, který je hostitelem datové služby. Při použití zosobnění se [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace můžete spustit s použitím identity Windows (uživatelský účet) uživatele, který zadal žádost. Zosobnění se běžně používá v aplikacích, které k ověření uživatele využívají službu IIS, a pro přístup k požadovaným prostředkům se používají pověření tohoto typu. Další informace najdete v tématu [zosobnění technologie ASP.NET](https://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d).  
  
## <a name="configuring-data-service-authorization"></a>Konfigurace autorizace datové služby  
 Autorizace představuje udělení přístupu k prostředkům aplikace pro objekt zabezpečení nebo proces, který je identifikován na základě dřívějšího úspěšného ověření. Obecně platí, že uživatelům datové služby je vhodné udělit pouze práva dostatečná k provedení operací vyžadovaných klientskými aplikacemi.  
  
### <a name="restrict-access-to-data-service-resources"></a>Omezení přístupu k prostředkům datové služby  
 Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vám umožní udělit běžné přístup pro čtení a zápis proti prostředkům datové služby (entity nastavit a operace služby) kterémukoli uživateli, který je možné získat přístup ke službě data. Pravidla určující přístup pro čtení a zápis lze definovat samostatně pro každou sadu entit, která je datovou službou vystavena, a pro jakékoli operace služby. Doporučujeme omezit přístup pro čtení a zápis pouze na prostředky vyžadované klientskou aplikací. Další informace najdete v tématu [minimální požadavky na přístup prostředků](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Implementace zachycovacích dotazů založených na rolích  
 Zachycovací dotazy umožňují zachytit požadavky na prostředky datové služby předtím, než je datová služba vykoná. Další informace najdete v tématu [sběrače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Zachycovací dotazy dovolují přijímat rozhodnutí o autorizaci na základě ověřeného uživatele, který požadavek zadává. Příklad toho, jak omezit přístup k prostředkům datové služby podle identity ověřeného uživatele, najdete v části [jak na: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Omezení přístupu k trvalému úložišti dat a místním prostředkům  
 Účtům používaným pro přístup k trvalému úložišti je vhodné poskytnout pouze dostatečná práva pro databázi nebo systém souborů tak, aby byly podporovány požadavky datové služby. Pokud se používá anonymní ověřování, slouží právě tento účet ke spouštění hostitelské aplikace. Další informace najdete v tématu [postup: vývoj WCF Data Service běžících v IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Při použití zosobnění musí být k těmto prostředkům udělen přístup ověřeným uživatelům, obvykle v rámci skupiny systému Windows.  
  
## <a name="other-security-considerations"></a>Další informace o zabezpečení  
  
### <a name="secure-the-data-in-the-payload"></a>Zabezpečení dat v datové části  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] je založené na protokolu HTTP. Hlavička zprávy HTTP může v závislosti na typu ověřování implementovaného datovou službou obsahovat důležitá uživatelská pověření. Cenná zákaznická data, která je třeba ochránit, mohou být obsažena také v textu zprávy. V obou těchto případech doporučujeme k ochraně informací přenášených v síti používat protokol SSL.  
  
### <a name="ignored-message-headers-and-cookies"></a>Ignorované hlavičky zpráv a soubory cookie  
 Hlavičky požadavků HTTP s výjimkou těch, které deklarují typy obsahu a umístění prostředků, se ignorují a datová služba je nenastavuje.  
  
 Soubory cookie slouží jako součást ověřovacího schématu, jako například s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ověřování pomocí formulářů. Nicméně jsou ignorovány všechny soubory cookie HTTP, nastavte pro příchozí požadavek podle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Hostitele datové služby může zpracovat soubor cookie, ale [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] runtime neanalyzuje ani nevrací soubory cookie. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna nezpracovává ani soubory cookie odesílané v odpovědi.  
  
### <a name="custom-hosting-requirements"></a>Vlastní požadavky na hostování  
 Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] se vytvoří jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace hostované ve službě IIS. To datové službě dovoluje těžit z bezpečného chování této platformy. Můžete definovat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , které jsou hostované u vlastního hostitele. Další informace najdete v tématu [hostitelem datové služby](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Součásti a platforma hostující datovou službu musí jako prevenci proti útokům na datovou službu zajistit následující bezpečnostní chování:  
  
-   Omezení délky identifikátoru URI přijímaného v požadavku na datovou službu pro všechny možné operace.  
  
-   Omezení velikosti příchozí a odchozí zprávy HTTP.  
  
-   Omezení celkového počtu nevyřízených požadavků v kterémkoli okamžiku.  
  
-   Omezení velikosti hlaviček protokolu HTTP a jejich hodnoty a poskytují [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] přístup k údajům v hlavičce.  
  
-   Rozpoznání a odvracení známých útoků, jako jsou útoky TCP SYN a útoky pomocí opakovaného přehrávání zprávy.  
  
### <a name="values-are-not-further-encoded"></a>Hodnoty se dále nešifrují  
 Hodnoty vlastností odesílané datové službě dále nešifrují [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] modulu runtime. Pokud například řetězcová vlastnost entity obsahuje formátovaný obsah ve formátu HTML, jeho značky nejsou datovou službou zašifrovány do jazyka HTML. Datová služby zároveň dále nešifruje hodnoty vlastností v odezvě. Další šifrování neprovádí ani knihovna klienta.  
  
### <a name="considerations-for-client-applications"></a>Důležité informace o klientských aplikacích  
 Platí následující aspekty zabezpečení pro aplikace, které používají [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientovi přístup k [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby:  
  
-   Knihovna klienta předpokládá, že protokoly použité k přístupu k datové službě poskytují odpovídající úroveň zabezpečení.  
  
-   Knihovna klienta používá veškeré výchozí hodnoty pro časové limity a možnosti analýzy transportních zásobníků poskytovaných podkladovou platformou.  
  
-   Knihovna klienta nenačítá žádná nastavení z konfiguračních souborů aplikace.  
  
-   Knihovna klienta neimplementuje žádné mechanismy přístupu napříč doménami. Místo toho využívá mechanismy poskytované podkladovým zásobníkem HTTP.  
  
-   Knihovna klienta neobsahuje žádné prvky uživatelského rozhraní a nikdy se nepokouší zobrazit ani vykreslit data, která přijímá nebo odesílá.  
  
-   Doporučujeme, aby klientské aplikace vždy ověřovaly uživatelské vstupy i údaje přijímané z nedůvěryhodných služeb.  
  
## <a name="see-also"></a>Viz také  
 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
