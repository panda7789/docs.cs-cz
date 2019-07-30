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
ms.openlocfilehash: a59223bfbe9506aa0028933d55b74e24d5595c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629549"
---
# <a name="ui-automation-and-screen-scaling"></a>Automatizace uživatelského rozhraní a změna velikosti obrazovky
> [!NOTE]
>  Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]umožňuje uživatelům změnit nastavení bodů na palec (dpi) tak, aby se většina [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvků na obrazovce zobrazovala větší. I když je tato funkce dlouhodobě dostupná [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]v, v předchozích verzích bylo škálování nutné implementovat aplikacemi. V [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]nástroji Správce oken plochy provádí výchozí škálování pro všechny aplikace, které nezpracovávají vlastní škálování. Klientské aplikace automatizace uživatelského rozhraní musí tuto funkci vzít v úvahu.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Škálování v systému Windows Vista  
 Výchozí nastavení DPI je 96, což znamená, že 96 pixelů zabírají šířku nebo výšku jednoho fiktivního palce. Přesné měření "palce" závisí na velikosti a fyzickém rozlišení monitoru. Například na monitoru o velikosti 12 palců v horizontálním rozlišení 1280 pixelů je vodorovná čára o velikosti 96 pixelů prodloužena o 9/10 palce.  
  
 Změna nastavení DPI není stejná jako změna rozlišení obrazovky. Při škálování dpi zůstane počet fyzických pixelů na obrazovce stejný. Škálování se ale aplikuje na velikost a umístění [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvků. Toto škálování se dá automaticky provádět Správce oken plochy (DWM) pro stolní počítače a pro aplikace, které explicitně nevyžadují jejich škálování.  
  
 V důsledku toho, když uživatel nastaví faktor škálování na 120 dpi, změní se na obrazovku svislá nebo vodorovná palec o 25 procent. Všechny rozměry jsou odpovídajícím způsobem upraveny. Posun okna aplikace od horního a pravého okraje obrazovky se zvyšuje o 25 procent. Pokud je povoleno škálování aplikace a aplikace nezohledňuje rozlišení DPI, velikost okna se zvětšuje ve stejném poměru, a to spolu s posuny a velikostmi všech [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvků, které obsahuje.  
  
> [!NOTE]
>  Ve výchozím nastavení DWM neprovádí škálování pro aplikace, které nepodporují rozlišení DPI, když uživatel nastaví DPI na 120, ale provede ho, když je DPI nastaveno na vlastní hodnotu 144 nebo vyšší. Uživatel však může přepsat výchozí chování.  
  
 Škálování obrazovky vytvoří nové výzvy pro aplikace, které jsou v jakémkoli případě v souřadnicích obrazovky. Obrazovka teď obsahuje dva systémy souřadnic: fyzické a logické. Fyzické souřadnice bodu jsou skutečný posun v pixelech od levého horního rohu od počátku. Logické souřadnice jsou posuny, protože by se jednalo o škálu pixelů samotných.  
  
 Řekněme, že navrhujete dialogové okno s tlačítkem na souřadnicích (100, 48). Pokud se toto dialogové okno zobrazí na výchozím 96 dpi, tlačítko se nachází na fyzických souřadnicích (100, 48). V 120 dpi se nachází na fyzických souřadnicích (125, 60). Ale logické souřadnice jsou stejné u libovolného nastavení dpi: (100, 48).  
  
 Logické souřadnice jsou důležité, protože provádějí chování operačního systému a aplikací konzistentních bez ohledu na nastavení DPI. Například <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normálně vrací logické souřadnice. Pokud přesunete kurzor nad prvek v dialogovém okně, budou stejné souřadnice vráceny bez ohledu na nastavení DPI. Pokud nakreslíte ovládací prvek na pozici (100, 100), vykreslí se tyto logické souřadnice a zachová se stejná relativní poloha u libovolného nastavení DPI.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>Škálování v klientech automatizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Rozhraní API nepoužívá logické souřadnice. Následující metody a vlastnosti buď vracejí fyzické souřadnice, nebo je převezmou jako parametry.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Ve výchozím nastavení nebudou klientské aplikace pro automatizaci uživatelského rozhraní spuštěné v prostředí bez 96 DPI moci získat správné výsledky z těchto metod a vlastností. Například vzhledem k tomu, že pozice kurzoru je v logických souřadnicích, nemůže klient jednoduše předat tyto <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> souřadnice k získání prvku, který je pod kurzorem. Kromě toho aplikace nebude moci správně umístit systém Windows mimo jeho klientskou oblast.  
  
 Řešení je ve dvou částech.  
  
1. Nejprve zajistěte, aby klientská aplikace mohla zohledňovat rozlišení DPI. Chcete-li to provést, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] zavolejte `SetProcessDPIAware` funkci při spuštění. Ve spravovaném kódu je tato funkce k dispozici následující deklarace.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Tato funkce umožňuje celému procesu zohledňovat rozlišení DPI, což znamená, že všechny systémy Windows, které patří do procesu, jsou bez měřítka. V [ukázce zvýrazňovače](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)například čtyři okna, která tvoří zvýrazněný obdélník, jsou umístěna na fyzických souřadnicích získaných z automatizace uživatelského rozhraní, nikoli v logických souřadnicích. Pokud Ukázka nezohledňuje rozlišení DPI, zvýrazní se zvýraznění na logických souřadnicích na ploše, což by vedlo k nesprávnému umístění v prostředí, které není 96 dpi.  
  
2. Chcete-li získat souřadnice kurzoru, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] zavolejte `GetPhysicalCursorPos`funkci. Následující příklad ukazuje, jak deklarovat a používat tuto funkci.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Nepoužívejte <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Chování této vlastnosti mimo klientské okna v prostředí s měřítkem není definováno.  
  
 Pokud vaše aplikace provádí přímou komunikaci mezi procesy s aplikacemi, které nepodporují rozlišení DPI, možná jste převedli převod mezi logickými a fyzickými [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] souřadnicemi `LogicalToPhysicalPoint`pomocí funkcí `PhysicalToLogicalPoint` a.  
  
## <a name="see-also"></a>Viz také:

- [Ukázka zvýrazňovače](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
