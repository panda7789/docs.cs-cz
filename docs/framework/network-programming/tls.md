---
title: Zabezpečení TLS (Transport Layer) osvědčené postupy s použitím rozhraní .NET Framework
description: Popisuje osvědčené postupy zabezpečení TLS (Transport Layer) pomocí rozhraní .NET Framework
ms.date: 03/15/2018
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
ms.openlocfilehash: a421b73edc1dd90be53d301d12160d39abe78f90
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577716"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Zabezpečení TLS (Transport Layer) osvědčené postupy s použitím rozhraní .NET Framework

Protokol zabezpečení TLS (Transport Layer) je standardní navržená k ochraně soukromí informace přes Internet. [Protokol TLS 1.2](https://tools.ietf.org/html/rfc5246) je nejnovější vydanou standard a přináší oproti předchozím verzím vylepšení zabezpečení. Protokol TLS 1.2 nakonec se nahradí [TLS 1.3](https://tools.ietf.org/html/draft-ietf-tls-tls13-22). Tento článek představuje doporučení k zabezpečení aplikace rozhraní .NET Framework, které používají protokol TLS.

K zajištění toho, zůstaly zabezpečené aplikace rozhraní .NET Framework, verze protokolu TLS by **není** být pevně zakódované. Aplikace rozhraní .NET framework by měly používat protokol TLS verze, kterou podporuje operační systém (OS).

Tento dokument, zaměřuje vývojáři, kteří jsou:

- Přímo pomocí <xref:System.Net> rozhraní API (například <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- Klienti WCF a služby pomocí přímo pomocí <xref:System.ServiceModel?displayProperty=nameWithType> oboru názvů.
- Pomocí [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) webové a pracovní role pro hostování a spuštění aplikace. Zobrazit [Azure Cloud Services](#azure-cloud-services) oddílu.

Doporučujeme vám:

- Cílit na rozhraní .NET Framework 4.7 nebo novější verze na aplikace. Cílové rozhraní .NET Framework 4.7.1 nebo novější verze na aplikace WCF.
- Nezadávejte verze TLS. Konfigurace kódu umožňuje při rozhodování o TLS verze operačního systému.
- Proveďte audit důkladné kód pro ověření, že nejsou určení verze protokolu TLS nebo SSL.

Když vaše aplikace umožňuje operačního systému, zvolte verzi protokolu TLS:

- Automaticky využívá nové protokoly přidá v budoucnosti, jako je například TLS 1.3.
- Operační systém blokuje protokoly, které jsou zjištěny nechcete být bezpečné.

V části [auditu kódu a změny kódu](#audit-your-code-and-make-code-changes) pokrývá auditování a aktualizaci kódu.

Tento článek vysvětluje, jak povolit nejvyšší zabezpečení, které jsou k dispozici pro verzi rozhraní .NET Framework, zaměřuje a běží na vaší aplikace. Když aplikaci explicitně nastaví zabezpečení protokolu a verze, výslovný jiná možnost a požádá o mimo rozhraní .NET Framework a operační systém výchozí chování. Pokud chcete být schopni vyjednat protokol TLS 1.2 připojení vaší aplikace, explicitním nastavením na nižší verzi TLS brání připojení protokolu TLS 1.2.

Pokud se nelze vyhnout hardcoding verzi protokolu, důrazně doporučujeme, že zadáte TLS 1.2. Pokyny k identifikaci a odebrání závislostí protokolu TLS 1.0, stáhněte si [řešení problému TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266) dokument White Paper.

WCF podporuje protokol TLS 1.0, 1.1 a 1.2 jako výchozí hodnotou v rozhraní .NET Framework 4.7. Od verze rozhraní .NET Framework 4.7.1, výchozí hodnoty WCF v operačním systému nakonfigurovat verzi. Pokud aplikace explicitně nakonfigurovanou `SslProtocols.None`, WCF používá výchozí nastavení operačního systému při použití NetTcp přenosu.

Můžete klást otázky o tomto dokumentu v problém Githubu [zabezpečení TLS (Transport Layer) osvědčené postupy s použitím rozhraní .NET Framework](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Auditovat kódu a změny kódu

Pro aplikace ASP.NET, zkontrolujte `<system.web><httpRuntime targetFramework>` prvek _web.config_ k ověření, že používáte odpovídající verzi rozhraní .NET Framework.

Windows Forms a další aplikace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

Pomocí následujících částí k ověření, že nepoužíváte konkrétní verzi protokolu TLS nebo SSL.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Pokud vaše aplikace cílí na .NET Framework 4.7 nebo novější verze

Následující části vysvětlují, jak ověřit, že nepoužíváte konkrétní verzi protokolu TLS nebo SSL.

### <a name="for-http-networking"></a>Práce se sítí protokolu HTTP

<xref:System.Net.ServicePointManager>, pomocí rozhraní .NET Framework 4.7 a novějších verzích, výchozí hodnota je výběr nejlepší zabezpečení protokolu a verze operačního systému. Pokud chcete získat nejlepší volbou výchozí operační systém, pokud je to možné, nenastaví hodnotu pro <xref:System.Net.ServicePointManager.SecurityProtocol> vlastnost. Jinak ji nastavte <xref:System.Net.SecurityProtocolType.SystemDefault>.

Zbývající část tohoto článku není relevantní, při cílení na rozhraní .NET Framework 4.7 nebo novější verze HTTP sítě.

### <a name="for-tcp-sockets-networking"></a>Pro sítě sockety TCP

<xref:System.Net.Security.SslStream>, pomocí rozhraní .NET Framework 4.7 a novějších verzích, výchozí hodnota je výběr nejlepší zabezpečení protokolu a verze operačního systému. Pokud chcete získat nejlepší volbou výchozí operační systém, pokud je to možné, nepoužívejte přetížení metody <xref:System.Net.Security.SslStream> , které přebírají explicitní <xref:System.Security.Authentication.SslProtocols> parametru. Jinak předejte <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Doporučujeme vám, že nepoužíváte <xref:System.Security.Authentication.SslProtocols.Default>; nastavení `SslProtocols.Default` vynutí použití protokolu SSL 3.0 /TLS 1.0 a brání TLS 1.2.

Nenastavujte hodnotu <xref:System.Net.ServicePointManager.SecurityProtocol> vlastnost (pro HTTP sítě).

Nepoužívejte přetížení metody <xref:System.Net.Security.SslStream> , které přebírají explicitní <xref:System.Security.Authentication.SslProtocols> parametr (pro TCP sockety sítě). Pokud můžete změnit cílení aplikace na rozhraní .NET Framework 4.7 nebo novější verze, budete následující doporučení osvědčených postupů.

Zbývající část tohoto tématu není relevantní, při cílení na rozhraní .NET Framework 4.7 nebo novější verze pro protokol TCP sockets sítě.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Pro protokol TCP WCF přenosu pomocí zabezpečení přenosu pomocí přihlašovacích údajů k certifikátu

WCF používá jeden síťový zásobník jako v ostatních rozhraní .NET Framework.

Pokud se zaměřujete na 4.7.1, WCF nakonfigurována, aby umožňovala operačního systému a zvolit nejlepší protokol zabezpečení ve výchozím nastavení, pokud:

- V konfiguračním souboru aplikace.
- **Nebo**, v aplikaci ve zdrojovém kódu.

Ve výchozím nastavení .NET Framework 4.7 a novějších verzích je nakonfigurován pro použití protokolu TLS 1.2 a umožňuje připojení pomocí protokolu TLS 1.1 a TLS 1.0. Konfigurace WCF umožňuje operačního systému a zvolit nejlepší protokol zabezpečení tím, že nakonfigurujete použité vazby <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. To lze nastavit na <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. `SslProtocols.None` je přístupný z <xref:System.ServiceModel.NetTcpSecurity.Transport>. `NetTcpSecurity.Transport` je přístupný z <xref:System.ServiceModel.NetTcpBinding.Security>.

Pokud používáte vlastní vazby:

- Konfigurace WCF umožňuje operačního systému a vybrat nejlepší protokol zabezpečení nastavením <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> používat <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>.
- **Nebo** nakonfigurovat protokol použitý s konfigurační cestou `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`.

Pokud jste **není** použití vlastní vazby **a** nastavujete vaše vazby WCF pomocí konfigurace, nastavte protokol použitý s konfigurační cestou `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Pro zabezpečení zpráv WCF pomocí přihlašovacích údajů k certifikátu

Rozhraní .NET framework 4.7 a novějších ve výchozím nastavení používá protokol uvedený v poli <xref:System.Net.ServicePointManager.SecurityProtocol> vlastnost. Když [Uselegacyaccessibilityfeatures.n](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` je nastavena na `true`, WCF vybere nejlepší protokol až TLS 1.0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Pokud svojí aplikací cílíte na verzi rozhraní .NET Framework starší než 4.7

Auditovat váš kód pro ověření, že nejsou nastavení na konkrétní verzi protokolu TLS nebo SSL pomocí následující části:

### <a name="for-net-framework-46---462-and-not-wcf"></a>Pro rozhraní .NET Framework 4.6 – 4.6.2 a ne WCF

Nastavte `DontEnableSystemDefaultTlsVersions` `AppContext` přepnout na `false`. Zobrazit [konfigurace zabezpečení prostřednictvím přepínačů AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>WCF pomocí rozhraní .NET Framework 4.6 – 4.6.2 pomocí zabezpečení přenosu protokolu TCP s přihlašovacími údaji certifikátu

Je nutné nainstalovat nejnovější opravy operačního systému. Zobrazit [aktualizace zabezpečení](#security-updates).

Rozhraní WCF automaticky vybere nejvyšší protokol, který je k dispozici až po TLS 1.2, pokud explicitně nenakonfigurujete verze protokolu. Další informace najdete v předchozí části [přenos pro protokol TCP WCF pomocí zabezpečení přenosu pomocí přihlašovacích údajů k certifikátu](#wcf-tcp-cert).

### <a name="for-net-framework-35---452-and-not-wcf"></a>Pro rozhraní .NET Framework 3.5 – 4.5.2 a ne WCF

Doporučujeme, abyste že upgrade vaší aplikace na rozhraní .NET Framework 4.7 nebo novější verze. Pokud nemůžete upgradovat, proveďte následující kroky. V určitém okamžiku v budoucnu, vaší aplikací se pravděpodobně nezdaří dokud neprovedete upgrade na rozhraní .NET Framework 4.7 nebo novější verze.

Nastavte [SchUseStrongCrypto](#schusestrongcrypto) a [SystemDefaultTlsVersions](#systemdefaulttlsversions) klíče registru na 1. Zobrazit [konfigurace zabezpečení prostřednictvím registru Windows](#configuring-security-via-the-windows-registry). Podporuje rozhraní .NET Framework verze 3.5 `SchUseStrongCrypto` příznak, pouze pokud je předán explicitní hodnotu TLS.

Pokud spustíte v rozhraní .NET Framework 3.5, potřebujete aktivní opravu nainstalovali, tak, aby TLS 1.2, je možné zadat tak váš program:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Spolehlivost kumulativní HR-1605 – podpora protokolu TLS systému výchozí verzí zahrnuty v rozhraní .NET Framework 3.5.1 na Windows 7 SP1 a Server 2008 R2 SP1 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Spolehlivost kumulativní HR-1605 – podpora pro verze výchozí společnosti TLS systému zahrnuty v rozhraní .NET Framework 3.5 ve Windows serveru 2012 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Spolehlivost kumulativní HR-1605 – podpora protokolu TLS systému výchozí verzí je součástí rozhraní .NET Framework 3.5 ve Windows 8.1 a Windows Server 2012 R2 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | Kumulativní oprava Hotfix 1605 3154521 pro rozhraní .NET Framework 4.5.2 a 4.5.1 ve Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>WCF pomocí rozhraní .NET Framework 3.5 – 4.5.2 pomocí zabezpečení přenosu protokolu TCP s přihlašovacími údaji certifikátu

Tyto verze architektury WCF jsou pevně nastavená na použití hodnoty SSL 3.0 a TLS 1.0. Tyto hodnoty nelze změnit. Musíte aktualizovat a změnit cílení na NET Framework 4.6 nebo novější verze protokolu TLS 1.1 a 1.2.

## <a name="if-your-app-targets-net-framework-35"></a>Pokud svojí aplikací cílíte na rozhraní .NET Framework 3.5

Pokud musíte explicitně nastavit protokol zabezpečení místo rozhraní .NET framework nebo operační systém vyberte protokol zabezpečení, přidejte `SecurityProtocolTypeExtensions` a `SslProtocolsExtension` výčty do vašeho kódu. `SecurityProtocolTypeExtensions` a `SslProtocolsExtension` zahrnují hodnoty `Tls12`, `Tls11`a `SystemDefault` hodnotu. Zobrazit [podpora verzí výchozí společnosti TLS systému zahrnuty v rozhraní .NET Framework 3.5 on Windows 8.1 a Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Konfigurace zabezpečení prostřednictvím AppContext přepínače (pro rozhraní .NET Framework 4.6 nebo novější verze)

[AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepínače, které jsou popsané v této části jsou relevantní Pokud vaší aplikaci zaměřuje nebo spuštění v rozhraní .NET Framework 4.6 nebo novější verze. Ať už ve výchozím nastavení, nebo když je explicitně nastavíte, přepínače by měla být `false` Pokud je to možné. Pokud chcete provést konfiguraci zabezpečení prostřednictvím jednoho nebo obou přepínačů, potom nezadávejte hodnotu protokolu zabezpečení ve vašem kódu; To uděláte tak, by se mělo přepsat vypínače.

Přepínače mají stejný účinek, ať už provádíte sítě protokolu HTTP (<xref:System.Net.ServicePointManager>) nebo TCP sockets sítě (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Hodnota `false` pro `Switch.System.Net.DontEnableSchUseStrongCrypto` způsobí, že vaše aplikace bude moct používat silné šifrování. Hodnota `false` pro `DontEnableSchUseStrongCrypto` používá bezpečnější síťové protokoly (TLS 1.2, protokol TLS 1.1 a TLS 1.0) a blokuje protokoly, které nejsou zabezpečeny. Další informace najdete v tématu [The SCH_USE_STRONG_CRYPTO příznak](#the-schusestrongcrypto-flag). Hodnota `true` zakáže silné šifrování pro vaši aplikaci.

Pokud svojí aplikací cílíte na rozhraní .NET Framework 4.6 nebo novější verze, tento přepínač výchozí `false`. To je zabezpečené výchozí, což doporučujeme. Pokud vaše aplikace běží na rozhraní .NET Framework 4.6, ale zaměřuje na starší verzi, přepínač výchozí `true`. V takovém případě byste měli explicitně nastavit ho na `false`.

`DontEnableSchUseStrongCrypto` by měl mít pouze hodnotu `true` potřebujete připojení k starších verzí služeb, které nepodporují silného šifrování a proto nejde upgradovat.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Hodnota `false` pro `Switch.System.Net.DontEnableSystemDefaultTlsVersions` způsobí, že vaši aplikaci povolit operačnímu systému, aby zvolit protokol. Hodnota `true` způsobí, že vaše aplikace bude moct používat protokoly prodlouží rozhraní .NET Framework.

Pokud vaše aplikace cílí na .NET Framework 4.7 nebo novější verze, tento přepínač výchozí `false`. To je zabezpečené, doporučujeme, abyste výchozí. Pokud vaše aplikace běží na rozhraní .NET Framework 4.7 nebo novější verze, ale zaměřuje na starší verzi, přepínač výchozí `true`. V takovém případě byste měli explicitně nastavit ho na `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Hodnota `false` pro `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` způsobí, že vaše aplikace použít hodnotu definovanou v `ServicePointManager.SecurityProtocols` pro zabezpečení zpráv pomocí přihlašovacích údajů pro certifikát. Hodnota `true` používá nejvyšší protokol, který je k dispozici, až protokol TLS 1.0

Pro aplikace cílené na .NET Framework 4.7 a novějších verzích, výchozí hodnota je `false`. Pro aplikace cílené na rozhraní .NET Framework 4.6.2 a starší, výchozí hodnota je `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Hodnota `false` pro `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` nastaví výchozí konfigurace umožňuje zvolit protokol operačního systému. Hodnota `true` nastaví výchozí k dispozici, až TLS1.2 nejvyšší protokolu.

Pro aplikace cílené na rozhraní .NET Framework 4.7.1 a novějších verzích, výchozí hodnota je `false`. Pro aplikace cílené na rozhraní .NET Framework 4.7 a starších, výchozí hodnota je `true`.

Další informace o protokoly TLS najdete v tématu [omezení rizik: protokoly TLS](../migration-guide/mitigation-tls-protocols.md). Další informace o `AppContext` přepínače, naleznete v tématu [ `<AppContextSwitchOverrides> Element` ](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Konfigurace zabezpečení prostřednictvím registru Windows

> [!WARNING]
> Nastavení klíče registru ovlivní všechny aplikace v systému. Tuto možnost použijte pouze v případě počítače plně pod kontrolou a můžete řídit změny do registru.

Pokud nastavení jednoho nebo obou `AppContext` přepínače nejsou možnost, můžete kontrolovat protokoly zabezpečení, které vaše aplikace používá s klíči registru Windows, které jsou popsané v této části. Nebudete moct používat jeden nebo oba `AppContext` přepne, pokud se svojí aplikací cílíte na verzi rozhraní .NET Framework starší než 4.6, nebo nelze upravit konfigurační soubor. Pokud chcete provést konfiguraci zabezpečení s registrem, potom nezadávejte hodnotu protokolu zabezpečení ve vašem kódu; To uděláte tak, by se mělo přepsat registru.

Názvy klíčů registru se podobně jako názvy odpovídajících `AppContext` ale bez přepínače `DontEnable` přidáno před název. Například `AppContext` přepnout `DontEnableSchUseStrongCrypto` klíč registru se nazývá [SchUseStrongCrypto](#schusestrongcrypto).

Tyto klíče jsou k dispozici ve všech verzích rozhraní .NET Framework, pro které je nejnovější úroveň opravy zabezpečení. Zobrazit [aktualizace zabezpečení](#security-updates).

Všechny klíče registru popsané níže mají stejný účinek, ať už provádíte sítě protokolu HTTP (<xref:System.Net.ServicePointManager>) nebo TCP sockets sítě (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` Klíč registru obsahuje hodnotu typu DWORD. Hodnotu 1 způsobí, že vaše aplikace bude moct používat silné šifrování. Silné šifrování používá bezpečnější síťové protokoly (TLS 1.2, protokol TLS 1.1 a TLS 1.0) a blokuje protokoly, které nejsou zabezpečeny. Hodnota 0 zakáže silného šifrování. Další informace najdete v tématu [The SCH_USE_STRONG_CRYPTO příznak](#the-schusestrongcrypto-flag).

Pokud svojí aplikací cílíte na rozhraní .NET Framework 4.6 nebo novější verze, výchozí hodnota tohoto klíče na hodnotu 1. To je zabezpečené, doporučujeme, abyste výchozí. Pokud vaše aplikace běží na rozhraní .NET Framework 4.6, ale zaměřuje na starší verzi, pak klíč výchozí hodnota 0. V takovém případě byste měli explicitně nastavit její hodnotu na 1.

Tento klíč by měl mít pouze hodnotu 0, pokud je potřeba připojit k starších verzí služeb, které nepodporují silného šifrování a proto nejde upgradovat.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` Klíč registru obsahuje hodnotu typu DWORD. Hodnotu 1 způsobí, že vaši aplikaci povolit operačnímu systému, aby zvolit protokol. Hodnota 0 způsobí, že vaše aplikace bude moct používat protokoly prodlouží rozhraní .NET Framework.

`<VERSION>` (pro rozhraní .NET Framework 3.5) musí být v4.0.30319 (pro rozhraní .NET Framework 4 a novější) nebo v2.0.50727.

Pokud vaše aplikace cílí na .NET Framework 4.7 nebo novější verze, výchozí hodnota tohoto klíče na hodnotu 1. To je zabezpečené, doporučujeme, abyste výchozí. Pokud vaše aplikace běží na rozhraní .NET Framework 4.7 nebo novější verze, ale zaměřuje na starší verzi, výchozí hodnota klíče na hodnotu 0. V takovém případě byste měli explicitně nastavit její hodnotu na 1.

Další informace najdete v tématu [kumulativní aktualizace pro Windows 10 verzi 1511 a Windows Server 2016 Technical Preview 4: 10. května 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016).

Další informace o rozhraní .NET framework 3.5.1, naleznete v tématu [podpora verzí výchozí společnosti TLS systému součástí rozhraní .NET Framework 3.5.1 na Windows 7 SP1 a Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Následující _. REG_ souboru nastaví na nejvíce bezpečné hodnoty klíče registru a jeho variant:

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

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Protokoly Schannel konfigurace v registru Windows

V registru můžete použít pro velice přesně kontrolovat, protokol, který vyjednává klienta nebo serveru pro aplikaci. Aplikace sítě prochází zprostředkovatele Schannel (což je jiný název pro [Secure Channel](/windows/desktop/SecAuthN/secure-channel). Tím, že nakonfigurujete `Schannel`, můžete provádět konfiguraci chování vaší aplikace.

Začněte `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` klíč registru. Pod tímto klíčem můžete vytvořit všechny podklíče v sadě `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1`, a `TLS 1.2`. Pod každým z těchto podklíčích, můžete vytvořit podklíče `Client` a/nebo `Server`. V části `Client` a `Server`, vytvořením hodnoty DWORD `DisabledByDefault` (0 nebo 1) a `Enabled` (0 nebo hodnotu 0xFFFFFFFF).

## <a name="the-schusestrongcrypto-flag"></a>Příznak SCH_USE_STRONG_CRYPTO

Pokud je povolená (ve výchozím nastavení, pomocí `AppContext` přepnout, nebo pomocí registru Windows), používá rozhraní .NET Framework `SCH_USE_STRONG_CRYPTO` příznak, když vaše aplikace požaduje protokol zabezpečení TLS. `SCH_USE_STRONG_CRYPTO` Příznak můžete povolit ve výchozím nastavení, `AppContext` přepnout, nebo s registrem. Operační systém předává příznak, který `Schannel`dáte pokyn, aby ho zakázat známé slabé kryptografické algoritmy, šifer sady a verze protokolu TLS/SSL, které může být jinak povoleno pro lepší spolupráci. Další informace naleznete v tématu:

- [Zabezpečený kanál](/windows/desktop/SecAuthN/secure-channel)
- [Struktura SCHANNEL_CRED](/windows/desktop/api/schannel/ns-schannel-_schannel_cred)

`SCH_USE_STRONG_CRYPTO` Příznak také předat `Schannel` explicitně použijete `Tls` (protokol TLS 1.0) `Tls11`, nebo `Tls12` hodnot z výčtu <xref:System.Net.SecurityProtocolType> nebo <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Aktualizace zabezpečení

Osvědčené postupy v tomto článku, závisí na instalaci nejnovější aktualizace zabezpečení. Tyto aktualizace zahrnují možnost využívat novější funkce a rozšířené rozhraní .NET Framework 4.7. Nejnovější aktualizace zabezpečení jsou důležité, pokud vaše aplikace běží na rozhraní .NET Framework 4.7 a novějších verzích (i v případě, že je cílen na dřívější verze).

Pokud chcete aktualizovat rozhraní .NET Framework umožňuje zvolit nejlepší verzi TLS použití operačního systému, musíte nainstalovat alespoň:

- [Rozhraní .NET Framework. srpna 2017 Preview kvality kumulativní](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup).
- **Nebo** [kumulativní kvality a zabezpečení rozhraní .NET Framework. září 2017](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup).

Viz také:

- [Verze rozhraní .NET framework a závislosti](../migration-guide/versions-and-dependencies.md)
- [Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>Podpora protokolu TLS 1.2

Pro vaši aplikaci pro vyjednávání protokolu TLS 1.2, operační systém a verzi rozhraní .NET Framework obě musí podporovat protokol TLS 1.2.

**Požadavky na operační systém pro podporu protokolu TLS 1.2**

Pokud chcete povolit nebo opětovné povolení protokolu TLS 1.2 a/nebo protokolu TLS 1.1 v systému, který je podporuje, najdete v článku [zabezpečení TLS (Transport Layer), nastavení registru](/windows-server/security/tls/tls-registry-settings).

| **OS** | **Podpora protokolu TLS 1.2** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | Podporované a ve výchozím nastavení povolená. |
| Windows 8.1</br>Windows Server 2012 R2 | Podporované a ve výchozím nastavení povolená. |
| Windows 8.0</br>Windows Server 2012 | Podporované a ve výchozím nastavení povolená. |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | Podporované, ale není ve výchozím nastavení povolená. Zobrazit [zabezpečení TLS (Transport Layer), nastavení registru](/windows-server/security/tls/tls-registry-settings) webové stránky, podrobné informace o postupu povolení protokolu TLS 1.2. |
| Windows Server 2008 | Podpora protokolu TLS 1.2 a TLS 1.1 vyžaduje aktualizaci. Zobrazit [aktualizace přidává funkce pro protokol TLS 1.1 a TLS 1.2 v systému Windows Server 2008 SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Není podporováno. |

Informace, o které TLS/SSL protokoly jsou povolené ve výchozím nastavení v každé verzi systému Windows najdete v tématu [protokolů TLS/SSL (zprostředkovateli zabezpečení Schannel)](https://msdn.microsoft.com/library/windows/desktop/mt808159).

**Požadavky na podporu protokolu TLS 1.2 v rozhraní .NET Framework 3.5**

Tato tabulka zobrazuje aktualizace operačního systému, že které budete potřebovat pro podporu protokolu TLS 1.2 v rozhraní .NET Framework 3.5. Doporučujeme, abyste že je provedli všechny aktualizace operačního systému.

| **OS** | **Minimální aktualizace, které jsou potřebné pro podporu protokolu TLS 1.2 v rozhraní .NET Framework 3.5** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | [Kumulativní aktualizace pro Windows 10 verze 1511 a Windows Server 2016 Technical Preview 4: 10. května 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1</br>Windows Server 2012 R2 | [Podpora verzí výchozí společnosti TLS systému zahrnuty v rozhraní .NET Framework 3.5 ve Windows 8.1 a Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0</br>Windows Server 2012 | [Podpora verzí výchozí společnosti TLS systému zahrnuty v rozhraní .NET Framework 3.5 ve Windows serveru 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | [Podpora verzí výchozí společnosti TLS systému zahrnuty v rozhraní .NET Framework 3.5.1 na Windows 7 SP1 a Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Podpora verzí výchozí společnosti TLS systému zahrnuty v rozhraní .NET Framework 2.0 SP2 ve Windows Vista SP2 a Server 2008 SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Nepodporováno |

## <a name="azure-cloud-services"></a>Azure Cloud Services

Pokud používáte [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) webové a pracovní role pro hostování a spuštění aplikace, existují některé aspekty, které je potřeba vzít v úvahu pro podporu protokolu TLS 1.2.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>Rozhraní .NET framework 4.7 není nainstalována na hostovaný operační systém Azure ve výchozím nastavení

Je nainstalovaná v nejnovější verzi Azure hostovaného operačního systému řady 5 (Windows Server 2016) nejnovější verze 4.6.2. Pokud chcete zobrazit, jaké verze rozhraní .NET Framework jsou nainstalovány na každý hostovaný operační systém Azure, najdete v článku [SDK kompatibility přehled verzí hostovaného operačního systému Azure a](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Pokud svojí aplikací cílíte na verzi rozhraní .NET Framework, která není k dispozici ve verzi hostovaného operačního systému Azure, budete muset nainstalovat sami. Zobrazit [instalace rozhraní .NET pro Azure Cloud Service role](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Pokud instalace rozhraní framework vyžaduje restartování, může také restartovat službu role před vstupem stavu Připraveno.

### <a name="azure-guest-os-registry-settings"></a>Nastavení registru Azure hostovaného operačního systému

Image operačního systému hosta Azure pro [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) již `SchUseStrongCrypto` klíče registru nastavte na hodnotu 1. Další informace najdete v tématu [SchUseStrongCrypto](#schusestrongcrypto).

Nastavte [SystemDefaultTlsVersions](#systemdefaulttlsversions) klíče registru na 1. Zobrazit [konfigurace zabezpečení prostřednictvím registru Windows](#configuring-security-via-the-windows-registry).
