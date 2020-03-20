---
title: Zabezpečení datových služeb WCF Data Services
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: e09007e786772e838a9aaa76eb8ef7a3fe2b7cca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174651"
---
# <a name="securing-wcf-data-services"></a>Zabezpečení datových služeb WCF Data Services
Toto téma popisuje důležité informace o zabezpečení, které jsou specifické pro vývoj, nasazení a spuštění služby WCF Data Services a aplikací, které přistupují ke službám, které podporují protokol OData (Open Data Protocol). Měli byste také dodržovat doporučení pro vytváření zabezpečených aplikací rozhraní .NET Framework.  
  
Při plánování zabezpečení služby OData založené na službě WCF Data Services je nutné řešit ověřování, proces zjišťování a ověřování identity objektu zabezpečení a autorizaci proces uzavírky, zda je ověřený objekt zabezpečení přístup k požadovaným zdrojům. Dále je vhodné zvážit, zda chcete zprávy šifrovat pomocí protokolu SSL.  
  
## <a name="authenticating-client-requests"></a>Ověřování požadavků klientů  
WCF Data Services neimplementuje žádný druh ověřování vlastní, ale spíše spoléhá na ověřování ustanovení hostitele datové služby. To znamená, že služba předpokládá, že všechny požadavky, které obdrží již byla ověřena hostitelem sítě a že hostitel správně určil zásadu pro požadavek odpovídajícím způsobem prostřednictvím rozhraní poskytovaných WCF Data Services. Tyto možnosti ověřování a přístupy jsou podrobně popsány v řadě [Vícedílných Dat a ověřování](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Možnosti ověřování ve službě WCF Data  
 Následující tabulka shrnuje některé mechanismy, které jsou k dispozici pro ověřování požadavků na službu WCF Data Service.  
  
|Možnosti ověřování|Popis|  
|----------------------------|-----------------|  
|Anonymní ověření|Pokud je aktivováno anonymní ověřování HTTP, může se k datové službě připojit libovolný objekt zabezpečení. U anonymního přístupu nejsou požadována pověření. Tuto možnost použijte pouze v případě, že chcete přístup k datové službě povolit všem uživatelům.|  
|Základní ověřování a ověřování algoritmem Digest|Pro ověření jsou vyžadována pověření, která sestávají z uživatelského jména a hesla. Podporuje ověřování klientů jiných platforem než Windows. **Bezpečnostní poznámka:**  Základní ověřovací pověření (uživatelské jméno a heslo) jsou odesílány v jasné a mohou být zachyceny. Ověřování algoritmem Digest odešle hodnotu hash vycházející ze zadaných pověření. Je tedy bezpečnější než základní ověřování. Oba zmíněné typy ověřování jsou však náchylné k útoku prostředníkem (man-in-the-middle). Při použití těchto metod ověřování je vhodné zvážit šifrování komunikace mezi klientem a datovou službou pomocí protokolu SSL (Secure Sockets Layer). <br /><br /> Internetová informační služba (IIS) poskytuje implementaci základního ověřování i ověřování algoritmem digest pro požadavky HTTP v ASP.NET aplikaci. Tato implementace poskytovatele ověřování systému Windows umožňuje klientské aplikaci rozhraní .NET Framework vložit pověření do hlavičky HTTP požadavku na datovou službu. Dovoluje tak bez problémů vyjednat ověření uživatele systému Windows. Další informace naleznete v tématu [Digest Authentication Technical Reference](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782794(v=ws.10)).<br /><br /> Pokud chcete, aby datová služba používala základní ověřování založené na některé vlastní ověřovací službě a ne na pověřeních systému Windows, je nutné implementovat vlastní ADP.NET modulHTTP pro ověřování.<br /><br /> Příklad použití vlastního základního schématu ověřování s datovými službami WCF naleznete v příspěvku blogu [OData and Authentication – část 6 – Vlastní základní ověřování](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/).|  
|Ověřování systému Windows|Pověření systému Windows se vyměňují pomocí protokolu NTLM nebo Kerberos. Tento mechanismus je bezpečnější než základní ověřování nebo ověřování algoritmem Digest, vyžaduje však, aby klientská aplikace byla založena na systému Windows. Služba IIS také poskytuje implementaci ověřování systému Windows pro požadavky HTTP v ASP.NET aplikaci. Další informace naleznete [v tématu ASP.NET Přehled ověřování pomocí formulářů](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100)).<br /><br /> Příklad použití ověřování systému Windows se službou WCF Data Services najdete v příspěvku blogu [OData a ověřování – část 2 – Ověřování systému Windows](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/).|  
|ověřování ASP.NET formulářů|Ověřování pomocí formulářů umožňuje ověřovat uživatele pomocí vlastního kódu a poté uchovat ověřovací token v souboru cookie nebo v adrese URL stránky. Uživatelská jména a hesla uživatelů se ověřují pomocí přihlašovacího formuláře, který vytvoříte. Neověřené požadavky jsou přesměrovány na přihlašovací stránku, kde uživatel poskytne své údaje a formulář odešle. Pokud aplikace požadavek ověří, systém vydá ověřovací lístek obsahující klíč k ověření identity následných požadavků. Další informace naleznete v [tématu Zprostředkovatel ověřování formulářů](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100)). **Bezpečnostní poznámka:**  Ve výchozím nastavení není soubor cookie obsahující lístek ověřování formulářů zabezpečen při použití ověřování pomocí formulářů ve webové aplikaci ASP.NET. Je vhodné zvážit, že budete vyžadovat protokol SSL, což zajistí ochranu ověřovacího lístku i počátečních přihlašovacích pověření. <br /><br /> Příklad použití ověřování pomocí formulářů s datovými službami WCF najdete v příspěvku blogu [OData a ověřování – část 7 – Ověřování pomocí formulářů](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/).|  
|Ověřování na základě deklarací|Při ověřování na základě deklarací identity závisí datová služba k ověření uživatele důvěryhodnou službou zprostředkovatele identity "třetí strany". Tento poskytovatel identit pozitivně ověřuje uživatele, který žádá o přístup k prostředkům datové služby, a vydá token zajišťující přístup k požadovaným prostředkům. Tento token se pak předává datové službě, která udělí uživateli přístup na základě vztahu důvěry se službou identit, jež přístupový token vydala.<br /><br /> Výhodou poskytovatele ověřování na základě deklarací je, že ho lze použít k ověřování různých typů klientů napříč důvěryhodnými doménami. Díky použití takového poskytovatele třetí strany může datová služba předat požadavky na údržbu a ověřování uživatelů. OAuth 2.0 je ověřovací protokol založený na deklaracích podporovaný službou AppFabric Access Control na platformě Microsoft Azure, který je určen pro federované ověřování poskytované jako služba. Tento protokol podporuje služby založené na technologii REST. Příklad použití OAuth 2.0 s WCF Data Services najdete v příspěvku blogu [OData and Authentication – Část 8 – OAuth WRAP](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>
### <a name="authentication-in-the-client-library"></a>Ověřování v knihovně klienta  
 Ve výchozím nastavení klientská knihovna WCF Data Services neposkytuje pověření při vytváření požadavku na službu OData. Pokud datová služba vyžaduje přihlašovací údaje k ověření uživatele, mohou být <xref:System.Net.NetworkCredential> tato pověření <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> zadána <xref:System.Data.Services.Client.DataServiceContext>v přístupu z vlastnosti , jako v následujícím příkladu:  
  
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
  
 Další informace naleznete v [tématu How to: Specify Client Credentials for a Data Service Request](specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Pokud datová služba vyžaduje přihlašovací údaje, které <xref:System.Net.NetworkCredential> nelze zadat pomocí objektu, jako je například token založený na deklaracích `Authorization` `Cookie` identity nebo soubor cookie, je nutné ručně nastavit záhlaví v požadavku HTTP, obvykle a záhlaví. Další informace o tomto druhu ověřování scénář, naleznete v blogu [OData a ověřování – část 3 – ClientSide Háčky](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/). Příklad nastavení záhlaví protokolu HTTP ve zprávě požadavku naleznete v tématu [How to: Set Headers in the Client Request](how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Zosobnění  
 Obecně platí, že datová služba přistupuje k požadovaným prostředkům, například k souborům na serveru nebo v databázi, pomocí pověření pracovního procesu, který je hostitelem datové služby. Při použití zosobnění, ASP.NET aplikace lze spustit s identitou systému Windows (uživatelský účet) uživatele, který žádost. Zosobnění se běžně používá v aplikacích, které k ověření uživatele využívají službu IIS, a pro přístup k požadovaným prostředkům se používají pověření tohoto typu. Další informace naleznete [v tématu ASP.NET impersonati .](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100))  
  
## <a name="configuring-data-service-authorization"></a>Konfigurace autorizace datové služby  
 Autorizace představuje udělení přístupu k prostředkům aplikace pro objekt zabezpečení nebo proces, který je identifikován na základě dřívějšího úspěšného ověření. Obecně platí, že uživatelům datové služby je vhodné udělit pouze práva dostatečná k provedení operací vyžadovaných klientskými aplikacemi.  
  
### <a name="restrict-access-to-data-service-resources"></a>Omezení přístupu k prostředkům datové služby  
 Ve výchozím nastavení umožňuje datové služby WCF udělit běžný přístup pro čtení a zápis proti prostředkům datové služby (sada entit a operacím služby) všem uživatelům, kteří mají přístup k datové službě. Pravidla určující přístup pro čtení a zápis lze definovat samostatně pro každou sadu entit, která je datovou službou vystavena, a pro jakékoli operace služby. Doporučujeme omezit přístup pro čtení a zápis pouze na prostředky vyžadované klientskou aplikací. Další informace naleznete [v tématu Minimální požadavky na přístup ke zdrojům](configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Implementace zachycovacích dotazů založených na rolích  
 Zachycovací dotazy umožňují zachytit požadavky na prostředky datové služby předtím, než je datová služba vykoná. Další informace naleznete v tématu [Interceptors](interceptors-wcf-data-services.md). Zachycovací dotazy dovolují přijímat rozhodnutí o autorizaci na základě ověřeného uživatele, který požadavek zadává. Příklad omezení přístupu k prostředkům datové služby na základě ověřené identity uživatele naleznete v [tématu How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Omezení přístupu k trvalému úložišti dat a místním prostředkům  
 Účtům používaným pro přístup k trvalému úložišti je vhodné poskytnout pouze dostatečná práva pro databázi nebo systém souborů tak, aby byly podporovány požadavky datové služby. Pokud se používá anonymní ověřování, slouží právě tento účet ke spouštění hostitelské aplikace. Další informace naleznete v [tématu How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md). Při použití zosobnění musí být k těmto prostředkům udělen přístup ověřeným uživatelům, obvykle v rámci skupiny systému Windows.  
  
## <a name="other-security-considerations"></a>Další informace o zabezpečení  
  
### <a name="secure-the-data-in-the-payload"></a>Zabezpečení dat v datové části  
OData je založen na protokolu HTTP. Hlavička zprávy HTTP může v závislosti na typu ověřování implementovaného datovou službou obsahovat důležitá uživatelská pověření. Cenná zákaznická data, která je třeba ochránit, mohou být obsažena také v textu zprávy. V obou těchto případech doporučujeme k ochraně informací přenášených v síti používat protokol SSL.  
  
### <a name="ignored-message-headers-and-cookies"></a>Ignorované hlavičky zpráv a soubory cookie  
 Hlavičky požadavků HTTP s výjimkou těch, které deklarují typy obsahu a umístění prostředků, se ignorují a datová služba je nenastavuje.  
  
 Soubory cookie lze použít jako součást schématu ověřování, například s ověřováním ASP.NET formulářů. Všechny soubory cookie HTTP nastavené na příchozí požadavek jsou však ignorovány WCF DataServices. Hostitel datové služby může soubor cookie zpracovat, ale za běhu služby WCF Data Services nikdy neanalyzuje ani nevrátí soubory cookie. Klientská knihovna WCF Data Services také nezpracovává soubory cookie odeslané v odpovědi.  
  
### <a name="custom-hosting-requirements"></a>Vlastní požadavky na hostování  
 Ve výchozím nastavení je služba WCF Data Services vytvořena jako ASP.NET aplikace hostované ve službě IIS. To datové službě dovoluje těžit z bezpečného chování této platformy. Můžete definovat WCF datové služby, které jsou hostovány vlastní hostitele. Další informace naleznete [v tématu Hostování datové služby](hosting-the-data-service-wcf-data-services.md). Součásti a platforma hostující datovou službu musí jako prevenci proti útokům na datovou službu zajistit následující bezpečnostní chování:  
  
- Omezení délky identifikátoru URI přijímaného v požadavku na datovou službu pro všechny možné operace.  
  
- Omezení velikosti příchozí a odchozí zprávy HTTP.  
  
- Omezení celkového počtu nevyřízených požadavků v kterémkoli okamžiku.  
  
- Omezte velikost záhlaví PROTOKOLU HTTP a jejich hodnoty a poskytněte datovým službám WCF přístup k datům záhlaví.  
  
- Rozpoznání a odvracení známých útoků, jako jsou útoky TCP SYN a útoky pomocí opakovaného přehrávání zprávy.  
  
### <a name="values-are-not-further-encoded"></a>Hodnoty se dále nešifrují  
 Hodnoty vlastností odeslané datové službě nejsou dále kódovány za běhu služby WCF Data Services. Pokud například řetězcová vlastnost entity obsahuje formátovaný obsah ve formátu HTML, jeho značky nejsou datovou službou zašifrovány do jazyka HTML. Datová služby zároveň dále nešifruje hodnoty vlastností v odezvě. Další šifrování neprovádí ani knihovna klienta.  
  
### <a name="considerations-for-client-applications"></a>Důležité informace o klientských aplikacích  
 Následující aspekty zabezpečení platí pro aplikace, které používají klienta WCF Data Services pro přístup ke službám OData:  
  
- Knihovna klienta předpokládá, že protokoly použité k přístupu k datové službě poskytují odpovídající úroveň zabezpečení.  
  
- Knihovna klienta používá veškeré výchozí hodnoty pro časové limity a možnosti analýzy transportních zásobníků poskytovaných podkladovou platformou.  
  
- Knihovna klienta nenačítá žádná nastavení z konfiguračních souborů aplikace.  
  
- Knihovna klienta neimplementuje žádné mechanismy přístupu napříč doménami. Místo toho využívá mechanismy poskytované podkladovým zásobníkem HTTP.  
  
- Knihovna klienta neobsahuje žádné prvky uživatelského rozhraní a nikdy se nepokouší zobrazit ani vykreslit data, která přijímá nebo odesílá.  
  
- Doporučujeme, aby klientské aplikace vždy ověřovaly uživatelské vstupy i údaje přijímané z nedůvěryhodných služeb.  
  
## <a name="see-also"></a>Viz také

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
