---
title: Automatizace uživatelského rozhraní a změna velikosti obrazovky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: 4e101fffbd7e53cadce0b621d73ade2d1459ba00
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237448"
---
# <a name="ui-automation-and-screen-scaling"></a>Automatizace uživatelského rozhraní a změna velikosti obrazovky
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] Povolí uživatelům změnit [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] nastavení tak, který nejlépe [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvky na obrazovce zobrazí větší. I když tato funkce byla dlouhou dobu k dispozici v [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], v předchozích verzích škálování měli k implementaci aplikace. V [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], výchozí měřítko pro všechny aplikace, které ke zpracování vlastní škálování provede správce oken plochy. Automatizace uživatelského rozhraní klientské aplikace musí tuto funkci vezměte v úvahu.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Změna měřítka ve Windows Vista  
 Výchozí hodnota [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení je 96, což znamená, že zabírají 96 pixelů šířku nebo výšku jednomu palci pomyslná. Přesné měření "inch" závisí na velikosti a fyzické rozlišení monitoru. Vodorovná čára 96 pixelů rozšiřuje na monitoru 12 palce na horizontální rozlišení 1280 pixelů široký, asi 9 nebo 10 palce.  
  
 Změna [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení není stejný jako v případě změny rozlišení obrazovky. S [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] škálování, počet fyzických pixelech na obrazovce zůstává stejná. Škálování však platí pro velikost a umístění [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy. Tato škálování lze provádět automaticky podle Desktop okno správce (Správce oken plochy) pro desktop a pro aplikace, které nechcete škálovat explicitně neptat.  
  
 V důsledku toho pokud uživatel nastaví měřítko 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], bude o 25 % větší svislý nebo vodorovný palce na obrazovce. Všechny dimenze jsou odpovídajícím způsobem škálovat. Posun od horní a levé hrany obrazovky okna aplikace se zvýší o 25 procent. Pokud je povoleno škálování aplikace a aplikace není [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-vědět, velikost okna zvýší v poměru spolu s posuny a velikosti všech [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky, které obsahuje.  
  
> [!NOTE]
>  Ve výchozím nastavení, Správce oken plochy neprovádí škálování pro jinou hodnotu než[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]– aplikace používající, pokud uživatel nastaví [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 120, ale provést při [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] je nastavena na hodnotu vlastní 144 nebo vyšší. Uživatel však můžete přepsat výchozí chování.  
  
 Změna velikosti obrazovky vytvoří nové výzvy pro aplikace, které mají obavy z toho žádným způsobem s souřadnice obrazovky. Na obrazovce nyní obsahuje dvěma systémy souřadnic: fyzické a logické. Fyzické souřadnice bodu jsou skutečné odsazení v pixelech shora vlevo původu. Logické souřadnice jsou posunutí by se použily, pokud byly škálovat pixely sami.  
  
 Předpokládejme, že návrh dialogové okno s tlačítko na souřadnicích (100, 48). Když se toto dialogové okno objeví při výchozím 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], toto tlačítko se nachází na fyzické souřadnice (100, 48). Na 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], je umístěný na adrese fyzické souřadnice (125, 60). Ale logické souřadnice stejný na libovolné [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení: (100, 48).  
  
 Logické souřadnice jsou důležité, protože se chování operačního systému a aplikací konzistentní bez ohledu na to [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení. Například <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> obvykle vrací logické souřadnice. Pokud přesunete ukazatel nad prvkem v dialogovém okně, stejné souřadnice jsou vráceny bez ohledu [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení. Pokud si nakreslíte ovládacího prvku v (100, 100), je vykreslen na tyto logické souřadnice a budou zaměstnávat stejné relativní pozici na libovolné [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>Škálování u klientů automatizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API nepoužívá logické souřadnice. Následující metody a vlastnosti vrátit fyzické souřadnice nebo předat jako parametry.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Ve výchozím nastavení, automatizace uživatelského rozhraní klientské aplikace spuštěná v non-96 - [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] prostředí nebude moct získat správné výsledky z těchto metod a vlastností. Například protože pozice kurzoru v logické souřadnice, klient nelze předat jednoduše tyto souřadnice, kde <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> získat prvek, který je pod kurzorem. Kromě toho aplikace nebude možné správně umístit windows mimo jeho klientské oblasti.  
  
 Řešením je ve dvou částech.  
  
1. Nejprve se přesvědčte, klientská aplikace [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-vědět. Chcete-li to provést, zavolejte [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkce `SetProcessDPIAware` při spuštění. Ve spravovaném kódu následující deklarace zpřístupňuje tuto funkci.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Díky této funkci celý proces rozlišením DPI, což znamená, že jsou všechny systémy windows, které patří do procesu bez měřítka. V [zvýrazňovači nepoužívaného ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), například se nacházejí ve fyzické souřadnice získané z automatizace uživatelského rozhraní, není logický souřadnice čtyři windows, které tvoří zvýraznění obdélník. V případě ukázky nebyly rozlišením DPI, zvýraznění by být vykreslovat logické souřadnice ve stolním počítači, což by vytvořilo nesprávné umístění v prostředí 96 dpi.  
  
2. Chcete-li získat souřadnice kurzoru, zavolejte [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkce `GetPhysicalCursorPos`. Následující příklad ukazuje, jak deklarace a používání této funkce.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Nepoužívejte <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Chování této vlastnosti mimo klienta windows v prostředí s měřítkem není definováno.  
  
 Pokud vaše aplikace provádí přímou komunikaci mezi procesy s jinou hodnotu než [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]– aplikace používající, může mít převádění mezi logické a fyzické souřadnice pomocí [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkce `PhysicalToLogicalPoint` a `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Viz také:

- [Ukázka zvýrazňovači nepoužívaného](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
