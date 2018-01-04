---
title: "Přehled technologie oblastí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- window regions [WPF]
- Win32 code [WPF], WPF interoperation
- Win32 code [WPF], airspace
- airspace [WPF]
- interoperability [WPF], airspace
- Win32 code [WPF], window regions
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 142973793fd002925bbe2b4b09ce8e6d34553031
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="technology-regions-overview"></a>Přehled technologie oblastí
Pokud se používají více technologie prezentace v aplikaci, například WPF, Win32 nebo DirectX, sdílejí musí vykreslování oblasti v rámci běžných období nejvyšší úrovně. Toto téma popisuje problémy, které by mohly ovlivnit prezentace a vstup pro vaši aplikaci WPF součinnosti.  
  
## <a name="regions"></a>Oblasti  
 V okně nejvyšší úrovně a conceptualize který každý HWND, který zahrnuje technologií součinnosti aplikace má vlastní oblasti (také nazývané "vzdušného prostoru"). Každý pixelů v rámci okna patří do přesně jeden HWND, který představuje oblast této HWND. (Přesněji řečeno, je více než jedna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oblast, pokud je více než jedna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, ale pro účely tohoto vysvětlení, můžete předpokládat, existuje pouze jeden). Oblast znamená všechny vrstvy nebo jiných windows, které se pokoušejí o vykreslení výše této pixelů během životního cyklu aplikace se musí být součástí stejné úrovni vykreslení technologie. Při pokusu o vykreslení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pixelů přes [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] vede k nežádoucí výsledky a je zakázaná co nejvíce prostřednictvím vzájemná spolupráce [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].  
  
### <a name="region-examples"></a>Příklady oblast  
 Následující obrázek znázorňuje, zkombinuje aplikace [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)], a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Každou technologii používá vlastní samostatný, které se nepřekrývají sadu pixelů a zde nejsou žádné problémy oblast.  
  
 ![Okno, které nemá vzdušného prostoru problémy](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle01.png "MigrationInteropArchitectArticle01")  
  
 Předpokládejme, že tato aplikace používá k vytvoření animace, která se pokusí vykreslení pomocí kteréhokoli z těchto tří oblastí umístění ukazatele myši. Bez ohledu na to, technologii, která je zodpovědná za animace sám sebe že technologie by způsobila porušení oblasti Další dvě. Následující obrázek znázorňuje pokus o vykreslení WPF kruh přes Win32 oblast.  
  
 ![Spolupráce diagram](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle02.png "MigrationInteropArchitectArticle02")  
  
 Jiné porušení je, pokud se pokusíte použít průhlednost/alfa míchání mezi různé technologie.  Na následujícím obrázku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] porušuje pole [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] oblasti. Protože pixelů v tom, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Poloprůhledné pole se by musí být vlastnictvím obě [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], což není možné.  Tak, aby to jiného narušení a nemůže být sestaven.  
  
 ![Spolupráce diagram](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle03.png "MigrationInteropArchitectArticle03")  
  
 V předchozích příkladech tři používá obdélníková oblasti, ale je možné, různých tvarů.  Oblast může mít například díru. Následující obrázek znázorňuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblasti s obdélníkovou díru Toto je velikost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] oblasti kombinaci.  
  
 ![Spolupráce diagram](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle04.png "MigrationInteropArchitectArticle04")  
  
 Oblasti může být také úplně nepravoúhlý, nebo jakékoli describable ve tvaru [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HRGN (oblast).  
  
 ![Spolupráce diagram](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle05.png "MigrationInteropArchitectArticle05")  
  
## <a name="transparency-and-top-level-windows"></a>Průhlednost a nejvyšší úrovně Windows  
 Okno správce v systému Windows zpracovává jenom skutečně [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HWND. Proto každých [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> je popisovačem HWND. <xref:System.Windows.Window> HWND musíte dodržet obecná pravidla pro všechny HWND. V rámci této HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kódu můžete provést, ať celkovým [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] podporovat. Ale pro interakce s další HWND na ploše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] musíte dodržet [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zpracování a generování pravidel.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje obdélníkový windows pomocí [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]– HRGNs pro obdélníkový windows a windows vrstev pro platformu alpha za pixelů.  
  
 Konstantní alpha a barvu klíče nejsou podporovány.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]Vrstvený okno Možnosti se liší podle platformy.  
  
 Vrstvený windows provádět celé okno průhledná (poloprůhledné) tak, že zadáte hodnotu alfa a platí pro každý pixel v okně.  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve skutečnosti alpha podporuje za pixelů, ale je velmi obtížné použít v programech, praktické, protože v tomto režimu potřebovali byste k vykreslení všechny podřízené HWND sami, včetně dialogová okna a rozevíracích seznamů).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje HRGNs; Existují však ne spravované [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] pro tuto funkci. Můžete použít platformy vyvolání a <xref:System.Windows.Interop.HwndSource> volat odpovídajícího [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Další informace najdete v tématu [volání nativních funkcí ze spravovaného kódu](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vrstvený windows mají různé možnosti v různých operačních systémech. Důvodem je, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] k vykreslení, a vrstveného windows byly primárně určený pro [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] vykreslování, není [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] vykreslování.  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]hardware podporuje accelerated vrstvený windows na [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] a novější. Hardware accelerated vrstvený windows na [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] vyžadovat podporu [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)], takže možnosti závisí na verzi [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] na tomto počítači.  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nepodporuje průhlednost barva klíče, protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nemůže zaručit k vykreslení barvu přesný jste požádali, zejména při vykreslování je akcelerován hardwaru.  
  
-   Pokud vaše aplikace běží na [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)], na základě systému windows na [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] povrchy blikat při [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] vykreslí aplikace.  (Pořadí vykreslování skutečné je, že [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] skryje okno vrstveného pak [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] nevykresluje a potom [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] okno vrstveného vrátí zpět).  Jinou hodnotu než[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vrstveného windows také mít toto omezení.  
  
## <a name="see-also"></a>Viz také  
 [Vzájemná spolupráce grafického subsystému WPF a systému Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Návod: Hostování hodin WPF v systému Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-clock-in-win32.md)  
 [Hostování obsahu Win32 v subsystému WPF](../../../../docs/framework/wpf/advanced/hosting-win32-content-in-wpf.md)
