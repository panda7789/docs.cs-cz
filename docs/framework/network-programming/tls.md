---
title: "Zabezpečení TLS (Transport Layer) osvědčené postupy s rozhraním .NET Framework"
description: "Osvědčené postupy zabezpečení TLS (Transport Layer) pomocí rozhraní .NET Framework"
ms.date: 03/15/2018
ms.prod: .net-framework
ms.topic: article
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
author: blowdart
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64829eee5b21a44acb18cbec9b901d77d49cab90
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2018
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Zabezpečení TLS (Transport Layer) osvědčené postupy s rozhraním .NET Framework

Protokol zabezpečení TLS (Transport Layer) je standardní určené k ochraně osobní údaje přenášená přes Internet. [Protokol TLS 1.2](https://tools.ietf.org/html/rfc5246) je nejnovější vydanou standard a poskytuje vyšší zabezpečení porovnání s předchozími verzemi. TLS 1.2 se nahradí nakonec [TLS 1.3](https://tools.ietf.org/html/draft-ietf-tls-tls13-22). Tento článek představuje doporučení k zabezpečení aplikací rozhraní .NET Framework, které používají protokol TLS.

Aby aplikace rozhraní .NET Framework zůstávají zabezpečení, by měl TLS verze **není** být pevně zakódované. Aplikace rozhraní .NET framework by měly používat protokol TLS verze, kterou podporuje operační systém (OS).

Tento dokument cílem vývojáři, kteří jsou:

- Přímo pomocí <xref:System.Net> rozhraní API (například <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- Přímo pomocí protokolu WCF klienty a služby pomocí <xref:System.ServiceModel?displayProperty=nameWithType> oboru názvů.
- Pomocí [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) webové a pracovní role hostování a spuštění aplikace. Najdete v článku [Azure Cloud Services](#azure-cloud-services) části.

Doporučujeme vám:

- Cílí na rozhraní .NET Framework 4.7 nebo novější verze na vaše aplikace. Cílové rozhraní .NET Framework 4.7.1 nebo novější verze na aplikace WCF.
- Nezadávejte TLS verze. Nakonfigurujte kódu umožníte rozhodněte o TLS verze operačního systému.
- Proveďte audit důkladné kódu k ověření, že nejsou určení verze protokolu TLS nebo SSL.

Pokud vaše aplikace umožňuje zvolte TLS verze operačního systému:

- Automaticky využívá nové protokolů přidat v budoucnu, jako je například TLS 1.3.
- Operační systém blokuje protokoly, které jsou zjištěny nechcete zabezpečená.

V části [auditovat kódu a provádět změny kódu](#audit-your-code-and-make-code-changes) popisuje auditování a aktualizace vašeho kódu.

Tento článek vysvětluje, jak povolit nejvyšší zabezpečení, které jsou k dispozici pro verzi rozhraní .NET Framework, který vaše aplikace cílí a běží na. Když aplikace explicitně nastaví protokol zabezpečení a verze, výslovný nesouhlas jiná možnost a výslovný nesouhlas rozhraní .NET Framework a operační systém výchozí chování. Pokud chcete aplikaci, kterou chcete mít možnost připojení protokolu TLS 1.2, explicitně nastavení na nižší verzi TLS brání připojení protokolu TLS 1.2.

Pokud se nelze vyhnout hardcoding verzi protokolu, důrazně doporučujeme, aby zadáte TLS 1.2. Pokyny k identifikaci a odebrání závislostí TLS 1.0, stáhněte si [řešení tohoto problému TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266) dokument White Paper.

WCF podporuje TLS1.0, 1.1 a 1.2 jako výchozí v rozhraní .NET Framework 4.7. Od verze rozhraní .NET Framework 4.7.1, výchozí hodnoty WCF v operačním systému nakonfigurovat verze. Pokud aplikace explicitně nakonfigurovaný s `SslProtocols.None`, WCF používá výchozí nastavení operačního systému při použití NetTcp přenosu.

Můžete klást otázky o tomto dokumentu v potíže Githubu [zabezpečení TLS (Transport Layer) osvědčené postupy s rozhraním .NET Framework](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Audit kódu a provádět změny kódu

Pro aplikace ASP.NET, zkontrolujte `<system.web><httpRuntime targetFramework>` element _web.config_ k ověření, že používáte určený verzi rozhraní .NET Framework.

Windows Forms a dalších aplikací najdete v tématu [postupy: cílení na verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

V následujících částech použijte k ověření, že nepoužíváte na konkrétní verzi protokolu TLS nebo SSL.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Pokud vaše aplikace používá rozhraní .NET Framework 4.7 nebo novější verze

Následující části vysvětlují, jak ověřit, že nepoužíváte na konkrétní verzi protokolu TLS nebo SSL.

### <a name="for-http-networking"></a>Pro HTTP sítě

<xref:System.Net.ServicePointManager>, pomocí rozhraní .NET Framework 4.7 a novější verze, použije se výchozí hodnota výběr nejlepší protokol zabezpečení a verze operačního systému. Chcete-li získat výchozí nejlepší volbou operačního systému, pokud je to možné, nemáte nastavit hodnotu <xref:System.Net.ServicePointManager.SecurityProtocol> vlastnost. Jinak, nastavte ji na <xref:System.Net.SecurityProtocolType.SystemDefault>.

Zbývající část tohoto článku není relevantní, při cílení na rozhraní .NET Framework 4.7 nebo novější verze pro sítě protokolu HTTP.

### <a name="for-tcp-sockets-networking"></a>Sokety TCP sítě

<xref:System.Net.Security.SslStream>, pomocí rozhraní .NET Framework 4.7 a novější verze, použije se výchozí hodnota výběr nejlepší protokol zabezpečení a verze operačního systému. Chcete-li získat výchozí nejlepší volbou operačního systému, pokud je to možné, nepoužívejte přetížení metody <xref:System.Net.Security.SslStream> které přebírají explicitního <xref:System.Security.Authentication.SslProtocols> parametr. Jinak, předá <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Doporučujeme vám, že nepoužíváte <xref:System.Security.Authentication.SslProtocols.Default>; nastavení `SslProtocols.Default` vynutí použití protokolu SSL 3.0 /TLS 1.0 a zabránit TLS 1.2.

Není nastavený hodnotu <xref:System.Net.ServicePointManager.SecurityProtocol> vlastnost (pro HTTP sítě).

Nepoužívejte přetížení metody <xref:System.Net.Security.SslStream> které přebírají explicitního <xref:System.Security.Authentication.SslProtocols> parametr (pro TCP sockets sítě). Pokud jste změňte cíl pro rozhraní .NET Framework 4.7 nebo novější verze aplikace, budete následující osvědčené postupy doporučení.

Zbývající část tohoto tématu není relevantní, při cílení na rozhraní .NET Framework 4.7 nebo novější verze pro TCP soketů sítě.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Pro WCF TCP přenosu pomocí zabezpečení přenosu s přihlašovacími údaji certifikátu

WCF používá jeden síťový zásobník jako zbytek rozhraní .NET Framework.

Pokud cílíte 4.7.1, WCF konfigurace umožňuje vybrat nejlepší protokol zabezpečení ve výchozím nastavení, pokud není explicitně nakonfigurován operačního systému:

- V konfiguračním souboru aplikace.
- **Nebo**, v aplikaci ve zdrojovém kódu.

Ve výchozím nastavení rozhraní .NET Framework 4.7 a novějších verzích je nakonfigurovaný na použití protokolu TLS 1.2 a umožňuje připojení pomocí protokolu TLS 1.1 a TLS 1.0. Konfigurace WCF umožňuje operačního systému a vybrat nejlepší protokol zabezpečení podle konfigurace vašeho vazeb používat <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. To je možné nastavit na <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. `SslProtocols.None` je přístupný z <xref:System.ServiceModel.NetTcpSecurity.Transport>. `NetTcpSecurity.Transport` je přístupný z <xref:System.ServiceModel.NetTcpBinding.Security>.

Pokud používáte vlastní vazby:

- Konfigurace WCF umožňuje operačního systému a vybrat nejlepší protokol zabezpečení podle nastavení <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> používat <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>.
- **Nebo** nakonfigurovat protokol použitý se cesta ke konfiguračnímu `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`.

Pokud jste **není** použití vlastní vazby **a** nastavování vaší vazby WCF pomocí konfigurace, nastavte protokol použitý se cesta ke konfiguračnímu `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Zabezpečení zpráv WCF s přihlašovacími údaji certifikátu

4.7 rozhraní .NET framework a novějších verzích ve výchozím nastavení používá protokol uvedený v poli <xref:System.Net.ServicePointManager.SecurityProtocol> vlastnost. Když [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` je nastaven na `true`, WCF vybere nejlepší protokol až do protokolu TLS 1.0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Pokud aplikace cílí starší než 4.7 verze rozhraní .NET Framework

Audit kódu k ověření, že nejsou nastavení na konkrétní verzi protokolu TLS nebo SSL pomocí v následujících částech:

### <a name="for-net-framework-46---462-and-not-wfc"></a>Pro rozhraní .NET Framework 4.6 - 4.6.2 a není WFC

Nastavte `DontEnableSystemDefaultTlsVersions` `AppContext` přepnout `false`. V tématu [konfigurace zabezpečení pomocí přepínačů AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>Pro WCF pomocí rozhraní .NET Framework 4.6 - 4.6.2 pomocí zabezpečení přenosu TCP s přihlašovacími údaji certifikátu

Je nutné nainstalovat nejnovější opravy operačního systému. V tématu [aktualizace zabezpečení](#security-updates).

Rozhraní WCF automaticky zvolí nejvyšší protokol, který je k dispozici až TLS 1.2, pokud explicitně nakonfigurovat verzi protokolu. Další informace najdete v předchozí části [přenosu pro TCP WCF pomocí zabezpečení přenosu s přihlašovacími údaji certifikát](#wcf-tcp-cert).

### <a name="for-net-framework-35---451-and-not-wcf"></a>Pro rozhraní .NET Framework 3.5 - 4.5.1 a není WCF

Doporučujeme, abyste že upgradu vaší aplikace na rozhraní .NET Framework 4.7 nebo novější verze. Pokud nelze upgradovat, proveďte následující kroky. V určitém okamžiku v budoucnu, vaše aplikace může selhat dokud neprovedete upgrade rozhraní .NET Framework 4.7 nebo novější verze.

Nastavte [SchUseStrongCrypto](#schusestrongcrypto) a [SystemDefaultTlsVersions](#systemdefaulttlsversions) klíče registru na 1. V tématu [konfigurace zabezpečení pomocí registru systému Windows](#configuring-security-via-the-windows-registry). Podporuje rozhraní .NET Framework verze 3.5 `SchUseStrongCrypto` příznak, pouze pokud je předán explicitní hodnotu TLS.

Pokud používáte v rozhraní .NET Framework 3.5, budete muset nainstalovat aktivní oprava tak, aby TLS 1.2 může být určené programem:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Spolehlivost kumulativní HR-1605 – podpora pro TLS systému výchozí verze součástí rozhraní .NET Framework 3.5.1 na Windows 7 SP1 a Server 2008 R2 SP1 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Spolehlivost kumulativní HR-1605 – podpora pro TLS systému výchozí verze součástí rozhraní .NET Framework 3.5 v systému Windows Server 2012 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Souhrn spolehlivost HR 1605 – podpora pro TLS systému výchozí verze součástí rozhraní .NET Framework 3.5 ve Windows 8.1 a Windows Server 2012 R2 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | Kumulativní oprava Hotfix 1605 3154521 pro rozhraní .NET Framework 4.5.2 a 4.5.1 v systému Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>Pro WCF pomocí rozhraní .NET Framework 3.5 - 4.5.2 pomocí zabezpečení přenosu TCP s přihlašovacími údaji certifikátu

Tyto verze rozhraní WCF jsou pevně zakódované použít hodnoty SSL 3.0 a TLS 1.0. Tyto hodnoty nelze změnit. Musíte aktualizovat a změnit cílový k použití protokolu TLS 1.1 a 1.2 NET Framework 4.6 nebo novější verze.

## <a name="if-your-app-targets-net-framework-35"></a>Pokud aplikace cílí rozhraní .NET Framework 3.5

Pokud musíte explicitně nastavit protokol zabezpečení místo rozhraní .NET framework nebo OS vyberte protokol zabezpečení, přidejte `SecurityProtocolTypeExtensions` a `SslProtocolsExtension` výčty do vašeho kódu. `SecurityProtocolTypeExtensions` a `SslProtocolsExtension` zahrnout hodnoty pro `Tls12`, `Tls11`a `SystemDefault` hodnotu. V tématu [podpora TLS systému výchozí verze rozhraní .NET Framework 3.5 ve Windows 8.1 a Windows Server 2012 R2 součástí](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Konfigurace zabezpečení prostřednictvím AppContext přepne (pro rozhraní .NET Framework 4.6 nebo novější verze)

[AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepínače popsaných v této části jsou relevantní Pokud vaše aplikace cíle, nebo běží na rozhraní .NET Framework 4.6 nebo novější verze. Jestli ve výchozím nastavení, nebo je explicitně nastavíte, že přepínače by měla být `false` Pokud je to možné. Pokud chcete nakonfigurovat zabezpečení pomocí jednoho nebo obou přepínačů, nemusíte zadejte hodnotu protokol zabezpečení ve vašem kódu; to proto by se mělo přepsat vypínače.

Přepínače mají stejný účinek, jestli vaše změny sítě HTTP (<xref:System.Net.ServicePointManager>) nebo TCP soketů sítě (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Hodnota `false` pro `Switch.System.Net.DontEnableSchUseStrongCrypto` způsobí, že vaše aplikace používat silné šifrování. Hodnota `false` pro `DontEnableSchUseStrongCrypto` používá bezpečnější síťové protokoly (TLS 1.2, protokol TLS 1.1 a TLS 1.0) a blokuje protokoly, které nejsou zabezpečeny. Další informace najdete v tématu [SCH_USE_STRONG_CRYPTO příznak](#the-schusestrongcrypto-flag). Hodnota `true` zakáže silné šifrování pro vaši aplikaci.

Pokud vaše aplikace používá rozhraní .NET Framework 4.6 nebo novější verze, tento přepínač výchozí `false`. Který je zabezpečený výchozí, což vám doporučujeme. Pokud vaše aplikace běží na rozhraní .NET Framework 4.6, ale zaměřuje na starší verzi, přepínač výchozí `true`. V takovém případě je vhodné explicitně nastavit `false`.

`DontEnableSchUseStrongCrypto` by měla mít pouze hodnotu `true` Pokud potřebujete připojit k starší verze služby, které nepodporují silné šifrování a nelze ji upgradovat.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Hodnota `false` pro `Switch.System.Net.DontEnableSystemDefaultTlsVersions` způsobí, že aplikaci, kterou chcete povolit operačnímu systému vybrat protokol. Hodnota `true` způsobí, že vaše aplikace používat protokoly zachyceny pomocí rozhraní .NET Framework.

Pokud vaše aplikace používá rozhraní .NET Framework 4.7 nebo novější verze, tento přepínač výchozí `false`. Které je výchozí zabezpečení, který doporučujeme. Pokud vaše aplikace běží na rozhraní .NET Framework 4.7 nebo novější verze, ale zaměřuje na starší verzi, přepínač výchozí `true`. V takovém případě je vhodné explicitně nastavit `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Hodnota `false` pro `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` způsobí, že aplikace k používání hodnota definovaná v `ServicePointManager.SecurityProtocols` zabezpečení zpráv pomocí certifikátů přihlašovacích údajů. Hodnota `true` používá protokol nejvyšší k dispozici, až TLS1.0

Pro cílení na rozhraní .NET Framework 4.7 a novější verze aplikace, výchozí hodnota je `false`. Pro aplikace cílený na rozhraní .NET Framework 4.6.2 a starší, výchozí hodnota je `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Hodnota `false` pro `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` nastaví výchozí konfiguraci pro povolit operačnímu systému vybrat protokol. Hodnota `true` nastaví výchozí k dispozici, až TLS1.2 nejvyšší protokolu.

Pro cílení na rozhraní .NET Framework 4.7.1 a novější verze aplikace, výchozí hodnota je `false`. Pro cílení na rozhraní .NET Framework 4.7 a starší aplikace, výchozí hodnota je `true`.

Další informace o protokoly TLS najdete v tématu [omezení rizik: protokoly TLS](../migration-guide/mitigation-tls-protocols.md). Další informace o `AppContext` přepínače, najdete v části [ `<AppContextSwitchOverrides> Element` ](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Konfigurace zabezpečení pomocí registru systému Windows

Pokud nastavení jedné nebo obou `AppContext` přepínače nejsou možnost, můžete řídit protokolů zabezpečení, které vaše aplikace používá s klíči registru systému Windows, které jsou popsané v této části. Není možné použít jeden nebo oba `AppContext` přepne, pokud aplikace cílí na verzi rozhraní .NET Framework starší než 4.6, nebo nelze upravit konfigurační soubor. Pokud chcete nakonfigurovat registr zabezpečení, pak nezadávejte hodnotu protokol zabezpečení ve vašem kódu; to proto by se mělo přepsat registru.

Názvy klíčů registru jsou podobné názvy odpovídající `AppContext` ale bez přepne `DontEnable` před název. Například `AppContext` přepínač `DontEnableSchUseStrongCrypto` nazývá klíč registru [SchUseStrongCrypto](#schusestrongcrypto).

Tyto klíče jsou k dispozici ve všech verzích rozhraní .NET Framework, pro které je poslední opravy zabezpečení. V tématu [aktualizace zabezpečení](#security-updates).

Všechny klíče registru popsané dál mají stejný účinek, jestli vaše změny sítě HTTP (<xref:System.Net.ServicePointManager>) nebo TCP soketů sítě (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` Klíč registru má hodnotu typu DWORD. Hodnota 1 způsobí, že vaše aplikace používat silné šifrování. Silné šifrování používá bezpečnější síťové protokoly (TLS 1.2, protokol TLS 1.1 a TLS 1.0) a blokuje protokoly, které nejsou zabezpečeny. Hodnota 0 zakáže silného šifrování. Další informace najdete v tématu [SCH_USE_STRONG_CRYPTO příznak](#the-schusestrongcrypto-flag).

Pokud vaše aplikace používá rozhraní .NET Framework 4.6 nebo novější verze, tento klíč výchozí hodnotu 1. Které je výchozí zabezpečení, který doporučujeme. Pokud vaše aplikace běží na rozhraní .NET Framework 4.6, ale zaměřuje na starší verzi, pak klíč použije výchozí hodnota 0. V takovém případě byste měli explicitně nastavit jeho hodnotu na 1.

Tento klíč by měl mít pouze hodnota 0, pokud potřebujete připojit k starší verze služby, které nepodporují silné šifrování a nelze ji upgradovat.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` Klíč registru má hodnotu typu DWORD. Hodnota 1 způsobí, že aplikaci, kterou chcete povolit operačnímu systému vybrat protokol. Hodnota 0 způsobí, že vaše aplikace používat protokoly zachyceny pomocí rozhraní .NET Framework.

`<VERSION>` musí být v4.0.30319 (pro rozhraní .NET Framework 4 a novější) nebo v2.0.50727 (pro rozhraní .NET Framework 3.5).

Pokud vaše aplikace používá rozhraní .NET Framework 4.7 nebo novější verze, tento klíč výchozí hodnotu 1. Které je výchozí zabezpečení, který doporučujeme. Pokud vaše aplikace běží na rozhraní .NET Framework 4.7 nebo novější verze, ale zaměřuje na starší verzi, klíč bude jako výchozí nastavena na hodnotu 0. V takovém případě byste měli explicitně nastavit jeho hodnotu na 1.

Další informace najdete v tématu [kumulativní aktualizace pro Windows 10 verzi 1511 a Windows Server 2016 Technical Preview 4: 10. května 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016).

Další informace, pomocí rozhraní .NET framework 3.5.1, najdete v části [podpora TLS systému výchozí verze součástí rozhraní .NET Framework 3.5.1 na Windows 7 SP1 a Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Následující _. REG_ souboru nastaví na nejvíc bezpečné hodnoty klíče registru a jejich varianty:

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

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Protokoly Schannel konfigurace v registru systému Windows

Registru můžete použít pro jemně odstupňovanou kontrolu nad protokolů, které vyjedná aplikace klienta nebo serveru. Vaše aplikace sítě prochází Schannel (což je jiný název pro [Secure Channel](https://msdn.microsoft.com/library/windows/desktop/aa380123). Nakonfigurováním `Schannel`, můžete nakonfigurovat chování vaší aplikace.

Začínat `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` klíč registru. Pod tímto klíčem můžete vytvořit všechny podklíče v sadě `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1`, a `TLS 1.2`. V každém z těchto podklíče, můžete vytvořit podklíče `Client` nebo `Server`. V části `Client` a `Server`, vytvořením hodnoty DWORD `DisabledByDefault` (0 nebo 1) a `Enabled` (0 nebo 0xFFFFFFFF).

## <a name="the-schusestrongcrypto-flag"></a>Příznak SCH_USE_STRONG_CRYPTO

Pokud je povolená (ve výchozím nastavení, podle `AppContext` přepínač, nebo pomocí registru systému Windows), používá rozhraní .NET Framework `SCH_USE_STRONG_CRYPTO` příznak, když vaše aplikace požaduje protokol zabezpečení TLS. `SCH_USE_STRONG_CRYPTO` Příznak můžete povolit ve výchozím nastavení, `AppContext` přepínač, nebo pomocí registru. Příznak, který předává operačního systému `Schannel`dáte pokyn, aby ji zakázat známé slabé kryptografické algoritmy, šifer sad a verze protokolu TLS/SSL, které může být jinak povolena pro lepší spolupráci. Další informace naleznete v tématu:

- [Zabezpečený kanál](https://msdn.microsoft.com/library/windows/desktop/aa380123)
- [Struktura SCHANNEL_CRED](https://msdn.microsoft.com/library/windows/desktop/aa379810)

`SCH_USE_STRONG_CRYPTO` Příznak také předaný `Schannel` explicitně použijete `Tls` (TLS 1.0), `Tls11`, nebo `Tls12` uvedené hodnoty <xref:System.Net.SecurityProtocolType> nebo <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Aktualizace zabezpečení

Osvědčené postupy v tomto článku jsou závislé na nejnovější aktualizace zabezpečení během instalace. Tyto aktualizace zahrnují možnost používat rozšířené 4.7 rozhraní .NET Framework a novější funkce. Nejnovější aktualizace zabezpečení jsou důležité, pokud vaše aplikace běží v rozhraní .NET Framework 4.7 a novějším (i když se zaměřuje na starší verzi).

Pokud chcete aktualizovat rozhraní .NET Framework umožňuje vybrat nejlepší verzi TLS používat operační systém, musíte nainstalovat alespoň:

- [Rozhraní .NET Framework srpen 2017 Preview kvality souhrnu](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup).
- **Nebo** [kumulativní kvality a zabezpečení rozhraní .NET Framework září 2017](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup).

Viz také:

- [Rozhraní .NET framework verze a závislosti](../migration-guide/versions-and-dependencies.md)
- [Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>Podpora pro protokol TLS 1.2

Pro vaši aplikaci pro vyjednávání protokolu TLS 1.2, operačního systému a verzi rozhraní .NET Framework obě musí podporovat protokol TLS 1.2.

**Požadavky na operační systém na podporu protokolu TLS 1.2**

Pokud chcete povolit nebo opětovné povolení TLS 1.2 a/nebo protokolu TLS 1.1 v systému, který je podporuje, najdete v části [zabezpečení TLS (Transport Layer), nastavení registru](/windows-server/security/tls/tls-registry-settings).

| **OS** | **Podpora protokolu TLS 1.2** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | Podporované a ve výchozím nastavení povolené. |
| Windows 8.1</br>Windows Server 2012 R2 | Podporované a ve výchozím nastavení povolené. |
| Windows 8.0</br>Windows Server 2012 | Podporované a ve výchozím nastavení povolené. |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | Podporované, ale není povoleno ve výchozím nastavení. Najdete v článku [zabezpečení TLS (Transport Layer), nastavení registru](/windows-server/security/tls/tls-registry-settings) webovou stránku Podrobnosti o tom, jak povolit TLS 1.2. |
| Windows Server 2008 | Podpora protokolu TLS 1.2 a protokolu TLS 1.1 vyžaduje aktualizaci. V tématu [aktualizace přidání podpory pro protokoly TLS 1.1 a TLS 1.2 ve Windows Server 2008 SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Není podporováno. |

Informace, o který TLS/SSL jsou protokoly povolené ve výchozím nastavení v každé verzi systému Windows najdete v tématu [protokoly v TLS/SSL (Schannel SSP)](https://msdn.microsoft.com/library/windows/desktop/mt808159).

**Požadavky na podporu protokolu TLS 1.2 pro rozhraní .NET Framework 3.5**

Tato tabulka ukazuje aktualizace operačního systému, že budete potřebovat pro podporu protokolu TLS 1.2 v rozhraní .NET Framework 3.5. Doporučujeme že použít všechny aktualizace operačního systému.

| **OS** | **Minimální aktualizace, které jsou potřeba k podpoře protokolu TLS 1.2 v rozhraní .NET Framework 3.5** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | [Kumulativní aktualizace pro Windows 10 verzi 1511 a Windows Server 2016 Technical Preview 4: 10. května 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1</br>Windows Server 2012 R2 | [Podpora TLS systému výchozí verze součástí rozhraní .NET Framework 3.5 ve Windows 8.1 a Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0</br>Windows Server 2012 | [Podpora TLS systému výchozí verze součástí rozhraní .NET Framework 3.5 v systému Windows Server 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | [Podpora TLS systému výchozí verze součástí rozhraní .NET Framework 3.5.1 na Windows 7 SP1 a Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Podpora TLS systému výchozí verze součástí rozhraní .NET Framework 2.0 SP2 v systému Windows Vista SP2 a Server 2008 SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Nepodporováno |

## <a name="azure-cloud-services"></a>Cloudové služby Azure

Pokud používáte [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) webové a pracovní role hostování a spuštění aplikace, existují některé aspekty, které je nutné vzít v úvahu pro podporu protokolu TLS 1.2.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>Rozhraní .NET framework 4.7 není nainstalován na Azure hostovaného operačního systému ve výchozím nastavení

Nejnovější verze nainstalovány v nejnovější verzi Azure hostovaného operačního systému rodiny 5 (Windows Server 2016) je 4.6.2. Na každém hostovaného operačního systému Azure nainstalovaných verzí rozhraní .NET Framework, najdete v sekci [verze hostovaného operačního systému Azure a kompatibilních sad SDK](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Pokud aplikace cílí na verzi rozhraní .NET Framework, která není k dispozici na verzi Azure hostovaného operačního systému, budete muset nainstalovat sami. V tématu [instalaci rozhraní .NET na Azure Cloud Service role](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Pokud framework instalace vyžaduje restartování, může také restartovat službu role před přechodem do stavu Připraveno.

### <a name="azure-guest-os-registry-settings"></a>Nastavení registru Azure hostovaného operačního systému

Pro bitovou kopii operačního systému hosta Azure [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) již `SchUseStrongCrypto` klíče registru nastavte na hodnotu 1. Další informace najdete v tématu [SchUseStrongCrypto](#schusestrongcrypto).

Nastavte [SystemDefaultTlsVersions](#systemdefaulttlsversions) klíč registru na 1. V tématu [konfigurace zabezpečení pomocí registru systému Windows](#configuring-security-via-the-windows-registry).
