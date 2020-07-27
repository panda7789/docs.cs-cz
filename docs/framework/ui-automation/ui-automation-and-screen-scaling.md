---
title: Automatizace uživatelského rozhraní a změna velikosti obrazovky
description: Přečtěte si, jak automatizace Windows a uživatelského rozhraní zpracovává škálování obrazovky. DWM má výchozí velikost pro všechny aplikace, které musí vzít v úvahu klientské aplikace automatizace uživatelského rozhraní.
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
ms.openlocfilehash: 99239d7bac2e556d4da0d74f36c68916da7c688a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164018"
---
# <a name="ui-automation-and-screen-scaling"></a>Automatizace uživatelského rozhraní a změna velikosti obrazovky
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
Počínaje systémem Windows Vista umožňuje Windows uživatelům změnit nastavení bodů na palec (dpi) tak, aby se většina prvků uživatelského rozhraní (UI) na obrazovce zobrazovala větší. I když je tato funkce ve Windows dlouhodobě dostupná, v předchozích verzích bylo škálování nutné implementovat aplikacemi. Počínaje systémem Windows Vista Správce oken plochy provádí výchozí škálování pro všechny aplikace, které nezpracovávají jejich vlastní škálování. Klientské aplikace automatizace uživatelského rozhraní musí tuto funkci vzít v úvahu.  
  
<a name="Scaling_in_Windows_Vista"></a>
## <a name="scaling-in-windows-vista"></a>Škálování v systému Windows Vista  
 Výchozí nastavení DPI je 96, což znamená, že 96 pixelů zabírají šířku nebo výšku jednoho fiktivního palce. Přesné měření "palce" závisí na velikosti a fyzickém rozlišení monitoru. Například na monitoru o velikosti 12 palců v horizontálním rozlišení 1280 pixelů je vodorovná čára o velikosti 96 pixelů prodloužena o 9/10 palce.  
  
 Změna nastavení DPI není stejná jako změna rozlišení obrazovky. Při škálování dpi zůstane počet fyzických pixelů na obrazovce stejný. Škálování se ale aplikuje na velikost a umístění [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvků. Toto škálování se dá automaticky provádět Správce oken plochy (DWM) pro stolní počítače a pro aplikace, které explicitně nevyžadují jejich škálování.  
  
 V důsledku toho, když uživatel nastaví faktor škálování na 120 dpi, změní se na obrazovku svislá nebo vodorovná palec o 25 procent. Všechny rozměry jsou odpovídajícím způsobem upraveny. Posun okna aplikace od horního a pravého okraje obrazovky se zvyšuje o 25 procent. Pokud je povoleno škálování aplikace a aplikace nezohledňuje rozlišení DPI, velikost okna se zvětšuje ve stejném poměru, a to spolu s posuny a velikostmi všech prvků, které [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] obsahuje.  
  
> [!NOTE]
> Ve výchozím nastavení DWM neprovádí škálování pro aplikace, které nepodporují rozlišení DPI, když uživatel nastaví DPI na 120, ale provede ho, když je DPI nastaveno na vlastní hodnotu 144 nebo vyšší. Uživatel však může přepsat výchozí chování.  
  
 Škálování obrazovky vytvoří nové výzvy pro aplikace, které jsou v jakémkoli případě v souřadnicích obrazovky. Obrazovka teď obsahuje dva systémy souřadnic: fyzické a logické. Fyzické souřadnice bodu jsou skutečný posun v pixelech od levého horního rohu od počátku. Logické souřadnice jsou posuny, protože by se jednalo o škálu pixelů samotných.  
  
 Řekněme, že navrhujete dialogové okno s tlačítkem na souřadnicích (100, 48). Pokud se toto dialogové okno zobrazí na výchozím 96 dpi, tlačítko se nachází na fyzických souřadnicích (100, 48). V 120 dpi se nachází na fyzických souřadnicích (125, 60). Ale logické souřadnice jsou stejné na všech nastaveních dpi: (100, 48).  
  
 Logické souřadnice jsou důležité, protože provádějí chování operačního systému a aplikací konzistentních bez ohledu na nastavení DPI. Například <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normálně vrací logické souřadnice. Pokud přesunete kurzor nad prvek v dialogovém okně, budou stejné souřadnice vráceny bez ohledu na nastavení DPI. Pokud nakreslíte ovládací prvek na pozici (100, 100), vykreslí se tyto logické souřadnice a zachová se stejná relativní poloha u libovolného nastavení DPI.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>
## <a name="scaling-in-ui-automation-clients"></a>Škálování v klientech automatizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Rozhraní API nepoužívá logické souřadnice. Následující metody a vlastnosti buď vracejí fyzické souřadnice, nebo je převezmou jako parametry.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Ve výchozím nastavení nebudou klientské aplikace pro automatizaci uživatelského rozhraní spuštěné v prostředí bez 96 DPI moci získat správné výsledky z těchto metod a vlastností. Například vzhledem k tomu, že pozice kurzoru je v logických souřadnicích, nemůže klient jednoduše předat tyto souřadnice k <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> získání prvku, který je pod kurzorem. Kromě toho aplikace nebude moci správně umístit systém Windows mimo jeho klientskou oblast.  
  
 Řešení je ve dvou částech.  
  
1. Nejprve zajistěte, aby klientská aplikace mohla zohledňovat rozlišení DPI. Chcete-li to provést, zavolejte funkci Win32 `SetProcessDPIAware` při spuštění. Ve spravovaném kódu je tato funkce k dispozici následující deklarace.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Tato funkce umožňuje celému procesu zohledňovat rozlišení DPI, což znamená, že všechny systémy Windows, které patří do procesu, jsou bez měřítka. V [ukázce zvýrazňovače](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)například čtyři okna, která tvoří zvýrazněný obdélník, jsou umístěna na fyzických souřadnicích získaných z automatizace uživatelského rozhraní, nikoli v logických souřadnicích. Pokud Ukázka nezohledňuje rozlišení DPI, zvýrazní se zvýraznění na logických souřadnicích na ploše, což by vedlo k nesprávnému umístění v prostředí, které není 96 dpi.  
  
2. Chcete-li získat souřadnice kurzoru, zavolejte funkci Win32 `GetPhysicalCursorPos` . Následující příklad ukazuje, jak deklarovat a používat tuto funkci.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> Nepoužívejte <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> . Chování této vlastnosti mimo klientské okna v prostředí s měřítkem není definováno.  
  
 Pokud vaše aplikace provádí přímou komunikaci mezi procesy s aplikacemi, které nepodporují rozlišení DPI, možná jste převedli převod mezi logickými a fyzickými souřadnicemi pomocí funkcí Win32 `PhysicalToLogicalPoint` a `LogicalToPhysicalPoint` .  
  
## <a name="see-also"></a>Viz také

- [Ukázka zvýrazňovače](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
