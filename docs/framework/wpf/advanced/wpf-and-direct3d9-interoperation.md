---
title: Vzájemná spolupráce grafického subsystému WPF a systému Direct3D9
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 5fccd49b4f6fa64e5902197423d732ba0b31790e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917440"
---
# <a name="wpf-and-direct3d9-interoperation"></a>Vzájemná spolupráce grafického subsystému WPF a systému Direct3D9
Obsah Direct3D9 můžete zahrnout do aplikace Windows Presentation Foundation (WPF). Toto téma popisuje, jak vytvořit Direct3D9 obsah, aby efektivně spolupracuje s WPF.  
  
> [!NOTE]
> Při použití Direct3D9 obsahu v subsystému WPF je také potřeba zvážit výkon. Další informace o optimalizaci výkonu najdete v tématu [požadavky na výkon pro interoperabilitu Direct3D9 a WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Zobrazit vyrovnávací paměti  
 Třída spravuje dvě zobrazované vyrovnávací paměti, které se nazývají *Zpětná vyrovnávací paměť* a *front-buffer*. <xref:System.Windows.Interop.D3DImage> Zpětná vyrovnávací paměť je vaše Direct3D9 plocha. Změny vyrovnávací paměti jsou při volání <xref:System.Windows.Interop.D3DImage.Unlock%2A> metody zkopírovány do mezipaměti před frontou.  
  
 Následující ilustrace znázorňuje vztah mezi zadní vyrovnávací pamětí a frontou vyrovnávací pamětí.  
  
 ![Vyrovnávací paměti displeje D3DImage](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Vytváření zařízení Direct3D9  
 Pokud chcete vykreslit obsah Direct3D9, musíte vytvořit zařízení Direct3D9. Existují dva objekty Direct3D9, které můžete použít k vytvoření zařízení `IDirect3D9` a. `IDirect3D9Ex` Tyto objekty použijte k vytvoření `IDirect3DDevice9` a `IDirect3DDevice9Ex` zařízení, v uvedeném pořadí.  
  
 Vytvořte zařízení voláním jedné z následujících metod.  
  
- `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
- `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 V systému Windows Vista nebo novějším operačním systému použijte `Direct3DCreate9Ex` metodu se zobrazením, které je nakonfigurováno pro použití modelu WDDM (Windows Display Driver Model). `Direct3DCreate9` Použijte metodu na jakékoli jiné platformě.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Dostupnost metody Direct3DCreate9Ex  
 D3d9. dll má `Direct3DCreate9Ex` metodu pouze v systému Windows Vista nebo novějším operačním systému. Pokud přímo propojíte funkci v systému Windows XP, vaše aplikace se nepovede načíst. Chcete-li zjistit `Direct3DCreate9Ex` , zda je metoda podporována, načtěte knihovnu DLL a vyhledejte adresu procedury. Následující kód ukazuje, jak otestovat `Direct3DCreate9Ex` metodu. Úplný příklad kódu naleznete v tématu [Návod: Vytváření obsahu Direct3D9 pro hostování v subsystému WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>Vytvoření HWND  
 Vytvoření zařízení vyžaduje HWND. Obecně můžete vytvořit fiktivní HWND pro Direct3D9, který se má použít. Následující příklad kódu ukazuje, jak vytvořit fiktivní HWND.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Současné parametry  
 Vytvoření zařízení také vyžaduje `D3DPRESENT_PARAMETERS` strukturu, ale je důležité pouze několik parametrů. Tyto parametry se volí pro minimalizaci nároky na paměť.  
  
 Nastavte pole `BackBufferWidth` a na hodnotu 1. `BackBufferHeight` Nastavením na hodnotu 0 způsobí, že budou nastaveny na rozměry HWND.  
  
 Vždy nastavte `D3DCREATE_MULTITHREADED` příznaky a `D3DCREATE_FPU_PRESERVE` , abyste zabránili poškození paměti, kterou používá Direct3D9, a zabráníte tak Direct3D9 ve změně nastavení FPU.  
  
 Následující kód ukazuje, jak inicializovat `D3DPRESENT_PARAMETERS` strukturu.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Vytváření cíle vykreslování vyrovnávací paměti pro obnovení  
 Chcete-li zobrazit Direct3D9 obsah <xref:System.Windows.Interop.D3DImage>v, vytvoříte Direct3D9 plochu a přiřadíte ji <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> voláním metody.  
  
### <a name="verifying-adapter-support"></a>Ověřování podpory adaptéru  
 Před vytvořením povrchu ověřte, že všechny adaptéry podporují vlastnosti povrchu, které požadujete. I v případě, že vykreslíte pouze jeden adaptér, okno WPF může být zobrazeno na jakémkoli adaptéru v systému. Vždy byste měli napsat kód Direct3D9, který zpracovává konfigurace s více adaptéry, a měli byste zaškrtnout všechny adaptéry pro podporu, protože WPF může přesunout plochu mezi dostupné adaptéry.  
  
 Následující příklad kódu ukazuje, jak kontrolovat všechny adaptéry v systému pro podporu Direct3D9.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Vytváření povrchu  
 Před vytvořením povrchu ověřte, že funkce zařízení podporují dobrý výkon v cílovém operačním systému. Další informace najdete v tématu [požadavky na výkon pro interoperabilitu Direct3D9 a WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Když jste ověřili možnosti zařízení, můžete vytvořit plochu. Následující příklad kódu ukazuje, jak vytvořit cíl vykreslování.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>OVLADAČE  
 V systému Windows Vista a novějších operačních systémech, které jsou nakonfigurovány pro použití WDDM, lze vytvořit cílovou texturu vykreslování a předat do <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> metody plochu 0. Tento přístup se nedoporučuje v systému Windows XP, protože nemůžete vytvořit texturu cíle pro vykreslování a výkon bude snížen.  
  
## <a name="handling-device-state"></a>Zpracovává se stav zařízení.  
 Třída spravuje dvě zobrazované vyrovnávací paměti, které se nazývají *Zpětná vyrovnávací paměť* a *front-buffer*. <xref:System.Windows.Interop.D3DImage> Zpětná vyrovnávací paměť je vaše plocha Direct3D.  Změny ve vyrovnávací paměti se zkopírují dopředu do vyrovnávací paměti při volání <xref:System.Windows.Interop.D3DImage.Unlock%2A> metody, kde se zobrazí na hardwaru. V některých případech je vyrovnávací paměť pro frontu pokaždé neaktivní. Tato nedostatečná dostupnost může být způsobená uzamykáním obrazovky, aplikacemi s podporou Direct3D na celé obrazovce, přepínáním uživatelů nebo jinými činnostmi systému. V takovém případě je aplikace WPF upozorněna zpracováním <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> události.  Způsob, jakým aplikace reaguje na front-vyrovnávací paměť, se stane nedostupnou, záleží na tom, jestli je povolený WPF pro přechod k softwarovému vykreslování. <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> Metoda má přetížení, které přebírá parametr, který určuje, zda se WPF vrátí zpět k softwarovému vykreslování.  
  
 Při volání <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> přetížení nebo <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> volání přetížení s `enableSoftwareFallback` parametrem nastaveným na `false`, systém vykreslování uvolní svůj odkaz na zpětnou vyrovnávací paměť v případě, že je přední vyrovnávací paměť nedostupná a nic se nestane Zobrazit. Pokud je přední vyrovnávací paměť opět k dispozici, vykreslovací systém vyvolá <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> událost, aby upozornila vaši aplikaci WPF.  Můžete vytvořit obslužnou rutinu události pro <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> událost pro opětovné restartování vykreslování s platnou plochou Direct3D. Chcete-li restartovat vykreslování, je <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>nutné zavolat.  
  
 Když zavoláte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> `enableSoftwareFallback` přetížení s parametrem nastaveným `true`na, systém vykreslování uchová svůj odkaz na zpětnou vyrovnávací paměť, pokud není přední vyrovnávací paměť k dispozici, takže není nutné volat <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> , pokud je přední vyrovnávací paměť je opět k dispozici.  
  
 Pokud je povoleno vykreslování softwaru, mohou nastat situace, kdy zařízení uživatele nebude k dispozici, ale systém vykreslování uchovává odkaz na plochu Direct3D. Chcete-li ověřit, zda není zařízení Direct3D9 k dispozici, zavolejte `TestCooperativeLevel` metodu. Chcete-li ověřit Direct3D9Ex zařízení, `CheckDeviceState` volejte metodu, `TestCooperativeLevel` protože metoda je zastaralá a vždy vrátí úspěch. Pokud se zařízení uživatele stane nedostupným, <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> volejte odkaz na verzi WPF systému WPF na zpětnou vyrovnávací paměť.  Pokud je potřeba resetovat zařízení, <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> zavolejte `backBuffer` s parametrem nastaveným na `null`a potom zavolejte <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> znovu s `backBuffer` nastaveným na platnou plochu Direct3D.  
  
 `Reset` Volejte metodu pro obnovení z neplatného zařízení pouze v případě, že implementujete podporu více adaptérů. V opačném případě uvolněte všechna rozhraní Direct3D9 a znovu je vytvořte. Pokud se změnilo rozložení adaptéru, objekty Direct3D9 vytvořené před změnou se neaktualizují.  
  
## <a name="handling-resizing"></a>Zpracování změny velikosti  
 Pokud je zobrazen v jiném rozlišení než jeho nativní velikost, je zvětšena podle aktuálního <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>, s tím rozdílem, <xref:System.Windows.Media.BitmapScalingMode.Fant>že <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> je nahrazeno. <xref:System.Windows.Interop.D3DImage>  
  
 Pokud požadujete vyšší přesnost, je nutné při <xref:System.Windows.Interop.D3DImage> změně velikosti kontejneru vytvořit novou plochu.  
  
 Existují tři možné přístupy ke zpracování změny velikosti.  
  
- Podílet se na systému rozložení a při změně velikosti vytvoří novou plochu. Nevytvářejte příliš mnoho povrchů, protože můžete vyčerpat nebo fragmentovat paměť videa.  
  
- Počkejte, dokud nedojde k vytvoření nového povrchu události změny velikosti pro pevný časový úsek.  
  
- <xref:System.Windows.Threading.DispatcherTimer> Vytvořte, který vyhledá dimenze kontejneru několikrát za sekundu.  
  
## <a name="multi-monitor-optimization"></a>Optimalizace více monitorů  
 Výrazně snížený výkon může být způsobeno tím, že <xref:System.Windows.Interop.D3DImage> systém vykreslování přesune na jiný monitor.  
  
 Na WDDM, pokud jsou monitory na stejné video kartě a `Direct3DCreate9Ex`používáte, nedochází ke snížení výkonu. Pokud se monitory nacházejí na samostatných grafických kartách, sníží se výkon. V systému Windows XP je výkon vždy snížen.  
  
 <xref:System.Windows.Interop.D3DImage> Když přejdete na jiný monitor, můžete vytvořit novou plochu na odpovídajícím adaptéru, aby se obnovil dobrý výkon.  
  
 Abyste se vyhnuli snížení výkonu, napište kód speciálně pro případ s více monitory. Následující seznam uvádí jeden ze způsobů zápisu kódu s více monitory.  
  
1. Vyhledá bod <xref:System.Windows.Interop.D3DImage> v prostoru `Visual.ProjectToScreen` obrazovky metodou.  
  
2. Pomocí metody `MonitorFromPoint` GDI Najděte monitor, který zobrazuje bod.  
  
3. `IDirect3D9::GetAdapterMonitor` Pomocí metody Najděte, na kterém adaptéru Direct3D9 se monitorování nachází.  
  
4. Pokud adaptér není stejný jako adaptér s back-bufferou, vytvořte na novém monitorování novou vyrovnávací paměť a přiřaďte ji do <xref:System.Windows.Interop.D3DImage> vyrovnávací paměti.  
  
> [!NOTE]
> Pokud dojde <xref:System.Windows.Interop.D3DImage> ke sledování přeložených operací, výkon bude pomalý, s výjimkou případu WDDM a `IDirect3D9Ex` na stejném adaptéru. V této situaci neexistuje žádný způsob, jak zlepšit výkon.  
  
 Následující příklad kódu ukazuje, jak najít aktuální monitorování.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 Aktualizujte monitor, když <xref:System.Windows.Interop.D3DImage> se změní velikost nebo poloha kontejneru, nebo aktualizujte monitorování `DispatcherTimer` pomocí aktualizace, která bude několikrát za sekundu.  
  
## <a name="wpf-software-rendering"></a>Vykreslování softwaru WPF  
 WPF sekreslí synchronně na vlákně uživatelského rozhraní v softwaru v následujících situacích.  
  
- Tisk  
  
- <xref:System.Windows.Media.Effects.BitmapEffect>  
  
- <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Pokud nastane jedna z těchto situací, systém vykreslování zavolá <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> metodu pro zkopírování hardwarové vyrovnávací paměti na software. Výchozí implementace volá `GetRenderTargetData` metodu s vaší plochou. Vzhledem k tomu, že k tomuto volání dochází mimo vzor zámku/odemknutí, může dojít k selhání. V tomto případě `CopyBackBuffer` se metoda vrátí `null` a nezobrazí se žádný obrázek.  
  
 Můžete přepsat <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> metodu, zavolat základní implementaci a pokud se vrátí `null`, můžete vrátit zástupný symbol <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Místo volání základní implementace můžete také implementovat vlastní softwarové vykreslování.  
  
> [!NOTE]
> Pokud WPF vykresluje zcela v softwaru, není <xref:System.Windows.Interop.D3DImage> zobrazen, protože WPF nemá front-buffer.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.D3DImage>
- [Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Návod: Vytváření obsahu Direct3D9 pro hostování v subsystému WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Návod: Hostování Direct3D9 obsahu v subsystému WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
