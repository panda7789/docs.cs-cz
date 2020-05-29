---
title: TextPattern a vložené objekty – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: 7a3338a08d06320acdc2acb0647bc91541448d7d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201073"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern a vložené objekty – přehled
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Tento přehled popisuje [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , jak zpřístupňuje vložené objekty nebo podřízené prvky v rámci textového dokumentu nebo kontejneru.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rámci vloženého objektu je libovolný prvek, který obsahuje netextové hranice; například obrázek, hypertextový odkaz, tabulku nebo typ dokumentu, jako je například tabulka aplikace Microsoft Excel nebo soubor Microsoft Windows Media. To se liší od standardní definice, kde je prvek vytvořen v jedné aplikaci a vloženě nebo propojen v rámci jiného. Určuje, zda lze objekt upravovat v rámci původní aplikace, je irelevantní v kontextu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Vložené objekty a strom automatizace uživatelského rozhraní  
 Vložené objekty jsou považovány za jednotlivé prvky v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Jsou přístupné jako podřízené objekty kontejneru textu tak, aby mohly být přístupné prostřednictvím stejného modelu jako jiné ovládací prvky v nástroji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 ![Vložená tabulka s obrázkem v kontejneru textu](./media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Příklad kontejneru textu s vloženými objekty tabulka, obrázek a hypertextový odkaz  
  
 ![Zobrazení obsahu pro předchozí příklad](./media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Příklad zobrazení obsahu pro část předchozího textového kontejneru  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Vystavení vložených objektů pomocí TextPattern a TextPatternRange  
 Používá se ve spojení <xref:System.Windows.Automation.TextPattern> třídy vzoru ovládacího prvku a <xref:System.Windows.Automation.Text.TextPatternRange> třídy a zpřístupňuje metody a vlastnosti, které usnadňují navigaci a dotazování na vložené objekty.  
  
 Textový obsah (nebo vnitřní text) textového kontejneru a vložený objekt, jako je například hypertextový odkaz nebo buňka tabulky, je zveřejněn jako jediný souvislý textový Stream v zobrazení ovládacího prvku i v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. hranice objektů jsou ignorovány. Pokud klient služby automatizace uživatelského rozhraní načítá text pro účely reciting, interpretuje nebo analyzuje nějaký způsob, je nutné zkontrolovat rozsah textu pro zvláštní případy, jako je například tabulka s textovým obsahem nebo jinými vloženými objekty. To lze provést voláním metody pro <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> získání <xref:System.Windows.Automation.AutomationElement> každého vloženého objektu a následným voláním <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> k získání textového rozsahu pro každý prvek. To se provádí rekurzivně, dokud se všechen textový obsah nenačte.  
  
 ![Rozsahy textu rozložené vloženými objekty.](./media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Příklad textového streamu se vložené objekty a jejich rozsahy  
  
 Je-li nutné procházet obsah určitého rozsahu textu, je na pozadí zahrnuta řada kroků, aby <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> bylo možné metodu úspěšně spustit.  
  
1. Rozsah textu je normalizován; To znamená, že rozsah textu je sbalený do degenerovaného rozsahu na <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> koncovém bodu, což způsobuje, že <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncový bod je nadbytečný. Tento krok je nezbytný k odebrání nejednoznačnosti v situacích, kdy rozsah textu pokrývá <xref:System.Windows.Automation.Text.TextUnit> hranice: například `{The URL https://www.microsoft.com is embedded in text` Pokud jsou koncové body oblasti textu "{" a "}".  
  
2. Výsledný rozsah se přesune zpět do <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> začátku požadované <xref:System.Windows.Automation.Text.TextUnit> hranice.  
  
3. Rozsah se přesune dopředu nebo dozadu v požadovaném <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> počtu <xref:System.Windows.Automation.Text.TextUnit> hranic.  
  
4. Rozsah se pak rozšíří z negenerovaného stavu rozsahu přesunutím <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncového bodu o jednu požadovanou <xref:System.Windows.Automation.Text.TextUnit> hranici.  
  
 ![Úpravy rozsahu přesunutím & ExpandToEnclosingUnit](./media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Příklady přizpůsobení rozsahu textu pro Move () a ExpandToEnclosingUnit ()  
  
<a name="Common_Scenarios"></a>
## <a name="common-scenarios"></a>Obvyklé situace  
 Následující části obsahují příklady nejběžnějších scénářů, které zahrnují vložené objekty.  
  
 Legenda pro uvedené příklady:  
  
 { =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Hypertextový odkaz  

**Příklad 1 – textový rozsah, který obsahuje vložený textový hypertextový odkaz**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Metoda je volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec `The URL https://www.microsoft.com is embedded in text` .|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> text, který obklopuje rozsah textu; v tomto případě <xref:System.Windows.Automation.AutomationElement> představuje samotný poskytovatel textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí <xref:System.Windows.Automation.AutomationElement> reprezentující ovládací prvek hypertextový odkaz.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený předchozí `GetChildren` metodou.|Vrátí rozsah, který představuje `https://www.microsoft.com` .|  
  
 **Příklad 2 – textový rozsah, který je částečně rozložen k vloženému textovému odkazu**  
  
 Adresa URL `https://{[www]}` je vložena do textu.  
  
|Metoda je volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> , který obklopuje rozsah textu; v tomto případě ovládací prvek hypertextový odkaz.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí hodnotu, `null` protože rozsah textu nepokrývá celý řetězec adresy URL.|  
  
**Příklad 3 – rozsah textu, který je částečně rozložen na obsah kontejneru textu. Textový kontejner obsahuje vložený textový hypertextový odkaz, který není součástí rozsahu textu.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Metoda je volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "adresa URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> text, který obklopuje rozsah textu; v tomto případě <xref:System.Windows.Automation.AutomationElement> představuje samotný poskytovatel textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>s parametry (TextUnit. Word, 1).|Přesune rozsah textu na "http", protože text hypertextového odkazu se skládá z jednotlivých slov. V takovém případě se hypertextový odkaz nepovažuje za jeden objekt.<br /><br /> Adresa URL {[http]} je vložena do textu.|  
  
<a name="Image"></a>
### <a name="image"></a>Image  
 **Příklad 1 – textový rozsah obsahující vložený obrázek**  
  
 {Ukázka obrázku ![vložený](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") obrázek je vložená do textu}.  
  
|Metoda je volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec ", který je vložen do textu". U libovolného textu ALT přidruženého k imagi se nedá zahrnout do textového streamu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> text, který obklopuje rozsah textu; v tomto případě <xref:System.Windows.Automation.AutomationElement> představuje samotný poskytovatel textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Vrátí <xref:System.Windows.Automation.AutomationElement> reprezentující ovládací prvek obrázku.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený předchozí <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> metodou.|Vrátí rozsah degenerování, který představuje "![vložený obrázek příklad](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Příklad 2 – rozsah textu, který je částečně rozložen na obsah kontejneru textu. Kontejner textu obsahuje vložený obrázek, který není součástí rozsahu textu.**  
  
 {Image} ![Ukázka vloženého obrázku](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") je vložená v textu.  
  
|Metoda je volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Vrátí řetězec "image".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Vrátí nejvnitřnější <xref:System.Windows.Automation.AutomationElement> text, který obklopuje rozsah textu; v tomto případě <xref:System.Windows.Automation.AutomationElement> představuje samotný poskytovatel textu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>s parametry (TextUnit. Word, 1).|Přesune rozsah textu na hodnotu "is". Vzhledem k tomu, že pouze textové vložené objekty jsou považovány za součást textového streamu, obrázek v tomto příkladu nemá vliv na přesun nebo jeho návratovou hodnotu (1 v tomto případě).|  
  
<a name="Table"></a>
### <a name="table"></a>Table  
  
### <a name="table-used-for-examples"></a>Tabulka použitá pro příklady  
  
|Buňka s obrázkem|Buňka s textem|  
|---------------------|--------------------|  
|![Příklad vloženého obrázku](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Příklad vložené obrázku 2](./media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|Y|  
|![Příklad vložené Image 3](./media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Obrázek pro Z|Z|  
  
 **Příklad 1 – získání kontejneru textu z obsahu buňky**  
  
|Metoda je volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>s parametry (0, 0)|Vrátí <xref:System.Windows.Automation.AutomationElement> reprezentující obsah buňky tabulky. v tomto případě je element ovládacím prvkem text.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený předchozí `GetItem` metodou.|Vrátí rozsah, který je rozložen jako ![příklad obrázku vloženého](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")obrázku.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>pro objekt vrácený předchozí `RangeFromChild` metodou.|Vrátí <xref:System.Windows.Automation.AutomationElement> reprezentující buňku tabulky. v tomto případě je prvek textovým ovládacím prvkem, který podporuje TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>pro objekt vrácený předchozí `GetEnclosingElement` metodou.|Vrátí <xref:System.Windows.Automation.AutomationElement> reprezentaci tabulky.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>pro objekt vrácený předchozí `GetEnclosingElement` metodou.|Vrátí <xref:System.Windows.Automation.AutomationElement> , který představuje samotného poskytovatele textu.|  
  
 **Příklad 2 – získání textového obsahu buňky**  
  
|Metoda je volána|Výsledek|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>s parametry (1, 1).|Vrátí <xref:System.Windows.Automation.AutomationElement> reprezentující obsah buňky tabulky. v tomto případě je element ovládacím prvkem text.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>kde <xref:System.Windows.Automation.AutomationElement> je objekt vrácený předchozí `GetItem` metodou.|Vrátí "Y".|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní](access-embedded-objects-using-ui-automation.md)
- [Vystavení obsahu tabulky s použitím automatizace uživatelského rozhraní](expose-the-content-of-a-table-using-ui-automation.md)
- [Procházení textu s použitím automatizace uživatelského rozhraní](traverse-text-using-ui-automation.md)
- [Ukázka hledání a výběru TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
