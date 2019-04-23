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
ms.openlocfilehash: 1e134d877c45af00e2a2fb7e7ef0882ffd7ddc48
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119116"
---
# <a name="securing-wcf-data-services"></a>Zabezpečení datových služeb WCF Data Services
Toto téma popisuje důležité informace o zabezpečení, které jsou specifické pro vývoj, nasazování a spouštění datové služby WCF a aplikací tento přístup ke službám, které podporují Open Data Protocol (OData). Také postupujte podle doporučení pro vytváření zabezpečených aplikací rozhraní .NET Framework.  
  
Při plánování zabezpečení služby OData na základě služeb WCF Data Services, je třeba vyřešit proces zjišťování a ověření identity objektu zabezpečení, ověřování a autorizace, procesu, který určuje, zda je ověřený objekt zabezpečení povolen přístup k požadovaným prostředkům. Dále je vhodné zvážit, zda chcete zprávy šifrovat pomocí protokolu SSL.  
  
## <a name="authenticating-client-requests"></a>Ověřování požadavků klientů  
Služby WCF Data Services neimplementuje jakéhokoli druhu ověřování vlastní, ale využívá ověřování poskytované hostitele datové služby. To znamená, že služba předpokládá, že všechny požadavky, které obdrží, již byly ověřeny síťovým hostitelem a že hostitel správně vyhodnotil objekt zabezpečení požadavku prostřednictvím rozhraní poskytovaných službou WCF Data Services. Tyto možnosti ověřování a přístupy jsou podrobně popsány v multipart [OData a ověřovací série](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Možnosti ověřování ve službě WCF Data  
 Následující tabulka shrnuje některé mechanismy, které jsou k dispozici pro ověřování požadavků na službu WCF Data Service.  
  
|Možnosti ověřování|Popis|  
|----------------------------|-----------------|  
|Anonymní ověření|Pokud je aktivováno anonymní ověřování HTTP, může se k datové službě připojit libovolný objekt zabezpečení. U anonymního přístupu nejsou požadována pověření. Tuto možnost použijte pouze v případě, že chcete přístup k datové službě povolit všem uživatelům.|  
|Základní ověřování a ověřování algoritmem Digest|Pro ověření jsou vyžadována pověření, která sestávají z uživatelského jména a hesla. Podporuje ověřování klientů jiných platforem než Windows. **Poznámka k zabezpečení:**  Základní pověření pro ověřování (uživatelské jméno a heslo) se odesílají v nešifrované podobě a může dojít k jejich zachycení. Ověřování algoritmem Digest odešle hodnotu hash vycházející ze zadaných pověření. Je tedy bezpečnější než základní ověřování. Oba zmíněné typy ověřování jsou však náchylné k útoku prostředníkem (man-in-the-middle). Při použití těchto metod ověřování je vhodné zvážit šifrování komunikace mezi klientem a datovou službou pomocí protokolu SSL (Secure Sockets Layer). <br /><br /> Implementace obou basic poskytuje Microsoft Internetové informační služby (IIS) a ověřování algoritmem digest pro protokol HTTP požadavků v aplikaci technologie ASP.NET. Tato implementace poskytovatele ověřování systému Windows umožňuje klientské aplikaci rozhraní .NET Framework vložit pověření do hlavičky HTTP požadavku na datovou službu. Dovoluje tak bez problémů vyjednat ověření uživatele systému Windows. Další informace najdete v tématu [technické informace o ověřování algoritmem Digest](https://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Pokud chcete, aby vaše data služba používala základní ověřování založené na některé vlastní ověřovací službě, nikoli přihlašovací údaje Windows, musíte implementovat vlastní modul HTTP ADP.NET pro ověřování.<br /><br /> Příklad toho, jak pomocí služeb WCF Data Services vlastního schématu základního ověřování, najdete v příspěvku blogu [OData a ověřování – část 6 – vlastní základní ověřování](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/).|  
|Ověřování systému Windows|Pověření systému Windows se vyměňují pomocí protokolu NTLM nebo Kerberos. Tento mechanismus je bezpečnější než základní ověřování nebo ověřování algoritmem Digest, vyžaduje však, aby klientská aplikace byla založena na systému Windows. Služba IIS zároveň poskytuje implementaci ověřování Windows pro požadavky HTTP v aplikaci technologie ASP.NET. Další informace najdete v tématu [Přehled ověřování formulářů ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100)).<br /><br /> Příklad toho, jak používat ověřování Windows pomocí služby WCF Data Services, najdete v příspěvku blogu [OData a ověřování – část 2 – ověření Windows](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/).|  
|Ověřování pomocí formulářů ASP.NET|Ověřování pomocí formulářů umožňuje ověřovat uživatele pomocí vlastního kódu a poté uchovat ověřovací token v souboru cookie nebo v adrese URL stránky. Uživatelská jména a hesla uživatelů se ověřují pomocí přihlašovacího formuláře, který vytvoříte. Neověřené požadavky jsou přesměrovány na přihlašovací stránku, kde uživatel poskytne své údaje a formulář odešle. Pokud aplikace požadavek ověří, systém vydá ověřovací lístek obsahující klíč k ověření identity následných požadavků. Další informace najdete v tématu [zprostředkovatele ověřování formulářů](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100)). **Poznámka k zabezpečení:**  Ve výchozím nastavení není zabezpečená souboru cookie, který obsahuje ověřovací lístek při použití ověřování pomocí formulářů v ASP.NET Web application. Je vhodné zvážit, že budete vyžadovat protokol SSL, což zajistí ochranu ověřovacího lístku i počátečních přihlašovacích pověření. <br /><br /> Pro příklad, jak používat forms ověřování pomocí služby WCF Data Services, najdete v blogovém příspěvku [OData a ověřování – část 7 – ověřování pomocí formulářů](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/).|  
|Ověřování na základě deklarací|Při ověřování nezaloženého na deklaracích datové služby spoléhá na důvěryhodné identit "třetí strany" poskytovatele služby k ověření uživatele. Tento poskytovatel identit pozitivně ověřuje uživatele, který žádá o přístup k prostředkům datové služby, a vydá token zajišťující přístup k požadovaným prostředkům. Tento token se pak předává datové službě, která udělí uživateli přístup na základě vztahu důvěry se službou identit, jež přístupový token vydala.<br /><br /> Výhodou poskytovatele ověřování na základě deklarací je, že ho lze použít k ověřování různých typů klientů napříč důvěryhodnými doménami. Díky použití takového poskytovatele třetí strany může datová služba předat požadavky na údržbu a ověřování uživatelů. OAuth 2.0 je ověřovací protokol založený na deklaracích podporovaný službou AppFabric Access Control na platformě Microsoft Azure, který je určen pro federované ověřování poskytované jako služba. Tento protokol podporuje služby založené na technologii REST. Příklad toho, jak pomocí služeb WCF Data Services OAuth 2.0, naleznete v příspěvku blogu [OData a ověřování – část 8 – OAuth ZABALENÍ](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Ověřování v knihovně klienta  
 Ve výchozím nastavení klientské knihovny služby WCF Data Services neposkytuje přihlašovací údaje při požadavku na službu OData. Pokud jsou přihlašovací údaje jsou povinné datová služba k ověření uživatele, lze je zadat tyto přihlašovací údaje v <xref:System.Net.NetworkCredential> k němu přistupovat z <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> vlastnost <xref:System.Data.Services.Client.DataServiceContext>, jako v následujícím příkladu:  
  
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
  
 Další informace najdete v tématu [jak: Zadání přihlašovacích údajů klienta požadavku na datovou službu](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Pokud datová služba vyžaduje přihlašovací pověření, která nelze zadat s použitím <xref:System.Net.NetworkCredential> objektu, jako jsou založené na deklaracích token nebo soubor cookie, je nutné ručně nastavit hlavičky v požadavku HTTP, obvykle `Authorization` a `Cookie` záhlaví. Další informace o tomto typu scénáře ověřování naleznete v příspěvku blogu [ OData a ověřování – část 3 – na straně klienta háky](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/). Příklad nastavení hlaviček HTTP ve zprávě požadavku naleznete v tématu [jak: Nastavit hlavičky v požadavku klienta](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Zosobnění  
 Obecně platí, že datová služba přistupuje k požadovaným prostředkům, například k souborům na serveru nebo v databázi, pomocí pověření pracovního procesu, který je hostitelem datové služby. Při použití zosobnění se [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace můžete spustit s použitím identity Windows (uživatelský účet) uživatele, který zadal žádost. Zosobnění se běžně používá v aplikacích, které k ověření uživatele využívají službu IIS, a pro přístup k požadovaným prostředkům se používají pověření tohoto typu. Další informace najdete v tématu [zosobnění technologie ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)).  
  
## <a name="configuring-data-service-authorization"></a>Konfigurace autorizace datové služby  
 Autorizace představuje udělení přístupu k prostředkům aplikace pro objekt zabezpečení nebo proces, který je identifikován na základě dřívějšího úspěšného ověření. Obecně platí, že uživatelům datové služby je vhodné udělit pouze práva dostatečná k provedení operací vyžadovaných klientskými aplikacemi.  
  
### <a name="restrict-access-to-data-service-resources"></a>Omezení přístupu k prostředkům datové služby  
 Ve výchozím nastavení, služby WCF Data Services vám umožní udělit běžné přístup pro čtení a zápis proti prostředkům datové služby (entity nastavit a operace služby) kterémukoli uživateli, který je možné získat přístup ke službě data. Pravidla určující přístup pro čtení a zápis lze definovat samostatně pro každou sadu entit, která je datovou službou vystavena, a pro jakékoli operace služby. Doporučujeme omezit přístup pro čtení a zápis pouze na prostředky vyžadované klientskou aplikací. Další informace najdete v tématu [minimální požadavky na přístup prostředků](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Implementace zachycovacích dotazů založených na rolích  
 Zachycovací dotazy umožňují zachytit požadavky na prostředky datové služby předtím, než je datová služba vykoná. Další informace najdete v tématu [sběrače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Zachycovací dotazy dovolují přijímat rozhodnutí o autorizaci na základě ověřeného uživatele, který požadavek zadává. Příklad toho, jak omezit přístup k prostředkům datové služby podle identity ověřeného uživatele, najdete v části [jak: Zachycování zpráv datové služby](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Omezení přístupu k trvalému úložišti dat a místním prostředkům  
 Účtům používaným pro přístup k trvalému úložišti je vhodné poskytnout pouze dostatečná práva pro databázi nebo systém souborů tak, aby byly podporovány požadavky datové služby. Pokud se používá anonymní ověřování, slouží právě tento účet ke spouštění hostitelské aplikace. Další informace najdete v tématu [jak: Vývoj datové služby WCF ve službě IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Při použití zosobnění musí být k těmto prostředkům udělen přístup ověřeným uživatelům, obvykle v rámci skupiny systému Windows.  
  
## <a name="other-security-considerations"></a>Další informace o zabezpečení  
  
### <a name="secure-the-data-in-the-payload"></a>Zabezpečení dat v datové části  
OData je založené na protokolu HTTP. Hlavička zprávy HTTP může v závislosti na typu ověřování implementovaného datovou službou obsahovat důležitá uživatelská pověření. Cenná zákaznická data, která je třeba ochránit, mohou být obsažena také v textu zprávy. V obou těchto případech doporučujeme k ochraně informací přenášených v síti používat protokol SSL.  
  
### <a name="ignored-message-headers-and-cookies"></a>Ignorované hlavičky zpráv a soubory cookie  
 Hlavičky požadavků HTTP s výjimkou těch, které deklarují typy obsahu a umístění prostředků, se ignorují a datová služba je nenastavuje.  
  
 Soubory cookie slouží jako součást ověřovacího schématu, jako například ASP.NET s ověřováním pomocí formulářů. Všechny soubory cookie HTTP, nastavte pro příchozí požadavek se však ignorují WCF DataServices. Hostitele datové služby může soubor cookie zpracovat, ale modul runtime WCF Data Services neanalyzuje ani nevrací soubory cookie. Klientská knihovna služby WCF Data Services nezpracovává ani soubory cookie odesílané v odpovědi.  
  
### <a name="custom-hosting-requirements"></a>Vlastní požadavky na hostování  
 Ve výchozím nastavení služby WCF Data Services se vytvoří jako aplikace ASP.NET hostované ve službě IIS. To datové službě dovoluje těžit z bezpečného chování této platformy. Můžete definovat datové služby WCF, které jsou hostované u vlastního hostitele. Další informace najdete v tématu [hostitelem datové služby](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Součásti a platforma hostující datovou službu musí jako prevenci proti útokům na datovou službu zajistit následující bezpečnostní chování:  
  
-   Omezení délky identifikátoru URI přijímaného v požadavku na datovou službu pro všechny možné operace.  
  
-   Omezení velikosti příchozí a odchozí zprávy HTTP.  
  
-   Omezení celkového počtu nevyřízených požadavků v kterémkoli okamžiku.  
  
-   Omezení velikosti hlaviček protokolu HTTP a jejich hodnoty a služby WCF Data Services přístup k údajům v hlavičce.  
  
-   Rozpoznání a odvracení známých útoků, jako jsou útoky TCP SYN a útoky pomocí opakovaného přehrávání zprávy.  
  
### <a name="values-are-not-further-encoded"></a>Hodnoty se dále nešifrují  
 Hodnoty vlastností odesílané datové službě dále nešifrují modul runtime WCF Data Services. Pokud například řetězcová vlastnost entity obsahuje formátovaný obsah ve formátu HTML, jeho značky nejsou datovou službou zašifrovány do jazyka HTML. Datová služby zároveň dále nešifruje hodnoty vlastností v odezvě. Další šifrování neprovádí ani knihovna klienta.  
  
### <a name="considerations-for-client-applications"></a>Důležité informace o klientských aplikacích  
 Pro aplikace, které používají klienta WCF Data Services pro přístup ke službám OData, platí následující aspekty zabezpečení:  
  
-   Knihovna klienta předpokládá, že protokoly použité k přístupu k datové službě poskytují odpovídající úroveň zabezpečení.  
  
-   Knihovna klienta používá veškeré výchozí hodnoty pro časové limity a možnosti analýzy transportních zásobníků poskytovaných podkladovou platformou.  
  
-   Knihovna klienta nenačítá žádná nastavení z konfiguračních souborů aplikace.  
  
-   Knihovna klienta neimplementuje žádné mechanismy přístupu napříč doménami. Místo toho využívá mechanismy poskytované podkladovým zásobníkem HTTP.  
  
-   Knihovna klienta neobsahuje žádné prvky uživatelského rozhraní a nikdy se nepokouší zobrazit ani vykreslit data, která přijímá nebo odesílá.  
  
-   Doporučujeme, aby klientské aplikace vždy ověřovaly uživatelské vstupy i údaje přijímané z nedůvěryhodných služeb.  
  
## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
