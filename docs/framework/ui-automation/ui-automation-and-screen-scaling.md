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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c34c10ee1701adba2dfb64be8ef39d6bf9f203e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-and-screen-scaling"></a>Automatizace uživatelského rozhraní a změna velikosti obrazovky
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] umožňuje uživatelům změnit [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] nastavení, která nejvíc [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvky na obrazovce objeví větší. I když tato funkce se dlouho k dispozici v [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], v předchozích verzích škálování měly být aplikace. V [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], Správce oken plochy provede výchozí škálování pro všechny aplikace, které zpracovávají vlastní škálování. Automatizace uživatelského rozhraní klientské aplikace musí vzít v úvahu tuto funkci.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Škálování v systému Windows Vista  
 Výchozí hodnota [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení je 96, to znamená, že zabírají šířky nebo výšky jeden fiktivní palce 96 pixelů. Přesné měření "inch" závisí na velikosti a fyzické rozlišení monitoru. Na monitorování 12 palce, výška, na horizontální rozlišení 1 280 pixelů, například na vodorovném řádku 96 pixelů rozšiřuje o 9/10 palce.  
  
 Změna [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení není stejný jako změna rozlišení obrazovky. S [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] škálování, počet fyzických pixelů na obrazovce se nezmění. Ale škálování se použije na velikost a umístění [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy. Tato změna měřítka lze provést automaticky podle plochy okno správce (Správce oken plochy) pro plochy a aplikace, které explicitně nedotazovat se škálovat.  
  
 Platí, pokud uživatel nastaví měřítko 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], svislé nebo vodorovné cm na obrazovce se stane větší o 25 procent. Všechny dimenze jsou škálovat odpovídajícím způsobem. Posun okna aplikace z horní a levé hrany obrazovky se zvýší o 25 procent. Pokud je povoleno škálování aplikace a aplikace není [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-vědět, zvyšuje velikost okna ve stejném poměru, společně s odsazení a velikosti všech [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, které obsahuje.  
  
> [!NOTE]
>  Ve výchozím nastavení, Správce oken plochy neprovádí škálování pro jinou hodnotu než[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aplikace využívající, pokud uživatel nastaví [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 120, ale provést při [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] je nastavená na hodnotu vlastní 144 nebo vyšší. Uživatel však můžete přepsat výchozí chování.  
  
 Změna velikosti obrazovky vytvoří nové výzvy pro aplikace, které jsou na dané žádným způsobem s souřadnice obrazovky. Na obrazovce teď obsahuje dvě systém souřadnic: fyzické a logické. Fyzické souřadnice bodu jsou skutečné odsazení v pixelech shora zbývajících počátku. Logické souřadnice jsou posunutí, jako by se použily, pokud byly škálovat pixelů sami.  
  
 Předpokládejme, že návrhu dialogové okno s tlačítkem na souřadnice (100, 48). Když toto dialogové okno se zobrazí v výchozí 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], tlačítko nachází ve fyzické souřadnice (100, 48). Na 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], je umístěný na adrese fyzické souřadnice (125, 60). Ale logické souřadnice jsou stejné kdykoli [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení: (100, 48).  
  
 Logické souřadnice jsou důležité, protože chování operačního systému a aplikací konzistentní bez ohledu na to [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení. Například <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> obvykle vrací logické souřadnice. Pokud jste přesuňte kurzor na prvek v dialogovém okně, vrátí se stejné souřadnice bez ohledu na to [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení. Pokud vykreslení ovládacího prvku na (100, 100), jsou vykresleny pro tyto logické souřadnice a bude zabírat stejné relativní pozici kdykoli [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] nastavení.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>Nastavení velikosti v klientů automatizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] Nepoužívá logické souřadnice. Následující metody a vlastnosti vrátit fyzické souřadnice nebo je provést jako parametry.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Ve výchozím nastavení automatizace uživatelského rozhraní klientské aplikace spuštěna v jiný-96 - [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] prostředí, nebude možné získat správné výsledky z těchto metod a vlastností. Například, protože pozice kurzoru je v logické souřadnice, klient nelze předat jednoduše tyto souřadnice k <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> získat elementu, který je pod kurzor. Kromě toho aplikace nebude možné správně umístit mimo jeho klientské oblasti systému windows.  
  
 Řešení je ve dvou částech.  
  
1.  Nejprve zkontrolujte klientská aplikace [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-vědět. Chcete-li to provést, zavolejte [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkce `SetProcessDPIAware` při spuštění. Ve spravovaném kódu následující prohlášení zpřístupňuje tuto funkci.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Díky této funkci celý proces [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-vědět, což znamená, že jsou všechny systémy windows, které patří do procesu bez měřítka. V [zvýraznění ukázka](http://msdn.microsoft.com/library/19ba4577-753e-4efd-92cc-c02ee67c1b69), například jsou umístěné na fyzické souřadnice získané z čtyři windows, které tvoří rámeček zvýraznění [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], není logické souřadnice. Pokud nebyly v ukázkovém [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-vědět, zvýraznění by vyznačovat logické souřadnice na ploše, což by způsobilo nesprávné umístění v jiný-96 - [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] prostředí.  
  
2.  Chcete-li získat souřadnice kurzoru, volejte [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkce `GetPhysicalCursorPos`. Následující příklad ukazuje, jak deklarace a používání této funkce.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Nepoužívejte <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Nastavení této vlastnosti mimo klienta windows v přizpůsobeném prostředí není definován.  
  
 Pokud vaše aplikace provede přímou komunikaci mezi procesy s jinou hodnotu než [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aplikací, může mít převedete mezi logické a fyzické souřadnice pomocí [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funkce `PhysicalToLogicalPoint` a `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka zvýraznění](http://msdn.microsoft.com/library/19ba4577-753e-4efd-92cc-c02ee67c1b69)
