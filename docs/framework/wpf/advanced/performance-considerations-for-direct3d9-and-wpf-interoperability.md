---
title: Požadavky na výkon pro interoperabilitu Direct3D9 a WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 2445732c27d210a41da26303d6a9ce07ef6fcc94
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743928"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Předpokládaný výkon pro Direct3D9 a interoperabilitu WPF
Direct3D9 obsah můžete hostovat pomocí třídy <xref:System.Windows.Interop.D3DImage>. Hostování Direct3D9 obsahu může ovlivnit výkon vaší aplikace. V tomto tématu jsou popsány osvědčené postupy pro optimalizaci výkonu při hostování Direct3D9 obsahu v aplikaci Windows Presentation Foundation (WPF). Tyto osvědčené postupy zahrnují použití <xref:System.Windows.Interop.D3DImage> a osvědčených postupů při zobrazení Windows Vista, Windows XP a multi-monitor.  
  
> [!NOTE]
> Příklady kódu, které předvádějí tyto osvědčené postupy, najdete v tématu [spolupráce WPF a Direct3D9](wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>Používejte D3DImage zřídka.  
 Obsah Direct3D9 hostovaný v instanci <xref:System.Windows.Interop.D3DImage> se nevykresluje jako rychlá jako v aplikaci čistě Direct3D. Zkopírování povrchu a vyprázdnění vyrovnávací paměti příkazů může být nákladné operace. Vzhledem k tomu, že se počet instancí <xref:System.Windows.Interop.D3DImage> zvyšuje, dochází k většímu počtu vyprázdnění a snížení výkonu. Proto byste měli použít <xref:System.Windows.Interop.D3DImage> bez omezeného využití.  
  
## <a name="best-practices-on-windows-vista"></a>Osvědčené postupy v systému Windows Vista  
 Pro dosažení nejlepšího výkonu v systému Windows Vista se zobrazením, které je nakonfigurováno pro použití modelu WDDM (Windows Display Driver Model), vytvořte Direct3D9 plochu na zařízení `IDirect3DDevice9Ex`. To umožňuje sdílení Surface. Grafická karta musí podporovat možnosti ovladače `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` a `D3DCAPS2_CANSHARERESOURCE` v systému Windows Vista. Jakékoli jiné nastavení způsobí, že se plocha bude kopírovat prostřednictvím softwaru, což výrazně snižuje výkon.  
  
> [!NOTE]
> Pokud má systém Windows Vista zobrazení, které je nakonfigurováno pro použití modelu XDDM (Windows XP Display Driver Model), je plocha vždy zkopírována prostřednictvím softwaru bez ohledu na nastavení. Pomocí správného nastavení a videokarty se při použití ovladače WDDM v systému Windows Vista zobrazí lepší výkon, protože se kopie povrchu provádějí v hardwaru.  
  
## <a name="best-practices-on-windows-xp"></a>Osvědčené postupy v systému Windows XP  
 Pro zajištění nejlepšího výkonu v systému Windows XP, který používá model ovladače zobrazení systému Windows XP (XDDM), vytvořte uzamykatelný povrch, který se bude chovat správně při volání metody `IDirect3DSurface9::GetDC`. Interně `BitBlt` metoda přenáší plochu napříč zařízeními v hardwaru. Metoda `GetDC` vždy funguje na plochách XRGB. Pokud však na klientském počítači běží systém Windows XP s aktualizací SP3 nebo SP2 a klient má také opravu hotfix pro funkci vrstveného okna, tato metoda funguje pouze na ARGB površích. Grafická karta musí podporovat možnosti ovladače `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`.  
  
 16bitová hloubka zobrazení plochy může významně snížit výkon. Doporučuje se 32 Desktop.  
  
 Pokud vyvíjíte pro systémy Windows Vista a Windows XP, otestujte výkon v systému Windows XP. Nedostatek grafické paměti v systému Windows XP je obavou. Kromě toho <xref:System.Windows.Interop.D3DImage> v systému Windows XP k dispaměti větší množství videí a šířku pásma než Windows Vista WDDM z důvodu potřebné kopie dodatečné videopaměti. Proto můžete očekávat, že výkon systému Windows XP je horší než v systému Windows Vista pro stejný hardware videa.  
  
> [!NOTE]
> XDDM je k dispozici v systémech Windows XP i Windows Vista; WDDM je však k dispozici pouze v systému Windows Vista.  
  
## <a name="general-best-practices"></a>Obecné osvědčené postupy  
 Při vytváření zařízení použijte příznak vytváření `D3DCREATE_MULTITHREADED`. Tím se snižuje výkon, ale systém vykreslování WPF volá metody v tomto zařízení z jiného vlákna. Ujistěte se, že se správně dodržují protokol uzamykání, takže se zařízení nepřístupí současně.  
  
 Pokud je vykreslování prováděno ve spravovaném vlákně WPF, důrazně doporučujeme vytvořit zařízení s příznakem vytváření `D3DCREATE_FPU_PRESERVE`. Bez tohoto nastavení může vykreslování D3D snížit přesnost operací s dvojitou přesností WPF a způsobit problémy s vykreslováním.  
  
 Dělení <xref:System.Windows.Interop.D3DImage> je rychlé, Pokud neprovedete dlaždici mimo pow2 plochu bez hardwarové podpory, nebo Pokud podržíte <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush>, které obsahují <xref:System.Windows.Interop.D3DImage>.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Osvědčené postupy pro zobrazení s více monitory  
 Pokud používáte počítač, který obsahuje více monitorů, měli byste postupovat podle výše uvedených osvědčených postupů. K dispozici jsou také další požadavky na výkon pro konfiguraci s více monitory.  
  
 Když vytvoříte zpětnou vyrovnávací paměť, vytvoří se na konkrétním zařízení a adaptéru, ale WPF může zobrazit front-buffer na jakémkoli adaptéru. Kopírování v rámci adaptérů pro aktualizaci front-buffer může být velmi nákladné. V systému Windows Vista, který je nakonfigurovaný tak, aby používal WDDM s více grafickými kartami a s `IDirect3DDevice9Ex`m zařízením, pokud je front-buffer na jiném adaptéru, ale stále stejná grafická karta, nedošlo k žádnému snížení výkonu. V systému Windows XP a v XDDM s více grafickými kartami je ale při zobrazení vyrovnávací paměti na jiném adaptéru než vyrovnávací paměť k dispozici významná snížení výkonu. Další informace najdete v tématu [spolupráce WPF a Direct3D9](wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Souhrn výkonu  
 Následující tabulka ukazuje výkon přední aktualizace vyrovnávací paměti jako funkce operačního systému, formátu pixelů a možností uzamčení povrchu. Předpokládá se, že je front-buffer a zpětná vyrovnávací paměť na stejném adaptéru. V závislosti na konfiguraci adaptéru jsou aktualizace hardwaru všeobecně mnohem rychlejší než aktualizace softwaru.  
  
|Formát Surface pixelů|Windows Vista, WDDM a 9Ex|Další konfigurace systému Windows Vista|Systém Windows XP SP3 nebo SP2 s aktualizací hotfix|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (není uzamykatelný)|**Aktualizace hardwaru**|Aktualizace softwaru|Aktualizace softwaru|Aktualizace softwaru|  
|D3DFMT_X8R8G8B8 (lockable)|**Aktualizace hardwaru**|Aktualizace softwaru|**Aktualizace hardwaru**|**Aktualizace hardwaru**|  
|D3DFMT_A8R8G8B8 (není uzamykatelný)|**Aktualizace hardwaru**|Aktualizace softwaru|Aktualizace softwaru|Aktualizace softwaru|  
|D3DFMT_A8R8G8B8 (lockable)|**Aktualizace hardwaru**|Aktualizace softwaru|**Aktualizace hardwaru**|Aktualizace softwaru|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Interop.D3DImage>
- [Vzájemná spolupráce grafického subsystému WPF a systému Direct3D9](wpf-and-direct3d9-interoperation.md)
- [Návod: Vytvoření obsahu Direct3D9 pro hostování v subsystému WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Návod: Hostování obsahu Direct3D9 v subsystému WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
