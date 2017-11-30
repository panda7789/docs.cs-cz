---
title: "Návod: Hostování hodin WPF v systému Win32"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55e5aa633e3d788ac8acaa09684c92b8608e7cfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Návod: Hostování hodin WPF v systému Win32
Uvést [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uvnitř [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace, použijte <xref:System.Windows.Interop.HwndSource>, který poskytuje HWND, která obsahuje vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Nejdřív vytvoříte <xref:System.Windows.Interop.HwndSource>, předá podobná CreateWindow parametry.  Pak můžete zjistit <xref:System.Windows.Interop.HwndSource> o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu chcete uvnitř ho.  Nakonec můžete získat HWND mimo <xref:System.Windows.Interop.HwndSource>. Tento návod ukazuje, jak vytvořit smíšený [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uvnitř [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace, která reimplements operačního systému **vlastnosti data a času** dialogové okno.  
  
## <a name="prerequisites"></a>Požadavky  
 V tématu [WPF a vzájemná spolupráce Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## <a name="how-to-use-this-tutorial"></a>Jak používat v tomto kurzu  
 V tomto kurzu soustřeďuje na důležité kroky k vytvoření aplikace součinnosti. Tento kurz je zálohovaný díky ukázku, [ukázka vzájemná spolupráce hodin Win32](http://go.microsoft.com/fwlink/?LinkID=160051), ale tato ukázka je neodpovídajícím end produktu. V tomto kurzu dokumenty kroky, jako kdyby byly počínaje existující [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu vlastní, možná již existující projekt a byly přidání hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do vaší aplikace. Můžete porovnat svůj produkt end s [ukázka vzájemná spolupráce hodin Win32](http://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Návod Windows Presentation Framework uvnitř Win32 (HwndSource)  
 Následující obrázek ukazuje zamýšlené koncovým produkt v tomto kurzu:  
  
 ![Dialogové okno Vlastnosti data a času](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")  
  
 Tento dialog můžete znovu vytvořit tak, že vytvoříte C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]a použití editoru dialogových oken k vytvoření následující:  
  
 ![Dialogové okno Vlastnosti data a času](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")  
  
 (Není potřeba použít [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] používat <xref:System.Windows.Interop.HwndSource>, a není potřeba použít C++ k zápisu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programy, ale to je celkem obvyklý způsob, jak to provést a různě dobře stupňový kurz vysvětlení).  
  
 Je třeba provést pět konkrétní dílčích kroků, aby bylo možné umístit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny do dialogu:  
  
1.  Povolit vaše [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu volat spravovaného kódu (**/CLR**) změnou nastavení projektu v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
2.  Vytvoření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> v samostatné knihovny DLL.  
  
3.  Uveďte, která [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> uvnitř <xref:System.Windows.Interop.HwndSource>.  
  
4.  Získat popisovačem HWND pro tento <xref:System.Windows.Controls.Page> pomocí <xref:System.Windows.Interop.HwndSource.Handle%2A> vlastnost.  
  
5.  Použití [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] rozhoduje, kam umístit HWND v rámci delší [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace  
  
## <a name="clr"></a>/ CLR  
 Prvním krokem je chcete-li to nespravované [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu do jednoho, které můžete volat spravovaného kódu.  Použít / CLR – možnost kompilátoru, která bude propojit potřebné knihovny DLL, kterou chcete použít a upravit metodu Main pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Povolit používání spravovaného kódu v projektu C++: klikněte pravým tlačítkem na projekt win32clock a vyberte **vlastnosti**.  Na **Obecné** stránka vlastností (výchozí), změnit modul Common Language Runtime podporu, aby `/clr`.  
  
 Dál přidejte odkazy na knihovny DLL, které jsou nezbytné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: knihovně PresentationCore.dll, knihovně PresentationFramework.dll, System.dll, knihovně WindowsBase.dll, UIAutomationProvider.dll a UIAutomationTypes.dll. (Tyto pokyny předpokládají, že je nainstalovaný operační systém na jednotce C:.)  
  
1.  Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** a v tomto dialogovém okně:  
  
2.  Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .  
  
3.  Klikněte na tlačítko **přidat nový odkaz**, klikněte na kartu Procházet, zadejte C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll a klikněte na tlačítko OK.  
  
4.  Opakujte pro knihovně PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.  
  
5.  Opakujte pro knihovně WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.  
  
6.  Opakujte pro UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.  
  
7.  Opakujte pro UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.  
  
8.  Klikněte na tlačítko **přidat nový odkaz**vyberte System.dll a klikněte na tlačítko **OK**.  
  
9. Klikněte na tlačítko **OK** ukončíte win32clock stránek vlastností pro přidání odkazů.  
  
 Nakonec přidejte `STAThreadAttribute` k `_tWinMain` metoda pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 Tento atribut informuje [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] , když inicializuje [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], měla by používat model jeden model typu apartment (STA), který je potřebný pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).  
  
## <a name="create-a-windows-presentation-framework-page"></a>Vytvoření stránky Windows Presentation Framework  
 Dále vytvořte knihovnu DLL, kterou definuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>. Často je nejjednodušší vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> jako samostatná aplikace a zápis a ladění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] část tímto způsobem.  Po dokončení tohoto projektu, mohou být změněny na knihovnu DLL kliknete pravým tlačítkem projekt kliknete na **vlastnosti**, přejdete na stránku aplikace a změna výstupní typ pro knihovny tříd systému Windows.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Je pak možné kombinovat projektu knihovny dll s [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu (jedno řešení, které obsahuje dva projekty) – klikněte pravým tlačítkem na řešení, vyberte **Add\Existing projektu**.  
  
 Použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] knihovny dll z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu, budete muset přidat odkaz:  
  
1.  Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .  
  
2.  Klikněte na tlačítko **přidat nový odkaz**.  
  
3.  Klikněte **projekty** kartě.  Vyberte WPFClock, klikněte na tlačítko OK.  
  
4.  Klikněte na tlačítko **OK** ukončíte win32clock stránek vlastností pro přidání odkazů.  
  
## <a name="hwndsource"></a>HwndSource  
 V dalším kroku použijete <xref:System.Windows.Interop.HwndSource> aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> vypadat popisovačem HWND.  Tento blok kódu přidáte do souboru C++:  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
  
    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
        HwndSource^ source = gcnew HwndSource(  
            0, // class style  
            WS_VISIBLE | WS_CHILD, // style  
            0, // exstyle  
            x, y, width, height,  
            "hi", // NAME  
            IntPtr(parent)        // parent window   
            );  
  
        UIElement^ page = gcnew WPFClock::Clock();  
        source->RootVisual = page;  
        return (HWND) source->Handle.ToPointer();  
    }  
}  
}  
```  
  
 Toto je dlouhý úsek kódu, který může použít vysvětlení.  První část je různé klauzule, takže není nutné k plnému určení všechna volání:  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 Potom můžete definovat funkci, která vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, PUT <xref:System.Windows.Interop.HwndSource> kolem a vrátí HWND:  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 Nejdřív vytvoříte <xref:System.Windows.Interop.HwndSource>, jejíž parametry jsou podobné CreateWindow:  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 Potom můžete vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu voláním jeho konstruktoru třídy:  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 Potom připojíte stránku a <xref:System.Windows.Interop.HwndSource>:  
  
```  
source->RootVisual = page;  
```  
  
 A na posledním řádku vrátí HWND pro <xref:System.Windows.Interop.HwndSource>:  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a>Umístění Hwnd  
 Teď, když máte popisovačem HWND, který obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny, které potřebujete k odeslání tohoto HWND uvnitř [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialogové okno.  Pokud budete vědět, právě umístění HWND, by stačí předat tento velikost a umístění `GetHwnd` funkce definovaného dříve.  Ale používá zdrojového souboru k definování dialogovém okně, takže jste si jisti, přesně, kde jsou umístěny žádné HWND.  Můžete použít [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] editoru dialogového okna se umístí [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] statické řídit, kam chcete hodiny přejdete ("Insert hodiny zde") a použít jej k umístění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny.  
  
 Kde zpracováváte WM_INITDIALOG, použijete `GetDlgItem` načtení HWND pro zástupný symbol statické:  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 Můžete pak vypočítat velikost a umístění tento zástupný symbol STATIC, tak můžete umístit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] taktovací na tomto místě:  
  
 Rect – obdélníku;  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 Potom můžete skrýt zástupný symbol statické:  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 A vytvořte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] taktovací HWND v tomto umístění:  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 Chcete-li kurz zajímavé a k vytvoření reálné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny, budete muset vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] taktovací ovládací prvek v tomto okamžiku. Můžete provést tak nejčastěji v značek, s několika obslužné rutiny událostí v kódu. Vzhledem k tomu, že v tomto kurzu je o vzájemné spolupráci a nikoli o ovládací prvek návrhu, kód pro dokončení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny je k dispozici zde jako blok kódu bez diskrétní pokyny pro vytváření nebo co znamená každou část. Nebojte se, že experimentovat s tímto kódem změnit vzhled a chování nebo funkce ovládacího prvku.  
  
 Zde je kód:  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 A tady je doprovodné kódu:  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 Konečný výsledek bude vypadat takto:  
  
 ![Dialogové okno Vlastnosti data a času](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")  
  
 K porovnání vaší konečný výsledek na kód, který vytvořil tento snímek obrazovky, najdete v části [ukázka vzájemná spolupráce hodin Win32](http://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF a vzájemná spolupráce Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Ukázka součinnosti hodin Win32](http://go.microsoft.com/fwlink/?LinkID=160051)
