---
title: Vzájemná spolupráce grafického subsystému WPF a systému Direct3D9
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: a66f37e26d8d86e29e81161ea4585737140441ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-and-direct3d9-interoperation"></a>Vzájemná spolupráce grafického subsystému WPF a systému Direct3D9
Můžete zahrnout procesu Direct3D9 obsahu v aplikaci Windows Presentation Foundation (WPF). Toto téma popisuje postup vytvoření procesu Direct3D9 obsah tak, aby se efektivně spolupracuje s WPF.  
  
> [!NOTE]
>  Při použití procesu Direct3D9 obsah v grafickém subsystému WPF, budete také muset myslíte o výkonu. Další informace o optimalizaci výkonu najdete v tématu [otázky výkonu při procesu Direct3D9 a interoperabilita WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Vyrovnávací paměti zobrazení  
 <xref:System.Windows.Interop.D3DImage> Třída spravuje dva vyrovnávací paměti zobrazení, které se nazývají *back vyrovnávací paměti* a *front vyrovnávací paměti*. Back vyrovnávací paměť je váš prostor procesu Direct3D9. Změny zpět vyrovnávací paměti se zkopírují předat do front vyrovnávací paměti při volání <xref:System.Windows.Interop.D3DImage.Unlock%2A> metoda.  
  
 Následující obrázek znázorňuje vztahy mezi back vyrovnávací paměti a front vyrovnávací paměti.  
  
 ![Vyrovnávací paměti zobrazení D3DImage](../../../../docs/framework/wpf/advanced/media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Vytvoření procesu Direct3D9 zařízení  
 K vykreslení procesu Direct3D9 obsahu, musíte vytvořit procesu Direct3D9 zařízení. Existují dva procesu Direct3D9 objekty, které můžete použít k vytvoření zařízení, `IDirect3D9` a `IDirect3D9Ex`. Použít tyto objekty k vytvoření `IDirect3DDevice9` a `IDirect3DDevice9Ex` zařízení, v uvedeném pořadí.  
  
 Vytvoření zařízení voláním jednu z následujících metod.  
  
-   `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
-   `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Ve Windows Vista nebo novějšího operačního systému, použijte `Direct3DCreate9Ex` metoda s zobrazení, který je nakonfigurován pro použití Windows zobrazit ovladač WDDM (Model). Použití `Direct3DCreate9` metoda na jiné platformě.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Dostupnost Direct3DCreate9Ex metody  
 Má d3d9.dll `Direct3DCreate9Ex` metoda pouze v systému Windows Vista nebo novějšího operačního systému. Pokud vytváříte přímo odkaz funkce v systému Windows XP, aplikace se nepodaří načíst. Chcete-li určit, zda `Direct3DCreate9Ex` metoda je podporovaná, načíst knihovnu DLL a vyhledejte adresu proc. Následující kód ukazuje, jak chcete otestovat `Direct3DCreate9Ex` metoda. Úplný příklad, naleznete v tématu [návod: vytváření obsahu procesu Direct3D9 pro hostitelský v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>Vytvoření HWND  
 Vytvoření zařízení vyžaduje, aby popisovačem HWND. Obecně platí můžete vytvořit fiktivní HWND pro procesu Direct3D9 používat. Následující příklad kódu ukazuje, jak vytvořit fiktivní HWND.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Existuje parametry  
 Vytváření zařízení taky vyžaduje `D3DPRESENT_PARAMETERS` struktura, ale pouze několik parametrů, které jsou důležité. Tyto parametry se rozhodli minimalizovat nároky na paměť.  
  
 Nastavte `BackBufferHeight` a `BackBufferWidth` pole na hodnotu 1. Jejich nastavením na hodnotu 0 způsobí je nastaven do dimenze HWND.  
  
 Vždy nastaven `D3DCREATE_MULTITHREADED` a `D3DCREATE_FPU_PRESERVE` příznaky, aby se zabránilo poškozování paměti procesu Direct3D9 a zabránit procesu Direct3D9 změna FPU nastavení.  
  
 Následující kód ukazuje, jak k chybě při inicializaci `D3DPRESENT_PARAMETERS` struktura.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Vytvořením cíle vykreslení Back vyrovnávací paměti  
 Zobrazit obsah procesu Direct3D9 <xref:System.Windows.Interop.D3DImage>, vytvořte procesu Direct3D9 prostor a přiřaďte ho voláním <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> metoda.  
  
### <a name="verifying-adapter-support"></a>Podpora ověřování adaptéru  
 Před vytvořením prostor, ověřte, zda všechny adaptéry podporovat prostor vlastnosti, které vyžadujete. I v případě, že jste vykreslovat jenom jeden adaptér, může se zobrazit okno WPF na každého adaptéru v systému. Vždy byste měli zapsat procesu Direct3D9 kód, který zpracovává konfigurací s více adaptérů a měli byste zkontrolovat všechny adaptéry pro podporu, protože WPF může přesunout na povrch mezi dostupných adaptérů.  
  
 Následující příklad kódu ukazuje, jak můžete zjistit všechny adaptéry v systému procesu Direct3D9 podporují.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Vytváření na povrch  
 Před vytvořením prostor, ověřte, zda možnosti zařízení podporovat dobrý výkon na cílovém operačním systému. Další informace najdete v tématu [otázky výkonu při procesu Direct3D9 a interoperabilita WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Po ověření možnosti zařízení, můžete vytvořit na povrch. Následující příklad kódu ukazuje, jak vytvořit cíl vykreslení.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 Na Windows Vista a novějších operačních systémech, které jsou nakonfigurovány pro použití WDDM, můžete vytvořit texturou cíl vykreslování a předat povrch úroveň 0 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> metoda. Tento přístup se nedoporučuje v systému Windows XP, protože nelze vytvořit cílový texturou možno zablokovat vykreslování a bude snížit výkon.  
  
## <a name="handling-device-state"></a>Zpracování stavu zařízení  
 <xref:System.Windows.Interop.D3DImage> Třída spravuje dva vyrovnávací paměti zobrazení, které se nazývají *back vyrovnávací paměti* a *front vyrovnávací paměti*. Back vyrovnávací paměť je váš prostor Direct3D.  Změny zpět vyrovnávací paměti se zkopírují předat do front vyrovnávací paměti při volání <xref:System.Windows.Interop.D3DImage.Unlock%2A> metoda, kde se zobrazí na hardware. V některých případech nedostupný front vyrovnávací paměti. Kvůli chybějící dostupnosti může být způsobeno zámek obrazovky, přes celou obrazovku výhradní Direct3D – aplikace, přepínání uživatelů nebo dalšími aktivitami systému. V takovém případě aplikace WPF proběhne zpracování <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> událostí.  Jak aplikace odpovídá do front vyrovnávací paměti k dispozici závisí na tom, jestli je WPF povolena a vrátit zpět k vykreslování softwaru. <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> Metoda má přetížení, které přebírá parametr, který určuje, zda WPF spadne zpět na vykreslování softwaru.  
  
 Při volání <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> přetížení nebo volejte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> přetížení s `enableSoftwareFallback` parametr nastaven na `false`, systém vykreslování uvolní jeho odkaz na pozadí vyrovnávací paměti při nedostupný front vyrovnávací paměti a nic se zobrazí. Když front vyrovnávací paměť je opět k dispozici, vyvolá systému vykreslování <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> události pro upozornění aplikace WPF.  Můžete vytvořit obslužnou rutinu události pro <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> událostí restartovat vykreslování znovu s platnou Direct3D – prostor. Pokud chcete restartovat vykreslování, musí volat <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 Při volání <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> přetížení s `enableSoftwareFallback` parametr nastaven na `true`, vykreslování systému zachová jeho odkaz na pozadí vyrovnávací paměti při front vyrovnávací paměť není k dispozici, takže není nutné volat <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> při před vyrovnávací paměť je opět k dispozici.  
  
 Při vykreslování softwaru je povoleno, mohou nastat situace, kdy zařízení uživatele přestane být dostupný, ale vykreslování systému zachová odkaz na povrch Direct3D –. Chcete-li zkontrolovat, jestli má zařízení procesu Direct3D9 není k dispozici, zavolejte `TestCooperativeLevel` metoda. Zkontrolujte zařízení volání Direct3D9Ex `CheckDeviceState` metoda, protože `TestCooperativeLevel` metoda je zastaralá a vždy vrátí hodnotu úspěch. Pokud zařízení uživatele již není dostupná, zavolejte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> k uvolnění WPF na odkaz na pozadí vyrovnávací paměti.  Pokud potřebujete obnovit v zařízení, zavolejte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> s `backBuffer` parametr nastaven na `null`a pak zavolají <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> znovu s `backBuffer` nastavena na platný Direct3D – prostor.  
  
 Volání `Reset` metoda obnovení ze zařízení s neplatnou pouze v případě, že budete implementovat podporu více adaptéru. Jinak verze všech rozhraní procesu Direct3D9 a úplně je znovu vytvořit. Pokud došlo ke změně rozložení adaptéru se neaktualizují procesu Direct3D9 objekty vytvořené před provedením změny.  
  
## <a name="handling-resizing"></a>Zpracování Změna velikosti  
 Pokud <xref:System.Windows.Interop.D3DImage> se zobrazí s rozlišením než jeho nativní velikost je škálovat podle aktuální <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>kromě toho, že <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> je nahrazena pro <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Pokud požadujete vyšší věrnost, musíte vytvořit nový surface kdy kontejner <xref:System.Windows.Interop.D3DImage> změny velikosti.  
  
 Existují tři možných přístupů pro zpracování, změnu velikosti.  
  
-   Účast v systému rozložení a vytvořte nový prostor při změně velikosti. Nevytvářejte příliš mnoho povrchy, protože může vyčerpat nebo fragmentu grafické paměti.  
  
-   Počkejte, dokud událost změny velikosti nedošlo k pro určitou dobu, chcete-li vytvořit nový prostor.  
  
-   Vytvoření <xref:System.Windows.Threading.DispatcherTimer> , zkontroluje dimenze kontejneru několikrát za sekundu.  
  
## <a name="multi-monitor-optimization"></a>Optimalizace více monitorování  
 Výrazně snížený výkon může dojít při vykreslování systém přesune <xref:System.Windows.Interop.D3DImage> na jiné monitorování.  
  
 Na WDDM, také monitorování jsou na stejné grafické karty a použijete `Direct3DCreate9Ex`, neexistuje žádný snížení výkonu. Pokud monitorování jsou v samostatných videokaret, se snižuje výkon. V systému Windows XP je vždy snížit výkon.  
  
 Když <xref:System.Windows.Interop.D3DImage> přesune na jiné monitorování, můžete vytvořit nový prostor na odpovídající adaptér, který má obnovit dobrý výkon.  
  
 Aby se zabránilo snížení výkonu, napište kód speciálně pro případ, více monitorování. Následující seznam obsahuje jeden způsob, jak napsat kód více monitorování.  
  
1.  Hledání bodu služby <xref:System.Windows.Interop.D3DImage> v prostoru obrazovky s `Visual.ProjectToScreen` metoda.  
  
2.  Použití `MonitorFromPoint` GDI metody k vyhledání monitorování, které je zobrazení bodem.  
  
3.  Použití `IDirect3D9::GetAdapterMonitor` metody k vyhledání monitorování procesu Direct3D9 adaptéru, který je na.  
  
4.  Pokud adaptér není stejná jako na adaptér s back vyrovnávací paměť, vyrovnávací paměť nového back vytvořit na nové monitorování a přiřadit ji ke <xref:System.Windows.Interop.D3DImage> back vyrovnávací paměti.  
  
> [!NOTE]
>  Pokud <xref:System.Windows.Interop.D3DImage> přechází monitorování výkonu bude pomalé, s výjimkou v případě WDDM a `IDirect3D9Ex` stejný adaptér. Neexistuje žádný způsob, jak zlepšit výkon v této situaci.  
  
 Následující příklad kódu ukazuje, jak najít aktuálního monitorování.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 Aktualizace monitorování při <xref:System.Windows.Interop.D3DImage> změny velikosti nebo umístění kontejneru nebo aktualizace monitorování pomocí `DispatcherTimer` , aktualizuje několikrát za sekundu.  
  
## <a name="wpf-software-rendering"></a>Vykreslování Software grafického subsystému WPF  
 WPF vykreslí synchronně ve vlákně UI v softwaru v následujících situacích.  
  
-   Tisk  
  
-   <xref:System.Windows.Media.Effects.BitmapEffect>  
  
-   <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Při jedné z těchto situací, systém vykreslování zavolá <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> metoda kopírování vyrovnávací paměti hardwaru do softwaru. Výchozí implementace volá `GetRenderTargetData` metoda s váš prostor. Protože k tomuto volání mimo uzamčení nebo odemčení vzor, může dojít k selhání. V takovém případě `CopyBackBuffer` metoda vrátí `null` a zobrazí se žádný obrázek.  
  
 Můžete přepsat <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> metody volat základní implementaci, a vrátí-li `null`, můžete se vrátit zástupný symbol <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Můžete také implementovat vlastní software vykreslování namísto volání základní implementaci.  
  
> [!NOTE]
>  Pokud úplně vykreslování grafického subsystému WPF v softwaru, <xref:System.Windows.Interop.D3DImage> není zobrazena, protože WPF nemá front vyrovnávací paměti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.D3DImage>  
 [Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [Návod: Vytvoření obsahu Direct3D9 pro hostování v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [Návod: Hostování obsahu Direct3D9 v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
