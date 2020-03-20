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
ms.openlocfilehash: 2a68a74fa6aadcaba21f142d394a1f8a3d8af371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179968"
---
# <a name="ui-automation-and-screen-scaling"></a>Automatizace uživatelského rozhraní a změna velikosti obrazovky
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
Počínaje systémem Windows Vista umožňuje systém Windows uživatelům změnit nastavení na palec (dpi) tak, aby většina prvků uživatelského rozhraní (UI) na obrazovce vypadala větší. Ačkoli tato funkce je již dlouho k dispozici v systému Windows, v předchozích verzích škálování musely být implementovány aplikacemi. Počínaje systémem Windows Vista provádí Správce oken plochy výchozí změnu měřítka pro všechny aplikace, které nezpracovávají vlastní měřítko. Klientské aplikace Automatizace uživatelského rozhraní musí tuto funkci zohlednit.  
  
<a name="Scaling_in_Windows_Vista"></a>
## <a name="scaling-in-windows-vista"></a>Změna velikosti v systému Windows Vista  
 Výchozí nastavení dpi je 96, což znamená, že 96 pixelů zabírá šířku nebo výšku jednoho pomyslného palce. Přesná míra "palce" závisí na velikosti a fyzickém rozlišení monitoru. Například na monitoru o šířce 12 palců při vodorovném rozlišení 1280 pixelů se vodorovná čára 96 pixelů rozprostírá přibližně 9/10 palce.  
  
 Změna nastavení dpi není stejná jako změna rozlišení obrazovky. Při změně měřítka dpi zůstává počet fyzických pixelů na obrazovce stejný. Změna měřítka se však použije [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na velikost a umístění prvků. Toto škálování může provádět automaticky Správce oken plochy (DWM) pro plochu a pro aplikace, které explicitně nežádají, aby nebyly škálovány.  
  
 Ve skutečnosti, když uživatel nastaví faktor měřítka na 120 dpi, svislý nebo vodorovný palec na obrazovce se zvětší o 25 procent. Všechny rozměry jsou odpovídajícím způsobem změněny. Posun okna aplikace od horního a levého okraje obrazovky se zvýší o 25 procent. Pokud je povoleno škálování aplikace a aplikace není dpi vědomi, velikost okna se zvětší ve stejném poměru, spolu s posuny a velikosti všech [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvků, které obsahuje.  
  
> [!NOTE]
> Ve výchozím nastavení DWM neprovádí škálování pro aplikace, které nejsou vhodné pro dpi, když uživatel nastaví dpi na 120, ale provede jej, když je dpi nastavena na vlastní hodnotu 144 nebo vyšší. Uživatel však může přepsat výchozí chování.  
  
 Škálování obrazovky vytváří nové výzvy pro aplikace, které se jakýmkoli způsobem týkají souřadnic obrazovky. Obrazovka nyní obsahuje dva souřadné systémy: fyzické a logické. Fyzické souřadnice bodu jsou skutečné odsazení v obrazových bodech od levého horního rohu počátku. Logické souřadnice jsou posuny, jako by byly, kdyby byly měřítko samotných obrazových bodů.  
  
 Předpokládejme, že navrhnete dialogové okno s tlačítkem na souřadnicích (100, 48). Pokud je toto dialogové okno zobrazeno ve výchozím 96 dpi, je tlačítko umístěno na fyzických souřadnicích (100, 48). Při 120 dpi se nachází na fyzických souřadnicích (125, 60). Ale logické souřadnice jsou stejné v každém nastavení dpi: (100, 48).  
  
 Logické souřadnice jsou důležité, protože chování operačního systému a aplikací konzistentní bez ohledu na nastavení dpi. Například <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> obvykle vrátí logické souřadnice. Pokud přesunete kurzor nad prvek v dialogovém okně, budou vráceny stejné souřadnice bez ohledu na nastavení dpi. Pokud nakreslíte ovládací prvek na (100, 100), je nakreslena na tyto logické souřadnice a bude zabírat stejnou relativní pozici v libovolném nastavení dpi.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>
## <a name="scaling-in-ui-automation-clients"></a>Škálování v klientech automatizace uživatelského rozhraní  
 Rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API nepoužívá logické souřadnice. Následující metody a vlastnosti buď vrátit fyzické souřadnice nebo je považovat za parametry.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Ve výchozím nastavení klientská aplikace Automatizace uživatelského rozhraní spuštěná v prostředí s dpi s možností získat správné výsledky z těchto metod a vlastností. Například protože pozice kurzoru je v logické souřadnice, <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> klient nemůže jednoduše předat tyto souřadnice získat prvek, který je pod kurzorem. Kromě toho aplikace nebude moci správně umístit okna mimo svou klientskou oblast.  
  
 Roztok je ve dvou částech.  
  
1. Nejprve proveďte klientskou aplikaci dpi vědomi. Chcete-li to provést, zavolejte funkci `SetProcessDPIAware` Win32 při spuštění. Ve spravovaném kódu následující deklarace zpřístupňuje tuto funkci.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Tato funkce umožňuje celý proces dpi vědomi, což znamená, že všechna okna, která patří do procesu jsou bez měřítka. V [ukázkové masce zvýrazňovače](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)jsou například čtyři okna, která tvoří obdélník zvýraznění, umístěna na fyzických souřadnicích získaných z automatizace uživatelského rozhraní, nikoli na logických souřadnicích. Pokud ukázka nebyla dpi vědomi, zvýraznění by být vykreslen na logické souřadnice na ploše, což by mělo za následek nesprávné umístění v prostředí bez 96 dpi.  
  
2. Chcete-li získat souřadnice kurzoru, zavolejte funkci `GetPhysicalCursorPos`Win32 . Následující příklad ukazuje, jak deklarovat a používat tuto funkci.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> Nepoužívejte <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Chování této vlastnosti mimo okna klienta v prostředí s měřítkem není definováno.  
  
 Pokud aplikace provádí přímou meziprocesovou komunikaci s aplikacemi, které nejsou uvědoměly dpi, můžete `PhysicalToLogicalPoint` provést `LogicalToPhysicalPoint`převod mezi logickými a fyzickými souřadnicemi pomocí funkcí Win32 a .  
  
## <a name="see-also"></a>Viz také

- [Ukázka zvýrazňovače](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
