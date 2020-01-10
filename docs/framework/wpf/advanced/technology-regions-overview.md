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
ms.openlocfilehash: 0b6ad222737f992da3074770fb5a2bff17860c00
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740290"
---
# <a name="technology-regions-overview"></a>Přehled technologie oblastí
Pokud je v aplikaci použito více prezentačních technologií, například WPF, Win32 nebo DirectX, musí sdílet oblasti vykreslování v rámci společného okna nejvyšší úrovně. Toto téma popisuje problémy, které mohou ovlivnit prezentaci a vstup pro vaši aplikaci WPF pro zpracování.  
  
## <a name="regions"></a>Oblasti  
 V rámci okna nejvyšší úrovně můžete conceptualize, že každý HWND, který obsahuje jednu z technologií aplikace vzájemného provozního prostředí, má svou vlastní oblast (označuje se také jako "vzdušný prostor"). Každý pixel v rámci okna patří k přesně jednomu HWND, který představuje oblast tohoto HWND. (V případě, že je k dispozici více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, ale pro účely této diskuze existuje více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oblastí, můžete předpokládat, že existuje pouze jedna). Tato oblast znamená, že všechny vrstvy nebo jiné systémy Windows, které se pokoušejí vykreslit nad tento pixel během životního cyklu aplikace, musí být součástí stejné technologie na úrovni vykreslování. Při pokusu o vykreslení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pixelů přes Win32 vede k nežádoucím výsledkům a v rámci rozhraní API pro mezichody se nepovolují co nejvíce.  
  
### <a name="region-examples"></a>Příklady oblastí  
 Následující ilustrace znázorňuje aplikaci, která kombinuje Win32, DirectX a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Každá technologie používá svou vlastní samostatnou sadu pixelů, která se nepřekrývá, a nedochází k žádným problémům s oblastí.  
  
 ![Příklad aplikace, která kombinuje Win32, DirectX a WPF.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Předpokládejme, že tato aplikace používá pozici ukazatele myši k vytvoření animace, která se pokusí o vykreslení v kterékoli z těchto tří oblastí. Bez ohledu na to, která technologie byla zodpovědná za samotnou animaci, by tato technologie ponarušila oblast druhé dvě. Následující ilustrace znázorňuje pokus o vykreslení kruhu WPF v oblasti Win32.  
  
 ![Pokus o vykreslení kruhu WPF v oblasti Win32.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Dalším porušením je, že se pokusíte použít prolnutí transparentnosti a alfa mezi různými technologiemi.  Na následujícím obrázku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rámeček porušuje oblasti Win32 a DirectX. Vzhledem k tomu, že pixely v tomto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ovém poli jsou poloprůhledné, musí být vlastněné společně rozhraním DirectX i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], což není možné.  To je tak další porušení a nelze je sestavit.  
  
 ![Diagram znázorňující pole WPF, které porušuje oblasti Win32 a DirectX](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 Předchozí tři příklady používaly obdélníkové oblasti, ale možné různé tvary.  Například oblast může mít díru. Následující ilustrace znázorňuje oblast Win32 s pravoúhlou otvorem, což je velikost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a oblastí DirectX v kombinaci.  
  
 ![Diagram, který zobrazuje oblast Win32 s obdélníkovou děr.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 Oblasti mohou být také zcela nepravoúhlé nebo jakýkoli tvar describable pomocí Win32 HRGN (region).  
  
 ![Diagram, který zobrazuje oblast, která není obdélníková](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Průhlednost a okna nejvyšší úrovně  
 Správce oken v systému Windows skutečně zpracovává HWND v prostředí Win32. Proto každý [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> je HWND. <xref:System.Windows.Window> HWND musí dodržovat obecná pravidla pro libovolný HWND. V rámci tohoto HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kód může dělat bez ohledu na to, jak celková [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API podporuje. Pro interakce s ostatními HWND na ploše ale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] musí dodržovat pravidla pro zpracování a vykreslování Win32.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje nepravoúhlá okna pomocí rozhraní Win32 API – HRGNs pro neobdélníková okna a vrstvená okna pro pixely na pixel alfa.  
  
 Konstantní alfa a barevné klíče se nepodporují.  Možnosti okna vrstev v prostředí Win32 se liší podle platformy.  
  
 Vrstvená okna mohou mít celé okno průsvitně (částečně transparentní) zadáním hodnoty alfa, která se má použít pro každý pixel v okně.  (Win32 ve skutečnosti podporuje pixel alfa, ale je velmi obtížné ho použít v praktických programech, protože v tomto režimu byste museli nakreslit všechny podřízené HWND sami, včetně dialogových oken a rozevíracích seznamů).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje HRGNs; pro tuto funkci ale neexistují žádná spravovaná rozhraní API. K volání odpovídajících rozhraní Win32 API můžete použít vyvolání platformy a <xref:System.Windows.Interop.HwndSource>. Další informace naleznete v tématu [volání nativních funkcí ze spravovaného kódu](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vrstvených oken mají různé možnosti v různých operačních systémech. Důvodem je to, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] využívá rozhraní DirectX k vykreslování a vrstvená okna byla primárně navržena pro vykreslování GDI, nikoli pro vykreslování rozhraní DirectX.  
  
- WPF podporuje hardwarově akcelerovaná okna s vrstvami.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nepodporuje barevné klíče transparentnosti, protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nemůže zaručit, aby vygeneroval přesnou barvu, zejména pokud je vykreslování hardwarové-urychlené.  
  
## <a name="see-also"></a>Viz také:

- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Návod: Hostování hodin WPF v systému Win32](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [Hostování obsahu Win32 v subsystému WPF](hosting-win32-content-in-wpf.md)
