---
title: Osvědčené postupy TLS (Transport Layer Security) s .NET Framework
description: Popisuje osvědčené postupy pomocí protokolu TLS (Transport Layer Security) s .NET Framework.
ms.date: 10/22/2018
helpviewer_keywords:
- sending data, Internet security
- protocols, Internet security
- Network security
- network resources, Internet security
- receiving data, Internet security
- authentication [.NET Framework], Internet security
- Internet, security
- security [.NET Framework], Internet
- permissions [.NET Framework], Internet
ms.openlocfilehash: 87ca9b75d641035b268c6737822f198d1eea87e3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777507"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Osvědčené postupy TLS (Transport Layer Security) s .NET Framework

Protokol TLS (Transport Layer Security) je oborovým standardem, který pomáhá chránit soukromí informací přenášených přes Internet. [TLS 1,2](https://tools.ietf.org/html/rfc5246) je standard, který poskytuje vylepšení zabezpečení v předchozích verzích. Protokol TLS 1,2 bude nakonec nahrazen nejnovějším vydaným standardem [tls 1,3](https://tools.ietf.org/html/rfc8446) , který je rychlejší a má vyšší zabezpečení. Tento článek obsahuje doporučení pro zabezpečení .NET Frameworkch aplikací, které používají protokol TLS.

Aby se zajistilo, že .NET Framework aplikace zůstanou zabezpečené, **neměla by být** verze TLS pevně zakódované. .NET Framework aplikace by měly používat verzi TLS, kterou operační systém (OS) podporuje.

Tento dokument cílí na vývojáře, kteří jsou:

- Přímo pomocí <xref:System.Net> rozhraní API ( <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> například a <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- Přímo pomocí klientů a služeb WCF pomocí <xref:System.ServiceModel?displayProperty=nameWithType> oboru názvů.
- Použití webových a pracovních rolí [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) k hostování a spuštění vaší aplikace. Podívejte se na část [Azure Cloud Services](#azure-cloud-services) .

Doporučujeme:

- Cílová verze .NET Framework 4,7 nebo novější ve vašich aplikacích. Cílová .NET Framework 4.7.1 nebo novější verze v aplikacích WCF.
- Nezadávejte verzi TLS. Nakonfigurujte kód tak, aby se operační systém mohl rozhodnout o verzi TLS.
- Proveďte důkladné audit kódu, abyste ověřili, že neurčíte verzi TLS nebo SSL.

Když aplikace umožňuje operačnímu systému zvolit verzi TLS:

- Automaticky využívá nové protokoly přidané v budoucnu, jako je třeba TLS 1,3.
- Operační systém blokuje protokoly, které jsou zjištěny jako nezabezpečené.

Část [audit kódu a provádění změn kódu](#audit-your-code-and-make-code-changes) pokrývá auditování a aktualizaci kódu.

Tento článek vysvětluje, jak povolit nejsilnější zabezpečení, které je k dispozici pro verzi .NET Framework, na které vaše aplikace cílí a běží. Když aplikace explicitně nastaví protokol a verzi zabezpečení, výslovný se z jakékoli jiné alternativy a výslovný z .NET Framework a výchozí chování operačního systému. Pokud chcete, aby aplikace mohla vyjednávat připojení TLS 1,2, explicitní nastavení na nižší verzi TLS brání připojení TLS 1,2.

Pokud se nemůžete vyhnout zakódujeme verze protokolu, důrazně doporučujeme zadat TLS 1,2. Pokyny k identifikaci a odebrání závislostí TLS 1,0 najdete v dokumentu White Paper [k řešení potíží s protokolem tls 1,0](https://www.microsoft.com/download/details.aspx?id=55266) .

WCF podporuje TLS 1.0, 1,1 a 1,2 jako výchozí v .NET Framework 4,7. Počínaje .NET Framework 4.7.1 se standardně pro WCF používá nakonfigurovaná verze operačního systému. Pokud je aplikace explicitně nakonfigurovaná pomocí `SslProtocols.None`, WCF při použití přenosu NetTcp použije výchozí nastavení operačního systému.

Otázky k tomuto dokumentu můžete klást v [doporučených postupech pro zabezpečení TLS (Transport Layer Security)](https://github.com/dotnet/docs/issues/4675)na githubu .NET Framework.

## <a name="audit-your-code-and-make-code-changes"></a>Audit kódu a provádění změn kódu

V případě aplikací `<system.web><httpRuntime targetFramework>` ASP.NET zkontrolujte element _Web. config_ a ověřte, že používáte zamýšlenou verzi .NET Framework.

Informace o model Windows Forms a dalších aplikacích naleznete [v tématu How to: Cílí na verzi .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

Pomocí následujících částí ověříte, že nepoužíváte konkrétní verzi TLS nebo SSL.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Pokud vaše aplikace cílí na .NET Framework 4,7 nebo novějších verzí

V následujících částech se dozvíte, jak ověřit, že nepoužíváte konkrétní verzi TLS nebo SSL.

### <a name="for-http-networking"></a>Pro sítě HTTP

<xref:System.Net.ServicePointManager>pomocí .NET Framework 4,7 a novějších verzí použije výchozí protokol zabezpečení nakonfigurovaný v operačním systému. Chcete-li nastavit výchozí operační systém, pokud je to možné, nenastavujte hodnotu <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> vlastnosti, která je <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>výchozím nastavením.

Vzhledem k tomu, že <xref:System.Net.ServicePointManager> nastavenízpůsobí,žebudepoužívatvýchozíprotokolzabezpečenínakonfigurovanýoperačnímsystémem,vašeaplikacemůžeběžetodlišněvzávislostinaoperačnímsystému,nakterémjespuštěný.<xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> Například Windows 7 SP1 používá TLS 1,0, zatímco Windows 8 a Windows 10 používají TLS 1,2.

Zbývající část tohoto článku není relevantní, pokud cílíte .NET Framework 4,7 nebo novějších verzí pro sítě HTTP.

### <a name="for-tcp-sockets-networking"></a>Pro sítě TCP Sockets

<xref:System.Net.Security.SslStream>, pomocí .NET Framework 4,7 a novějších verzí se ve výchozím nastavení používá operační systém, který vybírá nejlepší protokol zabezpečení a verzi. Chcete-li získat výchozí nejlepší volbu pro operační systém, pokud je to možné, nepoužívejte přetížení <xref:System.Net.Security.SslStream> metod, které přebírají explicitní <xref:System.Security.Authentication.SslProtocols> parametr. V opačném <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>případě předejte. Doporučujeme nepoužívat <xref:System.Security.Authentication.SslProtocols.Default>. nastavení `SslProtocols.Default` vynutí použití protokolu SSL 3,0/TLS 1,0 a zabraňuje TLS 1,2.

Nenastavujte hodnotu <xref:System.Net.ServicePointManager.SecurityProtocol> vlastnosti (pro sítě http).

Nepoužívejte přetížení <xref:System.Net.Security.SslStream> metod, které přebírají explicitní <xref:System.Security.Authentication.SslProtocols> parametr (u sítě TCP Sockets). Když změníte cíl aplikace na .NET Framework 4,7 nebo novější, budete postupovat podle doporučení k osvědčeným postupům.

Zbývající část tohoto tématu není relevantní, pokud cílíte .NET Framework 4,7 nebo novějších verzí pro sítě TCP Sockets.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Pro přenos WCF TCP pomocí zabezpečení přenosu s přihlašovacími údaji certifikátu

WCF používá stejný zásobník sítě jako zbytek .NET Framework.

Pokud cílíte na 4.7.1, služba WCF je nakonfigurovaná tak, aby umožňovala operačnímu systému zvolit nejlepší protokol zabezpečení, pokud se explicitně nenakonfigurovala tato hodnota:

- V konfiguračním souboru aplikace.
- **Nebo**v aplikaci ve zdrojovém kódu.

Ve výchozím nastavení je .NET Framework 4,7 a novější verze nakonfigurovaná na používání protokolu TLS 1,2 a umožňuje připojení pomocí protokolu TLS 1,1 nebo TLS 1,0. Nakonfigurujte WCF tak, aby operační systém mohl zvolit nejlepší protokol zabezpečení nakonfigurováním vaší vazby na použití <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Dá se nastavit na <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. `SslProtocols.None`lze použít z <xref:System.ServiceModel.NetTcpSecurity.Transport>. `NetTcpSecurity.Transport`lze použít z <xref:System.ServiceModel.NetTcpBinding.Security>.

Pokud používáte vlastní vazbu:

- Nakonfigurujte WCF tak, aby operační systém mohl zvolit nejlepší protokol <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> zabezpečení nastavením použít. <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- **Nebo** nakonfigurujte protokol použitý s cestou `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`konfigurace.

Pokud nepoužíváte vlastní vazbu **a** nakonfigurujete vazbu **WCF pomocí konfigurace** , nastavte protokol použitý s cestou `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`konfigurace.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Pro zabezpečení zpráv WCF s přihlašovacími údaji certifikátu

Ve výchozím nastavení .NET Framework 4,7 a novější verze používá protokol určený ve <xref:System.Net.ServicePointManager.SecurityProtocol> vlastnosti. Pokud je [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` nastaveno na `true`, WCF zvolí nejlepší protokol až do TLS 1,0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Pokud se vaše aplikace zaměřuje na verzi .NET Framework starší než 4,7

Auditujte kód, abyste ověřili, že nenastavujete konkrétní verzi TLS nebo SSL, a to pomocí následujících částí:

### <a name="for-net-framework-46---462-and-not-wcf"></a>Pro .NET Framework 4,6-4.6.2 a ne WCF

Nastavte přepínač na`false`. `DontEnableSystemDefaultTlsVersions` `AppContext` Viz [Konfigurace zabezpečení prostřednictvím přepínačů AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>Pro WCF používající .NET Framework 4,6-4.6.2 pomocí zabezpečení přenosu protokolu TCP s přihlašovacími údaji certifikátu

Je nutné nainstalovat nejnovější opravy operačního systému. Viz [aktualizace zabezpečení](#security-updates).

Rozhraní WCF automaticky zvolí nejvyšší dostupný protokol až na TLS 1,2, pokud explicitně nenakonfigurujete verzi protokolu. Další informace najdete v předchozí části [pro přenos WCF TCP pomocí zabezpečení přenosu s přihlašovacími údaji certifikátu](#wcf-tcp-cert).

### <a name="for-net-framework-35---452-and-not-wcf"></a>Pro .NET Framework 3,5 – 4.5.2 a nikoli WCF

Doporučujeme, abyste aplikaci upgradovali na verzi .NET Framework 4,7 nebo novější. Pokud nemůžete upgradovat, proveďte následující kroky. V některých případech může aplikace selhat, dokud neprovedete upgrade na verzi .NET Framework 4,7 nebo novější.

Nastavte klíče registru [do schusestrongcrypto](#schusestrongcrypto) a [SystemDefaultTlsVersions](#systemdefaulttlsversions) na hodnotu 1. Viz téma [Konfigurace zabezpečení pomocí registru systému Windows](#configuring-security-via-the-windows-registry). .NET Framework verze 3,5 podporuje příznak pouze `SchUseStrongCrypto` v případě, že je předána explicitní hodnota TLS.

Pokud používáte v .NET Framework 3,5, je nutné nainstalovat Hot patch, aby bylo možné určit protokol TLS 1,2 pro váš program:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Kumulativní spolehlivost HR-1605-podpora systémových výchozích verzí TLS, které jsou součástí služby .NET Framework 3.5.1 v systému Windows 7 SP1 a Server 2008 R2 SP1 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Kumulativní spolehlivost HR-1605-podpora systémových výchozích verzí TLS, které jsou součástí .NET Framework 3,5 na Windows Serveru 2012 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Kumulativní spolehlivost HR-1605-podpora systémových výchozích verzí TLS, které jsou součástí .NET Framework 3,5 v Windows 8.1 a Windows Serveru 2012 R2 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | 1605 kumulativní opravy hotfix 3154521 pro .NET Framework 4.5.2 a 4.5.1 ve Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>Pro WCF používající .NET Framework 3,5-4.5.2 pomocí protokolu TCP Transport Security s přihlašovacími údaji certifikátu

V těchto verzích rozhraní WCF se pevně zakódované použít hodnoty SSL 3,0 a TLS 1,0. Tyto hodnoty nelze změnit. Aby bylo možné používat protokol TLS 1,1 a 1,2, je nutné aktualizovat a změnit cílení na verzi .NET Framework 4,6 nebo novější.

## <a name="if-your-app-targets-net-framework-35"></a>Pokud se vaše aplikace zaměřuje .NET Framework 3,5

Pokud je nutné explicitně nastavit protokol zabezpečení a neumožnit rozhraní .NET Framework nebo operačnímu systému vybrat protokol zabezpečení, přidejte `SecurityProtocolTypeExtensions` a `SslProtocolsExtension` výčty do kódu. `SecurityProtocolTypeExtensions`a `SslProtocolsExtension` zahrnout hodnoty pro `Tls12`, `Tls11` ahodnotu.`SystemDefault` Viz [Podpora systémových výchozích verzí TLS, které jsou součástí .NET Framework 3,5 v Windows 8.1 a Windows serveru 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Konfigurace zabezpečení prostřednictvím přepínačů AppContext (pro .NET Framework 4,6 nebo novější verze)

Přepínače [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) popsané v této části jsou relevantní, pokud je vaše aplikace cílena nebo běží na .NET Framework 4,6 nebo novějších verzích. Bez ohledu na to, jestli je ve výchozím nastavení nebo explicitně nastavené `false` , by měly být přepínače, pokud je to možné. Pokud chcete nakonfigurovat zabezpečení prostřednictvím jednoho nebo obou přepínačů, nezadávejte v kódu hodnotu protokolu zabezpečení. Tím by se přepsal přepínač (ES).

Přepínače mají stejný účinek, ať už provádíte síť http (<xref:System.Net.ServicePointManager>) nebo TCP Sockets (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Hodnota `false` pro`Switch.System.Net.DontEnableSchUseStrongCrypto` způsobí, že vaše aplikace bude používat silné šifrování. Hodnota `false` pro`DontEnableSchUseStrongCrypto` používá bezpečnější síťové protokoly (TLS 1,2, TLS 1,1 a TLS 1,0) a blokuje protokoly, které nejsou zabezpečené. Další informace najdete v tématu [příznak SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag). Hodnota `true` zakáže silné šifrování vaší aplikace.

Pokud se vaše aplikace zaměřuje .NET Framework 4,6 nebo novější verze, tento přepínač se `false`nastaví jako výchozí. To je zabezpečené výchozí nastavení, které doporučujeme. Pokud je vaše aplikace spuštěná na .NET Framework 4,6, ale cílí na starší verzi, přepínač se `true`nastaví na výchozí hodnotu. V takovém případě byste ji měli explicitně nastavit na `false`.

`DontEnableSchUseStrongCrypto``true` Pokud se potřebujete připojit ke starším službám, které nepodporují silné šifrování a nelze je upgradovat, měla by mít pouze hodnotu.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Hodnota `false` pro`Switch.System.Net.DontEnableSystemDefaultTlsVersions` způsobí, že aplikace umožní operačnímu systému zvolit protokol. Hodnota `true` způsobí, že vaše aplikace bude používat protokoly vydané .NET Framework.

Pokud se vaše aplikace zaměřuje .NET Framework 4,7 nebo novější verze, tento přepínač se `false`nastaví jako výchozí. To je zabezpečené výchozí nastavení, které doporučujeme. Pokud je vaše aplikace spuštěná na .NET Framework 4,7 nebo novějších verzích, ale cílí na starší verzi, přepínač `true`se nastaví na výchozí hodnotu. V takovém případě byste ji měli explicitně nastavit na `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Hodnota `false` `ServicePointManager.SecurityProtocols` pro `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` způsobí, že aplikace použije hodnotu definovanou v pro zabezpečení zprávy pomocí pověření certifikátu. Hodnota `true` používá nejvyšší dostupný protokol, až do TLS 1.0.

Pro aplikace cílené na .NET Framework 4,7 a novějších verzích je tato hodnota `false`standardně nastavena na. Pro aplikace cílené .NET Framework 4.6.2 a dříve tato hodnota je výchozím nastavením `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Hodnota `false` pro`Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` nastaví výchozí konfiguraci tak, aby operační systém mohl zvolit protokol. Hodnota `true` nastaví výchozí hodnotu nejvyššího dostupného protokolu, až do TLS 1.2.

Pro aplikace cílené .NET Framework 4.7.1 a novějších verzí se tato hodnota nastaví `false`jako výchozí. Pro aplikace cílené .NET Framework 4,7 a starších se tato hodnota nastaví jako `true`výchozí.

Další informace o protokolech TLS najdete v [tématu zmírnění rizika: Protokoly](../migration-guide/mitigation-tls-protocols.md)TLS. Další informace o `AppContext` přepínačích naleznete v [`<AppContextSwitchOverrides> Element`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)tématu.

## <a name="configuring-security-via-the-windows-registry"></a>Konfigurace zabezpečení prostřednictvím registru Windows

> [!WARNING]
> Nastavení klíčů registru má vliv na všechny aplikace v systému. Tuto možnost použijte pouze v případě, že máte plnou kontrolu nad počítačem a můžete řídit změny v registru.

Pokud nastavení jednoho nebo obou `AppContext` přepínačů není možnost, můžete řídit protokoly zabezpečení, které vaše aplikace používá, s klíči registru Windows popsanými v této části. Pokud vaše aplikace běží na .NET Framework 4.5.2 nebo starších verzích nebo `AppContext` Pokud konfigurační soubor nemůžete upravit, možná nebudete moct použít jeden nebo oba přepínače. Pokud chcete nakonfigurovat zabezpečení pomocí registru, nezadávejte v kódu hodnotu protokolu zabezpečení. Tím se přepíše nastavení registru.

Názvy klíčů registru se podobají názvům odpovídajících `AppContext` přepínačů, ale `DontEnable` bez předpony názvu. Například `AppContext` přepínač `DontEnableSchUseStrongCrypto` je klíč registru s názvem [do schusestrongcrypto](#schusestrongcrypto).

Tyto klíče jsou k dispozici ve všech .NET Framework verzích, pro které je k dispozici nová oprava zabezpečení. Viz [aktualizace zabezpečení](#security-updates).

Všechny klíče registru popsané níže mají stejný účinek, ať už provádíte síť http (<xref:System.Net.ServicePointManager>) nebo TCP Sockets (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

Klíč `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` registru má hodnotu typu DWORD. Hodnota 1 způsobí, že aplikace bude používat silné šifrování. Silná kryptografie používá bezpečnější síťové protokoly (TLS 1,2, TLS 1,1 a TLS 1,0) a blokuje protokoly, které nejsou zabezpečené. Hodnota 0 zakáže silnou kryptografii. Další informace najdete v tématu [příznak SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag).

Pokud se vaše aplikace zaměřuje .NET Framework 4,6 nebo novější verze, tento klíč se nastaví na hodnotu 1. To je zabezpečené výchozí nastavení, které doporučujeme. Pokud je vaše aplikace spuštěná na .NET Framework 4,6, ale zaměřuje se na starší verzi, pak se výchozí klíč nastaví na 0. V takovém případě byste měli explicitně nastavit jeho hodnotu na 1.

Tento klíč by měl mít hodnotu 0, pokud se potřebujete připojit ke starším službám, které nepodporují silné šifrování a nelze je upgradovat.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

Klíč `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` registru má hodnotu typu DWORD. Hodnota 1 způsobí, že aplikace umožní operačnímu systému zvolit protokol. Hodnota 0 způsobí, že vaše aplikace bude používat protokoly vydané .NET Framework.

`<VERSION>`musí být v 4.0.30319 (pro .NET Framework 4 a vyšší) nebo v 2.0.50727 (pro .NET Framework 3,5).

Pokud se vaše aplikace zaměřuje .NET Framework 4,7 nebo novější verze, tento klíč se nastaví na hodnotu 1. To je zabezpečené výchozí nastavení, které doporučujeme. Pokud vaše aplikace běží na .NET Framework 4,7 nebo novějších verzích, ale cílí na starší verzi, klíč se nastaví na hodnotu 0. V takovém případě byste měli explicitně nastavit jeho hodnotu na 1.

Další informace najdete v tématu [kumulativní aktualizace pro Windows 10 verze 1511 a Windows Server 2016 Technical Preview 4: 10. května 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016).

Další informace o rozhraní .NET Framework 3.5.1 najdete v tématu [Podpora výchozích verzí systému TLS, které jsou součástí služby .NET Framework 3.5.1 v systému Windows 7 SP1 a Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Následující _. Soubor REG_ nastaví klíče registru a jejich varianty na jejich nejbezpečnější hodnoty:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001
```

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Konfigurace protokolů Schannel v registru Windows

Registr můžete použít pro jemně odstupňovanou kontrolu nad protokoly, které klient nebo server aplikace vyjednává. Sítě vaší aplikace přecházejí přes Schannel (což je jiný název [zabezpečeného kanálu](/windows/desktop/SecAuthN/secure-channel). Konfigurací `Schannel`můžete nakonfigurovat chování vaší aplikace.

Začněte s `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` klíčem registru. V tomto klíči můžete vytvořit všechny podklíče v sadě `SSL 2.0`, `SSL 3.0`, `TLS 1.0` `TLS 1.1`, a `TLS 1.2`. Pod každým z těchto podklíčů můžete vytvořit podklíče `Client` a/nebo `Server`. V `Client` části `Server`a můžete vytvořit hodnoty `DisabledByDefault` DWORD (0 nebo 1) a `Enabled` (0 nebo 0xFFFFFFFF).

## <a name="the-sch_use_strong_crypto-flag"></a>Příznak SCH_USE_STRONG_CRYPTO

Pokud je povolená (ve výchozím nastavení je to `AppContext` přepínačem nebo v registru Windows), .NET Framework `SCH_USE_STRONG_CRYPTO` používá příznak, když vaše aplikace požaduje protokol zabezpečení TLS. Příznak může být povolen ve výchozím nastavení, `AppContext` s přepínačem nebo s registrem. `SCH_USE_STRONG_CRYPTO` Operační systém předá příznak `Schannel`, aby vypnul známé slabé algoritmy, šifrovací sady a verze protokolů TLS/SSL, které mohou být jinak povoleny pro lepší interoperabilitu. Další informace naleznete v tématu:

- [Zabezpečený kanál](/windows/desktop/SecAuthN/secure-channel)
- [Struktura SCHANNEL_CRED](/windows/win32/api/schannel/ns-schannel-schannel_cred)

`Tls11` `Tls` `Tls12` <xref:System.Security.Authentication.SslProtocols> <xref:System.Net.SecurityProtocolType> Příznak je také `Schannel` předán, pokud explicitně použijete (TLS 1,0), nebo výčtové hodnoty nebo. `SCH_USE_STRONG_CRYPTO`

## <a name="security-updates"></a>Aktualizace zabezpečení

Osvědčené postupy v tomto článku závisí na nedávno nainstalovaných aktualizacích zabezpečení. Tyto aktualizace zahrnují možnost používat pokročilé .NET Framework 4,7 a novější funkce. Nedávné aktualizace zabezpečení jsou důležité, pokud je vaše aplikace spuštěná na .NET Framework 4,7 a novějších verzích (i když cílí na starší verzi).

Chcete-li aktualizovat .NET Framework, aby operační systém mohl zvolit nejlepší verzi protokolu TLS, která se má použít, je nutné nainstalovat alespoň:

- [.NET Framework srpna 2017 Preview k kumulativní kvalitě](https://devblogs.microsoft.com/dotnet/net-framework-august-2017-preview-of-quality-rollup/).
- **Nebo** [.NET Framework zabezpečení a kumulativní kvality od září 2017](https://devblogs.microsoft.com/dotnet/net-framework-september-2017-security-and-quality-rollup/).

Viz také:

- [.NET Framework verze a závislosti](../migration-guide/versions-and-dependencies.md)
- [Postupy: Určete, které verze .NET Framework jsou](../migration-guide/how-to-determine-which-versions-are-installed.md)nainstalovány.

## <a name="support-for-tls-12"></a>Podpora protokolu TLS 1.2

Aby mohla aplikace vyjednávat TLS 1,2, musí operační systém a .NET Framework verze podporovat protokol TLS 1,2.

**Požadavky na operační systém pro podporu TLS 1,2**

Pokud chcete povolit nebo znovu povolit TLS 1,2 nebo TLS 1,1 v systému, který je podporuje, přečtěte si téma [nastavení registru TLS (Transport Layer Security)](/windows-server/security/tls/tls-registry-settings).

| **OS** | **Podpora TLS 1,2** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | Podporované a ve výchozím nastavení povolená. |
| Windows 8.1<br>Windows Server 2012 R2 | Podporované a ve výchozím nastavení povolená. |
| Windows 8.0<br>Windows Server 2012 | Podporované a ve výchozím nastavení povolená. |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | Podporované, ale není ve výchozím nastavení povolená. Podrobnosti o tom, jak povolit protokol TLS 1,2, najdete na webové stránce [nastavení registru TLS (Transport Layer Security)](/windows-server/security/tls/tls-registry-settings) . |
| Windows Server 2008 | Podpora TLS 1,2 a TLS 1,1 vyžaduje aktualizaci. [V článku aktualizace můžete přidat podporu pro tls 1,1 a tls 1,2 ve Windows serveru 2008 SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Není podporováno. |

Informace o tom, které protokoly TLS/SSL jsou ve výchozím nastavení povolené v každé verzi Windows, najdete v tématu [protokoly TLS/SSL (Schannel SSP)](/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).

**Požadavky na podporu TLS 1,2 s .NET Framework 3,5**

V této tabulce je uvedena aktualizace operačního systému, kterou budete potřebovat pro podporu TLS 1,2 s .NET Framework 3,5. Doporučujeme použít všechny aktualizace operačního systému.

| **OS** | **Minimální aktualizace nutná pro podporu TLS 1,2 s .NET Framework 3,5** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | [Kumulativní aktualizace pro Windows 10 verze 1511 a Windows Server 2016 Technical Preview 4: 10. května 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1<br>Windows Server 2012 R2 | [Podpora výchozích verzí systému TLS obsažených v .NET Framework 3,5 v Windows 8.1 a Windows Serveru 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0<br>Windows Server 2012 | [Podpora výchozích verzí systému TLS obsažených v .NET Framework 3,5 ve Windows Serveru 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | [Podpora výchozích verzí systému TLS obsažených ve službě .NET Framework 3.5.1 v systému Windows 7 SP1 a Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Podpora výchozích verzí systému TLS obsažených v .NET Framework 2,0 SP2 v systému Windows Vista SP2 a Server 2008 SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Není podporováno |

## <a name="azure-cloud-services"></a>Azure Cloud Services

Pokud používáte webové a pracovní role [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) k hostování a spuštění vaší aplikace, existuje několik důležitých informací, které je potřeba vzít v úvahu při podpoře TLS 1,2.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>Ve výchozím nastavení není v hostovaném operačním systému Azure nainstalovaná .NET Framework 4,7.

Nejnovější verze nainstalovaná v nejnovější verzi služby hostovaného operačního systému Azure v řadě 5 (Windows Server 2016) je 4.6.2. Pokud chcete zjistit, které verze .NET Framework jsou nainstalované na každém hostovaném operačním systému Azure, přečtěte si část vydaných verzí [hostovaného operačního systému Azure a kompatibility SDK](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Pokud se vaše aplikace zaměřuje na verzi .NET Framework, která není dostupná na verzi hostovaného operačního systému Azure, je potřeba ji nainstalovat sami. Viz [instalace rozhraní .NET do rolí cloudové služby Azure](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Pokud instalace rozhraní vyžaduje restart, role služby se můžou taky restartovat před vstupem do stavu připraveno.

### <a name="azure-guest-os-registry-settings"></a>Nastavení registru hostovaného operačního systému Azure

Image řady operačních systémů hosta Azure pro [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) už má `SchUseStrongCrypto` klíč registru nastavený na hodnotu 1. Další informace najdete v tématu [do schusestrongcrypto](#schusestrongcrypto).

Nastavte klíč registru [SystemDefaultTlsVersions](#systemdefaulttlsversions) na hodnotu 1. Viz téma [Konfigurace zabezpečení pomocí registru systému Windows](#configuring-security-via-the-windows-registry).
