---
title: TextPattern a vložené objekty – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: ab732ffedfbe05b1b246d8d8eef1c374e223eb39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401177"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern a vložené objekty – přehled
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled popisuje jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zpřístupňuje vložené objekty nebo podřízených elementů v rámci textový dokument nebo kontejneru.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vložený objekt je libovolný element, který má jiný než textový hranice, například bitové kopie, hypertextový odkaz, tabulka nebo dokumentu zadejte například [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] tabulky nebo [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] souboru. To se liší od standardní definice, kde je element vytvořené v jedné aplikaci a vložené nebo propojené v rámci jiného. Jestli se dá upravit objekt v rámci jeho původní aplikace je důležité v kontextu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Vložené objekty a stromu automatizace uživatelského rozhraní  
 Vložené objekty jsou považovány za jednotlivé prvky v rámci zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Jsou vystaveny jako podřízené objekty kontejneru text tak, aby je přístupná prostřednictvím stejný model jako další ovládací prvky v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 ![Vložené tabulky s bitové kopie v kontejneru Text](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Příklad kontejner textu pomocí tabulky, Image a hypertextový odkaz vložené objekty  
  
 ![Zobrazení pro předchozí příklad obsahu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Příklad zobrazení obsahu část předchozí kontejneru textu  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Vložené objekty pomocí TextPattern a TextPatternRange vystavit  
 Používá ve spojení, <xref:System.Windows.Automation.TextPattern> vzor třídu ovládacího prvku a <xref:System.Windows.Automation.Text.TextPatternRange> třída vystavit metody a vlastnosti, které usnadňují navigaci a dotazování vložené objekty.  
  
 Textový obsah (nebo vnitřní text), kontejner textu a vložený objekt, jako je například hypertextový odkaz nebo tabulce buňku, je k dispozici jako datový proud jeden, průběžné text v zobrazení ovládacího prvku a zobrazení obsahu z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu; objekt hranice jsou ignorovány. Pokud klient automatizace uživatelského rozhraní je načítání textu za účelem reciting, interpretace nebo analýza nějakým způsobem, rozsah text zkontrolovat zvláštních případech, jako je například tabulka s textový obsah nebo jiných vložené objekty. To můžete provést voláním <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> získat <xref:System.Windows.Automation.AutomationElement> pro každý vložený objekt a potom volání <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> získat rozsah textu pro jednotlivé elementy. To se provádí rekurzivní, dokud načtení veškerý textový obsah.  
  
 ![Rozsahy textu určené vložené objekty. ] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Příklad pro text datový proud vložené objekty a jejich rozsah rozpětí  
  
 Pokud je nutné procházení obsahu rozsahu text, sérii kroků se podílejí na pozadí, aby <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> metoda proběhl úspěšně.  
  
1.  Rozsah textu je normalized; To znamená, rozsah text sbalena na degenerovanou rozsah v <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> koncový bod, díky čemuž <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> nadbytečné koncový bod. Tento krok je potřeba odebrat nejednoznačnosti v situacích, kde text rozsah zahrnuje <xref:System.Windows.Automation.Text.TextUnit> hranice: například "{U} RL [ http://www.microsoft.com ](http://www.microsoft.com) vložené v textu" kde "{" a "}" jsou koncové body rozsahu text.  
  
2.  Výsledná oblast je přesunout zpátky <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> na začátek požadované <xref:System.Windows.Automation.Text.TextUnit> hranic.  
  
3.  Rozsah je přesunut nebo předchozí v <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> podle požadovaného počtu <xref:System.Windows.Automation.Text.TextUnit> hranice.  
  
4.  Rozsah je pak rozšířena z degenerovanou rozsah stavu přesunutím <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncový bod pomocí jedné požadovaný <xref:System.Windows.Automation.Text.TextUnit> hranic.  
  
 ![Úpravy podle přesunout & ExpandToEnclosingUnit rozsahu](../../../docs/framework/ui-automation/media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Příklady, jak je text rozsah upraveno Move() a ExpandToEnclosingUnit()  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Běžné scénáře  
 V následující části jsou uvedeny příklady nejběžnější scénáře, které zahrnují vložené objekty.  
  
 Legenda příklady zobrazí:  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
<a name="Hyperlink"></a>   
### <a name="hyperlink"></a>Hypertextový odkaz  
 **Příklad 1 - rozsah text, který obsahuje hypertextový odkaz vložený text**  
  
 {Adresu URL [ http://www.microsoft.com ](http://www.microsoft.com) vložené do text}.  
  
|Metoda volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "adresa URL http://www.microsoft.com vložené v textu".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> která obklopuje rozsah textu; v takovém případě <xref:System.Windows.Automation.AutomationElement> představující samotného poskytovatele text.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí <xref:System.Windows.Automation.AutomationElement> představující ovládacího prvku hypertextový odkaz.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený předchozím `GetChildren` metoda.|Vrátí rozsahu, který představuje "http://www.microsoft.com".|  
  
 **Příklad 2 - text oblast, která částečně přesahuje hypertextový odkaz vložený text**  
  
 Adresa URL http://{[www]} je vložený text.  
  
|Metoda volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> která obklopuje rozsah textu; v takovém případě hypertextový odkaz řízení.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí `null` vzhledem k tomu, že rozsah text není span celý řetězce adresy URL.|  
  
 **Příklad 3 - text oblast, která částečně přesahuje obsah kontejner textu. Kontejner text obsahuje vložený text hypertextový odkaz, který není součástí textu rozsahu.**  
  
 {{URL} [ http://www.microsoft.com ](http://www.microsoft.com) vložené v textu.  
  
|Metoda volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "Adresa URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> která obklopuje rozsah textu; v takovém případě <xref:System.Windows.Automation.AutomationElement> představující samotného poskytovatele text.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> s parametry (TextUnit.Word, 1).|Vzhledem k tomu, že text hypertextový odkaz se skládá z jednotlivých slov přesune rozpětí rozsah text "http". V takovém případě hypertextový odkaz nepovažuje se za jeden objekt.<br /><br /> Adresu URL {[http]} je vložený text.|  
  
<a name="Image"></a>   
### <a name="image"></a>Image  
 **Příklad 1 - rozsah text, který obsahuje vložený obrázek**  
  
 {Bitovou kopii ![vložený obrázek – příklad](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") vložené do text}.  
  
|Metoda volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "vložené v textu". Žádné alternativní text související s bitovou kopii nelze očekává mají být zahrnuty do proudu textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> která obklopuje rozsah textu; v takovém případě <xref:System.Windows.Automation.AutomationElement> představující samotného poskytovatele text.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí <xref:System.Windows.Automation.AutomationElement> představující ovládacího prvku obrázek.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený předchozím <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> metoda.|Vrátí degenerovanou rozsahu, který představuje "![vložený obrázek – příklad](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Příklad 2 - text oblast, která částečně přesahuje obsah kontejner textu. Kontejner text obsahuje vložený obrázek, který není součástí textu rozsahu.**  
  
 {Bitová kopie} ![Vložený obrázek – příklad](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") vložené v textu.  
  
|Metoda volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "image".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> která obklopuje rozsah textu; v takovém případě <xref:System.Windows.Automation.AutomationElement> představující samotného poskytovatele text.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> s parametry (TextUnit.Word, 1).|Přesune rozpětí textu rozsahu "je". Protože pouze založený na textu vložené objekty jsou považovány za součást text datového proudu, bitové kopie v tomto příkladu nemá vliv přesunutí nebo hodnoty (1 v tomto případě).|  
  
<a name="Table"></a>   
### <a name="table"></a>Tabulka  
  
### <a name="table-used-for-examples"></a>Tabulka použitá pro příklady  
  
|Buňky pomocí bitové kopie|Buňky s textem|  
|---------------------|--------------------|  
|![Vložený obrázek – příklad](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Vložený obrázek – příklad 2](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|A|  
|![Vložený obrázek – příklad 3](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Obrázek pro Z|Z|  
  
 **Příklad 1 – získání kontejneru text z obsahu buňky.**  
  
|Metodu s názvem|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> s parametry (0,0)|Vrátí <xref:System.Windows.Automation.AutomationElement> představující obsah buňky tabulky; v takovém případě elementu je ovládací prvek text.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený předchozím `GetItem` metoda.|Vrátí oblast, která zahrnuje bitovou kopii ![vložený obrázek – příklad](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> pro objekt vrácený předchozím `RangeFromChild` metoda.|Vrátí <xref:System.Windows.Automation.AutomationElement> představující buňky tabulky; v takovém případě elementu je ovládacího prvku typu textový, která podporuje vlastnost TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> pro objekt vrácený předchozím `GetEnclosingElement` metoda.|Vrátí <xref:System.Windows.Automation.AutomationElement> představující tabulku.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> pro objekt vrácený předchozím `GetEnclosingElement` metoda.|Vrátí <xref:System.Windows.Automation.AutomationElement> představující samotného poskytovatele text.|  
  
 **Příklad 2 - získat obsah textu buňky.**  
  
|Metodu s názvem|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> s parametry (1,1).|Vrátí <xref:System.Windows.Automation.AutomationElement> představující obsah buňky tabulky; v takovém případě elementu je ovládací prvek text.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený předchozím `GetItem` metoda.|Vrátí "Y".|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.TextPattern>  
 <xref:System.Windows.Automation.Text.TextPatternRange>  
 <xref:System.Windows.Automation.Provider.ITextProvider>  
 <xref:System.Windows.Automation.Provider.ITextRangeProvider>  
 [Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)  
 [Vystavení obsahu tabulky s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/expose-the-content-of-a-table-using-ui-automation.md)  
 [Procházení textu s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/traverse-text-using-ui-automation.md)  
 [TextPattern vyhledávání a výběru vzorku](http://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)
