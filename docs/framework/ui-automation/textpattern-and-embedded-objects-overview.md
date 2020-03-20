---
title: TextPattern a vložené objekty – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: 635c06a03107b33134b015e2643c5281dd86798b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180004"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern a vložené objekty – přehled
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Tento přehled popisuje, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zpřístupňuje vložené objekty nebo podřízené prvky v textovém dokumentu nebo kontejneru.  
  
 Ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vloženém objektu je libovolný prvek, který má netextové hranice; například obrázek, hypertextový odkaz, tabulka nebo typ dokumentu, například tabulka aplikace Microsoft Excel nebo soubor Microsoft Windows Media. To se liší od standardní definice, kde je prvek vytvořen v jedné aplikaci a vložený nebo propojený v rámci jiné. Zda lze objekt upravovat v rámci původní aplikace, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]je v kontextu aplikace irelevantní.  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Vložené objekty a strom automatizace uživatelského rozhraní  
 Vložené objekty jsou považovány za jednotlivé prvky v ovládacím pohledu stromu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Jsou vystaveny jako podřízené textového kontejneru tak, aby k nim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bylo možné přistupovat prostřednictvím stejného modelu jako ostatní ovládací prvky v aplikaci .  
  
 ![Vložená tabulka s obrazem v textovém kontejneru](./media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Příklad textového kontejneru s vloženými objekty tabulky, obrazu a hypertextového odkazu  
  
 ![Zobrazení obsahu pro předchozí příklad](./media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Příklad zobrazení obsahu pro část předchozího textového kontejneru  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Vystavit vložené objekty pomocí TextPattern a TextPatternRange  
 Používá se ve <xref:System.Windows.Automation.TextPattern> spojení, třída <xref:System.Windows.Automation.Text.TextPatternRange> vzor ovládacího prvku a třída vystavit metody a vlastnosti, které usnadňují navigaci a dotazování vložených objektů.  
  
 Textový obsah (nebo vnitřní text) textového kontejneru a vloženého objektu, například hypertextový odkaz nebo buňka tabulky, je vystaven jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jeden souvislý textový proud v zobrazení ovládacího prvku i v zobrazení obsahu stromu; hranice objektu jsou ignorovány. Pokud klient automatizace uživatelského rozhraní načítá text za účelem recitování, interpretace nebo analýzy nějakým způsobem, rozsah textu by měl být zkontrolován pro zvláštní případy, jako je například tabulka s textovým obsahem nebo jiné vložené objekty. Toho lze provést voláním <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> získat <xref:System.Windows.Automation.AutomationElement> pro každý vložený <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> objekt a volání získat rozsah textu pro každý prvek. To se provádí rekurzivně, dokud není načten veškerý textový obsah.  
  
 ![Rozsahy textu rozložené vloženými objekty.](./media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Příklad datového proudu textu s vloženými objekty a jejich rozsahem  
  
 Pokud je nutné procházet obsah rozsahu textu, jsou zapojeny řady kroků na <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> pozadí, aby metoda úspěšně spustit.  
  
1. Rozsah textu je normalizován; to znamená, že rozsah textu je sbalen <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> do degenerované oblasti <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> v koncovém bodě, což činí koncový bod nadbytečným. Tento krok je nezbytný k odstranění nejednoznačnosti v <xref:System.Windows.Automation.Text.TextUnit> situacích, `{The URL https://www.microsoft.com is embedded in text` kdy rozsah textu zahrnuje hranice: například kde "{" a "}" jsou koncové body rozsahu textu.  
  
2. Výsledný rozsah se posune <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> zpět na začátek <xref:System.Windows.Automation.Text.TextUnit> požadované hranice.  
  
3. Rozsah se posune dopředu <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> nebo dozadu v <xref:System.Windows.Automation.Text.TextUnit> požadovaném počtu hranic.  
  
4. Oblast je pak rozbalena ze stavu <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> degenerované oblasti <xref:System.Windows.Automation.Text.TextUnit> přesunutím koncového bodu o jednu požadovanou hranici.  
  
 ![Úpravy rozsahu pomocí přesunout & ExpandToEnclosingUnit](./media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Příklady úpravy rozsahu textu pro Move() a ExpandToEnclosingUnit()  
  
<a name="Common_Scenarios"></a>
## <a name="common-scenarios"></a>Obvyklé situace  
 V následujících částech jsou uvedeny příklady nejběžnějších scénářů, které zahrnují vložené objekty.  
  
 Legenda pro zobrazené příklady:  
  
 { =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Hypertextový odkaz  

**Příklad 1 – Oblast textu obsahující vložený textový hypertextový odkaz**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Metoda volaná|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec `The URL https://www.microsoft.com is embedded in text`.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější, <xref:System.Windows.Automation.AutomationElement> který obklopuje rozsah textu; v tomto <xref:System.Windows.Automation.AutomationElement> případě, který představuje samotného poskytovatele textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí <xref:System.Windows.Automation.AutomationElement> ovládací prvek představující hypertextový odkaz.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácen `GetChildren` předchozí metodou.|Vrátí oblast, kteráhttps://www.microsoft.compředstavuje " ".|  
  
 **Příklad 2 – Oblast textu, která částečně pokrývá vložený textový hypertextový odkaz**  
  
 Adresa `https://{[www]}` URL je vložena do textu.  
  
|Metoda volaná|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější, <xref:System.Windows.Automation.AutomationElement> který obklopuje rozsah textu; v tomto případě ovládací prvek hypertextového odkazu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí `null` se, protože rozsah textu nezahrnuje celý řetězec adresy URL.|  
  
**Příklad 3 – Oblast textu, která částečně pokrývá obsah textového kontejneru. Textový kontejner obsahuje vložený textový hypertextový odkaz, který není součástí rozsahu textu.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Metoda volaná|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "Adresa URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější, <xref:System.Windows.Automation.AutomationElement> který obklopuje rozsah textu; v tomto <xref:System.Windows.Automation.AutomationElement> případě, který představuje samotného poskytovatele textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>s parametry (TextUnit.Word, 1).|Přesune rozsah rozsahu textu na "http", protože text hypertextového odkazu se skládá z jednotlivých slov. V tomto případě není hypertextový odkaz považován za jeden objekt.<br /><br /> Adresa URL {[http]} je vložena do textu.|  
  
<a name="Image"></a>
### <a name="image"></a>Image  
 **Příklad 1 – Oblast textu, která obsahuje vložený obrázek**  
  
 {Příklad ![vloženého obrázku](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") je vložen do textu}.  
  
|Metoda volaná|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "Je vložen do textu". Nelze očekávat, že do datového proudu textu bude zahrnut žádný text ALT přidružený k obrázku.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější, <xref:System.Windows.Automation.AutomationElement> který obklopuje rozsah textu; v tomto <xref:System.Windows.Automation.AutomationElement> případě, který představuje samotného poskytovatele textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí <xref:System.Windows.Automation.AutomationElement> ovládací prvek představující obraz.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácen <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> předchozí metodou.|Vrátí degenerovaný rozsah, který představuje "![Příklad vloženého obrázku](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Příklad 2 – Oblast textu, která částečně pokrývá obsah textového kontejneru. Textový kontejner má vložený obraz, který není součástí rozsahu textu.**  
  
 {Obrázek} ![Příklad vloženého obrázku](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") je vložen do textu.  
  
|Metoda volaná|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "Obrázek".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější, <xref:System.Windows.Automation.AutomationElement> který obklopuje rozsah textu; v tomto <xref:System.Windows.Automation.AutomationElement> případě, který představuje samotného poskytovatele textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>s parametry (TextUnit.Word, 1).|Přesune rozsah rozsahu textu na "je ". Vzhledem k tomu, že pouze textové vložené objekty jsou považovány za součást datového proudu textu, obraz v tomto příkladu nemá vliv přesunout nebo jeho vrácená hodnota (1 v tomto případě).|  
  
<a name="Table"></a>
### <a name="table"></a>Table  
  
### <a name="table-used-for-examples"></a>Tabulka použitá pro příklady  
  
|Buňka s obrazem|Buňka s textem|  
|---------------------|--------------------|  
|![Příklad vloženého obrázku](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|×|  
|![Příklad vloženého obrázku 2](./media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|Ano|  
|![Příklad vloženého obrázku 3](./media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Obrázek pro Z|Z|  
  
 **Příklad 1 – Získejte textový kontejner z obsahu buňky.**  
  
|Metoda volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>s parametry (0,0)|Vrátí <xref:System.Windows.Automation.AutomationElement> obsah buňky tabulky; v tomto případě prvek je textový ovládací prvek.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácen `GetItem` předchozí metodou.|Vrátí rozsah, který pokrývá ![příklad vloženého obrazu](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>pro objekt vrácený `RangeFromChild` předchozí metodou.|Vrátí <xref:System.Windows.Automation.AutomationElement> představující buňku tabulky; v tomto případě prvek je textový ovládací prvek, který podporuje TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>pro objekt vrácený `GetEnclosingElement` předchozí metodou.|Vrátí <xref:System.Windows.Automation.AutomationElement> představující tabulku.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>pro objekt vrácený `GetEnclosingElement` předchozí metodou.|<xref:System.Windows.Automation.AutomationElement> Vrátí, který představuje samotného poskytovatele textu.|  
  
 **Příklad 2 – Získání textového obsahu buňky.**  
  
|Metoda volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>s parametry (1,1).|Vrátí <xref:System.Windows.Automation.AutomationElement> obsah buňky tabulky; v tomto případě prvek je textový ovládací prvek.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácen `GetItem` předchozí metodou.|Vrátí "Y".|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní](access-embedded-objects-using-ui-automation.md)
- [Vystavení obsahu tabulky s použitím automatizace uživatelského rozhraní](expose-the-content-of-a-table-using-ui-automation.md)
- [Procházení textu s použitím automatizace uživatelského rozhraní](traverse-text-using-ui-automation.md)
- [Ukázka hledání a výběru textových vzorů](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
