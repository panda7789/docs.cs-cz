---
title: Osvědčené postupy zabezpečení transportní vrstvy (TLS) s rozhraním .NET Framework
description: Popisuje osvědčené postupy pomocí zabezpečení transportní vrstvy (TLS) s rozhraním .NET Framework
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
ms.openlocfilehash: 81ac469f75f925ea00c02ff94ade0e8793e7efff
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546708"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Osvědčené postupy zabezpečení transportní vrstvy (TLS) s rozhraním .NET Framework

Protokol TLS (Transport Layer Security) je oborový standard, který pomáhá chránit soukromí informací sdělovaných prostřednictvím Internetu. [TLS 1.2](https://tools.ietf.org/html/rfc5246) je standard, který poskytuje vylepšení zabezpečení oproti předchozím verzím. TLS 1.2 bude nakonec nahrazen nejnovějším uvolněným standardem [TLS 1.3,](https://tools.ietf.org/html/rfc8446) který je rychlejší a má lepší zabezpečení. Tento článek představuje doporučení k zabezpečení aplikací rozhraní .NET Framework, které používají protokol TLS.

Chcete-li zajistit, aby aplikace rozhraní .NET Framework zůstaly zabezpečené, verze TLS by **neměla** být pevně zakódována. Aplikace rozhraní .NET Framework by měly používat verzi TLS, kterou podporuje operační systém (OS).

Tento dokument cílí na vývojáře, kteří jsou:

- Přímo pomocí <xref:System.Net> api (například <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType>a).
- Přímo pomocí wcf klientů <xref:System.ServiceModel?displayProperty=nameWithType> a služeb pomocí oboru názvů.

Doporučený postup:

- Cílte na rozhraní .NET Framework 4.7 nebo novější verze ve vašich aplikacích. Cíl .NET Framework 4.7.1 nebo novější verze v aplikacích WCF.
- Nezadávejte verzi TLS. Nakonfigurujte kód tak, aby operační systém mohl rozhodovat o verzi TLS.
- Proveďte důkladný audit kódu a ověřte, že nezadáváte verzi TLS nebo SSL.

Když vaše aplikace umožní operačnímu systému zvolit verzi TLS:

- Automaticky využívá nové protokoly přidané v budoucnu, například TLS 1.3.
- Operační ho zablokuje protokoly, u kterých se zjistí, že nejsou zabezpečené.

Část [Auditování kódu a provádění změn kódu](#audit-your-code-and-make-code-changes) zahrnuje auditování a aktualizaci kódu.

Tento článek vysvětluje, jak povolit nejsilnější zabezpečení, které je k dispozici pro verzi rozhraní .NET Framework, na kterou vaše aplikace cílí a na které běží. Když aplikace explicitně nastaví protokol zabezpečení a verzi, odhlásí se z jakékoli jiné alternativy a odhlásí se z rozhraní .NET Framework a výchozího chování operačního systému. Pokud chcete, aby vaše aplikace mohla vyjednat připojení TLS 1.2, explicitně nastavení na nižší verzi TLS zabrání připojení TLS 1.2.

Pokud se nemůžete vyhnout hardcoding verze protokolu, důrazně doporučujeme zadat TLS 1.2. Pokyny k identifikaci a odebrání závislostí TLS 1.0 si stáhněte dokument white [paper řešení problému TLS 1.0.](https://www.microsoft.com/download/details.aspx?id=55266)

WCF podporuje TLS1.0, 1.1 a 1.2 jako výchozí v rozhraní .NET Framework 4.7. Počínaje rozhraním .NET Framework 4.7.1 je wcf výchozí verze nakonfigurovaná operačním systémem. Pokud je aplikace explicitně nakonfigurována pomocí `SslProtocols.None`aplikace , wcf používá výchozí nastavení operačního systému při použití přenosu NetTcp.

Můžete klást otázky týkající se tohoto dokumentu v github problém [zabezpečení transportní vrstvy (TLS) osvědčené postupy s rozhraním .NET Framework](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Auditování kódu a provádění změn kódu

U ASP.NET aplikací `<system.web><httpRuntime targetFramework>` zkontrolujte prvek _web.config_ a ověřte, zda používáte zamýšlenou verzi rozhraní .NET Framework.

Informace o formulářích Windows a dalších aplikacích najdete v [tématu Postup: Cílení na verzi rozhraní .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).

V následujících částech ověřte, že nepoužíváte konkrétní verzi TLS nebo SSL.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Pokud vaše aplikace cílí na rozhraní .NET Framework 4.7 nebo novější verze

Následující části ukazují, jak ověřit, že nepoužíváte konkrétní verzi TLS nebo SSL.

### <a name="for-http-networking"></a>Pro sítě HTTP

<xref:System.Net.ServicePointManager>, pomocí rozhraní .NET Framework 4.7 a novějších verzí, použije výchozí protokol zabezpečení nakonfigurovaný v os. Chcete-li získat výchozí volbu operačního systému, pokud <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> je to možné, nenastavovat hodnotu vlastnosti, která je výchozí . <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>

Vzhledem <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> k <xref:System.Net.ServicePointManager> tomu, že nastavení způsobí použití výchozího protokolu zabezpečení nakonfigurovaného operačním systémem, může aplikace běžet odlišně v závislosti na operačním systému, na který je spuštěn. Například Windows 7 SP1 používá TLS 1.0, zatímco Windows 8 a Windows 10 používají TLS 1.2.

Zbývající část tohoto článku není relevantní při cílení na rozhraní .NET Framework 4.7 nebo novější verze pro sítě HTTP.

### <a name="for-tcp-sockets-networking"></a>Pro sítě tcp soketů

<xref:System.Net.Security.SslStream>, pomocí rozhraní .NET Framework 4.7 a novějších verzí, je ve výchozím nastavení nastaven operační systém a vybere nejlepší protokol zabezpečení a verzi. Chcete-li získat výchozí os nejlepší volbou, pokud je to <xref:System.Net.Security.SslStream> možné, <xref:System.Security.Authentication.SslProtocols> nepoužívejte metodu přetížení, které trvat explicitní parametr. V opačném <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>případě předavte . Doporučujeme, abyste nepoužívali <xref:System.Security.Authentication.SslProtocols.Default>; vynutí `SslProtocols.Default` použití SSL 3.0 /TLS 1.0 a zabrání TLS 1.2.

Nenastavovat hodnotu <xref:System.Net.ServicePointManager.SecurityProtocol> vlastnosti (pro sítě HTTP).

Nepoužívejte přetížení <xref:System.Net.Security.SslStream> metody, které trvat <xref:System.Security.Authentication.SslProtocols> explicitní parametr (pro tcp sokety sítě). Když znovu zacílíte na rozhraní .NET Framework 4.7 nebo novější verze, budete se budete dodržovat doporučení doporučených postupů.

Zbývající část tohoto tématu není relevantní při cílení na rozhraní .NET Framework 4.7 nebo novější verze pro sítě TCP sockets.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Pro přenos WCF TCP pomocí zabezpečení přenosu s pověřeními certifikátu

WCF používá stejný síťový zásobník jako zbytek rozhraní .NET Framework.

Pokud cílíte na 4.7.1, wcf je nakonfigurován tak, aby operační systém zvolit nejlepší protokol zabezpečení ve výchozím nastavení, pokud explicitně nakonfigurován:

- V konfiguračním souboru aplikace.
- **Nebo**v aplikaci ve zdrojovém kódu.

Ve výchozím nastavení je rozhraní .NET Framework 4.7 a novější verze nakonfigurovány pro použití tls 1.2 a umožňují připojení pomocí TLS 1.1 nebo TLS 1.0. Nakonfigurujte WCF tak, aby operační systém mohl zvolit <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>nejlepší protokol zabezpečení konfigurací vazby pro použití . To lze nastavit <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>na . `SslProtocols.None`lze přistupovat <xref:System.ServiceModel.NetTcpSecurity.Transport>z . `NetTcpSecurity.Transport`lze přistupovat <xref:System.ServiceModel.NetTcpBinding.Security>z .

Pokud používáte vlastní vazbu:

- Nakonfigurujte wcf tak, aby operační <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> systém <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>mohl zvolit nejlepší protokol zabezpečení nastavením použití .
- **Nebo** nakonfigurujte protokol `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`používaný s konfigurační cestou .

Pokud **nepoužíváte** vlastní vazbu **a** nastavujete vazbu WCF pomocí konfigurace, nastavte `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`protokol používaný s konfigurační cestou .

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Pro zabezpečení zpráv WCF s pověřeními certifikátu

Rozhraní .NET Framework 4.7 a novější verze ve <xref:System.Net.ServicePointManager.SecurityProtocol> výchozím nastavení používá protokol zadaný ve vlastnosti. Když [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` je `true`nastavena na , WCF zvolí nejlepší protokol, až TLS 1.0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Pokud vaše aplikace cílí na verzi rozhraní .NET Framework starší než 4.7

Auditujte kód, abyste ověřili, že nenastavujete konkrétní verzi TLS nebo SSL pomocí následujících částí:

### <a name="for-net-framework-46---462-and-not-wcf"></a>Pro rozhraní .NET Framework 4.6 - 4.6.2 a ne wcf

`DontEnableSystemDefaultTlsVersions` `AppContext` Nastavte přepínač `false`na . Viz [Konfigurace zabezpečení pomocí přepínačů AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>Pro WCF pomocí rozhraní .NET Framework 4.6 - 4.6.2 pomocí zabezpečení přenosu TCP s pověřeními certifikátu

Je nutné nainstalovat nejnovější opravy operačního systému. Viz [Aktualizace zabezpečení](#security-updates).

WCF framework automaticky vybere nejvyšší protokol, který je k dispozici až do TLS 1.2, pokud explicitně nenakonfigurujete verzi protokolu. Další informace naleznete v předchozí části [Pro přenos WCF TCP pomocí zabezpečení přenosu s pověřeními certifikátu](#wcf-tcp-cert).

### <a name="for-net-framework-35---452-and-not-wcf"></a>Pro rozhraní .NET Framework 3.5 - 4.5.2 a ne wcf

Doporučujeme upgradovat aplikaci na .NET Framework 4.7 nebo novější verze. Pokud nelze provést upgrade, postupujte podle následujících kroků. V určitém okamžiku v budoucnu může selhat vaše aplikace, dokud upgradovat na rozhraní .NET Framework 4.7 nebo novější verze.

Nastavte klíče registru [SchUseStrongCrypto](#schusestrongcrypto) a [SystemDefaultTlsVersions](#systemdefaulttlsversions) na hodnotu 1. Viz [Konfigurace zabezpečení prostřednictvím registru systému Windows](#configuring-security-via-the-windows-registry). Rozhraní .NET Framework verze 3.5 podporuje příznak pouze v `SchUseStrongCrypto` případě, že je předána explicitní hodnota TLS.

Pokud používáte rozhraní .NET Framework 3.5, je třeba nainstalovat opravu hot patch tak, aby TLS 1.2 může být určen programem:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Kumulativní spolehlivost HR-1605 – podpora výchozích verzí systému TLS zahrnutých v rozhraní .NET Framework 3.5.1 v systémech Windows 7 SP1 a Server 2008 R2 SP1 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Kumulativní spolehlivost HR-1605 – podpora výchozích verzí systému TLS zahrnutých v rozhraní .NET Framework 3.5 v systému Windows Server 2012 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Kumulativní spolehlivost HR-1605 – podpora výchozích verzí systému TLS zahrnutých v rozhraní .NET Framework 3.5 v systémech Windows 8.1 a Windows Server 2012 R2 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | Kumulativní oprava hotfix 1605 3154521 pro rozhraní .NET Framework 4.5.2 a 4.5.1 v systému Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>Pro WCF pomocí rozhraní .NET Framework 3.5 - 4.5.2 pomocí zabezpečení přenosu TCP s pověřeními certifikátu

Tyto verze wcf framework upevněny pro použití hodnot SSL 3.0 a TLS 1.0. Tyto hodnoty nelze změnit. Chcete-li používat tls 1.1 a 1.2, je nutné aktualizovat a znovu zacílit na rozhraní NET Framework 4.6 nebo novější verze.

## <a name="if-your-app-targets-net-framework-35"></a>Pokud vaše aplikace cílí na rozhraní .NET Framework 3.5

Pokud je nutné explicitně nastavit protokol zabezpečení namísto toho, aby `SecurityProtocolTypeExtensions` rozhraní `SslProtocolsExtension` .NET nebo operační systém vybralo protokol zabezpečení, přidejte a vyčtete do kódu. `SecurityProtocolTypeExtensions`a `SslProtocolsExtension` zahrnout `Tls12`hodnoty `Tls11`pro `SystemDefault` , a hodnotu. Další informace naleznete [v tématu Podpora výchozích verzí systému TLS zahrnutých v rozhraní .NET Framework 3.5 v systémech Windows 8.1 a Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Konfigurace zabezpečení pomocí přepínačů AppContext (pro rozhraní .NET Framework 4.6 nebo novější verze)

Přepínače [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) popsané v této části jsou relevantní, pokud vaše aplikace cílí nebo běží na rozhraní .NET Framework 4.6 nebo novější verze. Ať už ve výchozím nastavení, nebo jejich `false` nastavením explicitně, přepínače by měly být pokud je to možné. Pokud chcete nakonfigurovat zabezpečení pomocí jednoho nebo obou přepínačů, nezadávejte v kódu hodnotu protokolu zabezpečení. by to přepsalo přepínač (přepínače).

Přepínače mají stejný účinek, ať už<xref:System.Net.ServicePointManager>provádíte síť HTTP<xref:System.Net.Security.SslStream>( ) nebo síť soketů TCP ( ).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Hodnota for `false` `Switch.System.Net.DontEnableSchUseStrongCrypto` způsobí, že vaše aplikace používá silnou kryptografii. Hodnota `false` for `DontEnableSchUseStrongCrypto` používá bezpečnější síťové protokoly (TLS 1.2, TLS 1.1 a TLS 1.0) a blokuje protokoly, které nejsou zabezpečené. Další informace naleznete [v tématu příznak SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag). Hodnota `true` zakáže silnou kryptografii pro vaši aplikaci.

Pokud vaše aplikace cílí na rozhraní .NET Framework 4.6 nebo novější verze, tento přepínač je výchozí na `false`. To je bezpečné výchozí nastavení, které doporučujeme. Pokud vaše aplikace běží na rozhraní .NET Framework 4.6, ale `true`cílí na starší verzi, přepne výchozí na . V takovém případě byste jej `false`měli explicitně nastavit na .

`DontEnableSchUseStrongCrypto`by měl mít `true` hodnotu pouze v případě, že potřebujete připojit ke starším službám, které nepodporují silnou kryptografii a nelze je upgradovat.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Hodnota for `false` `Switch.System.Net.DontEnableSystemDefaultTlsVersions` způsobí, že vaše aplikace umožní operačnímu systému zvolit protokol. Hodnota způsobí, `true` že vaše aplikace používat protokoly vybrané rozhraním .NET Framework.

Pokud vaše aplikace cílí na rozhraní .NET Framework 4.7 nebo novější verze, tento přepínač je výchozí na `false`. To je bezpečné výchozí, které doporučujeme. Pokud vaše aplikace běží na rozhraní .NET Framework 4.7 nebo novější verze, `true`ale cíle starší verze, přepínač výchozí na . V takovém případě byste jej `false`měli explicitně nastavit na .

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Hodnota for `false` `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` způsobí, že aplikace použít `ServicePointManager.SecurityProtocols` hodnotu definovanou v aplikaci pro zabezpečení zpráv pomocí pověření certifikátu. Hodnota `true` používá nejvyšší dostupný protokol až tls1.0

U aplikací, které cílí na rozhraní .NET Framework `false`4.7 a novější verze, je tato hodnota výchozí na . U aplikací, které cílí na rozhraní .NET Framework `true`4.6.2 a starší, je tato hodnota výchozí pro rozhraní .

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Hodnota `false` pro `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` nastaví výchozí konfiguraci, aby operační systém mohl zvolit protokol. Hodnota nastaví `true` výchozí hodnotu na nejvyšší dostupný protokol, až tls1.2.

U aplikací, které cílí na rozhraní .NET Framework 4.7.1 a novější verze, je tato hodnota výchozí . `false` U aplikací, které cílí na rozhraní .NET `true`Framework 4.7 a starší, je tato hodnota výchozí pro .

Další informace o protokolech TLS naleznete v [tématu Mitigation: TLS Protocols](../migration-guide/mitigation-tls-protocols.md). Další informace `AppContext` o přepínačích naleznete v tématu [`<AppContextSwitchOverrides> Element`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Konfigurace zabezpečení prostřednictvím registru systému Windows

> [!WARNING]
> Nastavení klíčů registru ovlivní všechny aplikace v systému. Tuto možnost použijte pouze v případě, že máte plně pod kontrolou počítač a můžete řídit změny v registru.

Pokud nastavení jednoho `AppContext` nebo obou přepínačů není možné, můžete řídit protokoly zabezpečení, které vaše aplikace používá, pomocí klíčů registru systému Windows popsaných v této části. Pokud aplikace běží v rozhraní .NET Framework 4.5.2 nebo starších verzích nebo pokud konfigurační soubor nelze upravit, nemusí být možné použít jeden nebo oba `AppContext` přepínače. Pokud chcete nakonfigurovat zabezpečení s registrem, nezadávejte hodnotu protokolu zabezpečení v kódu; tím přepíše nastavení registru.

Názvy klíčů registru jsou podobné názvům `AppContext` odpovídajících přepínačů, ale bez `DontEnable` předřazeného názvu. `AppContext` Přepínač `DontEnableSchUseStrongCrypto` je například klíč registru s názvem [SchUseStrongCrypto](#schusestrongcrypto).

Tyto klíče jsou k dispozici ve všech verzích rozhraní .NET Framework, pro které je poslední oprava zabezpečení. Viz [Aktualizace zabezpečení](#security-updates).

Všechny níže popsané klíče registru mají stejný účinek, ať<xref:System.Net.ServicePointManager>už provádíte síť HTTP<xref:System.Net.Security.SslStream>( ) nebo síť soketů TCP ( ).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

Klíč `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` registru má hodnotu typu DWORD. Hodnota 1 způsobí, že vaše aplikace používá silnou kryptografii. Silná kryptografie používá bezpečnější síťové protokoly (TLS 1.2, TLS 1.1 a TLS 1.0) a blokuje protokoly, které nejsou zabezpečené. Hodnota 0 zakáže silnou kryptografii. Další informace naleznete [v tématu příznak SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag).

Pokud vaše aplikace cílí na rozhraní .NET Framework 4.6 nebo novější verze, tento klíč výchozí hodnotu 1. To je bezpečné výchozí, které doporučujeme. Pokud vaše aplikace cílí na rozhraní .NET Framework 4.5.2 nebo starší verze, výchozí hodnota klíče je 0. V takovém případě byste měli explicitně nastavit jeho hodnotu na 1.

Tento klíč by měl mít hodnotu 0 pouze v případě, že se potřebujete připojit ke starším službám, které nepodporují silnou kryptografii a nelze je upgradovat.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

Klíč `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` registru má hodnotu typu DWORD. Hodnota 1 způsobí, že vaše aplikace umožní operačnímu systému zvolit protokol. Hodnota 0 způsobí, že vaše aplikace používat protokoly vychýlává rozhraní .NET Framework.

`<VERSION>`musí být v4.0.30319 (pro rozhraní .NET Framework 4 a vyšší) nebo v2.0.50727 (pro rozhraní .NET Framework 3.5).

Pokud vaše aplikace cílí na rozhraní .NET Framework 4.7 nebo novější verze, výchozí hodnota tohoto klíče je na hodnotu 1. To je bezpečné výchozí, které doporučujeme. Pokud vaše aplikace cílí na rozhraní .NET Framework 4.6.1 nebo starší verze, výchozí hodnota klíče je 0. V takovém případě byste měli explicitně nastavit jeho hodnotu na 1.

Další informace najdete [v tématu Kumulativní aktualizace pro Windows 10 verze 1511 a Windows Server 2016 Technical Preview 4: 10.](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016)

Další informace pomocí rozhraní .NET Framework 3.5.1 naleznete [v tématu Podpora výchozích verzí systému TLS zahrnutých v rozhraní .NET Framework 3.5.1 v systémech Windows 7 SP1 a Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Následující _. REG_ soubor nastaví klíče registru a jejich varianty na jejich nejbezpečnější hodnoty:

```text
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

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Konfigurace protokolů Schannel v registru systému Windows

Registr můžete použít pro jemně odstupňovanou kontrolu nad protokoly, které váš klient nebo serverová aplikace vyjednává. Síť vaší aplikace prochází schannelem (což je jiný název pro [Zabezpečený kanál](/windows/desktop/SecAuthN/secure-channel). Konfigurací `Schannel`můžete nakonfigurovat chování aplikace.

Začněte `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` s klíčem registru. Pod tímto klíčem můžete vytvořit libovolné `SSL 2.0` `SSL 3.0`podklíče `TLS 1.1`v `TLS 1.2`sadě , , `TLS 1.0`a . Pod každým z těchto podklíčů můžete `Client` vytvořit `Server`podklíče a/nebo . V `Client` `Server`části a , můžete `DisabledByDefault` vytvořit hodnoty DWORD (0 nebo 1) a `Enabled` (0 nebo 0xFFFFFFFF).

## <a name="the-sch_use_strong_crypto-flag"></a><a name="the-sch_use_strong_crypto-flag"></a>Vlajka SCH_USE_STRONG_CRYPTO

Pokud je povoleno (ve výchozím `AppContext` nastavení přepínačem nebo registrem systému Windows), rozhraní .NET Framework používá `SCH_USE_STRONG_CRYPTO` příznak, když aplikace požaduje protokol zabezpečení TLS. Příznak `SCH_USE_STRONG_CRYPTO` lze povolit ve výchozím `AppContext` nastavení, pomocí přepínače nebo registru. Operační systém předá `Schannel`příznak pokyn k zakázání známé slabé kryptografické algoritmy, šifrovací sady a verze protokolu TLS/SSL, které mohou být jinak povoleny pro lepší interoperabilitu. Další informace naleznete v tématu:

- [Zprostředkovatel Schannel](/windows/desktop/SecAuthN/secure-channel)
- [SCHANNEL_CRED struktura](/windows/win32/api/schannel/ns-schannel-schannel_cred)

Příznak `SCH_USE_STRONG_CRYPTO` je také `Schannel` předán, pokud `Tls` explicitně používáte (TLS 1.0) `Tls11` <xref:System.Net.SecurityProtocolType> nebo <xref:System.Security.Authentication.SslProtocols> `Tls12` výčtové hodnoty nebo .

## <a name="security-updates"></a>Aktualizace zabezpečení

Doporučené postupy v tomto článku závisí na nejnovějšíaktualizace zabezpečení jsou nainstalovány. Tyto aktualizace zahrnují možnost používat pokročilé funkce rozhraní .NET Framework 4.7 a novější. Poslední aktualizace zabezpečení jsou důležité, pokud vaše aplikace běží na rozhraní .NET Framework 4.7 a novější verze (i v případě, že se zaměřuje na starší verzi).

Chcete-li aktualizovat rozhraní .NET Framework, aby operační systém mohl zvolit nejlepší verzi tls, kterou chcete použít, musíte nainstalovat alespoň:

- .NET [Framework srpen 2017 Náhled kvality Kumulativní](https://devblogs.microsoft.com/dotnet/net-framework-august-2017-preview-of-quality-rollup/).
- **Nebo** [.NET Framework září 2017 Kumulativní zabezpečení a kvality](https://devblogs.microsoft.com/dotnet/net-framework-september-2017-security-and-quality-rollup/).

Viz také:

- [Verze a závislosti rozhraní .NET Framework](../migration-guide/versions-and-dependencies.md)
- [Postup: Určení, které verze rozhraní .NET Framework jsou nainstalovány](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>Podpora protokolu TLS 1.2

Aby vaše aplikace vyjednala TLS 1.2, operační systém i verze rozhraní .NET Framework musí podporovat TLS 1.2.

**Požadavky na operační systém pro podporu protokolu TLS 1.2**

Chcete-li povolit nebo znovu povolit protokol TLS 1.2 a/nebo TLS 1.1 v systému, který je podporuje, přečtěte si informace o [nastavení registru TLS (Transport Layer Security).](/windows-server/security/tls/tls-registry-settings)

| **OS** | **Podpora pro TLS 1.2** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | Podporováno a ve výchozím nastavení povoleno. |
| Windows 8.1<br>Windows Server 2012 R2 | Podporováno a ve výchozím nastavení povoleno. |
| Windows 8.0<br>Windows Server 2012 | Podporováno a ve výchozím nastavení povoleno. |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | Podporováno, ale ve výchozím nastavení není povoleno. Podrobnosti o povolení protokolu TLS 1.2 naleznete na webové stránce [nastavení registru TLS (Transport Layer Security).](/windows-server/security/tls/tls-registry-settings) |
| Windows Server 2008 | Podpora tls 1.2 a TLS 1.1 vyžaduje aktualizaci. Viz [Aktualizace, chcete-li přidat podporu pro TLS 1.1 a TLS 1.2 v systému Windows Server 2008 SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Není podporováno. |

Informace o tom, které protokoly TLS/SSL jsou ve výchozím nastavení povoleny v každé verzi systému Windows, naleznete [v tématu Protokoly v protokolu TLS/SSL (Schannel SSP)](/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).

**Požadavky pro podporu protokolu TLS 1.2 v rozhraní .NET Framework 3.5**

Tato tabulka zobrazuje aktualizaci operačního systému, kterou budete potřebovat k podpoře TLS 1.2 s rozhraním .NET Framework 3.5. Doporučujeme použít všechny aktualizace operačního systému.

| **OS** | **Minimální aktualizace potřebná pro podporu TLS 1.2 s rozhraním .NET Framework 3.5** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | [Kumulativní aktualizace pro Windows 10 verze 1511 a Windows Server 2016 Technical Preview 4: 10. května 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1<br>Windows Server 2012 R2 | [Podpora výchozích verzí systému TLS zahrnutých v rozhraní .NET Framework 3.5 v systémech Windows 8.1 a Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0<br>Windows Server 2012 | [Podpora výchozích verzí systému TLS zahrnutých v rozhraní .NET Framework 3.5 v systému Windows Server 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | [Podpora výchozích verzí systému TLS zahrnutých v rozhraní .NET Framework 3.5.1 v systémech Windows 7 SP1 a Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Podpora výchozích verzí systému TLS zahrnutých v rozhraní .NET Framework 2.0 SP2 v systémech Windows Vista SP2 a Server 2008 SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Nepodporuje se |
