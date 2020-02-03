---
title: Technologie interoperability WPF a Direct3D9
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 9ec83c48052e1ef29bb91a6b40b7c76f671bb99f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735179"
---
# <a name="wpf-and-direct3d9-interoperation"></a>Vzájemná spolupráce grafického subsystému WPF a systému Direct3D9
Obsah Direct3D9 můžete zahrnout do aplikace Windows Presentation Foundation (WPF). Toto téma popisuje, jak vytvořit Direct3D9 obsah, aby efektivně spolupracuje s WPF.  
  
> [!NOTE]
> Při použití Direct3D9 obsahu v subsystému WPF je také potřeba zvážit výkon. Další informace o optimalizaci výkonu najdete v tématu [požadavky na výkon pro interoperabilitu Direct3D9 a WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Zobrazit vyrovnávací paměti  
 Třída <xref:System.Windows.Interop.D3DImage> spravuje dvě zobrazovací vyrovnávací paměti, které se nazývají *Zpětná vyrovnávací paměť* a *front-buffer*. Zpětná vyrovnávací paměť je vaše Direct3D9 plocha. Změny ve vyrovnávací paměti jsou při volání metody <xref:System.Windows.Interop.D3DImage.Unlock%2A> zkopírovány do mezipaměti před frontou.  
  
 Následující ilustrace znázorňuje vztah mezi zadní vyrovnávací pamětí a frontou vyrovnávací pamětí.  
  
 ![Vyrovnávací paměti displeje D3DImage](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Vytváření zařízení Direct3D9  
 Pokud chcete vykreslit obsah Direct3D9, musíte vytvořit zařízení Direct3D9. Existují dva objekty Direct3D9, které můžete použít k vytvoření zařízení, `IDirect3D9` a `IDirect3D9Ex`. Tyto objekty použijte k vytvoření `IDirect3DDevice9` a `IDirect3DDevice9Ex` zařízení.  
  
 Vytvořte zařízení voláním jedné z následujících metod.  
  
- `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
- `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 V systému Windows Vista nebo novějším operačním systému použijte metodu `Direct3DCreate9Ex` se zobrazením, které je nakonfigurováno pro použití modelu WDDM (Windows Display Driver Model). Použijte metodu `Direct3DCreate9` na jakékoli jiné platformě.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Dostupnost metody Direct3DCreate9Ex  
 D3d9. dll má metodu `Direct3DCreate9Ex` pouze v systému Windows Vista nebo novějším operačním systému. Pokud přímo propojíte funkci v systému Windows XP, vaše aplikace se nepovede načíst. Chcete-li zjistit, zda je podporována metoda `Direct3DCreate9Ex`, načtěte knihovnu DLL a vyhledejte adresu procedury. Následující kód ukazuje, jak otestovat metodu `Direct3DCreate9Ex`. Úplný příklad kódu naleznete v tématu [Návod: vytvoření obsahu Direct3D9 pro hostování v](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)subsystému WPF.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>Vytvoření HWND  
 Vytvoření zařízení vyžaduje HWND. Obecně můžete vytvořit fiktivní HWND pro Direct3D9, který se má použít. Následující příklad kódu ukazuje, jak vytvořit fiktivní HWND.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Současné parametry  
 Vytvoření zařízení také vyžaduje strukturu `D3DPRESENT_PARAMETERS`, ale je důležité jenom několik parametrů. Tyto parametry se volí pro minimalizaci nároky na paměť.  
  
 Nastavte pole `BackBufferHeight` a `BackBufferWidth` na hodnotu 1. Nastavením na hodnotu 0 způsobí, že budou nastaveny na rozměry HWND.  
  
 Vždy nastavte příznaky `D3DCREATE_MULTITHREADED` a `D3DCREATE_FPU_PRESERVE`, abyste zabránili poškození paměti, kterou používá Direct3D9, a zabráníte tak Direct3D9 ve změně nastavení FPU.  
  
 Následující kód ukazuje, jak inicializovat strukturu `D3DPRESENT_PARAMETERS`.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Vytváření cíle vykreslování vyrovnávací paměti pro obnovení  
 Chcete-li zobrazit Direct3D9 obsah v <xref:System.Windows.Interop.D3DImage>, vytvoříte Direct3D9 plochu a přiřadíte ji voláním metody <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
### <a name="verifying-adapter-support"></a>Ověřování podpory adaptéru  
 Před vytvořením povrchu ověřte, že všechny adaptéry podporují vlastnosti povrchu, které požadujete. I v případě, že vykreslíte pouze jeden adaptér, okno WPF může být zobrazeno na jakémkoli adaptéru v systému. Vždy byste měli napsat kód Direct3D9, který zpracovává konfigurace s více adaptéry, a měli byste zaškrtnout všechny adaptéry pro podporu, protože WPF může přesunout plochu mezi dostupné adaptéry.  
  
 Následující příklad kódu ukazuje, jak kontrolovat všechny adaptéry v systému pro podporu Direct3D9.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Vytváření povrchu  
 Před vytvořením povrchu ověřte, že funkce zařízení podporují dobrý výkon v cílovém operačním systému. Další informace najdete v tématu [požadavky na výkon pro interoperabilitu Direct3D9 a WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Když jste ověřili možnosti zařízení, můžete vytvořit plochu. Následující příklad kódu ukazuje, jak vytvořit cíl vykreslování.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>OVLADAČE  
 V systému Windows Vista a novějších operačních systémech, které jsou nakonfigurovány pro použití WDDM, lze vytvořit cílovou texturu vykreslování a předat plochu úrovně 0 metodě <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>. Tento přístup se nedoporučuje v systému Windows XP, protože nemůžete vytvořit texturu cíle pro vykreslování a výkon bude snížen.  
  
## <a name="handling-device-state"></a>Zpracovává se stav zařízení.  
 Třída <xref:System.Windows.Interop.D3DImage> spravuje dvě zobrazovací vyrovnávací paměti, které se nazývají *Zpětná vyrovnávací paměť* a *front-buffer*. Zpětná vyrovnávací paměť je vaše plocha Direct3D.  Změny vyrovnávací paměti se zkopírují dopředu do mezipaměti při volání metody <xref:System.Windows.Interop.D3DImage.Unlock%2A>, kde se zobrazí na hardwaru. V některých případech je vyrovnávací paměť pro frontu pokaždé neaktivní. Tato nedostatečná dostupnost může být způsobená uzamykáním obrazovky, aplikacemi s podporou Direct3D na celé obrazovce, přepínáním uživatelů nebo jinými činnostmi systému. V takovém případě je aplikace WPF upozorňována zpracováním <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> události.  Způsob, jakým aplikace reaguje na front-vyrovnávací paměť, se stane nedostupnou, záleží na tom, jestli je povolený WPF pro přechod k softwarovému vykreslování. Metoda <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> má přetížení, které přijímá parametr, který určuje, zda se WPF vrátí zpět k softwarovému vykreslování.  
  
 Když zavoláte přetížení <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> nebo zavoláte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> přetížení s parametrem `enableSoftwareFallback` nastaveným na `false`, systém vykreslování uvolní svůj odkaz na zpětnou vyrovnávací paměť, pokud není přední vyrovnávací paměť k dispozici a nic se nezobrazí. Pokud je přední vyrovnávací paměť opět k dispozici, vykreslovací systém vyvolá událost <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> pro informování vaší aplikace WPF.  Můžete vytvořit obslužnou rutinu události pro událost <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> pro opětovné restartování vykreslování s platnou plochou Direct3D. Chcete-li restartovat vykreslování, je nutné volat <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 Když zavoláte metodu <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> přetížení s parametrem `enableSoftwareFallback` nastaveným na hodnotu `true`, systém vykreslování uchová svůj odkaz na zpětnou vyrovnávací paměť, pokud není přední vyrovnávací paměť k dispozici, takže není nutné volat <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>, pokud je přední vyrovnávací paměť opět k dispozici.  
  
 Pokud je povoleno vykreslování softwaru, mohou nastat situace, kdy zařízení uživatele nebude k dispozici, ale systém vykreslování uchovává odkaz na plochu Direct3D. Chcete-li ověřit, zda není zařízení Direct3D9 k dispozici, zavolejte metodu `TestCooperativeLevel`. Chcete-li ověřit, že zařízení Direct3D9Ex volají metodu `CheckDeviceState`, protože metoda `TestCooperativeLevel` je zastaralá a vždy vrátí úspěch. Pokud se zařízení uživatele stane nedostupným, zavolejte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>, aby se uvolnil odkaz na systém WPF na zpětnou vyrovnávací paměť.  Pokud je potřeba resetovat zařízení, zavolejte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> s parametrem `backBuffer` nastaveným na `null`a pak znovu zavolejte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> s `backBuffer` nastavenou na platnou plochu Direct3D.  
  
 Pokud implementujete podporu více adaptérů, volejte metodu `Reset` pro obnovení z neplatného zařízení. V opačném případě uvolněte všechna rozhraní Direct3D9 a znovu je vytvořte. Pokud se změnilo rozložení adaptéru, objekty Direct3D9 vytvořené před změnou se neaktualizují.  
  
## <a name="handling-resizing"></a>Zpracování změny velikosti  
 Pokud se <xref:System.Windows.Interop.D3DImage> zobrazí v jiném rozlišení než jeho nativní velikosti, bude zvětšena podle aktuálního <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>, s tím rozdílem, že <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> nahrazuje <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Pokud požadujete vyšší přesnost, je nutné vytvořit nový povrch, když se změní velikost kontejneru <xref:System.Windows.Interop.D3DImage>.  
  
 Existují tři možné přístupy ke zpracování změny velikosti.  
  
- Podílet se na systému rozložení a při změně velikosti vytvoří novou plochu. Nevytvářejte příliš mnoho povrchů, protože můžete vyčerpat nebo fragmentovat paměť videa.  
  
- Počkejte, dokud nedojde k vytvoření nového povrchu události změny velikosti pro pevný časový úsek.  
  
- Vytvořte <xref:System.Windows.Threading.DispatcherTimer>, který vyhledá dimenze kontejneru několikrát za sekundu.  
  
## <a name="multi-monitor-optimization"></a>Optimalizace více monitorů  
 Výrazně snížený výkon může nastat, pokud systém vykreslování přesune <xref:System.Windows.Interop.D3DImage> do jiného monitoru.  
  
 Na WDDM, pokud jsou monitory na stejné video kartě a používáte `Direct3DCreate9Ex`, nedochází ke snížení výkonu. Pokud se monitory nacházejí na samostatných grafických kartách, sníží se výkon. V systému Windows XP je výkon vždy snížen.  
  
 Když se <xref:System.Windows.Interop.D3DImage> přesune na jiný monitor, můžete vytvořit novou plochu na odpovídajícím adaptéru, aby se obnovil dobrý výkon.  
  
 Abyste se vyhnuli snížení výkonu, napište kód speciálně pro případ s více monitory. Následující seznam uvádí jeden ze způsobů zápisu kódu s více monitory.  
  
1. Vyhledá bod <xref:System.Windows.Interop.D3DImage> v prostoru obrazovky s metodou `Visual.ProjectToScreen`.  
  
2. Pomocí metody `MonitorFromPoint` GDI Najděte monitor, který zobrazuje bod.  
  
3. Pomocí metody `IDirect3D9::GetAdapterMonitor` zjistíte, na kterém adaptéru Direct3D9 se monitorování nachází.  
  
4. Pokud adaptér není stejný jako adaptér s back-bufferou, vytvořte na novém monitorování novou vyrovnávací paměť a přiřaďte ji do vyrovnávací paměti <xref:System.Windows.Interop.D3DImage> zpět.  
  
> [!NOTE]
> Pokud <xref:System.Windows.Interop.D3DImage> prochází monitory, výkon bude pomalý, s výjimkou případu WDDM a `IDirect3D9Ex` na stejném adaptéru. V této situaci neexistuje žádný způsob, jak zlepšit výkon.  
  
 Následující příklad kódu ukazuje, jak najít aktuální monitorování.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 Aktualizujte monitor, když se změní velikost nebo poloha kontejneru <xref:System.Windows.Interop.D3DImage>, nebo aktualizujte monitorování pomocí `DispatcherTimer`, který se aktualizuje několikrát za sekundu.  
  
## <a name="wpf-software-rendering"></a>Vykreslování softwaru WPF  
 WPF sekreslí synchronně na vlákně uživatelského rozhraní v softwaru v následujících situacích.  
  
- Tisk  
  
- <xref:System.Windows.Media.Effects.BitmapEffect>  
  
- <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Pokud nastane jedna z těchto situací, systém vykreslování zavolá metodu <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> ke zkopírování hardwarové vyrovnávací paměti na software. Výchozí implementace volá metodu `GetRenderTargetData` s vaším povrchem. Vzhledem k tomu, že k tomuto volání dochází mimo vzor zámku/odemknutí, může dojít k selhání. V tomto případě metoda `CopyBackBuffer` vrátí `null` a nezobrazí se žádný obrázek.  
  
 Můžete přepsat metodu <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A>, zavolat základní implementaci a pokud vrátí `null`, můžete vrátit zástupné symboly <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Místo volání základní implementace můžete také implementovat vlastní softwarové vykreslování.  
  
> [!NOTE]
> Pokud WPF vykresluje zcela v softwaru, <xref:System.Windows.Interop.D3DImage> není zobrazeno, protože WPF nemá frontu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Interop.D3DImage>
- [Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Návod: Vytvoření obsahu Direct3D9 pro hostování v subsystému WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Návod: Hostování obsahu Direct3D9 v subsystému WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
