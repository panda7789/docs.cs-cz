---
title: Ověření integrované Windows s rozšířenou ochranou
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1ab211a45b5a3cb835d051c53d321dc39cac2f9f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193828"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Ověření integrované Windows s rozšířenou ochranou
Vylepšení, které ovlivňují způsob integrované ověřování zařizuje služba Windows byly provedeny <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Mail.SmtpClient>, <xref:System.Net.Security.SslStream>, <xref:System.Net.Security.NegotiateStream>, a související třídy v <xref:System.Net> a souvisejících oborech názvů. Byla přidána podpora pro rozšířené ochrany pro zvýšení zabezpečení.  
  
 Tyto změny mohou ovlivnit aplikace, které používají tyto třídy pro vytvoření webových požadavků a přijímání odpovědí, kde se používá integrované ověřování Windows. Tato změna může ovlivnit také webové servery a klientské aplikace, které jsou nakonfigurovány pro použití integrovaného ověřování Windows.  
  
 Tyto změny mohou ovlivnit také aplikace, které používají tyto třídy pro ostatní typy požadavků a přijímání odpovědí, kde se používá integrované ověřování Windows.  
  
 Změny pro podporu rozšířenou ochranu jsou k dispozici pouze pro aplikace pro Windows 7 a Windows Server 2008 R2. Funkce rozšířené ochrany nejsou k dispozici v dřívějších verzích Windows.  
  
## <a name="overview"></a>Přehled  
 Návrh integrované ověřování Windows umožňuje některé přihlašovací údaje challenge odpovědí univerzální, což znamená, můžete opakovaně používat nebo přeposílání. Odpovědi na výzvu třeba vytvořit minimálně s konkrétní informace o cílové a pokud možno také s konkrétní informace o některých kanálu. Služby potom můžete zadat Rozšířená ochrana k zajištění, že odpovědi na výzvu přihlašovacích údajů obsahovat specifické informace službu jako je například hlavní název služby (SPN). Pomocí těchto informací v výměnu přihlašovacích údajů budou moct lepší ochranu proti zneužití přihlašovacích údajů challenge odpovědi, může být nesprávně použité služby.  
  
 Návrh rozšířené ochrany je vylepšení ověřovacích protokolů má zmírňovat útoky na přenos ověřování. Je zásadní kolem koncepce kanálu a vazbách služby.  
  
 Celkové cíle jsou následující:  
  
1.  Pokud klient je aktualizován, aby podporoval rozšířenou ochranu, aplikace by mělo nabízet vazeb kanálu a vazeb informace o službě, všechny protokoly podporované metody ověřování. Informace o vazbě kanálu lze zadat pouze po kanálu (TLS) k vytvoření vazby. Informace o vazbě služby by měl vždycky zadat.  
  
2.  Aktualizace serverů, které jsou správně nakonfigurovány, mohou ověření kanálu a informace o vazbě služby, pokud je k dispozici v ověřovacím tokenu klienta a zamítnout pokus o ověření, pokud se neshodují vazby kanálů. V závislosti na scénáři nasazení serverů ověřit vazby kanálu, vazby služby nebo obojí.  
  
3.  Aktualizace serverů se budou moct následně přijímal nebo odmítal požadavky klientů nižší úrovně, které neobsahují informace o vazbě kanál na základě zásad.  
  
 Informace využívané ve rozšířené ochrany se skládá z jednoho nebo obou následujících dvou částí:  
  
1.  Token vazby kanálu nebo CBT.  
  
2.  Informace o vazbách služby ve formě hlavní název služby nebo hlavní název služby.  
  
 Informace o vazbách služby je údaj o záměru klienta k ověření koncového bodu konkrétní služby. Její komunikace z klienta na server s následujícími vlastnostmi:  
  
-   Hodnota hlavního názvu služby musí být k dispozici na serveru, který provádí ověření klienta v podobě prostého textu.  
  
-   Hodnota hlavního názvu služby je veřejná.  
  
-   Hlavní název služby musí být kryptograficky chráněný během přenosu, tak, aby útok man-in-the-middle nelze vložit, odstranit nebo změnit jeho hodnotu.  
  
 CBT je vlastnost vnější zabezpečeného kanálu (například TLS) používá k tie (vazba) se do konverzace přes kanál vnitřní, ověření klienta. CBT musí mít následující vlastnosti (také definované v IETF RFC 5056):  
  
-   Když vnější kanálu existuje, hodnota CBT musí být vlastnost vnější kanálu nebo koncový bod serveru nezávisle na sobě byly přijaty klientských i serverových stranami konverzaci.  
  
-   Hodnota CBT odeslány klientem, nesmí být něco, co útočník může ovlivnit.  
  
-   O tajemství CBT hodnoty nebudou provedeny žádné záruky. To ale neznamená, že hodnota vazby služby a také informace o vazbě kanál vždy se dají prozkoumat jakýkoli jiný, ale serveru, který provádí ověřování, jak může být šifrování protokolu výkonu CBT.  
  
-   CBT musí být kryptograficky integrity chráněný během přenosu, tak, aby útočník nelze vložit, odstranit nebo změnit jeho hodnotu.  
  
 Klient přenosu na server v podobě tamperproof hlavní název služby a CBT provádí vazby kanálu. Server ověří informace o vazbě kanálu v souladu s jeho zásadami a odmítá pokusy o ověření, pro které je není myslíte, že samotný byla zamýšleným cílem. Tímto způsobem, jsou k dispozici dva kanály stát kryptograficky jsou technologicky propojené.  
  
 Zachování kompatibility s existující klienti a aplikace, může server nakonfigurován umožňující pokusy o ověření klientům, kteří se ještě nepodporuje rozšířenou ochranu. To se označuje jako "částečně odolný" konfigurace, na rozdíl od "plně odolný" konfigurace.  
  
 Více součástí <xref:System.Net> a <xref:System.Net.Security> obory názvů provést integrované ověřování Windows pro volající aplikaci. Tato část popisuje změny System.Net součástí, přidáte rozšířenou ochranu pomocí jejich používá integrované ověřování Windows.  
  
 Rozšířená ochrana je momentálně podporovaný na Windows 7. Poskytuje mechanismus, můžete určit aplikace, pokud operační systém podporoval rozšířenou ochranu.  
  
## <a name="changes-to-support-extended-protection"></a>Změny pro podporu rozšířené ochrany  
 Proces ověřování použít pro integrované ověřování Windows, v závislosti na ověřovací protokol používá, často vyžaduje challenge vydané do cílového počítače a odesílaných zpět do klientského počítače. Rozšířená ochrana přidává nové funkce pro tento proces ověřování  
  
 <xref:System.Security.Authentication.ExtendedProtection> Obor názvů poskytuje podporu pro ověřování s použitím rozšířené ochrany pro aplikace. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> Třídy v tomto oboru názvů představuje vazbu kanálu. <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Třídy v tomto oboru názvů představuje zásad rozšířené ochrany používaná serveru pro ověření příchozích připojení klientů. Ostatních členů třídy se používají s rozšířenou ochranu.  
  
 Tyto třídy pro serverové aplikace, patří následující:  
  
 A <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> , který obsahuje následující prvky:  
  
-   <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> Vlastnost, která určuje, zda operační systém podporuje integrované ověřování systému windows s rozšířenou ochranu.  
  
-   A <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> hodnotu, která určuje, kdy by se měly vynucovat zásady rozšířené ochrany.  
  
-   A <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> určující scénář nasazení. To ovlivňuje způsob rozšířené ochrany je zaškrtnuté políčko.  
  
-   Volitelně <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> , který obsahuje vlastní seznam hlavní název služby, který se používá k porovnání s hlavní název služby, který klient poskytl jako zamýšleným cílem ověřování.  
  
-   Volitelně <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> , který obsahuje vlastní vazbu kanálu pro účely ověření. Tento scénář není běžný případ  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration> Obor názvů poskytuje podporu pro konfiguraci ověřování s použitím rozšířené ochrany pro aplikace.  
  
 Počet funkcí změny byly provedeny pro podporu rozšířenou ochranu v existujícím <xref:System.Net> oboru názvů. Tyto změny patří:  
  
-   Nový <xref:System.Net.TransportContext> přidá do třídy <xref:System.Net> obor názvů, který reprezentuje kontext přenosu.  
  
-   Nové <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> a <xref:System.Net.HttpWebRequest.GetRequestStream%2A> přetížení metody v <xref:System.Net.HttpWebRequest> třídu, která povolí načítání <xref:System.Net.TransportContext> pro podporu rozšířené ochrany pro klientské aplikace.  
  
-   Doplňky <xref:System.Net.HttpListener> a <xref:System.Net.HttpListenerRequest> třídy pro podporu serverových aplikací.  
  
 Provedené změny funkcí pro podporu rozšířené ochrany pro klientské aplikace SMTP v existujícím <xref:System.Net.Mail> obor názvů:  
  
-   A <xref:System.Net.Mail.SmtpClient.TargetName%2A> vlastnost <xref:System.Net.Mail.SmtpClient> třídu, která představuje hlavní název služby pro účely ověření při používání aplikace Rozšířená ochrana pro klienta SMTP.  
  
 Počet funkcí změny byly provedeny pro podporu rozšířenou ochranu v existujícím <xref:System.Net.Security> oboru názvů. Tyto změny patří:  
  
-   Nové <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> a <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> přetížení metody v <xref:System.Net.Security.NegotiateStream> třídu, která povolí předávání CBT pro podporu rozšířené ochrany pro klientské aplikace.  
  
-   Nové <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> a <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> přetížení metody v <xref:System.Net.Security.NegotiateStream> třídu, která povolí předávání <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> pro podporu rozšířené ochrany pro serverové aplikace.  
  
-   Nový <xref:System.Net.Security.SslStream.TransportContext%2A> vlastnost <xref:System.Net.Security.SslStream> třída podporující rozšířené ochrany pro klientské a serverové aplikace.  
  
 A <xref:System.Net.Configuration.SmtpNetworkElement> vlastnost byla přidaná kvůli podpoře konfigurace rozšířené ochrany pro klienty SMTP v <xref:System.Net.Security> oboru názvů.  
  
## <a name="extended-protection-for-client-applications"></a>Rozšířená ochrana pro klientské aplikace  
 Podpora rozšířené ochrany pro většinu aplikací klienta se automaticky stane. <xref:System.Net.HttpWebRequest> a <xref:System.Net.Mail.SmtpClient> třídy podporovat rozšířenou ochranu pokaždé, když se na základní verzi Windows podporuje rozšířenou ochranu. <xref:System.Net.HttpWebRequest> Sestavený z názvu SPN odešle instanci <xref:System.Uri>. Ve výchozím nastavení <xref:System.Net.Mail.SmtpClient> instance odešle název SPN sestavený z názvu hostitele serveru SMTP, e-mailu.  
  
 Pro vlastní ověřování, klientské aplikace můžou použít <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> nebo <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> metody v <xref:System.Net.HttpWebRequest> třídu, která umožňují načítání <xref:System.Net.TransportContext> a CBT pomocí <xref:System.Net.TransportContext.GetChannelBinding%2A> metoda.  
  
 Hlavní název služby pro integrované ověřování Windows odeslané <xref:System.Net.HttpWebRequest> instance pro určitou službu lze přepsat nastavením <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> vlastnost.  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A> Vlastnost lze nastavit vlastní název SPN pro integrované ověřování Windows pro připojení SMTP.  
  
## <a name="extended-protection-for-server-applications"></a>Rozšířená ochrana pro serverové aplikace  
 <xref:System.Net.HttpListener> automaticky poskytuje mechanismy ověřování vazby služby při ověřování pomocí protokolu HTTP.  
  
 Nejbezpečnější scénářem je povolit rozšířenou ochranu u předpony HTTPS://. V takovém případě nastavte <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> do <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> s <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> nastavena na <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> nebo <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, a <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> nastavena na <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> hodnotu <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> vloží <xref:System.Net.HttpListener> v částečně odolný režim chráněno. současně <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> odpovídá plně zesíleném režimu.  
  
 V této konfiguraci po odeslání žádosti na server prostřednictvím vnější zabezpečený kanál channel vnější dotaz na vazby kanálu. Tato vazba kanálu je předána volání rozhraní SSPI ověřování, které ověření, které vazby kanálu v objektu blob odpovídá ověřování. Existují tři možné výsledky:  
  
1.  Základní operační systém serveru nepodporuje rozšířenou ochranu. Požadavek nesmí být vystavená pro aplikace a neoprávněným odpovědí (401) bude vrácen do klienta. Zpráva se budou protokolovat do <xref:System.Net.HttpListener> zdroj trasování, určení příčiny selhání.  
  
2.  Volání rozhraní SSPI selže, označující, že buď klienta zadaný vazby kanálu, který neodpovídal očekávané hodnotě načíst z vnějšího kanálu nebo klient dodat vazbu kanálu při konfiguraci zásad rozšířené ochrany na serveru se nezdařilo. pro <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>. V obou případech se žádost nebude možné vystavit aplikaci a neoprávněným odpovědí (401) bude vrácen do klienta. Zpráva se budou protokolovat do <xref:System.Net.HttpListener> zdroj trasování, určení příčiny selhání.  
  
3.  Klient určuje vazbu správném kanálu nebo se může připojit bez zadání vazby kanálů od zásady rozšířené ochrany na serveru se nakonfigurují <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> požadavek se vrátil do aplikace pro zpracování. Kontrola názvu služby neproběhne probíhá automaticky. Aplikace můžete provádět vlastní název ověření pomocí <xref:System.Net.HttpListenerRequest.ServiceName%2A> vlastností, ale za těchto okolností je redundantní.  
  
 Pokud aplikace zavolá vlastní SSPI pro ověřování na základě vzájemně předané v textu požadavku HTTP objektů BLOB a chce vazby kanálu, potřebuje načíst vazby očekávané kanálu z vnějšího zabezpečený kanál pomocí <xref:System.Net.HttpListener> Chcete-li předat do nativní Win32 [Funkce AcceptSecurityContext](https://go.microsoft.com/fwlink/?LinkId=147021) funkce. Chcete-li to provést, použijte <xref:System.Net.HttpListenerRequest.TransportContext%2A> vlastnosti a volání <xref:System.Net.TransportContext.GetChannelBinding%2A> metodu pro načtení CBT. Jsou podporovány pouze vazby koncového bodu. Pokud nic dalšího <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> není zadán, <xref:System.NotSupportedException> bude vyvolána výjimka. Pokud je základní operační systém nepodporuje vazby kanálu <xref:System.Net.TransportContext.GetChannelBinding%2A> metoda vrátí <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> obtékání ukazatele na vazby vhodné k předání do kanálu [Funkce AcceptSecurityContext](https://go.microsoft.com/fwlink/?LinkId=147021) – funkce jako pvBuffer člena struktury SecBuffer předaný `pInput` parametru. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> Vlastnost obsahuje délku v bajtech, vazba kanálu. Pokud příslušný operační systém nepodporuje vazby kanálů, funkce vrátí `null`.  
  
 Další možností je to možné je povolit rozšířenou ochranu u předpony HTTP://, pokud nejsou použity proxy servery. V takovém případě nastavte <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> do <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> s <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> nastavena na <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> nebo <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, a <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> nastavena na <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> hodnotu <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> vloží <xref:System.Net.HttpListener> v částečně odolný režim chráněno. současně <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> odpovídá plně zesíleném režimu.  
  
 Výchozí seznam povolených služeb názvů se vytvoří podle předpony, které byly zaregistrovány <xref:System.Net.HttpListener>. Toto výchozí seznam se dají prozkoumat prostřednictvím <xref:System.Net.HttpListener.DefaultServiceNames%2A> vlastnost. Pokud seznam není úplný, aplikaci můžete zadat název kolekce vlastní službu v konstruktoru pro <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> třídy, který se použije namísto seznamu název výchozí služby.  
  
 V této konfiguraci po provedení požadavku na server bez vnějším zabezpečené ověřování kanálem pokračuje obvykle bez kontroly vazby kanálu. Pokud je ověření úspěšné, kontext se dotazují pro název služby, že klient k dispozici a ověřovat na seznam přijatelných názvů služeb. Existují čtyři možných výsledků:  
  
1.  Základní operační systém serveru nepodporuje rozšířenou ochranu. Požadavek nesmí být vystavená pro aplikace a neoprávněným odpovědí (401) bude vrácen do klienta. Zpráva se budou protokolovat do <xref:System.Net.HttpListener> zdroj trasování, určení příčiny selhání.  
  
2.  Základní operační systém klienta nepodporuje rozšířenou ochranu. V <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> konfigurace, pokus o ověření proběhne úspěšně a požadavek se vrátil do aplikace. V <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> konfigurace, se nezdaří pokus o ověření. Požadavek nesmí být vystavená pro aplikace a neoprávněným odpovědí (401) bude vrácen do klienta. Zpráva se budou protokolovat do <xref:System.Net.HttpListener> zdroj trasování, určení příčiny selhání.  
  
3.  Základní operační systém klienta podporuje rozšířené ochrany, ale aplikace nejsou specifikovány vazby služby. Požadavek nesmí být vystavená pro aplikace a neoprávněným odpovědí (401) bude vrácen do klienta. Zpráva se budou protokolovat do <xref:System.Net.HttpListener> zdroj trasování, určení příčiny selhání.  
  
4.  Klient zadat vazby služby. Vazby služby je ve srovnání s seznam povolených služeb vazby. Pokud se nenajde, požadavek se vrátí do aplikace. V opačném případě požadavku nesmí být vystavená pro aplikace a neoprávněným odpovědí (401) se automaticky vrácen do klienta. Zpráva se budou protokolovat do <xref:System.Net.HttpListener> zdroj trasování, určení příčiny selhání.  
  
 Pokud tento jednoduchý přístup pomocí povolený seznam přijatelných názvů služeb není dostatečná, aplikace může poskytnout vlastní ověření názvu služby dotazováním <xref:System.Net.HttpListenerRequest.ServiceName%2A> vlastnost. V případech, 1 a 2 výše, vlastnost vrátí `null`. V případě 3 vrátí prázdný řetězec. V případě, 4, název služby zadán klient bude vrácen.  
  
 Tyto funkce rozšířené ochrany lze použít také aplikace serveru ověřování s jinými typy požadavků a jsou používány Důvěryhodné servery proxy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Authentication.ExtendedProtection>  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>
