---
title: Přehled technologie oblastí
ms.date: 03/30/2017
helpviewer_keywords:
- window regions [WPF]
- Win32 code [WPF], WPF interoperation
- Win32 code [WPF], airspace
- airspace [WPF]
- interoperability [WPF], airspace
- Win32 code [WPF], window regions
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
ms.openlocfilehash: e2c93f4471db2d72851a5d5bd8806b59a3e5ee28
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629859"
---
# <a name="technology-regions-overview"></a>Přehled technologie oblastí
Pokud je v aplikaci použito více prezentačních technologií, například WPF, Win32 nebo DirectX, musí sdílet oblasti vykreslování v rámci společného okna nejvyšší úrovně. Toto téma popisuje problémy, které mohou ovlivnit prezentaci a vstup pro vaši aplikaci WPF pro zpracování.  
  
## <a name="regions"></a>Regions  
 V rámci okna nejvyšší úrovně můžete conceptualize, že každý HWND, který obsahuje jednu z technologií aplikace vzájemného provozního prostředí, má svou vlastní oblast (označuje se také jako "vzdušný prostor"). Každý pixel v rámci okna patří k přesně jednomu HWND, který představuje oblast tohoto HWND. (Pouze v případě, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existuje více než jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvek HWND, ale pro účely této diskuze je možné předpokládat, že existuje pouze jedna oblast). Tato oblast znamená, že všechny vrstvy nebo jiné systémy Windows, které se pokoušejí vykreslit nad tento pixel během životního cyklu aplikace, musí být součástí stejné technologie na úrovni vykreslování. Pokus o vykreslení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pixelů v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] důsledku potenciálních výsledků na nežádoucí výsledky a je v rámci rozhraní API pro prochodování co nejvíce povolen.  
  
### <a name="region-examples"></a>Příklady oblastí  
 Následující ilustrace znázorňuje aplikaci, která kombinuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], DirectX a. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Každá technologie používá svou vlastní samostatnou sadu pixelů, která se nepřekrývá, a nedochází k žádným problémům s oblastí.  
  
 ![Příklad aplikace, která kombinuje Win32, DirectX a WPF.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Předpokládejme, že tato aplikace používá pozici ukazatele myši k vytvoření animace, která se pokusí o vykreslení v kterékoli z těchto tří oblastí. Bez ohledu na to, která technologie byla zodpovědná za samotnou animaci, by tato technologie ponarušila oblast druhé dvě. Následující ilustrace znázorňuje pokus o vykreslení kruhu WPF v oblasti Win32.  
  
 ![Pokus o vykreslení kruhu WPF v oblasti Win32.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Dalším porušením je, že se pokusíte použít prolnutí transparentnosti a alfa mezi různými technologiemi.  Na následujícím obrázku je toto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pole v rozporu s [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblastmi rozhraní DirectX a. Vzhledem k tomu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] že pixely v tomto políčku jsou poloprůhledné, musí být vlastněné společně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]rozhraním DirectX i, což není možné.  To je tak další porušení a nelze je sestavit.  
  
 ![Diagram znázorňující pole WPF, které porušuje oblasti Win32 a DirectX](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 Předchozí tři příklady používaly obdélníkové oblasti, ale možné různé tvary.  Například oblast může mít díru. Následující ilustrace znázorňuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblast s obdélníkovou otvorem, což je velikost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kombinovaných oblastí rozhraní DirectX.  
  
 ![Diagram, který zobrazuje oblast Win32 s obdélníkovou děr.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 Oblasti mohou být také zcela nepravoúhlé nebo jakýkoli tvar describable pomocí [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hrgn (region).  
  
 ![Diagram, který zobrazuje oblast, která není obdélníková](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Průhlednost a okna nejvyšší úrovně  
 Správce oken v systému Windows skutečně zpracovává [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HWND. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Každý<xref:System.Windows.Window> je proto HWND. <xref:System.Windows.Window> HWND musí dodržovat obecná pravidla pro libovolný HWND. V rámci tohoto HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] může kód dělat bez ohledu na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] celkovou podporu rozhraní API. Ale pro interakce s ostatními HWND na ploše se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] musí [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dodržovat pravidla zpracování a vykreslování.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje nepravoúhlá okna pomocí [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] rozhraní API – HRGNs pro neobdélníková okna a vrstvená okna pro pixely alfa.  
  
 Konstantní alfa a barevné klíče se nepodporují.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]možnosti vrstveného okna se liší podle platformy.  
  
 Vrstvená okna mohou mít celé okno průsvitně (částečně transparentní) zadáním hodnoty alfa, která se má použít pro každý pixel v okně.  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve skutečnosti podporuje pixel alfa, ale je velmi obtížné ho použít v praktických programech, protože v tomto režimu byste museli nakreslit všechny podřízené HWND sami, včetně dialogových oken a rozevíracích seznamů).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje HRGNs; pro tuto funkci ale neexistují žádná spravovaná rozhraní API. Můžete použít vyvolání platformy a <xref:System.Windows.Interop.HwndSource> volat relevantní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] rozhraní API. Další informace naleznete v tématu [volání nativních funkcí ze spravovaného kódu](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vrstvená okna mají různé možnosti v různých operačních systémech. Důvodem je to [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , že nástroj používá rozhraní DirectX k vykreslování a vrstvená okna byla [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] primárně navržena pro vykreslování, nikoli pro vykreslování rozhraní DirectX.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje hardwarově akcelerovaná vrstvená okna [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] v systémech a novějších. Hardwarově akcelerovaná vrstvená okna [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] na vyžádání podpory od rozhraní Microsoft DirectX, takže tyto možnosti budou záviset na verzi rozhraní Microsoft DirectX na daném počítači.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástroj nepodporuje barevné klíče transparentnosti, protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nemůže zaručit, aby vygeneroval přesnou barvu, zejména když je vykreslování hardwarové-urychlené.  
  
- Pokud je vaše aplikace spuštěná [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)]v systému, vrstvení oken na povrchu rozhraní DirectX blikání se při vykreslování aplikace DirectX vykreslí.  (Vlastní sekvence [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] vykreslování skrývá rozvrstvené okno, pak rozhraní DirectX nakreslí a následně [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] přenese do vrstev okno).  Toto omezení má také okna bezvrstev.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Návod: Hostování hodin WPF v systému Win32](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [Hostování obsahu Win32 v subsystému WPF](hosting-win32-content-in-wpf.md)
