---
title: Strategie zabezpečení WPF – engineering zabezpečení
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
ms.openlocfilehash: d5bcd5b06f6d922b29c2a494f1f63da1217e2b2d
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817869"
---
# <a name="wpf-security-strategy---security-engineering"></a>Strategie zabezpečení WPF – engineering zabezpečení
Důvěryhodná výpočetní aplikace je iniciativa Microsoftu pro zajištění výroby zabezpečeného kódu. Klíčovým prvkem pro důvěryhodný výpočetní iniciativou je [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Je technický postup, který se používá ve spojení se standardními technickými procesy pro usnadnění poskytování zabezpečeného kódu. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Skládá se z deseti fází, které kombinují osvědčené postupy s formalitou, měřitelnosti a další strukturou, včetně:  
  
- Analýza návrhu zabezpečení  
  
- Kontroly kvality založené na nástroji  
  
- Testování průniku  
  
- Poslední kontrola zabezpečení  
  
- Správa zabezpečení produktu po vydání  
  
## <a name="wpf-specifics"></a>Specifické pro WPF  
 Technický tým používá a [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]rozšiřuje, přičemž kombinace zahrnuje tyto klíčové aspekty: [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]  
  
 [Modelování hrozeb](#threat_modeling)  
  
 [Nástroje pro analýzu a úpravy zabezpečení](#tools)  
  
 [Techniky testování](#techniques)  
  
 [Správa kritického kódu](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Modelování hrozeb  
 Modelování hrozeb je základní součástí [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]nástroje, která se používá k profilování systému za účelem určení potenciálních ohrožení zabezpečení. Po zjištění ohrožení zabezpečení taky modelování hrozeb zajistí, že budou zavedena vhodná omezení.  
  
 Modelování hrozeb na vysoké úrovni zahrnuje následující klíčové kroky jako příklad v prodejnách:  
  
1. **Identifikují se prostředky**. Prostředky v prodejnách můžou zahrnovat zaměstnance, bezpečné, pokladní registry a inventář.  
  
2. **Vytváření výčtu vstupních bodů**. Vstupní body, které jsou v prodejnách, můžou zahrnovat přední a zadní dveře, Windows, dockou plošinu a jednotky klimatizace.  
  
3. **Zkoumání útoků na prostředky pomocí vstupních bodů**. Jedním z možných útoků by mohlo být, že se k bezpečnému assetu v obchodě v prodejnách cílí prostřednictvím vstupního bodu *klimatizace* ; nešroubovaná jednotka klimatizace by mohla být nešroubovaná, aby bylo možné ji bezpečně vystavit a ze Storu.  
  
 Modelování hrozeb se používá v [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] celém rozsahu a zahrnuje následující:  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] Jak analyzátor čte soubory, mapuje text na odpovídající třídy objektového modelu a vytvoří skutečný kód.  
  
- Jak je vytvořen popisovač okna (hWnd), odesílá zprávy a používá se k vykreslování obsahu okna.  
  
- Způsob, jakým datové vazby získávají prostředky a vzájemně spolupracuje se systémem.  
  
 Tyto modely hrozeb jsou důležité pro identifikaci požadavků na návrh zabezpečení a zmírnění hrozeb během procesu vývoje.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Nástroje pro analýzu a úpravy zdroje  
 Kromě prvků [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kontroly ručního zabezpečení kódu v týmu používá tým několik nástrojů pro analýzu zdrojové analýzy a přidružených úprav ke snížení slabých chyb zabezpečení. Používá se rozsáhlá škála zdrojových nástrojů a zahrnuje následující:  
  
- **FXCop**: Vyhledá běžné problémy se zabezpečením ve spravovaném kódu v rozsahu od pravidel dědičnosti až po použití zabezpečení přístupu kódu k bezpečné spolupráci s nespravovaným kódem. Viz [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Předpona/předrychlá**: Vyhledá chyby zabezpečení a běžné problémy zabezpečení v nespravovaném kódu, jako je přetečení vyrovnávací paměti, problémy formátu řetězce a kontrola chyb.  
  
- **Zakázaná rozhraní API**: Vyhledá zdrojový kód, aby identifikoval náhodné použití funkcí, které jsou dobře známé pro způsobující problémy se zabezpečením `strcpy`, jako je například. Po identifikaci jsou tyto funkce nahrazené alternativami, které jsou bezpečnější.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Techniky testování  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]používá celou řadu technik testování zabezpečení, které zahrnují:  
  
- **WhiteBOX testování**: Testeri si zobrazí zdrojový kód a pak vytvoří zneužití testů.
  
- **Blackbox testování**: Testery se snaží najít zneužití zabezpečení kontrolou rozhraní API a funkcí a pak se pokusí o útok na produkt.  
  
- **Řešení potíží se zabezpečením z jiných produktů**: V případě potřeby jsou testovány problémy zabezpečení ze souvisejících produktů. Například byly zjištěny vhodné varianty s 60 problémy zabezpečení pro Internet Explorer, které byly identifikovány a se [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]pokusily o jejich použitelnost.  
  
- **Testování průniku na základě nástrojů v rozmazaných souborech**: Fuzzy File je využití vstupního rozsahu čtečky souborů prostřednictvím řady různých vstupů. Jedním z [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] příkladů, kde se tato technika používá, je vyhledání chyby v kódu dekódování obrazu.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Správa kritického kódu  
 Pro [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)]vytvoří izolovaný prostor zabezpečení pomocí .NET Framework podpory pro označování a sledování kódu kritického pro zabezpečení, který zvyšuje oprávnění (viz **metodika kritické pro zabezpečení** v tématu strategie zabezpečení WPF – platforma [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] [ Zabezpečení](wpf-security-strategy-platform-security.md)). S ohledem na požadavky na kvalitu vysokého zabezpečení u kódu kritického pro zabezpečení tento kód obdrží další úroveň řízení správy zdrojů a auditu zabezpečení. Přibližně 5% až 10% [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] se skládá z kódu kritického pro zabezpečení, který je přezkoumán vyhrazeným týmem revize. Zdrojový kód a proces vrácení se změnami jsou spravovány sledováním kódu kritického pro zabezpečení a mapováním jednotlivých důležitých entit (tj. metoda, která obsahuje kritický kód) do svého stavu odhlášení. Stav odhlášení zahrnuje jména jednoho nebo více revidujících. Každý denní Build [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] porovná kritický kód s tímto v předchozích sestaveních a kontroluje neschválené změny. Pokud inženýr mění kritický kód bez schválení od týmu revize, je identifikován a opraven okamžitě. Tento proces umožňuje aplikaci a údržbu obzvláště vysoké úrovně kontroly nad [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kódem izolovaného prostoru (sandboxu).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení](security-wpf.md)
- [Částečné zabezpečení důvěryhodnosti WPF](wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)
- [Důvěryhodná výpočetní prostředí](https://www.microsoft.com/mscorp/twc/default.mspx)
- [Zabezpečení v .NET](../../standard/security/index.md)
