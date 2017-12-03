---
title: "Analytické trasování – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dd456401073d8c7f3c7bc9fbfbe5c11dbbd4e58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="analytic-tracing-overview"></a>Analytické trasování – přehled
Analytické trasování v [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] je vysoký výkon a nízkou podrobností trasování funkce nastavit nad událostí trasování pro Windows (ETW). Trasování událostí pro Windows se spustí na úrovni jádra k výrazně snížit režii trasování operací. Ho efektivně ukládá do vyrovnávací paměti události režimu uživatele a jádra a umožňuje dynamické povolení protokolování bez nutnosti restartování služby. Data trasování je k dispozici v případě, že byl vygenerované a přijaté protokoly za ním.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]Trasování událostí pro Windows, najdete v části [vylepšení ladění a optimalizace výkonu s ETW](http://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Kromě použití protokolů událostí systému Windows, zabezpečení a aplikace pro analýzu aplikace, [!INCLUDE[wv](../../../../../includes/wv-md.md)] a [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] zavedená další protokoly pod uzlem protokoly aplikací a služeb nejvyšší úrovně. Účelem tyto nové protokoly je k uložení událostí pro konkrétní aplikaci nebo konkrétní součást místo globální události, které mají vliv systémové (jako je například typ události, které může záznam v protokolu událostí zabezpečení). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]kombinuje a korelaci protokolování [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] události trasování, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] protokolů zpráv a [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] sledování záznamů protokoly aplikací a služeb.  
  
## <a name="concepts-and-capabilities"></a>Koncepty a funkce  
 Následující koncepty a možnosti použít [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytické trasování.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>Povolení nastavení diagnostiky WCF  
 Diagnostika WCF jsou povoleny v rámci \<system.serviceModel >\<diagnostics > konfigurační oddíl.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 WCF nastavení diagnostiky pro virtuální aplikace hostované webové služby IIS jsou povoleny v jeho ' souboru Web.config. Další možností je vytvořit soubor Web.config v podadresář v aplikaci.  Tato volba platí pro všechny služby v rámci podadresář nastavení.  Aby se zajistilo, že nastavení diagnostiky se inicializují konzistentně pro všechny služby v rámci aplikace, nastavení musí být v souboru Web.config v adresáři aplikace a ne v jednom z jednotlivých podadresářů v aplikaci.  
  
### <a name="channels"></a>Kanály  
 Trasování událostí pro Windows umožňuje softwarové součásti přímé trasování událostí pro konkrétní cílové skupině pomocí kanálů. Například můžete poslat události pro jeden kanál správcům systému a události tohoto pozor vývojáři aplikace o jiném kanálu. Kanály jsou s názvem a registrovány v systému Windows tak, aby spotřebitelé můžete zobrazit události kanál pomocí prohlížeče událostí.  
  
 Analytické trasování funkce pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] v [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] zapíše do kanálu Microsoft-Windows-aplikace-Server-aplikace. Tento kanál navrženy speciálně pro uživatele, kteří chtějí monitorovat stav [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby v produkčním prostředí. Definuje malá, nastavte událostí, které lze použít v mnoha sledování stavu a scénáře řešení potíží.  
  
 Pokud chcete povolit manifest trasování událostí pro Windows tak, aby zpráv jsou správně dekódovat v protokolu událostí, pomocí nástroje ServiceModelReg na příkazovém řádku následujícím způsobem:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Dynamické konfigurace  
 Trasování událostí pro Windows infrastruktury umožňuje trasování být povolené a nakonfigurované dynamické pomocí standardních nástrojů systému Windows. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Dynamické povolování analytického sledování](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>Trasování toku zpráv  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]Povolit trasování toku zpráv najdete v tématu [Konfigurace trasování toku zpráv](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Klíčová slova  
 Klíčová slova se používají k filtrování zprávy trasování a definovat jakou součást [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] vygenerované události. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Dynamické povolování analytického sledování](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).
