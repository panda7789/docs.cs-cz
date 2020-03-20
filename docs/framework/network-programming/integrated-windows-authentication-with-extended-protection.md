---
title: Integrované ověřování systému Windows s rozšířenou ochranou
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
ms.openlocfilehash: c4afc008f600c9be0040f8d7623f5e20623dfd7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74444241"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Integrované ověřování systému Windows s rozšířenou ochranou
Byla provedena vylepšení, která ovlivňují způsob, <xref:System.Net.HttpWebRequest>jakým <xref:System.Net.HttpListener> <xref:System.Net.Mail.SmtpClient>je <xref:System.Net.Security.SslStream>integrované ověřování systému Windows zpracováváno třídami , , , <xref:System.Net.Security.NegotiateStream>, a souvisejícími v oborech názvů <xref:System.Net> a souvisejících s nimi. Byla přidána podpora pro rozšířenou ochranu pro zvýšení zabezpečení.  
  
 Tyto změny mohou ovlivnit aplikace, které používají tyto třídy k provádění webových požadavků a přijímání odpovědí tam, kde se používá integrované ověřování systému Windows. Tato změna může mít vliv také na webové servery a klientské aplikace, které jsou nakonfigurovány pro použití integrovaného ověřování systému Windows.  
  
 Tyto změny mohou také ovlivnit aplikace, které používají tyto třídy k provádění jiných typů požadavků a přijímat odpovědi, kde se používá integrované ověřování systému Windows.  
  
 Změny podpory rozšířené ochrany jsou k dispozici pouze pro aplikace v systémech Windows 7 a Windows Server 2008 R2. Funkce rozšířené ochrany nejsou k dispozici ve starších verzích systému Windows.  
  
## <a name="overview"></a>Přehled  
 Návrh integrovaného ověřování systému Windows umožňuje, aby některé odpovědi na výzvu pověření byly univerzální, což znamená, že mohou být znovu použity nebo předány. Odpovědi na výzvy by měly být vytvořeny minimálně s konkrétními cílovými informacemi a pokud možno také s některými informacemi specifickými pro kanál. Služby pak mohou poskytovat rozšířenou ochranu, aby bylo zajištěno, že odpovědi na výzvu pověření obsahují informace specifické pro službu, jako je například hlavní název služby (SPN). S těmito informacemi ve výměně přihlašovacích údajů jsou služby schopny lépe chránit před škodlivým použitím odpovědí na výzvu pověření, které mohly být nesprávně použity.  
  
 Návrh rozšířené ochrany je vylepšení ověřovacích protokolů určených ke zmírnění útoků přenosu ověřování. To se točí kolem konceptu kanálu a informace o vazbě služby.  
  
 Celkové cíle jsou následující:  
  
1. Pokud je klient aktualizován na podporu rozšířené ochrany, aplikace by měly poskytnout informace o vazbě kanálu a služby všem podporovaným ověřovacím protokolům. Informace o vazbě kanálu lze poskytnout pouze v případě, že existuje kanál (TLS), na který se má vytvořit vazba. Informace o vazbě služby by měly být vždy poskytnuty.  
  
2. Aktualizované servery, které jsou správně nakonfigurovány, mohou ověřit informace o vazbě kanálu a služby, pokud jsou k dispozici v tokenu ověřování klienta, a odmítnout pokus o ověření, pokud se vazby kanálu neshodují. V závislosti na scénáři nasazení mohou servery ověřit vazbu kanálu, vazbu služby nebo obojí.  
  
3. Aktualizované servery mají možnost přijímat nebo zamítat požadavky klientů nižší úrovně, které neobsahují informace o vazbě kanálu založené na zásadách.  
  
 Informace používané rozšířenou ochranou se skládají z jedné nebo obou následujících částí:  
  
1. Token vazby kanálu nebo CBT.  
  
2. Informace o vazbě služby ve formě hlavního názvu služby nebo hlavního názvu služby.  
  
 Informace o vazbě služby je známkou záměru klienta ověřit konkrétní koncový bod služby. Je komunikován z klienta na server s následujícími vlastnostmi:  
  
- Hodnota spn musí být k dispozici serveru provádějícímu ověřování klienta ve formě prostého textu.  
  
- Hodnota hlavního spn je veřejná.  
  
- Hlavní aktualizace služeb při obslužné hodnotě musí být při přenosu kryptograficky chráněna tak, aby útok prostředníkem nemohl vložit, odebrat nebo změnit jeho hodnotu.  
  
 CBT je vlastnost vnější zabezpečený kanál (například TLS) slouží k vazbě (vázat) ji konverzační konverzace přes vnitřní, klient ověřený kanál. CBT musí mít následující vlastnosti (také definované IETF RFC 5056):  
  
- Pokud existuje vnější kanál, hodnota CBT musí být vlastnost identifikující vnější kanál nebo koncový bod serveru, nezávisle přijatá klientem i serverem na straně konverzace.  
  
- Hodnota CBT odeslané klientem nesmí být něco, co útočník může ovlivnit.  
  
- Nejsou žádné záruky týkající se utajení hodnoty CBT. To však neznamená, že hodnota vazby služby, jakož i informace o vazbě kanálu mohou být vždy zkontrolovány jiným, ale server provádějící ověřování, protože protokol nesoucí CBT může být šifrování.  
  
- CBT musí být kryptograficky integrity chráněné při přenosu tak, aby útočník nemůže vložit, odebrat nebo změnit jeho hodnotu.  
  
 Vazba kanálu je dosaženo klientem přenosu SPN a CBT na server způsobem, který je odolný proti manipulaci. Server ověří informace o vazbě kanálu v souladu se svými zásadami a odmítne pokusy o ověření, pro které se nedomnívá, že byl zamýšleným cílem. Tímto způsobem se dva kanály stanou kryptograficky svázané dohromady.  
  
 Chcete-li zachovat kompatibilitu s existujícími klienty a aplikacemi, může být server nakonfigurován tak, aby umožňoval pokusy o ověření klienty, kteří dosud nepodporují rozšířenou ochranu. To se označuje jako "částečně tvrzené" konfigurace, na rozdíl od "plně tvrzené" konfigurace.  
  
 Více součástí v <xref:System.Net> <xref:System.Net.Security> oborech názvů a provádění integrovaného ověřování systému Windows jménem volající aplikace. Tato část popisuje změny System.Net součástí pro přidání rozšířené ochrany při používání integrovaného ověřování systému Windows.  
  
 Rozšířená ochrana je v současné době podporována v systému Windows 7. Mechanismus je k dispozici tak aplikace můžete určit, zda operační systém podporuje rozšířenou ochranu.  
  
## <a name="changes-to-support-extended-protection"></a>Změny rozšířené ochrany podpory  
 Proces ověřování používaný s integrovaným ověřováním systému Windows v závislosti na použitém ověřovacím protokolu často zahrnuje výzvu vydanou cílovým počítačem a odeslanou zpět do klientského počítače. Rozšířená ochrana přidává do tohoto procesu ověřování nové funkce.  
  
 Obor <xref:System.Security.Authentication.ExtendedProtection> názvů poskytuje podporu pro ověřování pomocí rozšířené ochrany aplikací. Třída <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> v tomto oboru názvů představuje vazbu kanálu. Třída <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> v tomto oboru názvů představuje rozšířené zásady ochrany používané serverem k ověření příchozích klientských připojení. Ostatní členové třídy se používají s rozšířenou ochranou.  
  
 Pro serverové aplikace tyto třídy zahrnují následující:  
  
 A, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> který má následující prvky:  
  
- Vlastnost, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> která označuje, zda operační systém podporuje integrované ověřování systému Windows s rozšířenou ochranou.  
  
- Hodnota, <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> která označuje, kdy by měly být vynuceny zásady rozšířené ochrany.  
  
- Hodnota, <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> která označuje scénář nasazení. To má vliv na kontrolu rozšířené ochrany.  
  
- Volitelné, <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> který obsahuje vlastní seznam spn, který se používá k porovnání s hlavní název služby poskytované klientem jako zamýšlený cíl ověřování.  
  
- Volitelné, <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> který obsahuje vlastní kanál vazby pro ověření. Tento scénář není běžným případem  
  
 Obor <xref:System.Security.Authentication.ExtendedProtection.Configuration> názvů poskytuje podporu pro konfiguraci ověřování pomocí rozšířené ochrany aplikací.  
  
 Byla provedena řada změn funkcí, které podporují <xref:System.Net> rozšířenou ochranu v existujícím oboru názvů. Mezi tyto změny patří následující:  
  
- Nová <xref:System.Net.TransportContext> třída přidána <xref:System.Net> do oboru názvů, který představuje kontext přenosu.  
  
- Nové <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> <xref:System.Net.HttpWebRequest.GetRequestStream%2A> a přetížení <xref:System.Net.HttpWebRequest> metody ve třídě, <xref:System.Net.TransportContext> které umožňují načítání pro podporu rozšířené ochrany pro klientské aplikace.  
  
- Dodatky <xref:System.Net.HttpListener> k <xref:System.Net.HttpListenerRequest> a třídy pro podporu serverových aplikací.  
  
 Byla provedena změna funkce pro podporu rozšířené ochrany klientských <xref:System.Net.Mail> aplikací SMTP v existujícím oboru názvů:  
  
- Vlastnost <xref:System.Net.Mail.SmtpClient.TargetName%2A> ve <xref:System.Net.Mail.SmtpClient> třídě, která představuje název SPN pro ověřování při použití rozšířené ochrany pro klientské aplikace SMTP.  
  
 Byla provedena řada změn funkcí, které podporují <xref:System.Net.Security> rozšířenou ochranu v existujícím oboru názvů. Mezi tyto změny patří následující:  
  
- Nové <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> a přetížení <xref:System.Net.Security.NegotiateStream> metody ve třídě, které umožňují předávání CBT pro podporu rozšířené ochrany pro klientské aplikace.  
  
- Nové <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> a přetížení <xref:System.Net.Security.NegotiateStream> metody ve třídě, které umožňují předávání <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> pro podporu rozšířené ochrany pro serverové aplikace.  
  
- Nová <xref:System.Net.Security.SslStream.TransportContext%2A> vlastnost ve <xref:System.Net.Security.SslStream> třídě pro podporu rozšířené ochrany klientských a serverových aplikací.  
  
 Byla <xref:System.Net.Configuration.SmtpNetworkElement> přidána vlastnost pro podporu konfigurace rozšířené ochrany klientů <xref:System.Net.Security> SMTP v oboru názvů.  
  
## <a name="extended-protection-for-client-applications"></a>Rozšířená ochrana klientských aplikací  
 Rozšířená podpora ochrany pro většinu klientských aplikací probíhá automaticky. <xref:System.Net.HttpWebRequest> Třídy <xref:System.Net.Mail.SmtpClient> a podporují rozšířenou ochranu vždy, když základní verze systému Windows podporuje rozšířenou ochranu. Instance <xref:System.Net.HttpWebRequest> odešle hlavní název služby <xref:System.Uri>vytvořený z . Ve výchozím <xref:System.Net.Mail.SmtpClient> nastavení instance odešle název SPN vytvořený z názvu hostitele poštovního serveru SMTP.  
  
 Pro vlastní ověřování mohou klientské <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> aplikace <xref:System.Net.HttpWebRequest> použít metody <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> or <xref:System.Net.TransportContext> ve třídě, které <xref:System.Net.TransportContext.GetChannelBinding%2A> umožňují načítání a CBT pomocí metody.  
  
 Název SPN, který se má <xref:System.Net.HttpWebRequest> použít pro integrované ověřování systému Windows <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> odeslané instancí dané službě, lze přemluvit nastavením vlastnosti.  
  
 Vlastnost <xref:System.Net.Mail.SmtpClient.TargetName%2A> lze nastavit vlastní hlavní název služby pro použití pro integrované ověřování systému Windows pro připojení SMTP.  
  
## <a name="extended-protection-for-server-applications"></a>Rozšířená ochrana serverových aplikací  
 <xref:System.Net.HttpListener>automaticky poskytuje mechanismy pro ověřování vazeb služby při ověřování HTTP.  
  
 Nejbezpečnější scénář je povolit rozšířenou ochranu pro HTTPS:// předpony. V tomto případě <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> nastavte <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> na <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> s <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>nastavenou <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> na nebo <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Net.HttpListener> , a <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> nastavte hodnotu A vloží v částečně tvrzené režimu, zatímco odpovídá plně tvrzené režimu.  
  
 V této konfiguraci při požadavku na server prostřednictvím vnějšího zabezpečeného kanálu je vnější kanál dotazován na vazbu kanálu. Tato vazba kanálu je předána volání ověřování SSPI, která ověřují, že vazba kanálu v objektu blob ověřování odpovídá. Existují tři možné výsledky:  
  
1. Základní operační systém serveru nepodporuje rozšířenou ochranu. Požadavek nebude vystaven aplikaci a neoprávněná odpověď (401) bude vrácena klientovi. Zpráva bude zaznamenána do <xref:System.Net.HttpListener> zdroje trasování určující důvod selhání.  
  
2. Volání SSPI se nezdaří označující, že klient zadal vazbu kanálu, která neodpovídá očekávané hodnotě načtené z vnějšího kanálu, <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>nebo klientnepodařilo zadat vazbu kanálu, když byla nakonfigurována rozšířená zásada ochrany na serveru . V obou případech nebude požadavek vystaven aplikaci a klientovi bude vrácena neoprávněná odpověď (401). Zpráva bude zaznamenána do <xref:System.Net.HttpListener> zdroje trasování určující důvod selhání.  
  
3. Klient určuje správnou vazbu kanálu nebo je povoleno připojení bez zadání vazby kanálu, protože <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> rozšířené zásady ochrany na serveru jsou nakonfigurovány s Požadavek je vrácen do aplikace pro zpracování. Kontrola názvu služby se neprovádí automaticky. Aplikace se může rozhodnout provést vlastní <xref:System.Net.HttpListenerRequest.ServiceName%2A> ověření názvu služby pomocí vlastnosti, ale za těchto okolností je redundantní.  
  
 Pokud aplikace provádí vlastní volání SSPI k provedení ověřování na základě objektů BLOB předaných tam a zpět v rámci těla požadavku HTTP <xref:System.Net.HttpListener> a chce podporovat vazbu kanálu, musí načíst očekávanou vazbu kanálu z vnějšího zabezpečeného kanálu pomocí k jeho předání nativní funkci [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) aplikace Win32. Chcete-li to <xref:System.Net.HttpListenerRequest.TransportContext%2A> provést, <xref:System.Net.TransportContext.GetChannelBinding%2A> použijte vlastnost a metodu volání k načtení CBT. Podporovány jsou pouze vazby koncového bodu. Pokud je <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> zadáno <xref:System.NotSupportedException> něco jiného, bude vyvolána. Pokud základní operační systém podporuje <xref:System.Net.TransportContext.GetChannelBinding%2A> vazbu kanálu, <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> metoda vrátí obtékání ukazatel na vazbu kanálu vhodné pro předávání [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) funkce jako pvBuffer člen SecBuffer struktury předané v parametru. `pInput` Vlastnost <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> obsahuje délku v bajtů vazby kanálu. Pokud základní operační systém nepodporuje vazby kanálu, `null`funkce vrátí .  
  
 Dalším možným scénářem je povolení rozšířené ochrany pro HTTP:// předpony, pokud se nepoužívají proxy servery. V tomto případě <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> nastavte <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> na <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> s <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>nastavenou <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> na nebo <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Net.HttpListener> , a <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> nastavte hodnotu A vloží v částečně tvrzené režimu, zatímco odpovídá plně tvrzené režimu.  
  
 Výchozí seznam povolených názvů služeb je vytvořen na základě předpon, které byly zaregistrovány u <xref:System.Net.HttpListener>. Tento výchozí seznam lze <xref:System.Net.HttpListener.DefaultServiceNames%2A> zkontrolovány prostřednictvím vlastnosti. Pokud tento seznam není vyčerpávající, aplikace můžete zadat vlastní kolekce názvů <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> služeb v konstruktoru pro třídu, která bude použita namísto výchozího seznamu názvů služeb.  
  
 V této konfiguraci při požadavku na server bez vnější ho sazený kanál ověřování probíhá normálně bez kontroly vazby kanálu. Pokud je ověření úspěšné, kontext je dotazován na název služby, který klient poskytl a ověřil podle seznamu přijatelných názvů služeb. Existují čtyři možné výsledky:  
  
1. Základní operační systém serveru nepodporuje rozšířenou ochranu. Požadavek nebude vystaven aplikaci a neoprávněná odpověď (401) bude vrácena klientovi. Zpráva bude zaznamenána do <xref:System.Net.HttpListener> zdroje trasování určující důvod selhání.  
  
2. Základní operační systém klienta nepodporuje rozšířenou ochranu. V <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> konfiguraci bude pokus o ověření úspěšný a požadavek bude vrácen do aplikace. V <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> konfiguraci se pokus o ověření nezdaří. Požadavek nebude vystaven aplikaci a neoprávněná odpověď (401) bude vrácena klientovi. Zpráva bude zaznamenána do <xref:System.Net.HttpListener> zdroje trasování určující důvod selhání.  
  
3. Základní operační systém klienta podporuje rozšířenou ochranu, ale aplikace neurčila vazbu služby. Požadavek nebude vystaven aplikaci a neoprávněná odpověď (401) bude vrácena klientovi. Zpráva bude zaznamenána do <xref:System.Net.HttpListener> zdroje trasování určující důvod selhání.  
  
4. Klient zadal vazbu služby. Vazba služby je porovnána se seznamem povolených vazeb služby. Pokud odpovídá, požadavek je vrácena do aplikace. V opačném případě nebude požadavek vystaven aplikaci a neoprávněná odpověď (401) bude automaticky vrácena klientovi. Zpráva bude zaznamenána do <xref:System.Net.HttpListener> zdroje trasování určující důvod selhání.  
  
 Pokud tento jednoduchý přístup pomocí seznamu povolených názvů služeb je nedostatečná, aplikace může <xref:System.Net.HttpListenerRequest.ServiceName%2A> poskytnout vlastní název služby ověření dotazem na vlastnost. V případech 1 a 2 se `null`ubytování vrátí . V případě 3 vrátí prázdný řetězec. V případě 4 bude vrácen název služby určený klientem.  
  
 Tyto rozšířené funkce ochrany mohou být také použity serverovými aplikacemi pro ověřování s jinými typy požadavků a při použití důvěryhodných proxy serverů.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Security.Authentication.ExtendedProtection>
- <xref:System.Security.Authentication.ExtendedProtection.Configuration>
