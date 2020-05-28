---
title: Integrované ověřování systému Windows s rozšířenou ochranou
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
ms.openlocfilehash: d69471f4be0f102381dee4fc5037e8f8b0c625c3
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144848"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Integrované ověřování systému Windows s rozšířenou ochranou
Byla provedena vylepšení, která mají vliv na to, jak se integrované ověřování systému Windows zpracovává pomocí <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpListener> tříd,,, <xref:System.Net.Mail.SmtpClient> <xref:System.Net.Security.SslStream> , <xref:System.Net.Security.NegotiateStream> a souvisejících tříd v <xref:System.Net> souvisejících oborech názvů a. Byla přidána podpora pro rozšířenou ochranu za účelem vylepšení zabezpečení.  
  
 Tyto změny mohou ovlivnit aplikace, které používají tyto třídy k vytváření webových požadavků a přijímání odpovědí, kde se používá integrované ověřování systému Windows. Tato změna může mít dopad i na webové servery a klientské aplikace, které jsou nakonfigurované tak, aby používaly integrované ověřování systému Windows.  
  
 Tyto změny mohou také ovlivnit aplikace, které používají tyto třídy k vytváření dalších typů požadavků a přijímání odpovědí, kde se používá integrované ověřování systému Windows.  
  
 Změny pro podporu rozšířené ochrany jsou k dispozici pouze pro aplikace v systémech Windows 7 a Windows Server 2008 R2. Funkce rozšířené ochrany nejsou k dispozici v dřívějších verzích systému Windows.  
  
## <a name="overview"></a>Přehled  
 Při návrhu integrovaného ověřování systému Windows je možné, že některé reakce na výzvy přihlašovacích údajů budou univerzální, což znamená, že je můžete znovu použít nebo přeposlání. Odpovědi na výzvy by se měly vytvořit minimálně s konkrétními informacemi o cíli a přednostně i s některými konkrétními informacemi o kanálu. Služby pak můžou poskytovat rozšířenou ochranu a zajistit, aby odpovědi na výzvy přihlašovacích údajů obsahovaly informace specifické pro službu, jako je hlavní název služby (SPN). Díky těmto informacím v výměnách přihlašovacích údajů můžou služby lépe chránit před škodlivým použitím odpovědí na výzvy k pověření, které by mohly být nesprávně využité.  
  
 Návrh rozšířené ochrany je vylepšení ověřovacích protokolů navržených pro zmírnění útoků Relay s ověřováním. Roztéká se kolem konceptu informací o vazbě kanálu a služby.  
  
 Celkovými cíli jsou tyto:  
  
1. Pokud je klient aktualizován na podporu rozšířené ochrany, aplikace by měly poskytnout vazbu kanálu a informace o vazbě služby na všechny podporované ověřovací protokoly. Informace o vazbě kanálu můžou být dodány jenom v případě, že existuje kanál (TLS), ke kterému se má vytvořit vazba. Informace o vazbě služby by měly být vždy dodány.  
  
2. Aktualizované servery, které jsou správně nakonfigurovány, mohou ověřit informace o vazbě kanálu a služby, pokud jsou k dispozici v tokenu ověřování klienta, a zamítnout pokus o ověření, pokud se vazby kanálu neshodují. V závislosti na scénáři nasazení mohou servery ověřit vazbu kanálu, vazbu služby nebo obojí.  
  
3. Aktualizované servery mají možnost přijímat nebo odmítat požadavky klientů nižší úrovně, které neobsahují informace o vazbě kanálu na základě zásad.  
  
 Informace používané rozšířenou ochranou se skládají z jedné nebo obou následujících dvou částí:  
  
1. Token vazby kanálu nebo CBT.  
  
2. Informace o vazbě služby ve formě hlavního názvu služby nebo hlavního názvu služby (SPN).  
  
 Informace o vazbě služby jsou označením záměru klienta ověřit u konkrétního koncového bodu služby. Je přenášena z klienta na server s následujícími vlastnostmi:  
  
- Hodnota hlavního názvu služby (SPN) musí být k dispozici serveru, který provádí ověřování klienta ve formě prostého textu.  
  
- Hodnota hlavního názvu služby (SPN) je veřejná.  
  
- Hlavní název služby (SPN) musí být kryptograficky chráněný během přenosu, takže útok prostředníkem nemůže vkládat, odebírat ani upravovat jeho hodnotu.  
  
 CBT je vlastnost vnějšího zabezpečeného kanálu (například TLS), která se používá k propojení (vazbu) s konverzací přes vnitřní kanál ověřený klientem. CBT musí mít následující vlastnosti (definované v IETF RFC 5056):  
  
- Pokud existuje vnější kanál, hodnota CBT musí být vlastnost identifikující buď vnější kanál, nebo koncový bod serveru, nezávisle na straně klienta i serveru konverzace.  
  
- Hodnota CBT odesílaných klientem nesmí být taková, že by útočník mohl ovlivnit.  
  
- Nejsou k dispozici žádné záruky týkající se tajnosti hodnoty CBT. To však neznamená, že hodnota vazby služby a informace o vazbě kanálu mohou být vždy zkontrolovány jiným, ale serverem provádějícím ověřování, protože protokol, který CBT zakládá, může šifrovat.  
  
- CBT musí být kryptograficky integritou chráněny během přenosu tak, že Útočník nemůže vložit, odebrat ani změnit jeho hodnotu.  
  
 Vazba kanálu je zajištěna klientem, který přenáší hlavní název služby (SPN) a CBT na server tamperproof. Server ověřuje informace o vazbě kanálu v souladu se svými zásadami a odmítá pokusy o ověření, pro které se nepovažuje za zamýšleného cíle. Tímto způsobem se tyto dva kanály stanou kryptograficky propojeně.  
  
 Aby se zachovala kompatibilita se stávajícími klienty a aplikacemi, může být server nakonfigurovaný tak, aby umožňoval ověřování pokusů klientů, kteří ještě nepodporují rozšířenou ochranu. To se označuje jako "částečně posílená" konfigurace na rozdíl od "plně zpřísněné" konfigurace.  
  
 Více komponent v <xref:System.Net> <xref:System.Net.Security> oborech názvů a provádí integrované ověřování systému Windows jménem volající aplikace. Tato část popisuje změny součástí System.Net pro přidání rozšířené ochrany při použití integrovaného ověřování systému Windows.  
  
 Ve Windows 7 se aktuálně podporuje Rozšířená ochrana. K dispozici je mechanismus, takže aplikace může určit, jestli operační systém podporuje rozšířenou ochranu.  
  
## <a name="changes-to-support-extended-protection"></a>Změny pro podporu rozšířené ochrany  
 Proces ověřování použitý s integrovaným ověřováním systému Windows, v závislosti na použitém protokolu ověřování, často zahrnuje výzvu vydanou cílovým počítačem a odesílá se zpátky do klientského počítače. Rozšířená ochrana přidává do tohoto procesu ověřování nové funkce.  
  
 <xref:System.Security.Authentication.ExtendedProtection>Obor názvů poskytuje podporu pro ověřování pomocí rozšířené ochrany pro aplikace. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding>Třída v tomto oboru názvů představuje vazbu kanálu. <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>Třída v tomto oboru názvů představuje rozšířené zásady ochrany používané serverem k ověření příchozích připojení klientů. Jiní členové třídy se používají s rozšířenou ochranou.  
  
 Pro serverové aplikace tyto třídy zahrnují následující:  
  
 A <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> který má následující prvky:  
  
- <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A>Vlastnost, která určuje, zda operační systém podporuje integrované ověřování systému Windows s rozšířenou ochranou.  
  
- <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>Hodnota, která indikuje, kdy se má vyhovět zásada rozšířené ochrany  
  
- <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario>Hodnota, která označuje scénář nasazení. To ovlivňuje způsob, jakým je zaškrtnutá Rozšířená ochrana.  
  
- Volitelné <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> , který obsahuje vlastní seznam SPN, který se používá k porovnání s hlavním názvem služby, který poskytuje klient jako zamýšlený cíl ověřování.  
  
- Volitelný <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> , který obsahuje vazbu vlastního kanálu, který se má použít k ověření. Tento scénář není běžným případem.  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>Obor názvů poskytuje podporu pro konfiguraci ověřování pomocí rozšířené ochrany pro aplikace.  
  
 V existujícím oboru názvů byla provedena řada změn funkcí pro podporu rozšířené ochrany <xref:System.Net> . Mezi tyto změny patří následující:  
  
- Nová <xref:System.Net.TransportContext> Třída přidaná do <xref:System.Net> oboru názvů, který představuje přenosový kontext.  
  
- Nové <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> a <xref:System.Net.HttpWebRequest.GetRequestStream%2A> metody přetížení <xref:System.Net.HttpWebRequest> třídy, které umožňují načíst <xref:System.Net.TransportContext> pro podporu rozšířené ochrany pro klientské aplikace.  
  
- Přidání do <xref:System.Net.HttpListener> tříd a <xref:System.Net.HttpListenerRequest> pro podporu serverových aplikací.  
  
 Byla provedena změna funkce pro podporu rozšířené ochrany pro klientské aplikace SMTP v existujícím <xref:System.Net.Mail> oboru názvů:  
  
- <xref:System.Net.Mail.SmtpClient.TargetName%2A>Vlastnost ve <xref:System.Net.Mail.SmtpClient> třídě, která představuje hlavní název služby (SPN), která se má použít pro ověřování při použití rozšířené ochrany pro klientské aplikace SMTP.  
  
 V existujícím oboru názvů byla provedena řada změn funkcí pro podporu rozšířené ochrany <xref:System.Net.Security> . Mezi tyto změny patří následující:  
  
- Nové <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> a <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> přetížené metody <xref:System.Net.Security.NegotiateStream> třídy, které umožňují předávání CBT k podpoře rozšířené ochrany pro klientské aplikace.  
  
- Nové <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> a <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> metody přetížení <xref:System.Net.Security.NegotiateStream> třídy, které umožňují předávání <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> k podpoře rozšířené ochrany pro serverové aplikace.  
  
- Nová <xref:System.Net.Security.SslStream.TransportContext%2A> vlastnost ve <xref:System.Net.Security.SslStream> třídě pro podporu rozšířené ochrany pro klientské a serverové aplikace.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement>Přidala se vlastnost, která podporuje konfiguraci rozšířené ochrany pro klienty SMTP v <xref:System.Net.Security> oboru názvů.  
  
## <a name="extended-protection-for-client-applications"></a>Rozšířená ochrana pro klientské aplikace  
 Rozšířená podpora ochrany většiny klientských aplikací probíhá automaticky. <xref:System.Net.HttpWebRequest>Třídy a <xref:System.Net.Mail.SmtpClient> podporují rozšířenou ochranu vždy, když příslušná verze systému Windows podporuje rozšířenou ochranu. <xref:System.Net.HttpWebRequest>Instance odesílá hlavní název služby (SPN) sestavený z <xref:System.Uri> . Ve výchozím nastavení <xref:System.Net.Mail.SmtpClient> instance odesílá hlavní název služby (SPN) vytvořenou z názvu hostitele poštovního serveru SMTP.  
  
 Pro vlastní ověřování mohou klientské aplikace používat <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> metody nebo ve <xref:System.Net.HttpWebRequest> třídě, které umožňují načíst <xref:System.Net.TransportContext> a CBT pomocí <xref:System.Net.TransportContext.GetChannelBinding%2A> metody.  
  
 Hlavní název služby (SPN), který se má použít pro integrované ověřování systému Windows odeslané <xref:System.Net.HttpWebRequest> instancí na danou službu, lze přepsat nastavením <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> Vlastnosti.  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A>Vlastnost se dá použít k nastavení vlastního hlavního názvu služby (SPN) pro použití integrovaného ověřování systému Windows pro připojení SMTP.  
  
## <a name="extended-protection-for-server-applications"></a>Rozšířená ochrana pro serverové aplikace  
 <xref:System.Net.HttpListener>automaticky poskytuje mechanismy pro ověřování vazeb služby při provádění ověřování protokolem HTTP.  
  
 Nejbezpečnějším scénářem je povolení rozšířené ochrany pro `HTTPS://` předpony. V takovém případě nastavte na <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> hodnotu s parametrem <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> nastaveným na <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> nebo a <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> nastavte na <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> hodnotu <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Net.HttpListener> v částečně zpřísněném režimu, zatímco odpovídá plně posílenému <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> režimu.  
  
 V této konfiguraci, když se na Server provede požadavek přes vnější zabezpečený kanál, se pro vazbu kanálu dotáže na vnější kanál. Tato vazba kanálu je předána ověřovacím voláním SSPI, která ověřují, zda vazba kanálu v objektu BLOB ověřování odpovídá. Existují tři možné výsledky:  
  
1. Základní operační systém serveru nepodporuje rozšířenou ochranu. Požadavek se nezveřejňuje aplikaci a klientovi se vrátí Neautorizovaná odpověď (401). Do zdroje trasování se zaznamená zpráva, která <xref:System.Net.HttpListener> Určuje důvod selhání.  
  
2. Volání rozhraní SSPI se nezdařilo, což znamená, že klient zadal vazbu kanálu, která neodpovídá očekávané hodnotě načtené z vnějšího kanálu, nebo když klient nedodá vazbu kanálu, pokud byla nakonfigurovaná rozšířená zásada ochrany na serveru <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> . V obou případech se požadavek do aplikace nezveřejňuje a klientovi se vrátí Neautorizovaná odpověď (401). Do zdroje trasování se zaznamená zpráva, která <xref:System.Net.HttpListener> Určuje důvod selhání.  
  
3. Klient Určuje správnou vazbu kanálu nebo se smí připojit bez zadání vazby kanálu, protože rozšířená zásada ochrany na serveru je nakonfigurovaná s požadavkem, který se <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> vrátí do aplikace ke zpracování. Neprovádí se automatická kontroly názvu služby. Aplikace se může rozhodnout provést vlastní ověření názvu služby pomocí <xref:System.Net.HttpListenerRequest.ServiceName%2A> vlastnosti, ale za těchto okolností je redundantní.  
  
 Pokud aplikace vytvoří vlastní volání rozhraní SSPI na základě předaných objektů BLOB a v rámci těla požadavku HTTP a přeje by podporovat vazby kanálu, musí načíst očekávanou vazbu kanálu z vnějšího zabezpečeného kanálu pomocí příkazu, aby ji bylo možné <xref:System.Net.HttpListener> předat nativní funkci [Funkce AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) Win32. K tomu použijte <xref:System.Net.HttpListenerRequest.TransportContext%2A> vlastnost a <xref:System.Net.TransportContext.GetChannelBinding%2A> metodu volání k načtení CBT. Jsou podporovány pouze vazby koncového bodu. Pokud <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> je zadáno cokoli jiného, <xref:System.NotSupportedException> bude vyvolána výjimka. Pokud podkladový operační systém podporuje vazbu kanálu, <xref:System.Net.TransportContext.GetChannelBinding%2A> Metoda vrátí <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> zabalení ukazatele na vazbu kanálu vhodnou pro předání do [Funkce AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) funkce jako člen pvBuffery struktury SecBuffer předané v `pInput` parametru. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A>Vlastnost obsahuje délku vazby kanálu v bajtech. Pokud podkladový operační systém nepodporuje vazby kanálu, funkce vrátí `null` .  
  
 Dalším možným scénářem je povolit rozšířenou ochranu pro `HTTP://` předpony, když se proxy servery nepoužívají. V takovém případě nastavte na <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> hodnotu s parametrem <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> nastaveným na <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> nebo a <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> nastavte na <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> hodnotu <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Net.HttpListener> v částečně zpřísněném režimu, zatímco odpovídá plně posílenému <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> režimu.  
  
 Na základě předpon, které jsou zaregistrované pomocí, se vytvoří výchozí seznam povolených názvů služeb <xref:System.Net.HttpListener> . Tento výchozí seznam lze prozkoumat pomocí <xref:System.Net.HttpListener.DefaultServiceNames%2A> Vlastnosti. Pokud tento seznam není vyčerpávající, může aplikace zadat vlastní kolekci názvů služby v konstruktoru pro <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> třídu, která bude použita namísto výchozího seznamu názvů služby.  
  
 Když se v této konfiguraci provede požadavek na server bez ověření vnějšího zabezpečeného kanálu, pokračuje normálně bez kontroly vazby kanálu. Pokud je ověření úspěšné, je kontext dotazován na název služby, který klient zadal a ověřil v seznamu přijatelných názvů služeb. Existují čtyři možné výsledky:  
  
1. Základní operační systém serveru nepodporuje rozšířenou ochranu. Požadavek se nezveřejňuje aplikaci a klientovi se vrátí Neautorizovaná odpověď (401). Do zdroje trasování se zaznamená zpráva, která <xref:System.Net.HttpListener> Určuje důvod selhání.  
  
2. Základní operační systém klienta nepodporuje rozšířenou ochranu. V <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> konfiguraci bude pokus o ověření úspěšný a požadavek bude vrácen do aplikace. V <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> konfiguraci se pokus o ověření nezdaří. Požadavek se nezveřejňuje aplikaci a klientovi se vrátí Neautorizovaná odpověď (401). Do zdroje trasování se zaznamená zpráva, která <xref:System.Net.HttpListener> Určuje důvod selhání.  
  
3. Základní operační systém klienta podporuje rozšířenou ochranu, ale aplikace neurčila vazbu služby. Požadavek se nezveřejňuje aplikaci a klientovi se vrátí Neautorizovaná odpověď (401). Do zdroje trasování se zaznamená zpráva, která <xref:System.Net.HttpListener> Určuje důvod selhání.  
  
4. Klient zadal vazbu služby. Vazba služby je porovnána se seznamem povolených vazeb služby. Pokud se shoduje, požadavek se vrátí do aplikace. V opačném případě se požadavek do aplikace nezveřejňuje a klientovi se automaticky vrátí Neautorizovaná odpověď (401). Do zdroje trasování se zaznamená zpráva, která <xref:System.Net.HttpListener> Určuje důvod selhání.  
  
 Pokud tento jednoduchý přístup pomocí seznamu povolených přijatelných názvů služeb nestačí, může aplikace poskytnout vlastní ověření názvu služby dotazem na <xref:System.Net.HttpListenerRequest.ServiceName%2A> vlastnost. V případech 1 a 2 výše bude vlastnost vracet `null` . V případě 3 se vrátí prázdný řetězec. V případě 4 se vrátí název služby zadaný klientem.  
  
 Tyto funkce rozšířené ochrany můžou používat serverové aplikace pro ověřování s jinými typy požadavků a při použití důvěryhodných proxy serverů.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Security.Authentication.ExtendedProtection>
- <xref:System.Security.Authentication.ExtendedProtection.Configuration>
