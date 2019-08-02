---
title: 'Optimalizace výkonu: Využití výhod hardwaru'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: a47a4aae785d817904c30fe7c865a1c033eb3cca
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709228"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Optimalizace výkonu: Využití výhod hardwaru
Interní architektura nástroje má [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dva kanály pro vykreslování, hardware a software. V tomto tématu najdete informace o těchto kanálech pro vykreslování, které vám pomůžou dělat rozhodnutí o optimalizaci výkonu vašich aplikací.  
  
## <a name="hardware-rendering-pipeline"></a>Kanál pro vykreslování hardwaru  
 Jedním z nejdůležitějších faktorů při určování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výkonu je, že je vykreslování svázáno – více pixelů, které je třeba vykreslit, jsou vyššími náklady na výkon. Další vykreslování, které je možné přesměrovat na grafický procesor (GPU), vám ale umožní získat další výhody výkonu. Kanál pro vykreslování hardwaru aplikaceplněvyužíváfunkcerozhraníMicrosoftDirectXnahardwaru,kterýpodporujeminimálněrozhraníMicrosoftDirectXverze7,0.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Další optimalizace je možné obvěřit hardwarem, který podporuje funkce rozhraní Microsoft DirectX verze 7,0 a funkce PixelShader akceptuje 2.0 +.  
  
## <a name="software-rendering-pipeline"></a>Kanál pro vykreslování softwaru  
 Kanál [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro vykreslování softwaru je zcela vázaný na procesor. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]využívá sady SSE a SSE2 instrukcí v CPU k implementaci optimalizovaného a plně vybaveného rastrového rastrového softwaru. Přechod na software je bezproblémové, kdykoli nemůžete pomocí kanálu pro vykreslování hardwaru vykreslovat funkce aplikace.  
  
 Největší problémy s výkonem, se kterými se setkáte při vykreslování v softwarovém režimu, souvisí s sazbou výplně, která je definována jako počet pixelů, které vygenerujete. Pokud máte obavy o výkon v režimu vykreslování softwaru, pokuste se minimalizovat počet překreslování pixelu. Například pokud máte aplikaci s modrým pozadím, která následně vykreslí mírně transparentní obrázek, budou všechny pixely v aplikaci vykresleny dvakrát. V důsledku toho bude trvat dvojnásobnou dobu pro vykreslování aplikace s imagí, než kdyby bylo pouze modré pozadí.  
  
### <a name="graphics-rendering-tiers"></a>Vrstvy vykreslování grafiky  
 Může být velmi obtížné odhadnout hardwarovou konfiguraci, na které bude vaše aplikace běžet. Můžete ale chtít zvážit návrh, který vaší aplikaci umožní hladce přepínat funkce při spuštění na jiném hardwaru, aby mohl plně využít všechny různé konfigurace hardwaru.  
  
 K tomuto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] účelu poskytuje funkce pro určení schopnosti grafiky systému v době běhu. Funkce grafiky se určuje tak, že se tato grafická karta roztřídí jako jedna ze tří vrstev schopností vykreslování. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zpřístupňuje rozhraní API, které aplikaci umožňuje dotazovat se na úroveň schopností vykreslování. V závislosti na vrstvě vykreslování podporovanou hardwarem pak může aplikace v době běhu převzít různé cesty kódu.  
  
 Funkce grafického hardwaru, které mají největší vliv na úrovně vrstev vykreslování:  
  
- **Video RAM** Množství videopaměti v grafickém hardwaru určuje velikost a počet vyrovnávacích pamětí, které lze použít k skládání grafiky.  
  
- **Pixel shader** Pixel shader je funkce pro zpracování grafiky, která počítá efekty na základě jednotlivých pixelů. V závislosti na rozlišení zobrazené grafiky může být pro každý zobrazovací rámeček zpracováno několik milionů pixelů, které je třeba zpracovat.  
  
- **Vertex shader** Vertex shader je funkce pro zpracování grafiky, která provádí matematické operace s daty vrcholu objektu.  
  
- **Podpora více textur** Podpora více textur odkazuje na možnost použití dvou nebo více různých textur během operace prolnutí u objektu 3D grafiky. Úroveň podpory více textur je určena počtem jednotek s více texturami v grafickém hardwaru.  
  
 Funkce pixel shader, vertex shader a s více texturami slouží k definování specifických úrovní verze DirectX, které jsou pak použity k definování různých vrstev vykreslování v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Funkce grafického hardwaru určují schopnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování aplikace. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Systém definuje tři úrovně vykreslování:  
  
- **Vrstva vykreslování 0** Žádná hardwarová akcelerace grafiky Úroveň verze DirectX je nižší než verze 7,0.  
  
- **Vrstva vykreslování 1** Hardwarová akcelerace částečné grafiky. Úroveň verze DirectX je větší nebo rovna verzi 7,0 a **nižší** než verze 9,0.  
  
- **Vrstva vykreslování 2** Většina grafických funkcí používá hardwarovou akceleraci grafiky. Úroveň verze DirectX je větší nebo rovna verzi 9,0.  
  
 Další informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] úrovních vykreslování naleznete v tématu [úrovně vykreslování grafiky](graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Viz také:

- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další výkonnostní doporučení](optimizing-performance-other-recommendations.md)
