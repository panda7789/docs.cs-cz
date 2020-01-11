---
title: Analytické trasování – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 7718c8f2a82178bedc080eda0cd0fdf728213a27
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900626"
---
# <a name="analytic-tracing-overview"></a>Přehled analytického trasování

Analytické trasování v [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] je funkce pro sledování událostí s vysokým výkonem a s nízkou mírou podrobností nastavenou na trasování událostí pro Windows (ETW). ETW běží na úrovni jádra, aby významně snížila nároky na operace trasování. Efektivně ukládá do vyrovnávací paměti události režimu jádra a uživatele a umožňuje dynamické povolení protokolování bez nutnosti restartování služby. Data trasování jsou k dispozici v protokolech událostí poté, co byly vygenerovány a přijímány.

Další informace o trasování událostí pro Windows najdete v tématu [vylepšení ladění a ladění výkonu pomocí ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).

 Kromě použití protokolů událostí systému Windows, zabezpečení a aplikací k analýze aplikace systémy Windows Vista a Windows Server 2008 zavedly další protokoly pod uzlem protokoly aplikací a služeb na nejvyšší úrovni. Účelem těchto nových protokolů je ukládat události pro konkrétní aplikaci nebo konkrétní komponentu namísto globálních událostí, které mají vliv na systém (například typ událostí, které může protokol událostí zabezpečení zaznamenat). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] sjednocuje a koreluje protokolování událostí trasování WCF, protokolů zpráv WCF a [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] sledování záznamů do protokolů aplikací a služeb.

Následující části popisují koncepty a možnosti, které se vztahují na analytické trasování služby WCF.

## <a name="enable-wcf-diagnostics-settings"></a>Povolit nastavení diagnostiky WCF

Diagnostika služby WCF je povolená v rámci konfiguračního oddílu `<system.serviceModel><diagnostics>`.

```xml
<system.serviceModel>
  <diagnostics>
```

Nastavení diagnostiky WCF pro virtuální aplikaci hostovanou webovým prostředím IIS jsou v souboru *Web. config* povolena. Další možností je vytvořit soubor *Web. config* v podadresáři v rámci aplikace. Tato volba aplikuje nastavení na všechny služby v podadresáři. Aby se zajistilo, že nastavení diagnostiky se konzistentně inicializuje pro všechny služby v rámci aplikace, nastavení by mělo být v rámci souboru *Web. config* v adresáři aplikace, a ne v jednom z jednotlivých podadresářů v rámci aplikace.

## <a name="channels"></a>Kanály

ETW umožňuje softwarovým součástem směrovat události trasování na konkrétní cílovou skupinu pomocí kanálů. Můžete například odesílat události pro správce systému do jednoho kanálu a událostí, které vývojáři aplikací postarou o jiný kanál. Kanály se nazývají a registrují ve Windows, aby si uživatelé mohli zobrazit události kanálu pomocí Prohlížeč událostí.

 Funkce analytického trasování pro WCF v [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] zapisuje do kanálu Microsoft-Windows-Application-Server-Applications. Tento kanál je určený pro uživatele, kteří chtějí monitorovat stav služeb WCF v produkčním prostředí. Definuje malou sadu událostí, které je možné použít v mnoha scénářích monitorování stavu a odstraňování potíží.

 Chcete-li povolit trasování událostí pro manifest systému Windows, aby byly zprávy v protokolu událostí správně Dekódovatelné, použijte Nástroj ServiceModelReg na příkazovém řádku následujícím způsobem:

 `ServiceModelReg.exe -i -c:etw`

## <a name="dynamic-configuration"></a>Dynamická konfigurace

Infrastruktura ETW umožňuje, aby bylo trasování povolené a nakonfigurované dynamicky pomocí standardních nástrojů Windows. Další informace najdete v tématu [dynamické povolení analytického trasování](dynamically-enabling-analytic-tracing.md).

## <a name="message-flow-tracing"></a>Trasování toku zpráv

Další informace o tom, jak povolit trasování toku zpráv, najdete v tématu [Konfigurace trasování toku zpráv](configuring-message-flow-tracing.md).

## <a name="keywords"></a>Klíčová slova

Klíčová slova slouží k filtrování zpráv trasování a definování součásti .NET Framework vyvolaly událost. Další informace najdete v tématu [dynamické povolení analytického trasování](dynamically-enabling-analytic-tracing.md).
