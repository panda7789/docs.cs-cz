---
title: Analytické trasování – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: f1a24e34375e98d4bfb48c1e2fd84290e08f6eea
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544759"
---
# <a name="analytic-tracing-overview"></a>Analytické trasování – přehled
Analytické trasování v [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] je funkce pro sledování událostí s vysokým výkonem a s nízkou mírou podrobností nastavenou na trasování událostí pro Windows (ETW). ETW běží na úrovni jádra, aby významně snížila nároky na operace trasování. Efektivně ukládá do vyrovnávací paměti události režimu jádra a uživatele a umožňuje dynamické povolení protokolování bez nutnosti restartování služby. Data trasování jsou k dispozici v protokolech událostí poté, co byly vygenerovány a přijímány.  
  
 Další informace o trasování událostí pro Windows najdete v tématu [vylepšení ladění a ladění výkonu pomocí ETW](https://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Kromě použití protokolů událostí systému Windows, zabezpečení a aplikací k analýze aplikace systémy Windows Vista a Windows Server 2008 zavedly další protokoly pod uzlem protokoly aplikací a služeb na nejvyšší úrovni. Účelem těchto nových protokolů je ukládat události pro konkrétní aplikaci nebo konkrétní komponentu namísto globálních událostí, které mají vliv na systém (například typ událostí, které může protokol událostí zabezpečení zaznamenat). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] sjednocuje a koreluje protokolování událostí trasování WCF, protokolů zpráv WCF a [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] sledování záznamů do protokolů aplikací a služeb.  
  
## <a name="concepts-and-capabilities"></a>Koncepty a možnosti  
 Následující koncepty a možnosti se vztahují na analytické trasování WCF.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>Povoluje se nastavení diagnostiky WCF.  
 Diagnostika služby WCF je povolená v části \<System. serviceModel >\<Diagnostics > Configuration.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 Nastavení diagnostiky WCF pro virtuální aplikaci služby IIS hostovanou webovým prostředím jsou povolená v souboru Web. config. Další možností je vytvořit soubor Web. config v podadresáři v rámci aplikace.  Tato volba aplikuje nastavení na všechny služby v podadresáři.  Aby se zajistilo, že nastavení diagnostiky se konzistentně inicializuje pro všechny služby v rámci aplikace, měla by být nastavení v souboru Web. config v adresáři aplikace, a ne v jednom z dílčích adresářů v rámci aplikace.  
  
### <a name="channels"></a>Kanály  
 ETW umožňuje softwarovým součástem směrovat události trasování na konkrétní cílovou skupinu pomocí kanálů. Můžete například odesílat události pro správce systému do jednoho kanálu a události, které vývojáři aplikací postarou o jiný kanál. Kanály se nazývají a registrují ve Windows, aby si uživatelé mohli zobrazit události kanálu pomocí Prohlížeč událostí.  
  
 Funkce analytického trasování pro WCF v [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] zapisuje do kanálu Microsoft-Windows-Application-Server-Applications. Tento kanál je navržený speciálně pro uživatele, kteří chtějí monitorovat stav služeb WCF v produkčním prostředí. Definuje malou sadu událostí, která se dá použít v mnoha scénářích monitorování stavu a odstraňování potíží.  
  
 Chcete-li povolit trasování událostí pro manifest systému Windows, aby byly zprávy v protokolu událostí správně Dekódovatelné, použijte Nástroj ServiceModelReg na příkazovém řádku následujícím způsobem:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Dynamická konfigurace  
 Infrastruktura ETW umožňuje, aby bylo trasování povolené a nakonfigurované dynamicky pomocí standardních nástrojů Windows. Další informace najdete v tématu [dynamické povolení analytického trasování](dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>Trasování toku zpráv  
 Další informace o tom, jak povolit trasování toku zpráv, najdete v tématu [Konfigurace trasování toku zpráv](configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Klíčová slova  
 Klíčová slova slouží k filtrování zpráv trasování a definování součásti .NET Framework vyvolaly událost. Další informace najdete v tématu [dynamické povolení analytického trasování](dynamically-enabling-analytic-tracing.md).
