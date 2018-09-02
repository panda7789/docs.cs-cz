---
title: Analytické trasování – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 9918f07d9c26c1779a1eedfbc423c31e61659334
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401178"
---
# <a name="analytic-tracing-overview"></a>Analytické trasování – přehled
Analytické trasování v [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] je vysoký výkon a nízkou úroveň podrobností funkce trasování nastavit nad Event Tracing for Windows (ETW). Trasování událostí pro Windows se spustí na úrovni jádra výrazně snížit nároky na operations trasování. To efektivně ukládá do vyrovnávací paměti události uživatele a jádra režimu a umožňuje dynamické povolení protokolování bez nutnosti restartování služby. Data trasování je k dispozici v případě, že generované a přijaté protokolování po něm.  
  
 Další informace o trasování událostí pro Windows najdete v tématu [vylepšení ladění a optimalizace výkonu pomocí trasování událostí pro Windows](https://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Kromě použití protokolů událostí systému Windows, zabezpečení a aplikací pro analýzu aplikace, [!INCLUDE[wv](../../../../../includes/wv-md.md)] a [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] zavést další protokoly nejvyšší úrovně uzlu protokoly aplikací a služeb. Účelem tyto nové protokoly se k uložení událostí pro konkrétní aplikaci nebo konkrétní součást místo globální události, které mají vliv celý systém (jako je například typ události, které může zaznamenat protokolu událostí zabezpečení). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] sjednocuje a koreluje protokolování WCF trasování událostí, protokoly zpráv WCF, a [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] sledování záznamů protokoly aplikací a služeb.  
  
## <a name="concepts-and-capabilities"></a>Koncepty a funkce  
 Následující koncepty a možnosti použít analytické trasování WCF.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>Povolení nastavení diagnostiky WCF  
 V rámci je povolená Diagnostika WCF \<system.serviceModel >\<diagnostiky > konfigurační oddíl.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 WCF nastavení diagnostiky pro virtuální aplikace hostované na Web služby IIS jsou povolené v jeho "souboru Web.config. Další možností je vytvořit soubor Web.config v dílčí adresáře v rámci aplikace.  Tato volba platí pro všechny služby v rámci podadresář nastavení.  Aby bylo zajištěno, že jsou nastavení diagnostiky pro všechny služby v rámci aplikace konzistentně inicializovány, byste nastavit v souboru Web.config v adresáře aplikace a není v jednotlivých podadresářích v rámci aplikace.  
  
### <a name="channels"></a>Kanály  
 Trasování událostí pro Windows umožňuje softwarových komponent přímé trasování událostí pro konkrétní cílové skupiny pomocí kanálů. Například můžete poslat události pro správce systému na jeden kanál a události péče o tuto aplikaci vývojáře o jiném kanálu. Kanály jsou s názvem a registrovány s Windows, příjemci mohli zobrazit události kanál pomocí prohlížeče událostí.  
  
 Analytické trasování funkce pro službu WCF v [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] zapíše do kanálu Microsoft-Windows--Server-aplikace. Tento kanál je navržená speciálně pro uživatele, kteří chtějí sledovat stav služeb WCF v produkčním prostředí. Definuje malá, sadu událostí, které lze použít v mnoha monitorování stavu a řešení potíží se scénáři.  
  
 Chcete-li manifest události trasování pro Windows tak, aby zprávy jsou správně dekódovat. v protokolu událostí, pomocí nástroje ServiceModelReg na příkazovém řádku takto:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Dynamickou konfiguraci  
 Trasování událostí pro Windows infrastruktury umožňuje trasování, aby bylo možné povolené a nakonfigurované dynamické použití standardních nástrojů Windows. Další informace najdete v tématu [dynamické povolování analytického sledování](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>Trasování toku zpráv  
 Další informace o tom, jak povolit trasování toku zpráv najdete v tématu [Konfigurace trasování toku zpráv](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Klíčová slova  
 Klíčová slova se používají k filtrování zprávy trasování a definovat jakou součást [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] událost, protože ho. Další informace najdete v tématu [dynamické povolování analytického sledování](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).
