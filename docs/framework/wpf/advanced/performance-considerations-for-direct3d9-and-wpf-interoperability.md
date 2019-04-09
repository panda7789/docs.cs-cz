---
title: Předpokládaný výkon pro Direct3D9 a interoperabilitu WPF
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 1371fa901bebc503a0091f3229a8fd7e6ccc2c86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162630"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Předpokládaný výkon pro Direct3D9 a interoperabilitu WPF
Můžete hostovat pomocí obsahu Direct3D9 <xref:System.Windows.Interop.D3DImage> třídy. Hostování obsahu Direct3D9 může ovlivnit výkon vaší aplikace. Toto téma popisuje osvědčené postupy a optimalizovat výkon při hostování obsahu Direct3D9 v aplikaci Windows Presentation Foundation (WPF). Zahrnout tyto osvědčené postupy použití <xref:System.Windows.Interop.D3DImage> a osvědčené postupy při použití Windows Vista, Windows XP a zobrazí více monitorů.  
  
> [!NOTE]
>  Příklady kódu, které ukazují tyto osvědčené postupy, najdete v části [WPF a systému Direct3D9 vzájemná spolupráce grafického subsystému](wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>Používejte opatrně D3DImage  
 Konání obsahu Direct3D9 <xref:System.Windows.Interop.D3DImage> instance se nezobrazuje jako rychlý jako u čistě aplikace Direct3D. Kopírování na plochu a vyprazdňování vyrovnávací paměť může být nákladná operace. Jako počet <xref:System.Windows.Interop.D3DImage> zvýšení instancí, další vyprazdňování dojde k a zhorší výkon. Proto byste měli použít <xref:System.Windows.Interop.D3DImage> opatrně.  
  
## <a name="best-practices-on-windows-vista"></a>Osvědčené postupy v systému Windows Vista  
 Pro zajištění nejlepšího výkonu v systému Windows Vista s zobrazení, který je nakonfigurován pro použití Windows zobrazit ovladač WDDM (Model), vytvořit na vaší ploše Direct3D9 `IDirect3DDevice9Ex` zařízení. To umožňuje sdílení plochy. Grafická karta musí podporovat `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` a `D3DCAPS2_CANSHARERESOURCE` ovladač funkce v systému Windows Vista. Další nastavení způsobit, že na plochu ke zkopírování prostřednictvím softwaru, což výrazně snižuje výkon.  
  
> [!NOTE]
>  Pokud Windows Vista zobrazení, který je nakonfigurován pro použití Windows XP zobrazení ovladač modelu (XDDM), na plochu vždy kopírovány softwaru, bez ohledu na nastavení. Správné nastavení a grafickou kartu se zobrazí lepší výkon v systému Windows Vista, při použití WDDM vzhledem k tomu, že surface kopie jsou prováděny v hardwaru.  
  
## <a name="best-practices-on-windows-xp"></a>Osvědčené postupy pro Windows XP  
 Pro zajištění nejlepšího výkonu ve Windows XP, který používá Windows XP zobrazení ovladač modelu (XDDM), vytvořit možno zablokovat povrch, který se správně chová při `IDirect3DSurface9::GetDC` metoda je volána. Interně `BitBlt` metoda přenese na plochu napříč zařízeními v hardwaru. `GetDC` Metoda vždy se dá použít na površích XRGB. Nicméně pokud klientský počítač se systémem Windows XP s aktualizací SP3 nebo s aktualizací SP2 a oprava hotfix pro funkce na základě úrovní okno má klient, tato metoda funguje jenom na povrchu ARGB. Grafická karta musí podporovat `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` funkci ovladače.  
  
 Hloubka 16bitové zobrazení plochy může výrazně snížit výkon. 32-bit desktopů, které se doporučuje.  
  
 Pokud vyvíjíte pro Windows Vista a Windows XP, testování výkonu ve Windows XP. Spouštění mimo rozsah video paměti na Windows XP není žádný problém. Kromě toho <xref:System.Windows.Interop.D3DImage> na Windows XP používá další videa paměť a šířku pásma než Windows Vista WDDM, z důvodu potřeby kopie nadbytečná videa paměti. Proto můžete očekávat výkonu horší na Windows XP než v systému Windows Vista se stejným grafického hardwaru.  
  
> [!NOTE]
>  Je k dispozici ve Windows XP a Windows Vista; XDDM WDDM je však k dispozici pouze v systému Windows Vista.  
  
## <a name="general-best-practices"></a>Obecné osvědčené postupy  
 Při vytváření zařízení použít `D3DCREATE_MULTITHREADED` příznak vytváření. To snižuje výkon, ale systém vykreslování WPF volá metody na tomto zařízení z jiného vlákna. Je potřeba správně, postupujte podle protokolu uzamčení tak, aby žádná dvě vlákna ve stejnou dobu přistupovat k zařízení.  
  
 Pokud vaše vykreslování provádí na WPF spravovaná vlákna, důrazně doporučujeme vytvořit zařízení pomocí `D3DCREATE_FPU_PRESERVE` příznak vytváření. Bez tohoto nastavení může snížit přesnost WPF dvojité přesnosti operací D3D vykreslování a způsobit problémy s vykreslováním.  
  
 Dlaždice <xref:System.Windows.Interop.D3DImage> je rychlý, dokud dlaždici povrch bez pow2 bez hardwarovou podporu nebo pokud jste dlaždici <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush> , která obsahuje <xref:System.Windows.Interop.D3DImage>.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Osvědčené postupy pro zobrazí více monitorů  
 Pokud používáte počítač s více monitory, postupujte podle výše popsaným osvědčené postupy. Existují také zvážit další výkonnosti pro konfigurace s více monitory.  
  
 Při vytváření přípravné vyrovnávací paměti, vytvoří se na konkrétní zařízení a adaptér, ale WPF může zobrazit front-vyrovnávací paměť na žádném adaptéru. Kopírování mezi adaptéry k aktualizaci front-vyrovnávací paměti mohou být velmi náročné. V systému Windows Vista, který je nakonfigurován na použití WDDM s více grafických karet a `IDirect3DDevice9Ex` zařízení, pokud je front-vyrovnávací paměť na jiný adaptér, ale stále stejný grafická karta, neexistuje žádné snížení výkonu. Na Windows XP a XDDM s více grafickými kartami, existuje ale penalizace výkonu při front-vyrovnávací paměti se zobrazí na jiný adaptér než přípravné vyrovnávací paměti. Další informace najdete v tématu [WPF a systému Direct3D9 vzájemná spolupráce grafického subsystému](wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Souhrnné informace o výkonu  
 V následující tabulce jsou uvedeny výkonu aktualizace front-vyrovnávací paměti jako funkce operačního systému, formát pixelu a surface lockability. Front-vyrovnávací paměti a přípravné vyrovnávací paměti se předpokládá, že bude stejný adaptér. V závislosti na konfiguraci adaptéru hardwaru aktualizace jsou obvykle mnohem rychlejší než aktualizace softwaru.  
  
|Formát pixelů zařízení Surface|Windows Vista, WDDM a 9Ex|Další konfigurace Windows Vista|Windows XP SP3 nebo s aktualizací SP2 plánovaným bodem obnovení kratším opravy hotfix|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (není možno zablokovat)|**Aktualizace hardwaru**|Aktualizace softwaru|Aktualizace softwaru|Aktualizace softwaru|  
|D3DFMT_X8R8G8B8 (lockable)|**Aktualizace hardwaru**|Aktualizace softwaru|**Aktualizace hardwaru**|**Aktualizace hardwaru**|  
|D3DFMT_A8R8G8B8 (není možno zablokovat)|**Aktualizace hardwaru**|Aktualizace softwaru|Aktualizace softwaru|Aktualizace softwaru|  
|D3DFMT_A8R8G8B8 (lockable)|**Aktualizace hardwaru**|Aktualizace softwaru|**Aktualizace hardwaru**|Aktualizace softwaru|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.D3DImage>
- [Vzájemná spolupráce grafického subsystému WPF a systému Direct3D9](wpf-and-direct3d9-interoperation.md)
- [Návod: Vytvoření obsahu Direct3D9 pro hostování ve WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Návod: Hostování obsahu Direct3D9 ve WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
