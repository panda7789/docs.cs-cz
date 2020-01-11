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
ms.openlocfilehash: 7c47951268bf414a5a2833e9511e854c1c1437a8
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900942"
---
# <a name="securing-wcf-data-services"></a>Zabezpečení datových služeb WCF Data Services
V tomto tématu jsou popsány požadavky na zabezpečení, které jsou specifické pro vývoj, nasazení a spouštění WCF Data Services a aplikací, které přistupují ke službám, které podporují protokol OData (Open Data Protocol). Měli byste také postupovat podle doporučení pro vytváření zabezpečených .NET Framework aplikací.  
  
Při plánování zabezpečení služby OData založené na WCF Data Services musíte vyřešit ověřování, proces zjišťování a ověřování identity objektu zabezpečení a autorizaci, což je proces zjištění, zda je ověřený objekt zabezpečení povolený přístup k požadovaným prostředkům. Dále je vhodné zvážit, zda chcete zprávy šifrovat pomocí protokolu SSL.  
  
## <a name="authenticating-client-requests"></a>Ověřování požadavků klientů  
WCF Data Services neimplementuje žádné vlastní ověřování, ale místo toho spoléhá na pravidla ověřování hostitele datové služby. To znamená, že služba předpokládá, že všechny žádosti, které obdrží, již byly ověřeny síťovým hostitelem a že hostitel správně identifikoval princip pro požadavek prostřednictvím rozhraní poskytovaných WCF Data Services. Tyto možnosti a přístupy k ověřování jsou podrobně popsané v [řadách OData a ověřování řady](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22)multipart.  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Možnosti ověřování ve službě WCF Data  
 Následující tabulka shrnuje některé mechanismy, které jsou k dispozici pro ověřování požadavků na službu WCF Data Service.  
  
|Možnosti ověřování|Popis|  
|----------------------------|-----------------|  
|Anonymní ověření|Pokud je aktivováno anonymní ověřování HTTP, může se k datové službě připojit libovolný objekt zabezpečení. U anonymního přístupu nejsou požadována pověření. Tuto možnost použijte pouze v případě, že chcete přístup k datové službě povolit všem uživatelům.|  
|Základní ověřování a ověřování algoritmem Digest|Pro ověření jsou vyžadována pověření, která sestávají z uživatelského jména a hesla. Podporuje ověřování klientů jiných platforem než Windows. **Poznámka k zabezpečení:**  Přihlašovací údaje základního ověřování (uživatelské jméno a heslo) jsou odesílány jasně a lze je zachytit. Ověřování algoritmem Digest odešle hodnotu hash vycházející ze zadaných pověření. Je tedy bezpečnější než základní ověřování. Oba zmíněné typy ověřování jsou však náchylné k útoku prostředníkem (man-in-the-middle). Při použití těchto metod ověřování je vhodné zvážit šifrování komunikace mezi klientem a datovou službou pomocí protokolu SSL (Secure Sockets Layer). <br /><br /> Služba Microsoft Internetová informační služba (IIS) poskytuje implementaci základního ověřování a ověřování algoritmem Digest pro požadavky HTTP v aplikaci ASP.NET. Tato implementace poskytovatele ověřování systému Windows umožňuje klientské aplikaci rozhraní .NET Framework vložit pověření do hlavičky HTTP požadavku na datovou službu. Dovoluje tak bez problémů vyjednat ověření uživatele systému Windows. Další informace najdete v tématu [technické informace o ověřování algoritmem Digest](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782794(v=ws.10)).<br /><br /> Pokud chcete, aby datová služba používala základní ověřování na základě některé vlastní ověřovací služby a nikoli přihlašovacích údajů systému Windows, musíte implementovat vlastní modul HTTP ADP.NET pro ověřování.<br /><br /> Příklad toho, jak používat vlastní schéma základního ověřování s WCF Data Services, najdete v blogovém příspěvku [OData a ověřování – část 6 – vlastní základní ověřování](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/).|  
|Ověřování systému Windows|Pověření systému Windows se vyměňují pomocí protokolu NTLM nebo Kerberos. Tento mechanismus je bezpečnější než základní ověřování nebo ověřování algoritmem Digest, vyžaduje však, aby klientská aplikace byla založena na systému Windows. Služba IIS také poskytuje implementaci ověřování systému Windows pro požadavky HTTP v aplikaci ASP.NET. Další informace najdete v tématu [Přehled ověřování ASP.NET Forms](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100)).<br /><br /> Příklad použití ověřování systému Windows s WCF Data Services najdete v blogovém příspěvku [OData a ověřování – část 2 – ověřování systému Windows](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/).|  
|Ověřování ASP.NET Forms|Ověřování pomocí formulářů umožňuje ověřovat uživatele pomocí vlastního kódu a poté uchovat ověřovací token v souboru cookie nebo v adrese URL stránky. Uživatelská jména a hesla uživatelů se ověřují pomocí přihlašovacího formuláře, který vytvoříte. Neověřené požadavky jsou přesměrovány na přihlašovací stránku, kde uživatel poskytne své údaje a formulář odešle. Pokud aplikace požadavek ověří, systém vydá ověřovací lístek obsahující klíč k ověření identity následných požadavků. Další informace najdete v tématu [Zprostředkovatel ověřování na formuláři](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100)). **Poznámka k zabezpečení:**  Soubor cookie, který obsahuje lístek ověřování pomocí formulářů, není ve výchozím nastavení zabezpečený v případě, že používáte ověřování pomocí formulářů ve webové aplikaci v ASP.NET. Je vhodné zvážit, že budete vyžadovat protokol SSL, což zajistí ochranu ověřovacího lístku i počátečních přihlašovacích pověření. <br /><br /> Příklad použití ověřování pomocí formulářů s WCF Data Services najdete v blogovém příspěvku [OData a ověřování – část 7 – ověřování pomocí formulářů](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/).|  
|Ověřování na základě deklarací|V rámci ověřování založeného na deklaracích dat služba data Service spoléhá na to, že je k ověření uživatele Důvěryhodná služba poskytovatele identity od třetí strany. Tento poskytovatel identit pozitivně ověřuje uživatele, který žádá o přístup k prostředkům datové služby, a vydá token zajišťující přístup k požadovaným prostředkům. Tento token se pak předává datové službě, která udělí uživateli přístup na základě vztahu důvěry se službou identit, jež přístupový token vydala.<br /><br /> Výhodou poskytovatele ověřování na základě deklarací je, že ho lze použít k ověřování různých typů klientů napříč důvěryhodnými doménami. Díky použití takového poskytovatele třetí strany může datová služba předat požadavky na údržbu a ověřování uživatelů. OAuth 2.0 je ověřovací protokol založený na deklaracích podporovaný službou AppFabric Access Control na platformě Microsoft Azure, který je určen pro federované ověřování poskytované jako služba. Tento protokol podporuje služby založené na technologii REST. Příklad toho, jak použít OAuth 2,0 s WCF Data Services, najdete v blogovém příspěvku [OData a ověřování – část 8 – zalamování OAuth](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Ověřování v knihovně klienta  
 Ve výchozím nastavení neposkytuje Klientská knihovna WCF Data Services přihlašovací údaje při vytváření žádosti o službu OData. Když datová služba vyžaduje přihlašovací údaje k ověření uživatele, můžou se tyto přihlašovací údaje dodávat do <xref:System.Net.NetworkCredential>, ke kterému se přistupovalo z vlastnosti <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> <xref:System.Data.Services.Client.DataServiceContext>, jako v následujícím příkladu:  
  
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
  
 Další informace najdete v tématu [postupy: určení přihlašovacích údajů klienta Data žádosti o služby](specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Pokud datová služba vyžaduje přihlašovací údaje, které nelze zadat pomocí objektu <xref:System.Net.NetworkCredential>, jako je například token založený na deklaracích nebo soubor cookie, je nutné ručně nastavit hlavičky v požadavku HTTP, obvykle v hlavičce `Authorization` a `Cookie`. Další informace o tomto druhu scénáře ověřování najdete v blogovém příspěvku [OData a ověřování – část 3 – latence háky](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/). Příklad nastavení hlaviček protokolu HTTP ve zprávě požadavku naleznete v tématu [How to: set Headers in the Client Request](how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Zosobnění  
 Obecně platí, že datová služba přistupuje k požadovaným prostředkům, například k souborům na serveru nebo v databázi, pomocí pověření pracovního procesu, který je hostitelem datové služby. Při použití zosobnění se aplikace ASP.NET můžou spouštět s identitou systému Windows (uživatelský účet) uživatele, který požadavek odeslal. Zosobnění se běžně používá v aplikacích, které k ověření uživatele využívají službu IIS, a pro přístup k požadovaným prostředkům se používají pověření tohoto typu. Další informace najdete v tématu [zosobnění ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)).  
  
## <a name="configuring-data-service-authorization"></a>Konfigurace autorizace datové služby  
 Autorizace představuje udělení přístupu k prostředkům aplikace pro objekt zabezpečení nebo proces, který je identifikován na základě dřívějšího úspěšného ověření. Obecně platí, že uživatelům datové služby je vhodné udělit pouze práva dostatečná k provedení operací vyžadovaných klientskými aplikacemi.  
  
### <a name="restrict-access-to-data-service-resources"></a>Omezení přístupu k prostředkům datové služby  
 Ve výchozím nastavení vám WCF Data Services umožňuje udělit běžný přístup pro čtení a zápis proti prostředkům datové služby (sadě entit a operace služby) každému uživateli, který bude mít přístup k datové službě. Pravidla určující přístup pro čtení a zápis lze definovat samostatně pro každou sadu entit, která je datovou službou vystavena, a pro jakékoli operace služby. Doporučujeme omezit přístup pro čtení a zápis pouze na prostředky vyžadované klientskou aplikací. Další informace najdete v tématu [minimální požadavky na přístup k prostředkům](configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Implementace zachycovacích dotazů založených na rolích  
 Zachycovací dotazy umožňují zachytit požadavky na prostředky datové služby předtím, než je datová služba vykoná. Další informace naleznete v tématu [zachycení](interceptors-wcf-data-services.md). Zachycovací dotazy dovolují přijímat rozhodnutí o autorizaci na základě ověřeného uživatele, který požadavek zadává. Příklad toho, jak omezit přístup k prostředkům datové služby na základě identity ověřeného uživatele, najdete v tématu [Postup: zachycení zpráv datových služeb](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Omezení přístupu k trvalému úložišti dat a místním prostředkům  
 Účtům používaným pro přístup k trvalému úložišti je vhodné poskytnout pouze dostatečná práva pro databázi nebo systém souborů tak, aby byly podporovány požadavky datové služby. Pokud se používá anonymní ověřování, slouží právě tento účet ke spouštění hostitelské aplikace. Další informace naleznete v tématu [How to: vývoj a WCF Data Service běžící na službě IIS](how-to-develop-a-wcf-data-service-running-on-iis.md). Při použití zosobnění musí být k těmto prostředkům udělen přístup ověřeným uživatelům, obvykle v rámci skupiny systému Windows.  
  
## <a name="other-security-considerations"></a>Další informace o zabezpečení  
  
### <a name="secure-the-data-in-the-payload"></a>Zabezpečení dat v datové části  
Služba OData je založená na protokolu HTTP. Hlavička zprávy HTTP může v závislosti na typu ověřování implementovaného datovou službou obsahovat důležitá uživatelská pověření. Cenná zákaznická data, která je třeba ochránit, mohou být obsažena také v textu zprávy. V obou těchto případech doporučujeme k ochraně informací přenášených v síti používat protokol SSL.  
  
### <a name="ignored-message-headers-and-cookies"></a>Ignorované hlavičky zpráv a soubory cookie  
 Hlavičky požadavků HTTP s výjimkou těch, které deklarují typy obsahu a umístění prostředků, se ignorují a datová služba je nenastavuje.  
  
 Soubory cookie lze použít jako součást schématu ověřování, například s ověřováním pomocí formulářů ASP.NET. Služby WCF DataServices ale ignorují všechny soubory cookie HTTP nastavené u příchozího požadavku. Hostitel datové služby může soubor cookie zpracovat, ale modul runtime WCF Data Services nikdy neanalyzuje nebo nevrací soubory cookie. Klientská knihovna WCF Data Services také nezpracovává soubory cookie odeslané v odpovědi.  
  
### <a name="custom-hosting-requirements"></a>Vlastní požadavky na hostování  
 Ve výchozím nastavení je WCF Data Services vytvořena jako aplikace ASP.NET hostovaná ve službě IIS. To datové službě dovoluje těžit z bezpečného chování této platformy. Můžete definovat WCF Data Services hostovaných vlastním hostitelem. Další informace najdete v tématu [hostování datové služby](hosting-the-data-service-wcf-data-services.md). Součásti a platforma hostující datovou službu musí jako prevenci proti útokům na datovou službu zajistit následující bezpečnostní chování:  
  
- Omezení délky identifikátoru URI přijímaného v požadavku na datovou službu pro všechny možné operace.  
  
- Omezení velikosti příchozí a odchozí zprávy HTTP.  
  
- Omezení celkového počtu nevyřízených požadavků v kterémkoli okamžiku.  
  
- Omezte velikost hlaviček protokolu HTTP a jejich hodnot a poskytněte WCF Data Services přístup k datům záhlaví.  
  
- Rozpoznání a odvracení známých útoků, jako jsou útoky TCP SYN a útoky pomocí opakovaného přehrávání zprávy.  
  
### <a name="values-are-not-further-encoded"></a>Hodnoty se dále nešifrují  
 Hodnoty vlastností odeslané do datové služby nejsou dále kódovány modulem runtime WCF Data Services. Pokud například řetězcová vlastnost entity obsahuje formátovaný obsah ve formátu HTML, jeho značky nejsou datovou službou zašifrovány do jazyka HTML. Datová služby zároveň dále nešifruje hodnoty vlastností v odezvě. Další šifrování neprovádí ani knihovna klienta.  
  
### <a name="considerations-for-client-applications"></a>Důležité informace o klientských aplikacích  
 Následující požadavky na zabezpečení platí pro aplikace, které používají klienta WCF Data Services pro přístup ke službám OData:  
  
- Knihovna klienta předpokládá, že protokoly použité k přístupu k datové službě poskytují odpovídající úroveň zabezpečení.  
  
- Knihovna klienta používá veškeré výchozí hodnoty pro časové limity a možnosti analýzy transportních zásobníků poskytovaných podkladovou platformou.  
  
- Knihovna klienta nenačítá žádná nastavení z konfiguračních souborů aplikace.  
  
- Knihovna klienta neimplementuje žádné mechanismy přístupu napříč doménami. Místo toho využívá mechanismy poskytované podkladovým zásobníkem HTTP.  
  
- Knihovna klienta neobsahuje žádné prvky uživatelského rozhraní a nikdy se nepokouší zobrazit ani vykreslit data, která přijímá nebo odesílá.  
  
- Doporučujeme, aby klientské aplikace vždy ověřovaly uživatelské vstupy i údaje přijímané z nedůvěryhodných služeb.  
  
## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
