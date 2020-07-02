---
ms.openlocfilehash: 5c86be598ab6196ecf4da05451c7f22d2be52c12
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614469"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>Výchozí hodnota Třída ServicePointManager. Tato SecurityProtocol je SecurityProtocolType.System. Výchozí

#### <a name="details"></a>Podrobnosti

Počínaje aplikacemi, které cílí na .NET Framework 4,7, je výchozí hodnota <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> vlastnosti <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> . Tato změna umožňuje .NET Framework síťových rozhraní API založených na SslStream (například FTP, HTTPS a SMTP) k dědění výchozích protokolů zabezpečení z operačního systému namísto použití pevně zakódovaných hodnot definovaných .NET Framework. Výchozí hodnota se liší podle operačního systému a jakékoli vlastní konfigurace provedené správcem systému. Informace o výchozím protokolu SChannel v každé verzi operačního systému Windows najdete v tématu [protokoly TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>Pro aplikace, které cílí na starší verzi .NET Framework, je výchozí hodnota <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> vlastnosti závislá na verzi .NET Framework cílená. Další informace najdete v [části sítě v článku změny cílení změn pro migraci z .NET Framework 4.5.2 na 4,6](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking) .

#### <a name="suggestion"></a>Návrh

Tato změna ovlivní aplikace, které cílí na .NET Framework 4,7 nebo novější verze. Pokud upřednostňujete použití definovaného protokolu namísto spoléhání na výchozí systémové nastavení, můžete hodnotu vlastnosti explicitně nastavit <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> . Pokud je tato změna nežádoucí, můžete ji odhlásit přidáním nastavení konfigurace do [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace. Následující příklad ukazuje jak `<runtime>` oddíl, tak přepínač pro `Switch.System.Net.DontEnableSystemDefaultTlsVersions` výslovný souhlas:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSystemDefaultTlsVersions=true" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4,7         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>
