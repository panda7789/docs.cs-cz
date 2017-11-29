---
title: "Postupy: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b2d5c07be4ddebc3bfaa8c1979b39e3ef172a428
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Postupy: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel
Některé aplikace vyžadují formulář s rozložení, který samotné uspořádá správně při změně velikosti formuláře nebo se mění velikosti obsahu. Pokud potřebujete dynamické rozložení a nechcete zpracovat <xref:System.Windows.Forms.Control.Layout> události explicitně v kódu, zvažte pomocí panelů rozložení.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Řízení a <xref:System.Windows.Forms.TableLayoutPanel> řízení nabízejí intuitivní způsoby uspořádání ovládacích prvků na formuláři. Obě zadejte automatická, konfigurovat možnosti řízení relativní umístění podřízených ovládacích prvků v nich obsažená a obě získáte funkce dynamické rozložení v době běhu, takže jejich velikost a umístění můžete podřízené ovládací prvky jako rozměry nadřazeného formuláře změníte. Panelů rozložení lze začlenit do panelů rozložení, povolit provádění sofistikované uživatelská rozhraní.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Uspořádá jeho obsah v směr konkrétní toku: vodorovně nebo svisle. Jeho obsah může být uzavřen z jeden řádek na další, nebo z jednoho sloupce na další. Alternativně může být jeho obsah oříznut místo uzavřen. Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Uspořádá jeho obsah v mřížce, zajištění funkcí, které jsou podobné HTML \<tabulky > elementu. <xref:System.Windows.Forms.TableLayoutPanel> Řízení umožňuje umístit ovládací prvky v rozložení mřížky, aniž by bylo potřeba přesněji určit umístění každého jednotlivého ovládacího prvku. Jeho buněk jsou uspořádány do řádků a sloupců, a to může mít různou velikost. Buňky by se daly sloučit napříč řádků a sloupců. Buňky mohou obsahovat nic formuláře může obsahovat a chovat ve většině ostatních ohledech jako kontejnery.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek také poskytuje přímo úměrná změny velikosti funkci za běhu, takže rozložení můžete plynule změnit, protože se změnila velikost formuláře. Díky tomu <xref:System.Windows.Forms.TableLayoutPanel> řízení vhodný pro účely, například formuláře pro zadávání dat a lokalizované aplikace. Další informace najdete v tématu [návod: vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](http://msdn.microsoft.com/en-us/e193b4fc-912a-4917-b036-b76c7a6f58ab) a [návod: vytvoření formuláře Windows lokalizovatelný](http://msdn.microsoft.com/en-us/c5240b6e-aaca-4286-9bae-778a416edb9c).  
  
 Obecně byste neměli používat <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek jako kontejner pro celé rozložení. Použití <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvky zajistit přímo úměrná možnosti změny velikosti pro částí rozložení.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytvoření projektu modelu Windows Forms  
  
-   Uspořádání ovládacích prvků v řádků a sloupců  
  
-   Nastavení řádků a sloupců vlastnosti  
  
-   Rozložení řádků a sloupců s ovládacím prvkem  
  
-   Automatické zpracování přetečení  
  
-   Vkládání ovládacích prvků poklepáním na tyto v panelu nástrojů  
  
-   Vložení ovládacího prvku pomocí kreslení obrysu  
  
-   Nové přiřazení existujících ovládacích prvků jinému nadřazenému prvku  
  
 Jakmile budete hotovi, budete mít představu o úloze, kterou tyto funkce důležité rozložení.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavte formulář.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace pro systém Windows s názvem "TableLayoutPanelExample". Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Vybrat formuláře v **Windows** **Návrhář formulářů**.  
  
## <a name="arranging-controls-in-rows-and-columns"></a>Uspořádání ovládacích prvků v řádků a sloupců  
 <xref:System.Windows.Forms.TableLayoutPanel> Řízení umožňuje snadno uspořádání ovládacích prvků do řádků a sloupců.  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>K uspořádání ovládacích prvků v řádků a sloupců pomocí ovládacího prvku TableLayoutPanel  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře. Všimněte si, že se ve výchozím nastavení, <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek má čtyři buněk.  
  
2.  Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do <xref:System.Windows.Forms.TableLayoutPanel> řízení a umístěte jej do jednu z buněk. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek je vytvořen v rámci buňku vyberete.  
  
3.  Přetáhněte tři další <xref:System.Windows.Forms.Button> z ovládací prvky **sada nástrojů** do <xref:System.Windows.Forms.TableLayoutPanel> řídit, tak, aby každá buňka obsahuje tlačítko.  
  
4.  Získat svislé úchyt mezi dva sloupce a přesunout ho na levé straně. Všimněte si, že <xref:System.Windows.Forms.Button> menší šířka, při velikosti jsou změně velikosti ovládacích prvků v první sloupec <xref:System.Windows.Forms.Button> ovládací prvky v druhém sloupci se nemění.  
  
5.  Získat svislé úchyt mezi dva sloupce a přesunout ho vpravo. Všimněte si, že <xref:System.Windows.Forms.Button> ovládacích prvků v první sloupec vrátí k původní velikost, při <xref:System.Windows.Forms.Button> ovládací prvky v druhém sloupci přesunou vpravo.  
  
6.  Přesuňte vodorovné úchyt nahoru a dolů zobrazíte vliv na ovládací prvky v panelu.  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Umístění ovládacích prvků v buňkách pomocí ukotvení a ukotvení  
 Kotvícího chování podřízených ovládacích prvků v <xref:System.Windows.Forms.TableLayoutPanel> se liší od chování v další ovládací prvky kontejneru. Ukotvení podřízených ovládacích prvků chování je stejné jako další ovládací prvky kontejneru.  
  
#### <a name="positioning-controls-within-cells"></a>Umístění ovládacích prvků v buňkách  
  
1.  Vyberte první <xref:System.Windows.Forms.Button> ovládacího prvku. Změna hodnoty jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. Všimněte si, že <xref:System.Windows.Forms.Button> řízení zasahuje do jeho buňky.  
  
2.  Vyberte jednu z dalších <xref:System.Windows.Forms.Button> ovládací prvky. Změna hodnoty jeho <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.Right>. Všimněte si, že se přesune tak, aby jeho pravého okraje. je téměř pravého okraje buňky. Vzdálenost mezi ohraničením je součet hodnot <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti a na panelu <xref:System.Windows.Forms.Control.Padding%2A> vlastnost.  
  
3.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.Right> a <xref:System.Windows.Forms.AnchorStyles.Left>. Všimněte si, že je ovládací prvek velikosti šířky buňky, s <xref:System.Windows.Forms.Control.Margin%2A> a <xref:System.Windows.Forms.Control.Padding%2A> hodnoty vzít v úvahu.  
  
4.  Zopakujte kroky 2 a 3 s <xref:System.Windows.Forms.AnchorStyles.Top> a <xref:System.Windows.Forms.AnchorStyles.Bottom> styly.  
  
## <a name="setting-row-and-column-properties"></a>Nastavení řádků a sloupců vlastnosti  
 Jednotlivé vlastnosti řádků a sloupců lze nastavit pomocí <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> a <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekce.  
  
#### <a name="to-set-row-and-column-properties"></a>Chcete-li nastavit vlastnosti řádků a sloupců  
  
1.  Vyberte <xref:System.Windows.Forms.TableLayoutPanel> řídit ve **Návrhář formulářů Windows**.  
  
2.  V **vlastnosti** windows, otevřete <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekce kliknutím na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko vedle položky **sloupce** položku.  
  
3.  Vyberte první sloupec a změňte hodnotu jeho <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnost <xref:System.Windows.Forms.SizeType.AutoSize>. Klikněte na tlačítko **OK** potvrďte změny. Všimněte si, že šířka první sloupec je snížit podle <xref:System.Windows.Forms.Button> ovládacího prvku. Všimněte si také, že šířka sloupce není umožňující změnu velikosti.  
  
4.  V **vlastnosti** okno, otevřete <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekce a vyberte z prvního sloupce. Změna hodnoty jeho <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnost <xref:System.Windows.Forms.SizeType.Percent>. Klikněte na tlačítko **OK** potvrďte změny. Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> řídit k větší šířku a poznamenejte si, že rozšíří Šířka prvního sloupce. Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> řízení na menší šířku a Všimněte si, že jsou podle buňky dimenzované tlačítka prvního sloupce. Všimněte si také, že je šířka sloupce s možností změny velikosti.  
  
5.  V **vlastnosti** okno, otevřete <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> kolekce a vyberte všechny sloupců v seznamu. Nastavte hodnotu každých <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> vlastnost <xref:System.Windows.Forms.SizeType.Percent>. Klikněte na tlačítko **OK** potvrďte změny. Opakování s <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> kolekce.  
  
6.  Získat jeden z rohu Změna velikosti obslužné rutiny a změňte velikost šířku a výšku <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Všimněte si, že jsou změnit řádků a sloupců, jako <xref:System.Windows.Forms.TableLayoutPanel> změny velikosti ovládacího prvku. Také Upozorňujeme, že jsou řádky a sloupce s možností změny velikosti s ve vodorovném a svislého úchyty pro změnu velikosti.  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>Rozložení řádků a sloupců s ovládacím prvkem  
 <xref:System.Windows.Forms.TableLayoutPanel> Řízení přidá několik nových vlastností do ovládacích prvků v době návrhu. Dva z těchto vlastností jsou `RowSpan` a `ColumnSpan`. Tyto vlastnosti můžete použít k vytvoření ovládacího prvku rozpětí více než jeden řádek nebo sloupec.  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>Chcete-li rozpětí řádků a sloupců s ovládacím prvkem  
  
1.  Vyberte <xref:System.Windows.Forms.Button> ovládací prvek v prvním řádku a první sloupec.  
  
2.  V **vlastnosti** windows, změňte hodnotu `ColumnSpan` vlastnost **2**. Všimněte si, že <xref:System.Windows.Forms.Button> řízení doplní sloupci první a druhý sloupec. Všimněte si také než zvláštní řádek byl přidán do přizpůsobil této změně.  
  
3.  Opakujte krok 2 pro `RowSpan` vlastnost.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Vkládání ovládacích prvků poklepáním na tyto v panelu nástrojů  
 Jej můžete naplnit vaše <xref:System.Windows.Forms.TableLayoutPanel> řízení ovládacích prvků v dvojitým kliknutím **sada nástrojů**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Chcete-li vložit ovládací prvky dvojitým kliknutím na soubor v panelu nástrojů  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře.  
  
2.  Dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu ovládacího prvku v **sada nástrojů**. Všimněte si, že nový ovládací prvek tlačítko se zobrazí v <xref:System.Windows.Forms.TableLayoutPanel> první buňky ovládacího prvku.  
  
3.  Klikněte dvakrát na několik dalších ovládacích prvků v **sada nástrojů**. Zobrazit postupně v nových ovládacích prvků <xref:System.Windows.Forms.TableLayoutPanel> neobsazeného buňkách ovládacího prvku. Všimněte si také, že <xref:System.Windows.Forms.TableLayoutPanel> řízení rozšíří pro uložení nové ovládací prvky, pokud jsou k dispozici žádné otevřete buněk.  
  
## <a name="automatic-handling-of-overflows"></a>Automatické zpracování přetečení  
 Když jsou vkládání ovládacích prvků do <xref:System.Windows.Forms.TableLayoutPanel> řízení, můžete spustit z prázdných buněk pro nové prvky. <xref:System.Windows.Forms.TableLayoutPanel> Této situaci řízení automaticky zpracovává zvýšením počtu buněk.  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>Abyste mohli pozorovat automatické zpracování přetečení  
  
1.  Pokud jsou stále prázdných buněk v <xref:System.Windows.Forms.TableLayoutPanel> řídit, pokračovat vkládání nových <xref:System.Windows.Forms.Button> řídí až <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek je plný.  
  
2.  Jednou <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek je plná, dvakrát klikněte na <xref:System.Windows.Forms.Button> ikonu v **sada nástrojů** vložit jiné <xref:System.Windows.Forms.Button> ovládacího prvku. Všimněte si, že <xref:System.Windows.Forms.TableLayoutPanel> řízení vytvoří nové buňky pro umístění nového ovládacího prvku. Vložte několik další ovládací prvky a pozorovat chování změny velikosti.  
  
3.  Změňte hodnotu <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> vlastnost <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Dvakrát klikněte na <xref:System.Windows.Forms.Button> ikonu v **sada nástrojů** vložit <xref:System.Windows.Forms.Button> řídí až <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek je plný. Dvakrát klikněte <xref:System.Windows.Forms.Button> ikonu v **sada nástrojů** znovu. Všimněte si, zda se zobrazila chybová zpráva z **Návrhář formulářů Windows** že nelze vytvořit další řádků a sloupců.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku pomocí kreslení obrysu  
 Můžete vložit do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> řízení a kreslení obrysu v buňce zadejte jeho velikost.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Vložení ovládacího prvku pomocí kreslení obrysu  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře.  
  
2.  V **sada nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.Button> ikonu ovládacího prvku. Přetáhněte není jej do formuláře.  
  
3.  Přesuňte ukazatel myši <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Všimněte si, že se nezmění na záměrný kříž s <xref:System.Windows.Forms.Button> řízení ikonu připojen.  
  
4.  Klikněte na tlačítko a podržte tlačítko myši.  
  
5.  Přetáhněte ukazatel myši k vykreslení obrys <xref:System.Windows.Forms.Button> ovládacího prvku. Jakmile budete spokojeni s velikostí, uvolnění tlačítka myši. Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek je vytvořen v buňce, ve kterém obrázek ovládacího prvku outline.  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>Více ovládacích prvků v buňkách není povolený.  
 <xref:System.Windows.Forms.TableLayoutPanel> Řízení může obsahovat pouze jeden podřízený ovládací prvek v jedné buňce.  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>K předvedení toho, že nejsou povolené více ovládacích prvků v buňkách  
  
-   Přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do <xref:System.Windows.Forms.TableLayoutPanel> řízení a umístěte jej do jednoho z obsazené buněk. Všimněte si, že <xref:System.Windows.Forms.TableLayoutPanel> řízení neumožňuje vyřadit <xref:System.Windows.Forms.Button> ovládacího prvku do obsazené buňky.  
  
## <a name="swapping-controls"></a>Vzájemná záměna ovládací prvky  
 <xref:System.Windows.Forms.TableLayoutPanel> Řízení umožňuje odkládacího souboru v dvě různé buňky ovládacích prvků.  
  
#### <a name="to-swap-controls"></a>Chcete Prohodit ovládací prvky  
  
-   Přetáhněte jeden z <xref:System.Windows.Forms.Button> ovládacích prvků z obsazené buňky a drop do na jinou buňku obsazené. Všimněte si, že dvou ovládacích prvků přesunou z jedné buňky do druhé.  
  
## <a name="next-steps"></a>Další kroky  
 Komplexní rozložení pomocí kombinace panelů rozložení a ovládací prvky můžete dosáhnout. Návrhy na další průzkum patří:  
  
-   Zkuste upravit velikost mezi <xref:System.Windows.Forms.Button> ovládací prvky na větší velikost a Poznámka vliv na rozložení.  
  
-   Výběr více ovládacích prvků do vložit <xref:System.Windows.Forms.TableLayoutPanel> řízení a Všimněte si, jak jsou ovládací prvky vloženy.  
  
-   Panelů rozložení může obsahovat další panely rozložení. Experiment s vyřazování <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku do existujícího ovládacího prvku.  
  
-   Ukotvení <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku do nadřazené formuláře. Změnit velikost formuláře a poznamenejte si vliv na rozložení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Uživatelské prostředí pro Microsoft Windows, oficiální pokyny pro uživatelské rozhraní vývojářů a návrhářů. Brno: Společnosti Microsoft Press, 1999. (USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](http://msdn.microsoft.com/en-us/e193b4fc-912a-4917-b036-b76c7a6f58ab)  
 [Návod: Vytvoření formuláře lokalizovatelný Windows](http://msdn.microsoft.com/en-us/c5240b6e-aaca-4286-9bae-778a416edb9c)  
 [Osvědčené postupy pro ovládací prvek TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 [Přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Postupy: Ukotvování ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Postupy: Ukotvování ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Návod: Rozvrhování Windows Forms – ovládací prvky s odsazením, okraji a s vlastností AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
