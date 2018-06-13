---
title: Integrované ověřování systému Windows s rozšířené ochrany
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 88170162e4149580d532129666348d226540aced
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398128"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Integrované ověřování systému Windows s rozšířené ochrany
Byly provedeny vylepšení, které mají vliv jak integrované ověřování systému Windows, které se provádí ověřování <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Mail.SmtpClient>, <xref:System.Net.Security.SslStream>, <xref:System.Net.Security.NegotiateStream>, a související třídy v <xref:System.Net> a související obory názvů. Byla přidána podpora pro rozšířená ochrana pro zvýšení zabezpečení.  
  
 Tyto změny mohou ovlivnit aplikace, které používají tyto třídy webové požadavky a odpovědi přijímat, kde se používá integrované ověřování systému Windows. Tato změna může ovlivnit taky webové servery a klientské aplikace, které jsou nakonfigurovány pro použití integrovaného ověřování systému Windows.  
  
 Tyto změny může ovlivnit také aplikace, které používají tyto třídy Zkontrolujte ostatní typy požadavků a odpovědí přijímat, kde se používá integrované ověřování systému Windows.  
  
 K podpoře Rozšířená ochrana změny jsou k dispozici pouze pro aplikace v systému Windows 7 a Windows Server 2008 R2. Funkce rozšířené ochrany nejsou k dispozici v dřívějších verzích systému Windows.  
  
## <a name="overview"></a>Přehled  
 Návrh integrované ověřování systému Windows umožňuje některé odpovědí výzvy přihlašovacích údajů se univerzální, znamená, může být znovu použít nebo předají. Výzvy odpovědi musí zkonstruovat minimálně s konkrétní informace o cílové a pokud možno také některé specifické informace pro kanál. Služby jim pak můžou rozšířené ochrany a zajistit, že odpovědí výzvy přihlašovacích údajů obsahovat konkrétní informace služby například hlavní název služby (SPN). Pomocí těchto informací v výměnu přihlašovacích údajů budou moci lepší ochranu proti zneužití přihlašovacích údajů výzvy odpovědi, které mohou mít nesprávně použity služby.  
  
 Rozšířená ochrana je vylepšení ověřovací protokoly navržená tak, aby se minimalizoval útoky na přenos ověřování. Je zásadní kolem koncept kanál a informace o vazbě služby.  
  
 Celkové cíle jsou následující:  
  
1.  Pokud klient je aktualizovat, aby podporoval rozšířenou ochranu, aplikace by měla zadat vazeb kanálů a informace o vazbě služby pro všechny podporované ověřovací protokoly. Informace o vazbě kanál lze zadat pouze při kanál (TLS) pro vazbu. Informace o vazbě služby by měl vždy je nutné zadat.  
  
2.  Aktualizované serverů, které jsou správně nakonfigurovány, mohou ověřit kanál a informace o vazbě služby, pokud je k dispozici v tokenu ověřování klienta a odmítnout pokusu o ověření, pokud vazby kanálů se neshodují. V závislosti na scénáři nasazení mohou servery ověřit vytváření vazby kanálu, vazby služby nebo obojí.  
  
3.  Aktualizované servery mají možnost přijmout nebo odmítnout požadavky klientů nižší úrovně, které neobsahují informace o vazbě kanál na základě zásad.  
  
 Informace o používané Rozšířená ochrana se skládá z jedné nebo obou následujících dvou částí:  
  
1.  Tokenu s vazbou na kanál nebo CBT.  
  
2.  Informace o vazbě ve formě hlavní název služby nebo název SPN služby.  
  
 Vazby služby informace jsou údaje o záměr klienta k ověření koncového bodu konkrétní služby. Se zjištěnými z klienta na server s následujícími vlastnostmi:  
  
-   Hodnota SPN musí být k dispozici serveru, který provádí ověření klienta v podobě nešifrovaného textu.  
  
-   Hlavní název služby hodnotu veřejná.  
  
-   Hlavní název služby musí být kryptograficky chráněny během přenosu, tak, aby útok man-in-the-middle nelze vložit, odebrat nebo změnit jeho hodnotu.  
  
 Je vlastností vnější zabezpečený kanál (například TLS) používá ke svázání (vazby) CBT jeho konverzace přes kanál vnitřní, ověření klienta. CBT musí mít následující vlastnosti (také definované IETF RFC 5056):  
  
-   Pokud existuje vnější kanál, hodnota CBT musí být vlastnost identifikace vnější kanál nebo koncový bod serveru, nezávisle na dostali podle stranách klienta i serveru konverzace.  
  
-   Hodnota CBT odeslány klientem, nesmí být něco, co mohou mít vliv na útočník.  
  
-   O tajemství CBT hodnoty jsou vytvářeny žádné záruky. To ale neznamená, že hodnota vazby služby a také informace o vazbě kanál můžete vždy zkoumat žádné jiné, ale serveru, který provádí ověřování, jako může být šifrování protokol provádění CBT.  
  
-   CBT musí být kryptograficky integrity chráněný během přenosu, tak, že útočník nelze vložit, odebrat nebo změnit jeho hodnotu.  
  
 Vytváření vazby kanálu provádí převod hlavní název služby a CBT server způsobem tamperproof klienta. Server ověřuje informace o vazbě kanálu v souladu s své zásady a odmítá pokusy o ověření, pro které je není domníváte samotné byly zamýšleného cílového. Tímto způsobem dva kanály stát kryptograficky spojuje.  
  
 Zachování kompatibility s existující klienti a aplikace, může být server nakonfigurovat pro povolení pokusy o ověření klienty, kteří ještě nepodporují rozšířené ochrany. To se označuje jako "částečně odolný" konfigurace, na rozdíl od "plně odolný" konfigurace.  
  
 Několik součástí v <xref:System.Net> a <xref:System.Net.Security> obory názvů provést integrované ověřování systému Windows jménem volající aplikace. Tato část popisuje změny součástí System.NET – přidání rozšířené ochrany v jejich používání integrovaného ověřování systému Windows.  
  
 Rozšířená ochrana se aktuálně podporuje na systému Windows 7. Mechanismus je k dispozici, takže aplikace můžete určit, jestli operační systém podporuje rozšířené ochrany.  
  
## <a name="changes-to-support-extended-protection"></a>K podpoře Rozšířená ochrana změny  
 Proces ověřování pomocí integrovaného ověřování systému Windows, v závislosti na protokol ověřování používat, často zahrnuje výzvy od cílového počítače a odeslat zpátky do klientského počítače. Rozšířená ochrana pro tento proces ověřování přidává nové funkce  
  
 <xref:System.Security.Authentication.ExtendedProtection> Obor názvů poskytuje podporu pro ověřování pomocí Rozšířená ochrana pro aplikace. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> Třídy v tomto oboru názvů představuje vazbu kanálu. <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Třídy v tomto oboru názvů představuje zásady rozšířené ochrany server používá k ověření příchozí připojení klientů. Jiní členové třídy se používají s rozšířené ochrany.  
  
 Pro serverové aplikace tyto třídy patří:  
  
 A <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> který má následující prvky:  
  
-   <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> Vlastnost, která určuje, zda operační systém podporuje integrované ověřování systému windows s rozšířené ochrany.  
  
-   A <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> hodnotu, která určuje, kdy by se měly vynucovat zásady rozšířené ochrany.  
  
-   A <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> hodnotu, která určuje scénář nasazení. Vliv jak rozšířené ochrany je zaškrtnuté.  
  
-   Volitelný <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> obsahující vlastní seznam hlavní název služby, který se používá k porovnání SPN klient poskytl jako jeho cílem ověřování.  
  
-   Volitelný <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> obsahující vlastní kanál vazbu k ověření. Tento scénář není častých případech  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration> Obor názvů poskytuje podporu pro konfiguraci ověřování pomocí Rozšířená ochrana pro aplikace.  
  
 Počet změn, funkce, které byly provedeny pro podporu rozšířené ochrany v existující <xref:System.Net> oboru názvů. Tyto změny zahrnují následující:  
  
-   Nový <xref:System.Net.TransportContext> přidat do třídy <xref:System.Net> obor názvů, který reprezentuje kontext přenosu.  
  
-   Nové <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> a <xref:System.Net.HttpWebRequest.GetRequestStream%2A> přetížení metody v <xref:System.Net.HttpWebRequest> třídu, která povolí načítání <xref:System.Net.TransportContext> pro podporu rozšířené ochrany pro klientské aplikace.  
  
-   Doplňky <xref:System.Net.HttpListener> a <xref:System.Net.HttpListenerRequest> třídy pro podporu serverových aplikací.  
  
 Změna funkce došlo k podpoře Rozšířená ochrana pro klientské aplikace SMTP v existující <xref:System.Net.Mail> obor názvů:  
  
-   A <xref:System.Net.Mail.SmtpClient.TargetName%2A> vlastnost <xref:System.Net.Mail.SmtpClient> třídu, která představuje hlavní název služby bude používat pro ověření při používání aplikace Rozšířená ochrana pro klienta SMTP.  
  
 Počet změn, funkce, které byly provedeny pro podporu rozšířené ochrany v existující <xref:System.Net.Security> oboru názvů. Tyto změny zahrnují následující:  
  
-   Nové <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> a <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> přetížení metody v <xref:System.Net.Security.NegotiateStream> třídu, která povolí předávání CBT pro podporu rozšířené ochrany pro klientské aplikace.  
  
-   Nové <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> a <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> přetížení metody v <xref:System.Net.Security.NegotiateStream> třídu, která povolí předávání <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> pro podporu Rozšířená ochrana pro serverové aplikace.  
  
-   Nový <xref:System.Net.Security.SslStream.TransportContext%2A> vlastnost <xref:System.Net.Security.SslStream> třídy pro podporu rozšířené ochrany pro klientské a serverové aplikace.  
  
 A <xref:System.Net.Configuration.SmtpNetworkElement> vlastnost byla přidaná kvůli podpoře konfigurace rozšířené ochrany pro klienty SMTP v <xref:System.Net.Security> oboru názvů.  
  
## <a name="extended-protection-for-client-applications"></a>Rozšířená ochrana pro klientské aplikace  
 Rozšířená ochrana podpora pro většinu aplikací klienta se automaticky. <xref:System.Net.HttpWebRequest> a <xref:System.Net.Mail.SmtpClient> třídy podporují rozšířené ochrany vždy, když základní verze systému Windows podporuje rozšířené ochrany. <xref:System.Net.HttpWebRequest> Zkonstruován z SPN odešle instance <xref:System.Uri>. Ve výchozím nastavení <xref:System.Net.Mail.SmtpClient> instance odešle název SPN vytvářejí na základě názvu hostitele serveru SMTP, e-mailu.  
  
 Pro vlastní ověřování, můžete použít klientské aplikace <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> nebo <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> metody v <xref:System.Net.HttpWebRequest> třídu, která povolí načítání <xref:System.Net.TransportContext> a CBT pomocí <xref:System.Net.TransportContext.GetChannelBinding%2A> metoda.  
  
 Hlavní název služby pro integrované ověřování systému Windows poslal <xref:System.Net.HttpWebRequest> instanci dané služby je možné přepsat nastavení <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> vlastnost.  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A> Vlastnost lze nastavit vlastní název SPN pro integrované ověřování systému Windows pro připojení k SMTP.  
  
## <a name="extended-protection-for-server-applications"></a>Rozšířená ochrana pro serverové aplikace  
 <xref:System.Net.HttpListener> automaticky poskytuje mechanismy ověřování vazby služeb, při provádění ověřování protokolu HTTP.  
  
 Nejbezpečnější scénář je umožnit Rozšířená ochrana pro předpony HTTPS://. V takovém případě nastavte <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> k <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> s <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> nastavena na <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> nebo <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, a <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> nastavena na <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> hodnotu <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> vloží <xref:System.Net.HttpListener> v režimu částečně odolný při <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> odpovídá plně zesílený režim.  
  
 V této konfiguraci při požadavku na server prostřednictvím vnější zabezpečený kanál, je vnější kanál dotazován pro vytváření vazby kanálu. Tuto vazbu kanálu je předán ověřování volání rozhraní SSPI, které ověření, které vazby kanál v objektu blob shod ověřování. Existují tři možné případy:  
  
1.  Základní operační systém serveru nepodporuje rozšířené ochrany. Aplikace nebude vystaven požadavek a odpověď neoprávněným (401) bude vrácen do klienta. Zprávu se zaznamená do <xref:System.Net.HttpListener> zdroj trasování zadání příčinu selhání.  
  
2.  Volání rozhraní SSPI selže označující, že buď klienta Zadaná vazba kanálu, který neodpovídá očekávané hodnotě načíst z vnějšího kanálu nebo klientovi se nepodařilo zadat vazbu kanálu při konfiguraci zásady rozšířené ochrany na serveru pro <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>. V obou případech aplikace nebude vystaven požadavek a odpověď neoprávněným (401) bude vrácen do klienta. Zprávu se zaznamená do <xref:System.Net.HttpListener> zdroj trasování zadání příčinu selhání.  
  
3.  Klient určuje vazby správný kanál nebo se může připojit bez zadání vazby kanálů od zásady rozšířené ochrany na serveru je nakonfigurovaný s <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> požadavku je vrácen do aplikace pro zpracování. Automaticky je provedena žádná kontrola název služby. Zvolit aplikaci k provedení vlastní službu název ověření pomocí <xref:System.Net.HttpListenerRequest.ServiceName%2A> vlastnost, ale za těchto okolností je redundantní.  
  
 Pokud aplikace provede vlastní volání rozhraní SSPI k provedení ověřování založeného na objekty BLOB a zpět předán v textu požadavku HTTP a chce podporovat vytváření vazby kanálu, musí se načíst očekávaný kanál vazby z vnějšího zabezpečený kanál pomocí <xref:System.Net.HttpListener> Chcete-li předat nativní Win32 [Funkce AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) funkce. Chcete-li to provést, použijte <xref:System.Net.HttpListenerRequest.TransportContext%2A> vlastnost a volání <xref:System.Net.TransportContext.GetChannelBinding%2A> metoda pro načtení CBT. Jsou podporované jenom vazby koncového bodu. Pokud se něco jiných <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> je zadán, <xref:System.NotSupportedException> bude vyvolána. Pokud příslušný operační systém podporuje vytváření vazby kanálu, <xref:System.Net.TransportContext.GetChannelBinding%2A> metoda vrátí <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> zabalení ukazatel na kanál vazby vhodný pro předávání do [Funkce AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) – funkce jako pvBuffer členů struktury SecBuffer předaná `pInput` parametr. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> Vlastnost obsahuje délka v bajtech, vytváření vazby kanálu. Pokud příslušný operační systém nepodporuje vazby kanálů, funkce vrátí `null`.  
  
 Další možností možné je povolit Rozšířená ochrana pro HTTP:// předpon, pokud se nepoužívají proxy. V takovém případě nastavte <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> k <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> s <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> nastavena na <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> nebo <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, a <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> nastavena na <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> hodnotu <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> vloží <xref:System.Net.HttpListener> v režimu částečně odolný při <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> odpovídá plně zesílený režim.  
  
 Výchozí seznam názvů povolené služby se vytvoří podle předpony, které byly zaregistrovány <xref:System.Net.HttpListener>. Tento výchozí seznam můžete zkoumány prostřednictvím <xref:System.Net.HttpListener.DefaultServiceNames%2A> vlastnost. Pokud tento seznam není vyčerpávající, aplikace můžete zadat název kolekce vlastní služba v konstruktoru pro <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> třída, která se použije místo seznamu název výchozí služby.  
  
 V této konfiguraci po žádosti se k serveru bez vnější zabezpečený kanál ověřování pokračuje normálně bez kontrola s vazbou na kanál. Je-li ověření úspěšně, je dotazován kontext pro název služby, že klient poskytli a ověřený proti seznamu názvů přijatelné služby. Existují čtyři možné výsledky:  
  
1.  Základní operační systém serveru nepodporuje rozšířené ochrany. Aplikace nebude vystaven požadavek a odpověď neoprávněným (401) bude vrácen do klienta. Zprávu se zaznamená do <xref:System.Net.HttpListener> zdroj trasování zadání příčinu selhání.  
  
2.  Klienta příslušný operační systém nepodporuje rozšířené ochrany. V <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> konfigurace, bude úspěšné pokusy o ověření a požadavek se vrátí aplikaci. V <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> konfigurace, se nezdaří pokus o ověření. Aplikace nebude vystaven požadavek a odpověď neoprávněným (401) bude vrácen do klienta. Zprávu se zaznamená do <xref:System.Net.HttpListener> zdroj trasování zadání příčinu selhání.  
  
3.  Základní operační systém klienta podporuje rozšířené ochrany, ale aplikace nezadali vazby služby. Aplikace nebude vystaven požadavek a odpověď neoprávněným (401) bude vrácen do klienta. Zprávu se zaznamená do <xref:System.Net.HttpListener> zdroj trasování zadání příčinu selhání.  
  
4.  Klient zadat vazby služby. Seznam povolených služby vazeb se porovná s vazby služby. Pokud odpovídá, požadavek se vrátí do aplikace. Jinak požadavek nebude vystaven aplikace a odpověď neoprávněným (401) bude automaticky vrácen do klienta. Zprávu se zaznamená do <xref:System.Net.HttpListener> zdroj trasování zadání příčinu selhání.  
  
 Pokud tento jednoduchý přístup pomocí seznamu povolených názvů přijatelné služby není dostatečné, aplikace, může poskytnout vlastní ověření název služby pomocí dotazu <xref:System.Net.HttpListenerRequest.ServiceName%2A> vlastnost. V 1 a 2 výše, vlastnost vrátí `null`. V případě, že 3, vrátí prázdný řetězec. V případě, že 4, název služby zadaný klientem, bude vrácen.  
  
 Tyto funkce rozšířené ochrany lze také serverovými aplikacemi pro ověřování s jinými typy požadavků a Důvěryhodné servery proxy se používají.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Authentication.ExtendedProtection>  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>
