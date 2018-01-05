---
title: "Předpokládaný výkon pro Direct3D9 a interoperabilitu WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8142125eae26b15f12652d28fdf0c34f19d49c4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Předpokládaný výkon pro Direct3D9 a interoperabilitu WPF
Je možné hostovat procesu Direct3D9 obsahu pomocí <xref:System.Windows.Interop.D3DImage> třídy. Hostování procesu Direct3D9 obsahu může ovlivnit výkon aplikace. Toto téma popisuje osvědčené postupy za účelem optimalizace výkonu při hostování procesu Direct3D9 obsahu v aplikaci Windows Presentation Foundation (WPF). Tyto doporučené postupy zahrnují použití <xref:System.Windows.Interop.D3DImage> a osvědčené postupy, pokud používáte systém Windows Vista, Windows XP, a zobrazí se více monitorování.  
  
> [!NOTE]
>  Příklady kódu, která ukazují tyto doporučené postupy najdete v tématu [WPF a vzájemná spolupráce procesu Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>Doporučujeme použít D3DImage  
 Obsah procesu Direct3D9 hostované v <xref:System.Windows.Interop.D3DImage> instance nevykresluje jako rychlý jako u čistý Direct3D – aplikace. Kopírování na povrch a vyprazdňování vyrovnávací paměť může být nákladná operace. Jako počet <xref:System.Windows.Interop.D3DImage> nárůst instance, abyste vyprázdnili další dojde, a snižuje výkon. Proto byste měli používat <xref:System.Windows.Interop.D3DImage> opatrně.  
  
## <a name="best-practices-on-windows-vista"></a>Osvědčené postupy v systému Windows Vista  
 Nejlepšího výkonu v systému Windows Vista s zobrazení, který je nakonfigurován pro použití Windows zobrazit ovladač WDDM (Model), vytvořte na váš prostor procesu Direct3D9 `IDirect3DDevice9Ex` zařízení. To umožňuje sdílení plochy. Grafická karta musí podporovat `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` a `D3DCAPS2_CANSHARERESOURCE` možnosti ovladače v systému Windows Vista. Další nastavení způsobit prostor ke zkopírování prostřednictvím software, který výrazně snižuje výkon.  
  
> [!NOTE]
>  Pokud systém Windows Vista obsahuje zobrazení, který je nakonfigurován pro použití systému Windows XP zobrazit ovladač modelu (XDDM), na povrch zkopírován vždy prostřednictvím softwaru, bez ohledu na nastavení. Správné nastavení a grafické karty zobrazí se lepší výkon v systému Windows Vista při použití WDDM protože prostor kopie jsou prováděny v hardwaru.  
  
## <a name="best-practices-on-windows-xp"></a>Osvědčené postupy v systému Windows XP  
 Pro nejlepší výkon v systému Windows XP, který používá systém Windows XP zobrazení ovladačů modelu (XDDM), vytvořte možno zablokovat prostor, který chovat správně při `IDirect3DSurface9::GetDC` metoda je volána. Interně `BitBlt` metoda přenese na povrch na zařízeních v hardwaru. `GetDC` Metoda vždy funguje na XRGB plochy. Ale pokud klientský počítač se systémem Windows XP s aktualizací SP3 nebo SP2 a pokud má klient taky opravy hotfix pro funkci vrstvený okno, tato metoda funguje jenom na ARGB plochy. Grafická karta musí podporovat `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` schopností ovladačů.  
  
 Zobrazení plochy 16bitové hloubka může výrazně snížit výkon. Doporučuje se 32bitové plochy.  
  
 Pokud vyvíjíte pro systém Windows Vista a Windows XP, test výkonu v systému Windows XP. Obavu, nedošly grafické paměti v systému Windows XP. Kromě toho <xref:System.Windows.Interop.D3DImage> na systému Windows XP používá další grafické paměti a šířky pásma než Windows Vista WDDM, z důvodu kopii nezbytné velmi grafické paměti. Proto můžete očekávat výkon horší na systému Windows XP než v systému Windows Vista má pro stejný hardware videa.  
  
> [!NOTE]
>  XDDM je k dispozici v systému Windows XP a Windows Vista; WDDM je však k dispozici pouze v systému Windows Vista.  
  
## <a name="general-best-practices"></a>Obecné osvědčené postupy  
 Při vytváření zařízení pomocí `D3DCREATE_MULTITHREADED` vytvoření příznak. Tím se snižuje výkon, ale systém vykreslování WPF volá metody v tomto zařízení z jiného vlákna. Je nutné správně, postupujte podle protokol uzamčení, aby žádné dvěma vlákny přístupu k zařízení ve stejnou dobu.  
  
 Pokud vaše vykreslování provádí ve vlákně WPF spravované, důrazně doporučujeme vytvořit zařízení pomocí `D3DCREATE_FPU_PRESERVE` vytvoření příznak. Bez tohoto nastavení můžete vykreslování D3D snižte přesnost operations WPF dvojitou přesností a způsobit problémy vykreslování.  
  
 Dlaždice <xref:System.Windows.Interop.D3DImage> je rychlé, pokud dlaždici prostor jiný pow2 bez podpory hardwaru, nebo pokud jste dlaždici <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush> obsahující <xref:System.Windows.Interop.D3DImage>.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Osvědčené postupy pro více monitorování zobrazí  
 Pokud používáte počítač, který má více monitorů, postupujte podle výše popsaných osvědčené postupy. Existují také některé další výkonem pro konfigurace s více monitory.  
  
 Když vytvoříte back vyrovnávací paměti, vytváří se na konkrétní zařízení a adaptér, ale WPF může zobrazit front vyrovnávací paměť na každého adaptéru. Kopírování mezi adaptéry aktualizovat front vyrovnávací paměť může být velmi náročná. V systému Windows Vista, který je nakonfigurován pro použití WDDM s více videokaret a `IDirect3DDevice9Ex` zařízení, pokud front vyrovnávací paměť je na jiný adaptér, ale stále stejné grafické karty, neexistuje žádný snížení výkonu. V systému Windows XP a XDDM s více videokaret, je však snížení výkonu významné při front vyrovnávací paměti se zobrazí na jiný adaptér než back vyrovnávací paměť. Další informace najdete v tématu [WPF a vzájemná spolupráce procesu Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Souhrnné informace o výkonu  
 V následující tabulce jsou uvedeny výkonu aktualizace front vyrovnávací paměti jako funkce operačního systému, Pixelový formát a prostor lockability. Přední vyrovnávací paměti a zpět vyrovnávací paměť se předpokládá, že na stejný adaptér. V závislosti na konfiguraci adaptéru hardwaru aktualizace jsou obvykle mnohem rychlejší než aktualizace softwaru.  
  
|Prostor Pixelový formát|Windows Vista, WDDM a 9Ex|Ostatní konfigurace systému Windows Vista|Windows XP SP3 nebo s aktualizací SP2 s oprav hotfix|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (není možno zablokovat)|**Aktualizace hardwaru**|Aktualizace softwaru|Aktualizace softwaru|Aktualizace softwaru|  
|D3DFMT_X8R8G8B8 (možno zablokovat)|**Aktualizace hardwaru**|Aktualizace softwaru|**Aktualizace hardwaru**|**Aktualizace hardwaru**|  
|D3DFMT_A8R8G8B8 (není možno zablokovat)|**Aktualizace hardwaru**|Aktualizace softwaru|Aktualizace softwaru|Aktualizace softwaru|  
|D3DFMT_A8R8G8B8 (možno zablokovat)|**Aktualizace hardwaru**|Aktualizace softwaru|**Aktualizace hardwaru**|Aktualizace softwaru|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.D3DImage>  
 [Vzájemná spolupráce grafického subsystému WPF a systému Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)  
 [Návod: Vytvoření obsahu Direct3D9 pro hostování v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [Návod: Hostování obsahu Direct3D9 v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
