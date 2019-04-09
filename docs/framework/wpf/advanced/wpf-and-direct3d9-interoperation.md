---
title: Vzájemná spolupráce grafického subsystému WPF a systému Direct3D9
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 04a668ea18177d2a174569f064d9102239dd5e7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199320"
---
# <a name="wpf-and-direct3d9-interoperation"></a>Vzájemná spolupráce grafického subsystému WPF a systému Direct3D9
Můžete zahrnout obsahu Direct3D9 v aplikaci Windows Presentation Foundation (WPF). Toto téma popisuje postup vytvoření obsahu Direct3D9 tak, aby efektivně spolupracuje s WPF.  
  
> [!NOTE]
>  Při použití obsahu Direct3D9 v subsystému WPF, musíte také uvažovat o výkonu. Další informace o tom, jak optimalizovat výkon, naleznete v tématu [důležité informace o výkonu pro Direct3D9 a interoperabilitu WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Vyrovnávací paměti zobrazení  
 <xref:System.Windows.Interop.D3DImage> Třída spravuje dvě vyrovnávací paměti zobrazení, které se volají *přípravné vyrovnávací paměti* a *front-vyrovnávací paměti*. Přípravné vyrovnávací paměti je vaše plocha Direct3D9. Změny přípravné vyrovnávací paměti jsou zkopírovány vpřed na front-vyrovnávací paměti při volání <xref:System.Windows.Interop.D3DImage.Unlock%2A> metody.  
  
 Následující ilustrace znázorňuje vztah mezi přípravné vyrovnávací paměti a front-vyrovnávací paměti.  
  
 ![Vyrovnávací paměti zobrazení D3DImage](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Vytvoření zařízení Direct3D9  
 K vykreslení obsahu Direct3D9, musíte vytvořit Direct3D9 zařízení. Existují dva Direct3D9 objekty, které můžete použít k vytvoření zařízení, `IDirect3D9` a `IDirect3D9Ex`. Můžete vytvořit tyto objekty `IDirect3DDevice9` a `IDirect3DDevice9Ex` zařízení, v uvedeném pořadí.  
  
 Vytvoření zařízení voláním jedné z následujících metod.  
  
-   `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
-   `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Ve Windows Vista nebo novějšího operačního systému, použijte `Direct3DCreate9Ex` metodu s zobrazení, který je nakonfigurován pro použití Windows zobrazit ovladač WDDM (Model). Použití `Direct3DCreate9` metoda na libovolné platformě.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Dostupnost Direct3DCreate9Ex – metoda  
 Má d3d9.dll `Direct3DCreate9Ex` metoda pouze u Windows Vista nebo novějším operačním systémem. Pokud připojíte přímo funkce ve Windows XP, vaše aplikace se nepodaří načíst. Chcete-li zjistit, zda `Direct3DCreate9Ex` metoda je podporována, načíst knihovnu DLL a vyhledejte adresu proc. Následující kód ukazuje, jak otestovat `Direct3DCreate9Ex` metody. Příklad úplného kódu, naleznete v tématu [názorný postup: Vytvoření obsahu Direct3D9 pro hostování v subsystému WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>Vytvoření prvku HWND  
 Vytvoření zařízení vyžaduje popisovačem HWND. Obecně platí vytvořte fiktivního HWND pro Direct3D9 používat. Následující příklad kódu ukazuje, jak vytvořit fiktivního HWND.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>K dispozici parametry  
 Vytvoření zařízení také vyžaduje `D3DPRESENT_PARAMETERS` struktury, ale pouze několik parametrů, které jsou důležité. Tyto parametry se rozhodli minimalizovat nároky na paměť.  
  
 Nastavte `BackBufferHeight` a `BackBufferWidth` pole na hodnotu 1. Nastavení na hodnotu 0 způsobí, že se jejich nastavení na dimenze HWND.  
  
 Vždycky nastavený `D3DCREATE_MULTITHREADED` a `D3DCREATE_FPU_PRESERVE` příznaky zabránit poškození paměti používá Direct3D9 a systému Direct3D9 zabránit ve změně nastavení FPU.  
  
 Následující kód ukazuje, jak inicializovat `D3DPRESENT_PARAMETERS` struktury.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Vytvoření cíle vykreslování přípravné vyrovnávací paměti  
 K zobrazení obsahu Direct3D9 v <xref:System.Windows.Interop.D3DImage>, vytvořte Direct3D9 plochu a přiřaďte ho voláním <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> metody.  
  
### <a name="verifying-adapter-support"></a>Ověřuje se, jestli adaptér podpory  
 Před vytvořením povrch, ověřte, že všechny adaptéry podporují surface vlastnosti, které potřebujete. I v případě, že vykreslovat jenom jeden adaptér může zobrazit okno WPF na všech adaptérů v systému. Měli byste vždy psát Direct3D9 kód, který zpracovává konfigurací s více adaptérů a byste měli počítač zkontrolovat všechny adaptéry pro podporu, protože WPF může přejít na plochu mezi jsou k dispozici adaptéry.  
  
 Následující příklad kódu ukazuje, jak můžete zkontrolovat všechny adaptéry v systému pro Direct3D9 podporují.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Vytváření na plochu  
 Před vytvořením povrch, ověřte, zda možnosti zařízení podporovat dobrý výkon na cílovém operačním systému. Další informace najdete v tématu [důležité informace o výkonu pro Direct3D9 a interoperabilitu WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Po ověření schopnosti zařízení, můžete vytvořit na plochu. Následující příklad kódu ukazuje, jak vytvořit cíl vykreslování.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 Ve Windows Vista a novějších operačních systémech, které jsou nakonfigurovány pro použití WDDM, vytvořte textur cíl vykreslování a předat povrch úroveň 0 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> metody. Tento přístup není doporučen na Windows XP, protože nelze vytvořit cílovou texturu možno zablokovat vykreslování a sníží výkon.  
  
## <a name="handling-device-state"></a>Stav zařízení  
 <xref:System.Windows.Interop.D3DImage> Třída spravuje dvě vyrovnávací paměti zobrazení, které se volají *přípravné vyrovnávací paměti* a *front-vyrovnávací paměti*. Přípravné vyrovnávací paměti je vaše plocha rozhraní Direct3D.  Změny přípravné vyrovnávací paměti jsou zkopírovány vpřed na front-vyrovnávací paměti při volání <xref:System.Windows.Interop.D3DImage.Unlock%2A> metody, kde se zobrazí na hardwaru. V některých případech front-vyrovnávací paměť k dispozici. Tato nedostatečná dostupnosti může být způsobeno uzamčení obrazovky, exkluzivní aplikace Direct3D celou obrazovku, přepínání uživatelů nebo jiných aktivit systému. Pokud k tomu dojde, vaše aplikace WPF proběhne zpracování <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> událostí.  Jak vaše aplikace reaguje na front-vyrovnávací paměť k dispozici závisí na tom, zda je povoleno WPF náhradní softwarové vykreslování. <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> Metoda má přetížení přijímající parametr, který určuje, zda WPF spadne zpět na softwarové vykreslování.  
  
 Při volání <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> přetížení nebo volání <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> přetížení s `enableSoftwareFallback` parametr nastaven na `false`, systém vykreslování uvolní svůj odkaz na přípravné vyrovnávací paměti při front-vyrovnávací paměti přestane být k dispozici a nic není zobrazí. Když front-vyrovnávací paměti je opět k dispozici, systém vykreslování vyvolá <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> události upozornit aplikaci WPF.  Můžete vytvořit obslužná rutina události <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> události restartovat vykreslování znovu s platnou povrch rozhraní Direct3D. Pokud chcete restartovat vykreslování, musí volat <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 Při volání <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> přetížení s `enableSoftwareFallback` parametr nastaven na `true`, vykreslování systému zachová svůj odkaz na přípravné vyrovnávací paměti při front-vyrovnávací paměti stane nedostupným, takže není nutné volat <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> při front vyrovnávací paměť je opět k dispozici.  
  
 Když je povoleno vykreslování části softwaru, může být situacích, kdy zařízení uživatele k dispozici, ale systém vykreslování uchovává odkaz na povrchu Direct3D. Chcete-li zkontrolovat, zda Direct3D9 zařízení není k dispozici, zavolejte `TestCooperativeLevel` metody. Ke kontrole Direct3D9Ex zařízení volání `CheckDeviceState` metody, protože `TestCooperativeLevel` metoda je zastaralá a vždy vrátí hodnotu úspěch. Pokud uživatel zařízení je nedostupné, zavolejte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> uvolnit odkaz na WPF na přípravné vyrovnávací paměti.  Pokud potřebujete obnovit v zařízení, zavolejte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> s `backBuffer` parametr nastaven na `null`a pak vyvolejte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> znovu s `backBuffer` nastavena na platný povrch rozhraní Direct3D.  
  
 Volání `Reset` metoda obnovení ze zařízení s neplatnou pouze v případě, že implementujete podporu více adaptérů. V opačném případě uvolnit všechna rozhraní pro Direct3D9 a znovu je vytvořte zcela. Pokud došlo ke změně rozložení adaptér, se neaktualizují Direct3D9 objekty vytvořené před provedením změny.  
  
## <a name="handling-resizing"></a>Zpracování změny velikosti  
 Pokud <xref:System.Windows.Interop.D3DImage> se zobrazí v řešení než jeho nativní velikost se škálovat podle aktuální <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>, s tím rozdílem, že <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> nahrazuje <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Pokud budete potřebovat vyšší přesnosti, je třeba vytvořit nové zařízení surface, kdy kontejner <xref:System.Windows.Interop.D3DImage> změní velikost.  
  
 Existují tři možné přístupy k zpracování změny velikosti.  
  
-   Součástí systému rozložení a vytvořte novou plochu při změně velikosti. Nevytvářejte příliš mnoho zařízení Surface, protože může vyčerpat nebo fragment grafické paměti.  
  
-   Počkejte, až událost změny velikosti nedošlo k pro určitou dobu, chcete-li vytvořit novou plochu.  
  
-   Vytvoření <xref:System.Windows.Threading.DispatcherTimer> , která zkontroluje dimenze kontejneru několikrát za sekundu.  
  
## <a name="multi-monitor-optimization"></a>Optimalizace více monitorů  
 Výrazně nižší výkon může dojít při vykreslování systém přesune <xref:System.Windows.Interop.D3DImage> na jiný monitor.  
  
 Na WDDM, za předpokladu monitorování jsou na stejném videa karty a použijete `Direct3DCreate9Ex`, neexistuje žádné snížení výkonu. Pokud monitorování na samostatné grafické karty, se snižuje výkon. Na Windows XP je vždy snížení výkonu.  
  
 Když <xref:System.Windows.Interop.D3DImage> přesune na jiný monitor, vytvoříte novou plochu na odpovídající adaptér, který má obnovit dobrého výkonu.  
  
 Aby se zabránilo snížení výkonu, napište kód speciálně pro případ více monitorů. Následující seznam ukazuje jeden ze způsobů vytvoření kódu více monitorů.  
  
1.  Najít bod <xref:System.Windows.Interop.D3DImage> v prostor na obrazovce s `Visual.ProjectToScreen` metody.  
  
2.  Použití `MonitorFromPoint` GDI metody k vyhledání monitorování, které se zobrazuje bod.  
  
3.  Použití `IDirect3D9::GetAdapterMonitor` metody k vyhledání adaptéru, pro který Direct3D9 monitorování zapnutý.  
  
4.  Pokud adaptér není stejný jako adaptér s přípravné vyrovnávací paměti, vytvořte nový přípravné vyrovnávací paměti na nové monitorování a přiřaďte ho k <xref:System.Windows.Interop.D3DImage> přípravné vyrovnávací paměti.  
  
> [!NOTE]
>  Pokud <xref:System.Windows.Interop.D3DImage> přechází monitorování výkonu bude pomalé, s výjimkou v případě WDDM a `IDirect3D9Ex` na stejný adaptér. Neexistuje žádný způsob, jak zlepšit výkon v této situaci.  
  
 Následující příklad kódu ukazuje, jak najít aktuální monitorování.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 Aktualizovat monitorování při <xref:System.Windows.Interop.D3DImage> kontejneru velikost nebo pozice změny nebo aktualizace monitorování s využitím `DispatcherTimer` , která aktualizuje několikrát za sekundu.  
  
## <a name="wpf-software-rendering"></a>WPF softwarové vykreslování  
 WPF vykreslí synchronně ve vlákně uživatelského rozhraní v softwaru v následujících situacích.  
  
-   Tisk  
  
-   <xref:System.Windows.Media.Effects.BitmapEffect>  
  
-   <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Při jedné z těchto situací vykreslování systém volá <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> metoda kopírování vyrovnávací paměti hardware software. Výchozí implementace volá `GetRenderTargetData` metodu s vaší povrchu. Protože toto volání dochází mimo vzor Zamknout/odemknout, může dojít k selhání. V takovém případě `CopyBackBuffer` vrátí metoda `null` a zobrazí se žádný obrázek.  
  
 Můžete přepsat <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> metody volat základní implementaci a vrátí-li `null`, můžete se vrátit zástupný symbol <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Můžete také implementovat vlastní softwarové vykreslování namísto volání základní implementaci.  
  
> [!NOTE]
>  Pokud WPF je zcela vykreslování v softwaru, <xref:System.Windows.Interop.D3DImage> neuvádíme, protože WPF nemá front-vyrovnávací paměti.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.D3DImage>
- [Předpokládaný výkon pro Direct3D9 a interoperabilitu WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Návod: Vytvoření obsahu Direct3D9 pro hostování ve WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Návod: Hostování obsahu Direct3D9 ve WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
