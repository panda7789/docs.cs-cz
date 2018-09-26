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
ms.openlocfilehash: c3904ad60df3d9d7ce2b58d5911e4e19a2ebb7e3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073424"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern a vložené objekty – přehled
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled popisuje jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zpřístupňuje vložené objekty nebo podřízené prvky v rámci textového dokumentu nebo kontejneru.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vložený objekt je libovolný element, který má jiné textové hranice, například obrázek, hypertextový odkaz, tabulky nebo dokumentu zadejte třeba [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] tabulky nebo [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] souboru. Tím se liší od standardní definice, kde vytvořené v jedné aplikaci a vložené nebo propojené v rámci jiného elementu. Určuje, zda lze upravovat objekt v rámci původní aplikaci je bezvýznamná v kontextu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Vložené objekty a stromu automatizace uživatelského rozhraní  
 Vložené objekty jsou považovány za jednotlivé prvky v rámci zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Jsou vystaveny jako podřízené objekty daného kontejneru text tak, aby k nim může přistupovat prostřednictvím stejné modelu jako ostatní ovládací prvky v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 ![Vložené tabulky se obrázek v kontejneru Text](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Příklad zásobník textu pomocí tabulky, Image a hypertextový odkaz vložené objekty  
  
 ![Zobrazení pro předchozí příklad obsahu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Příklad zobrazení obsahu pro část předchozí zásobník textu  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Vystavení vložené objekty pomocí TextPattern a TextPatternRange  
 Používá ve spojení, <xref:System.Windows.Automation.TextPattern> třídu vzor ovládacího prvku a <xref:System.Windows.Automation.Text.TextPatternRange> třídy zpřístupnit metody a vlastnosti, které usnadňují navigace a dotazování na ně vložených objektů.  
  
 Textový obsah (nebo vnitřní text) zásobník textu a vložený objekt, jako je například hypertextový odkaz nebo tabulce buňku, je přístupný jako datový proud jeden, průběžné textu v ovládacím zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu; objekt hranice jsou ignorovány. Pokud klient automatizace uživatelského rozhraní je načítání textu pro účely reciting, interpretace nebo analýza nějakým způsobem, zkontrolovat rozsah textu pro zvláštní případy, jako je například tabulku s textový obsah nebo jiné vložené objekty. To lze provést zavoláním <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> získat <xref:System.Windows.Automation.AutomationElement> pro každý vložený objekt a následným voláním <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> získat rozsah textu pro každý prvek. To se provádí rekurzivně, dokud všechny textový obsah byl načten.  
  
 ![Oblasti textu předané vložené objekty. ](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Příklad textového datového proudu s vložené objekty a jejich rozsah rozpětí  
  
 V případě potřeby procházet obsah rozsah textu sérii kroků se podílejí na pozadí, aby <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> metodu úspěšně provést.  
  
1.  Rozsah textu je normalizovány; To znamená, je mimo rozsah textu sbaleny do na degenerovanou rozsah <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> koncový bod, díky čemuž je <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> nadbytečný koncový bod. Tento krok je potřeba odstranit nejednoznačnost v situacích, kdy rozsah textu zahrnuje <xref:System.Windows.Automation.Text.TextUnit> hranice: například "{U} RL [ http://www.microsoft.com ](https://www.microsoft.com) je vložený v textu" kde "{" a "}" jsou koncové body rozsah textu.  
  
2.  Výsledná oblast bude přesunut dozadu <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> začátek požadovanou <xref:System.Windows.Automation.Text.TextUnit> hranic.  
  
3.  Rozsah je přesunut dopředu nebo dozadu v <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> podle požadovaného počtu <xref:System.Windows.Automation.Text.TextUnit> hranice.  
  
4.  Rozsah je pak rozšířen ze stavu degenerovanou rozsah přesunutím <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncový bod pomocí jedné požadovaný <xref:System.Windows.Automation.Text.TextUnit> hranic.  
  
 ![Přesunout & ExpandToEnclosingUnit úpravy rozsahu](../../../docs/framework/ui-automation/media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Příklady, jak je upraveno rozsah textu pro Move() a ExpandToEnclosingUnit()  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Obvyklé scénáře  
 Následující části uvádějí příklady z nejběžnějších scénářů, které se týkají vložené objekty.  
  
 Legenda pro příkladů uvedených:  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
<a name="Hyperlink"></a>   
### <a name="hyperlink"></a>Hypertextový odkaz  
 **Příklad 1 - rozsah textu, který obsahuje vložený text hypertextového odkazu**  
  
 {Adresu URL [ http://www.microsoft.com ](https://www.microsoft.com) vložený text}.  
  
|Metodu s názvem|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "adresa URL http://www.microsoft.com vložený text".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> , který obklopuje rozsah textu; v takovém případě <xref:System.Windows.Automation.AutomationElement> , která představuje samotného poskytovatele textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí <xref:System.Windows.Automation.AutomationElement> představující ovládací prvek hypertextového odkazu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený rutinou předchozí `GetChildren` metody.|Vrátí rozsah, který představuje "http://www.microsoft.com".|  
  
 **Příklad 2 - rozsah textu, které částečně pokrývá vložený text hypertextového odkazu**  
  
 Adresa URL `http://{[www]}` se vloží do textu.  
  
|Metodu s názvem|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> , který obklopuje rozsah textu; v takovém případě ovládací prvek hypertextového odkazu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí `null` od rozsah textu nebude zahrnovat celý řetězec adresy URL.|  
  
 **Příklad 3 - rozsah textu, která částečně zahrnuje obsah zásobník textu. Zásobník textu se vložený text hypertextového odkazu, který není součástí rozsah textu.**  
  
 {URL} [ http://www.microsoft.com ](https://www.microsoft.com) se vloží do textu.  
  
|Metodu s názvem|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> , který obklopuje rozsah textu; v takovém případě <xref:System.Windows.Automation.AutomationElement> , která představuje samotného poskytovatele textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> s parametry (TextUnit.Word, 1).|Protože text hypertextového odkazu se skládá z jednotlivých slov přesune rozpětí rozsah textu "http". Hypertextový odkaz v tomto případě není považován za jeden objekt.<br /><br /> Adresa URL {[http]} se vloží do textu.|  
  
<a name="Image"></a>   
### <a name="image"></a>Image  
 **Příklad 1 - rozsah textu, který obsahuje vložený obrázek**  
  
 {Image ![vložený obrázek příkladu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") vložený text}.  
  
|Metodu s názvem|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "vložený text". Žádné alternativní text související s imagí nemůže očekávat mají být zahrnuty do textového datového proudu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> , který obklopuje rozsah textu; v takovém případě <xref:System.Windows.Automation.AutomationElement> , která představuje samotného poskytovatele textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí <xref:System.Windows.Automation.AutomationElement> představující ovládací prvek obrázku.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený rutinou předchozí <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> metody.|Vrátí degenerovanou rozsahu, který představuje "![vložený obrázek příkladu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Příklad 2 - rozsah textu, která částečně zahrnuje obsah zásobník textu. Zásobník textu obsahuje vložený obrázek, který není součástí rozsah textu.**  
  
 {Image} ![Vložený obrázek příkladu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") se vloží do textu.  
  
|Metodu s názvem|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "image".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> , který obklopuje rozsah textu; v takovém případě <xref:System.Windows.Automation.AutomationElement> , která představuje samotného poskytovatele textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> s parametry (TextUnit.Word, 1).|Přesune rozpětí textu rozsahu "je". Protože pouze textové vložené objekty jsou považovány za součást textového datového proudu, bitové kopie v tomto příkladu nemá vliv na přesunutí nebo jeho návratovou hodnotu (v tomto případě 1).|  
  
<a name="Table"></a>   
### <a name="table"></a>Tabulka  
  
### <a name="table-used-for-examples"></a>Tabulka použitá pro příklady  
  
|Buňka s Imagí|Buňka s textem|  
|---------------------|--------------------|  
|![Vložený obrázek příkladu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Vložený obrázek – příklad 2](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|A|  
|![Vložený obrázek – příklad 3](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Obrázek pro vykreslování|Z|  
  
 **Příklad 1 – získání zásobník textu z obsahu buňky.**  
  
|Metodu s názvem|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> s parametry (0; 0)|Vrátí <xref:System.Windows.Automation.AutomationElement> představující obsah buňky tabulky; v takovém případě prvek je ovládací prvek text.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený rutinou předchozí `GetItem` metody.|Vrátí rozsah, který zahrnuje obrázek ![vložený obrázek příkladu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> pro objekt vrácený rutinou předchozí `RangeFromChild` metody.|Vrátí <xref:System.Windows.Automation.AutomationElement> představující buňky tabulky; v takovém případě elementu je text ovládacího prvku, která podporuje vlastnost TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> pro objekt vrácený rutinou předchozí `GetEnclosingElement` metody.|Vrátí <xref:System.Windows.Automation.AutomationElement> představující tabulku.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> pro objekt vrácený rutinou předchozí `GetEnclosingElement` metody.|Vrátí <xref:System.Windows.Automation.AutomationElement> , která představuje samotného poskytovatele textu.|  
  
 **Příklad 2 – získání textový obsah buňky.**  
  
|Metodu s názvem|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> s parametry (1,1).|Vrátí <xref:System.Windows.Automation.AutomationElement> představující obsah buňky tabulky; v takovém případě prvek je ovládací prvek text.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený rutinou předchozí `GetItem` metody.|Vrátí "Y".|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.TextPattern>  
 <xref:System.Windows.Automation.Text.TextPatternRange>  
 <xref:System.Windows.Automation.Provider.ITextProvider>  
 <xref:System.Windows.Automation.Provider.ITextRangeProvider>  
 [Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)  
 [Vystavení obsahu tabulky s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/expose-the-content-of-a-table-using-ui-automation.md)  
 [Procházení textu s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/traverse-text-using-ui-automation.md)  
 [TextPattern vyhledávání a výběr ukázky](https://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)
