---
title: Strategie a strojírenství zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: 57ee0c8242c0bca1b2c76e7751ed25f6a889c264
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741846"
---
# <a name="wpf-security-strategy---security-engineering"></a>Strategie zabezpečení WPF – engineering zabezpečení
Důvěryhodná výpočetní aplikace je iniciativa Microsoftu pro zajištění výroby zabezpečeného kódu. Klíčovým prvkem pro nedůvěryhodný výpočetní iniciativou je Microsoft Security Development Lifecycle (SDL). SDL je technický postup, který se používá společně se standardními technickými procesy pro usnadnění poskytování zabezpečeného kódu. SDL se skládá z deseti fází, které kombinují osvědčené postupy s formalitou, měřitelnou a další strukturou, včetně těchto:  
  
- Analýza návrhu zabezpečení  
  
- Kontroly kvality založené na nástroji  
  
- Testování průniku  
  
- Poslední kontrola zabezpečení  
  
- Správa zabezpečení produktu po vydání  
  
## <a name="wpf-specifics"></a>Specifické pro WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] technický tým používá a rozšiřuje SDL, přičemž kombinace zahrnuje tyto klíčové aspekty:  
  
 [Modelování hrozeb](#threat_modeling)  
  
 [Nástroje pro analýzu a úpravy zabezpečení](#tools)  
  
 [Techniky testování](#techniques)  
  
 [Správa kritického kódu](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Modelování hrozeb  
 Modelování hrozeb je základní součástí SDL a používá se k profilování systému k určení potenciálních ohrožení zabezpečení. Po zjištění ohrožení zabezpečení taky modelování hrozeb zajistí, že budou zavedena vhodná omezení.  
  
 Modelování hrozeb na vysoké úrovni zahrnuje následující klíčové kroky jako příklad v prodejnách:  
  
1. **Identifikují se prostředky**. Prostředky v prodejnách můžou zahrnovat zaměstnance, bezpečné, pokladní registry a inventář.  
  
2. **Vytváření výčtu vstupních bodů**. Vstupní body, které jsou v prodejnách, můžou zahrnovat přední a zadní dveře, Windows, dockou plošinu a jednotky klimatizace.  
  
3. **Zkoumání útoků na prostředky pomocí vstupních bodů**. Jedním z možných útoků by mohlo být, že se k *bezpečnému* assetu v obchodě v prodejnách cílí prostřednictvím vstupního bodu *klimatizace* ; nešroubovaná jednotka klimatizace by mohla být nešroubovaná, aby bylo možné ji bezpečně vystavit a ze Storu.  
  
 Modelování hrozeb se používá v celém [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] a obsahuje následující:  
  
- Jak analyzátor [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] čte soubory, mapuje text na odpovídající třídy objektového modelu a vytvoří skutečný kód.  
  
- Jak je vytvořen popisovač okna (hWnd), odesílá zprávy a používá se k vykreslování obsahu okna.  
  
- Způsob, jakým datové vazby získávají prostředky a vzájemně spolupracuje se systémem.  
  
 Tyto modely hrozeb jsou důležité pro identifikaci požadavků na návrh zabezpečení a zmírnění hrozeb během procesu vývoje.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Nástroje pro analýzu a úpravy zdroje  
 Kromě prvků pro ruční kontrolu kódu zabezpečení v SDL používá [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tým několik nástrojů pro analýzu zdrojové analýzy a přidružených úprav pro snížení zabezpečení zabezpečení. Používá se rozsáhlá škála zdrojových nástrojů a zahrnuje následující:  
  
- **FXCop**: vyhledá běžné problémy se zabezpečením ve spravovaném kódu v rozsahu od pravidel dědičnosti až po použití zabezpečení přístupu ke kódu, jak bezpečně spolupracovat s nespravovaným kódem. Viz [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Prefix/PREfast**: vyhledá chyby zabezpečení a běžné problémy zabezpečení v nespravovaném kódu, jako je přetečení vyrovnávací paměti, problémy formátu řetězce a kontrola chyb.  
  
- **Zakázaná rozhraní API**: vyhledá zdrojový kód, aby identifikoval nechtěné použití funkcí, které jsou dobře známé pro účely potíží se zabezpečením, jako je například `strcpy`. Po identifikaci jsou tyto funkce nahrazené alternativami, které jsou bezpečnější.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Techniky testování  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] používá celou řadu technik testování zabezpečení, které zahrnují:  
  
- **Testování WhiteBOX**: testery zobrazují zdrojový kód a pak vytvářejí zneužití testů.
  
- **Testování Blackbox**: testery se snaží najít zneužití zabezpečení kontrolou rozhraní API a funkcí a pak se pokusí o útok na produkt.  
  
- Řešení **potíží se zabezpečením z jiných produktů**: v případě potřeby se testuje problémy zabezpečení ze souvisejících produktů. Například byly zjištěny vhodné varianty v aplikaci Internet Explorer, které byly identifikovány přibližně 60 problémy se zabezpečením, a pokusily se [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]jejich použitelnost.  
  
- **Testování průniku na základě nástrojů prostřednictvím fuzzy souboru**: rozkládání souborů je využitím vstupního rozsahu čtečky souborů prostřednictvím nejrůznějších vstupů. Jedním z příkladů v [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], kde se tato technika používá, je vyhledání chyby v kódu dekódování obrazu.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Správa kritického kódu  
 Pro aplikace prohlížeče XAML (XBAP) [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] vytvoří izolovaný prostor zabezpečení pomocí .NET Framework podpory pro označování a sledování kódu kritického pro zabezpečení, který zvyšuje oprávnění (viz **metodika kritické pro zabezpečení** v tématu řešení [zabezpečení pro WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)). S ohledem na požadavky na kvalitu vysokého zabezpečení u kódu kritického pro zabezpečení tento kód obdrží další úroveň řízení správy zdrojů a auditu zabezpečení. Přibližně 5% až 10% [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] se skládá z kódu kritického pro zabezpečení, který je přezkoumán vyhrazeným týmem revize. Zdrojový kód a proces vrácení se změnami jsou spravovány sledováním kódu kritického pro zabezpečení a mapováním jednotlivých důležitých entit (tj. metoda, která obsahuje kritický kód) do svého stavu odhlášení. Stav odhlášení zahrnuje jména jednoho nebo více revidujících. Každý denní Build [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] porovnává kritický kód s tímto kódem v předchozích sestaveních a kontroluje neschválené změny. Pokud inženýr mění kritický kód bez schválení od týmu revize, je identifikován a opraven okamžitě. Tento proces umožňuje aplikaci a údržbu obzvláště vysoké úrovně kontroly nad [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kódem izolovaného prostoru (sandboxu).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení](security-wpf.md)
- [Částečné zabezpečení důvěryhodnosti WPF](wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)
- [Důvěryhodná výpočetní prostředí](https://www.microsoft.com/mscorp/twc/default.mspx)
- [Zabezpečení v .NET](../../standard/security/index.md)
