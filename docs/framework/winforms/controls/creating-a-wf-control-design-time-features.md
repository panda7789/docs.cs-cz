---
title: Vytvoření ovládacího prvku, který využívá výhod funkcí nástroje Visual Studio pro dobu návrhu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7166b4203c54ab31f1d929c85cf1e6481ff120f8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744074"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a>Návod: vytvoření ovládacího prvku, který bude využívat funkce pro dobu návrhu

Prostředí pro návrh vlastního ovládacího prvku lze zvýšit vytvořením přidruženého vlastního návrháře.

Tento článek ukazuje, jak vytvořit vlastního návrháře vlastního ovládacího prvku. Implementujete `MarqueeControl` typ a přidruženou třídu návrháře nazvanou `MarqueeControlRootDesigner`.

Typ `MarqueeControl` implementuje zobrazení podobné textu v kino s animovanými indikátory a blikajícím textem.

Návrhář pro tento ovládací prvek komunikuje s vývojovým prostředím, aby poskytoval vlastní prostředí pro dobu návrhu. Pomocí vlastního návrháře můžete sestavit vlastní `MarqueeControl` implementaci pomocí animovaných světel a blikání textu v mnoha kombinacích. Můžete použít sestavený ovládací prvek na formuláři, stejně jako jakýkoli jiný ovládací prvek model Windows Forms.

Až budete s tímto návodem hotový, váš vlastní ovládací prvek bude vypadat přibližně takto:

![Aplikace, která zobrazuje text a tlačítka Spustit a zastavit](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

Úplný výpis kódu naleznete v tématu [How to: Create a model Windows Forms Control, který využívá funkce pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).

## <a name="prerequisites"></a>Předpoklady

Aby bylo možné dokončit tento návod, budete potřebovat aplikaci Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu aplikace. Pomocí tohoto projektu sestavíte aplikaci, která je hostitelem vlastního ovládacího prvku.

V aplikaci Visual Studio vytvořte nový projekt aplikace model Windows Forms a pojmenujte jej **MarqueeControlTest**.

## <a name="create-the-control-library-project"></a>Vytvořit projekt knihovny ovládacích prvků

1. Přidejte do řešení projekt knihovny ovládacích prvků model Windows Forms. Pojmenujte projekt **MarqueeControlLibrary**.

2. Pomocí **Průzkumník řešení**odstraňte výchozí ovládací prvek projektu odstraněním zdrojového souboru s názvem "UserControl1.cs" nebo "UserControl1. vb" v závislosti na zvoleném jazyce.

3. Přidejte novou <xref:System.Windows.Forms.UserControl>ovou položku do projektu `MarqueeControlLibrary`. Dejte novému zdrojovému souboru základní název **MarqueeControl**.

4. Pomocí **Průzkumník řešení**vytvořte novou složku v projektu `MarqueeControlLibrary`.

5. Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu. Pojmenujte ho **MarqueeControlRootDesigner**.

6. Budete muset použít typy ze sestavení System. design, takže přidejte tento odkaz do projektu `MarqueeControlLibrary`.

## <a name="reference-the-custom-control-project"></a>Odkaz na projekt vlastního ovládacího prvku

K otestování vlastního ovládacího prvku použijete `MarqueeControlTest` projekt. Testovací projekt se při přidání odkazu na projekt do sestavení `MarqueeControlLibrary` stane vědět o vlastním ovládacím prvku.

V projektu `MarqueeControlTest` přidejte odkaz na projekt do sestavení `MarqueeControlLibrary`. Nezapomeňte použít kartu **projekty** v dialogovém okně **Přidat odkaz** namísto odkazování na `MarqueeControlLibrary` sestavení přímo.

## <a name="define-a-custom-control-and-its-custom-designer"></a>Definování vlastního ovládacího prvku a jeho vlastního návrháře

Vlastní ovládací prvek bude odvozen z třídy <xref:System.Windows.Forms.UserControl>. To umožňuje vašemu ovládacímu prvku, aby obsahoval další ovládací prvky, a poskytuje vašemu ovládacímu prvku skvělou výchozí funkčnost.

Vlastní ovládací prvek bude mít přidružený vlastní Návrhář. To vám umožní vytvořit jedinečné vývojové prostředí, které se přizpůsobí speciálně pro váš vlastní ovládací prvek.

K přidružení ovládacího prvku ke svému návrháři použijte třídu <xref:System.ComponentModel.DesignerAttribute>. Vzhledem k tomu, že vyvíjíte celé chování vlastního ovládacího prvku v době návrhu, bude vlastní Návrhář implementovat rozhraní <xref:System.ComponentModel.Design.IRootDesigner>.

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Definování vlastního ovládacího prvku a jeho vlastního návrháře

1. Otevřete zdrojový soubor `MarqueeControl` v **editoru kódu**. V horní části souboru importujte následující obory názvů:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. Přidejte <xref:System.ComponentModel.DesignerAttribute> do deklarace třídy `MarqueeControl`. Tím přiřadíte vlastní ovládací prvek ke svému návrháři.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. Otevřete zdrojový soubor `MarqueeControlRootDesigner` v **editoru kódu**. V horní části souboru importujte následující obory názvů:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. Změňte deklaraci `MarqueeControlRootDesigner`, aby dědila z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy. Použijte <xref:System.ComponentModel.ToolboxItemFilterAttribute> k určení interakce návrháře pomocí **sady nástrojů**.

   > [!NOTE]
   > Definice pro třídu `MarqueeControlRootDesigner` byla uzavřená v oboru názvů s názvem MarqueeControlLibrary. Design. Tato deklarace umístí návrháře ve speciálním oboru názvů vyhrazeném pro typy související s návrhem.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. Definujte konstruktor pro třídu `MarqueeControlRootDesigner`. Do těla konstruktoru vložte příkaz <xref:System.Diagnostics.Trace.WriteLine%2A>. To bude užitečné pro ladění.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a>Vytvoření instance vlastního ovládacího prvku

1. Přidejte novou <xref:System.Windows.Forms.UserControl>ovou položku do projektu `MarqueeControlTest`. Dejte novému zdrojovému souboru základní název **DemoMarqueeControl**.

2. Otevřete `DemoMarqueeControl` soubor v **editoru kódu**. V horní části souboru importujte `MarqueeControlLibrary` obor názvů:

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. Změňte deklaraci `DemoMarqueeControl`, aby dědila z `MarqueeControl` třídy.

4. Sestavte projekt.

5. Otevřete Form1 v Návrhář formulářů.

6. V **sadě nástrojů** Najděte kartu **komponenty MarqueeControlTest** a otevřete ji. Přetáhněte `DemoMarqueeControl` ze **sady nástrojů** do formuláře.

7. Sestavte projekt.

## <a name="set-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu

Při vývoji vlastního prostředí v době návrhu bude nutné ladit ovládací prvky a komponenty. Existuje jednoduchý způsob, jak nastavit projekt tak, aby umožňoval ladění v době návrhu. Další informace naleznete v tématu [Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).

1. Klikněte pravým tlačítkem na projekt `MarqueeControlLibrary` a vyberte **vlastnosti**.

2. V dialogovém okně **stránky vlastností MarqueeControlLibrary** vyberte stránku **ladění** .

3. V části **spouštěcí akce** vyberte **spustit externí program**. Budete ladit samostatnou instanci aplikace Visual Studio, proto klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio](./media/visual-studio-ellipsis-button.png)) a vyhledejte integrované vývojové prostředí (IDE) sady Visual Studio. Název spustitelného souboru je devenv. exe a pokud jste nainstalovali do výchozího umístění, jeho cesta je *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<edition > \Common7\IDE\devenv.exe*.

4. Kliknutím na **tlačítko OK** zavřete dialogové okno.

5. Klikněte pravým tlačítkem na projekt MarqueeControlLibrary a vyberte **nastavit jako spouštěný projekt** , abyste mohli tuto konfiguraci ladění povolit.

## <a name="checkpoint"></a>CheckPoint

Nyní jste připraveni ladit chování vlastního ovládacího prvku v době návrhu. Jakmile zjistíte, že je prostředí ladění správně nastavené, otestujete přidružení mezi vlastním ovládacím prvkem a vlastním návrhářem.

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Otestování ladicího prostředí a přidružení návrháře

1. Otevřete zdrojový soubor MarqueeControlRootDesigner v **editoru kódu** a umístěte zarážku na příkaz <xref:System.Diagnostics.Trace.WriteLine%2A>.

2. Stisknutím klávesy **F5** spusťte relaci ladění.

   Vytvoří se nová instance sady Visual Studio.

3. V nové instanci aplikace Visual Studio otevřete řešení MarqueeControlTest. Řešení můžete snadno najít výběrem položky **Poslední projekty** v nabídce **soubor** . Soubor řešení MarqueeControlTest. sln bude uveden jako naposledy použitý soubor.

4. Otevřete `DemoMarqueeControl` v návrháři.

   Instance ladění aplikace Visual Studio získá fokus a provádění se zastaví na zarážce. Stisknutím klávesy **F5** pokračujte v relaci ladění.

V tomto okamžiku je vše pro vývoj a ladění vlastního ovládacího prvku a jeho přidruženého vlastního návrháře. Zbývající část tohoto článku se zaměřuje na podrobnosti o implementaci funkcí ovládacího prvku a návrháře.

## <a name="implement-the-custom-control"></a>Implementace vlastního ovládacího prvku

`MarqueeControl` je <xref:System.Windows.Forms.UserControl> s malým množstvím přizpůsobení. Zpřístupňuje dvě metody: `Start`, který spustí animaci běžící na hranice a `Stop`, která zastaví animaci. Vzhledem k tomu, že `MarqueeControl` obsahuje podřízené ovládací prvky, které implementují rozhraní `IMarqueeWidget`, `Start` a `Stop` vyčíslení každého podřízeného ovládacího prvku a volání `StartMarquee` a `StopMarquee` metody v uvedeném pořadí v každém podřízeném ovládacím prvku, který implementuje `IMarqueeWidget`.

Vzhled ovládacích prvků `MarqueeBorder` a `MarqueeText` je závislý na rozložení, takže `MarqueeControl` přepisuje metodu <xref:System.Windows.Forms.Control.OnLayout%2A> a volá <xref:System.Windows.Forms.Control.PerformLayout%2A> na podřízených ovládacích prvcích tohoto typu.

Toto je rozsah přizpůsobení `MarqueeControl`. Běhové funkce jsou implementovány ovládacími prvky `MarqueeBorder` a `MarqueeText` a funkce v době návrhu jsou implementovány třídami `MarqueeBorderDesigner` a `MarqueeControlRootDesigner`.

### <a name="to-implement-your-custom-control"></a>Implementace vlastního ovládacího prvku

1. Otevřete zdrojový soubor `MarqueeControl` v **editoru kódu**. Implementujte metody `Start` a `Stop`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. Přepsat metodu <xref:System.Windows.Forms.Control.OnLayout%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a>Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek

`MarqueeControl` bude hostovat dva druhy podřízených ovládacích prvků: ovládací prvek `MarqueeBorder` a ovládací prvek `MarqueeText`.

- `MarqueeBorder`: Tento ovládací prvek vykreslí ohraničení "světel" kolem jeho okrajů. Světla se zobrazí v sekvenci, takže se zdají kolem ohraničení pohybovat. Rychlost, s jakou jsou indikátory blesku ovládány vlastností nazvanou `UpdatePeriod`. Některé další vlastní vlastnosti určují další aspekty vzhledu ovládacího prvku. Dvě metody nazvané `StartMarquee` a `StopMarquee`určují, kdy se animace spouští a zastavuje.

- `MarqueeText`: Tento ovládací prvek vykreslí blikající řetězec. Podobně jako u ovládacího prvku `MarqueeBorder` je rychlost, s jakou je text blikající, ovládána vlastností `UpdatePeriod`. Ovládací prvek `MarqueeText` má také společné metody `StartMarquee` a `StopMarquee` s ovládacím prvkem `MarqueeBorder`.

V době návrhu `MarqueeControlRootDesigner` umožňuje přidat tyto dva typy ovládacích prvků do `MarqueeControl` v jakékoli kombinaci.

Společné funkce těchto dvou ovládacích prvků jsou přihlédnuto do rozhraní s názvem `IMarqueeWidget`. To umožňuje `MarqueeControl` objevit podřízené ovládací prvky související s rámečkem a dát jim speciální zacházení.

K implementaci funkce periodické animace budete používat <xref:System.ComponentModel.BackgroundWorker> objektů z oboru názvů <xref:System.ComponentModel?displayProperty=nameWithType>. Můžete použít <xref:System.Windows.Forms.Timer> objekty, ale v případě, že existuje mnoho objektů `IMarqueeWidget`, nemusí být jedno vlákno uživatelského rozhraní schopné s animací zůstat.

### <a name="to-create-a-child-control-for-your-custom-control"></a>Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek

1. Přidejte do projektu `MarqueeControlLibrary` novou položku třídy. Dejte novému zdrojovému souboru základní název "IMarqueeWidget".

2. Otevřete zdrojový soubor `IMarqueeWidget` v **editoru kódu** a změňte deklaraci z `class` na `interface`:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. Přidejte následující kód do rozhraní `IMarqueeWidget` pro vystavení dvou metod a vlastnost, která zpracovává animaci běžícího výběru:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. Přidejte novou položku **vlastního ovládacího prvku** do projektu `MarqueeControlLibrary`. Dejte novému zdrojovému souboru základní název "MarqueeText".

5. Přetáhněte komponentu <xref:System.ComponentModel.BackgroundWorker> z **panelu nástrojů** do ovládacího prvku `MarqueeText`. Tato součást umožní, aby se ovládací prvek `MarqueeText` sám aktualizoval asynchronně.

6. V okně **vlastnosti** nastavte vlastnost <xref:System.ComponentModel.BackgroundWorker> `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti na **hodnotu true**. Tato nastavení umožňují, aby součást <xref:System.ComponentModel.BackgroundWorker> pravidelně vyvolala událost <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a zrušila asynchronní aktualizace.

   Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).

7. Otevřete zdrojový soubor `MarqueeText` v **editoru kódu**. V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. Změňte deklaraci `MarqueeText`, aby dědila z <xref:System.Windows.Forms.Label> a implementovala rozhraní `IMarqueeWidget`:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru. Pole `isLit` určuje, zda se má text vykreslit barvou určenou vlastností `LightColor`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. Implementujte rozhraní `IMarqueeWidget`.

    Metody `StartMarquee` a `StopMarquee` vyvolají <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody komponenty <xref:System.ComponentModel.BackgroundWorker> ke spuštění a zastavení animace.

    Atributy <xref:System.ComponentModel.CategoryAttribute.Category%2A> a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> se aplikují na vlastnost `UpdatePeriod`, takže se zobrazí ve vlastní části okno Vlastnosti s názvem "výběr".

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. Implementujte přistupující objekty vlastnosti. Pro klienty vystavíte dvě vlastnosti: `LightColor` a `DarkColor`. Na tyto vlastnosti se aplikují atributy <xref:System.ComponentModel.CategoryAttribute.Category%2A> a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>, takže se vlastnosti zobrazí ve vlastní části okno Vlastnosti nazvané "výběr".

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. Implementujte obslužné rutiny pro události <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker> komponenty.

    Obslužná rutina události <xref:System.ComponentModel.BackgroundWorker.DoWork> v režimu spánku po dobu v milisekundách určené `UpdatePeriod` poté vyvolá událost <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, dokud váš kód nezastaví animaci voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.

    Obslužná rutina události <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> přepíná text mezi jeho světlým a tmavým stavem, aby bylo možné podobu blikání.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. Přepište metodu <xref:System.Windows.Forms.Control.OnPaint%2A> pro povolení animace.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. Stisknutím klávesy **F6** Sestavte řešení.

## <a name="create-the-marqueeborder-child-control"></a>Vytvoření podřízeného ovládacího prvku MarqueeBorder

`MarqueeBorder` ovládací prvek je poněkud složitější než ovládací prvek `MarqueeText`. Má více vlastností a další informace o animaci v metodě <xref:System.Windows.Forms.Control.OnPaint%2A>. V zásadě je poměrně podobný ovládacímu prvku `MarqueeText`.

Vzhledem k tomu, že ovládací prvek `MarqueeBorder` může mít podřízené ovládací prvky, musí mít informace o <xref:System.Windows.Forms.Control.Layout>ch událostech.

### <a name="to-create-the-marqueeborder-control"></a>Vytvoření ovládacího prvku MarqueeBorder

1. Přidejte novou položku **vlastního ovládacího prvku** do projektu `MarqueeControlLibrary`. Dejte novému zdrojovému souboru základní název "MarqueeBorder".

2. Přetáhněte komponentu <xref:System.ComponentModel.BackgroundWorker> z **panelu nástrojů** do ovládacího prvku `MarqueeBorder`. Tato součást umožní, aby se ovládací prvek `MarqueeBorder` sám aktualizoval asynchronně.

3. V okně **vlastnosti** nastavte vlastnost <xref:System.ComponentModel.BackgroundWorker> `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti na **hodnotu true**. Tato nastavení umožňují, aby součást <xref:System.ComponentModel.BackgroundWorker> pravidelně vyvolala událost <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a zrušila asynchronní aktualizace. Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).

4. V okně **vlastnosti** vyberte tlačítko **události** . Připojte obslužné rutiny pro události <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>.

5. Otevřete zdrojový soubor `MarqueeBorder` v **editoru kódu**. V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. Změňte deklaraci `MarqueeBorder`, aby dědila z <xref:System.Windows.Forms.Panel> a implementovala rozhraní `IMarqueeWidget`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. Deklarujete dva výčty pro správu stavu `MarqueeBorder` ovládacího prvku: `MarqueeSpinDirection`, který určuje směr, ve kterém se světla otáčí kolem ohraničení a `MarqueeLightShape`, která určuje tvar světel (čtvercové nebo kruhové). Tyto deklarace umístěte před deklaraci třídy `MarqueeBorder`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. Implementujte rozhraní `IMarqueeWidget`.

    Metody `StartMarquee` a `StopMarquee` vyvolají <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody komponenty <xref:System.ComponentModel.BackgroundWorker> ke spuštění a zastavení animace.

    Vzhledem k tomu, že ovládací prvek `MarqueeBorder` může obsahovat podřízené ovládací prvky, metoda `StartMarquee` vytvoří výčet všech podřízených ovládacích prvků a volání `StartMarquee` na těch, které implementují `IMarqueeWidget`. Metoda `StopMarquee` má podobnou implementaci.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. Implementujte přistupující objekty vlastnosti. Ovládací prvek `MarqueeBorder` má několik vlastností pro řízení jeho vzhledu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. Implementujte obslužné rutiny pro události <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker> komponenty.

    Obslužná rutina události <xref:System.ComponentModel.BackgroundWorker.DoWork> v režimu spánku po dobu v milisekundách určené `UpdatePeriod` poté vyvolá událost <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, dokud váš kód nezastaví animaci voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.

    Obslužná rutina události <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zvýší pozici "základního" světla, ze kterého je určován stav světla nebo tmavého světla, a zavolá metodu <xref:System.Windows.Forms.Control.Refresh%2A>, která způsobí, že ovládací prvek překreslí sám sebe.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. Implementujte pomocné metody `IsLit` a `DrawLight`.

    Metoda `IsLit` Určuje barvu světla na dané pozici. Indikátory, které jsou "osvětlené", jsou vykresleny barevnou vlastností `LightColor` a ty, které jsou "tmavé" jsou vykresleny v barvě dané vlastností `DarkColor`.

    Metoda `DrawLight` kreslí světlo pomocí příslušné barvy, tvaru a pozice.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. Přepište metody <xref:System.Windows.Forms.Control.OnLayout%2A> a <xref:System.Windows.Forms.Control.OnPaint%2A>.

    Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> kreslí světla podél okrajů ovládacího prvku `MarqueeBorder`.

    Vzhledem k tomu, že metoda <xref:System.Windows.Forms.Control.OnPaint%2A> závisí na rozměrech ovládacího prvku `MarqueeBorder`, je nutné jej zavolat při každé změně rozložení. Chcete-li to dosáhnout, přepište <xref:System.Windows.Forms.Control.OnLayout%2A> a zavolejte <xref:System.Windows.Forms.Control.Refresh%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a>Vytvoření vlastního návrháře pro stínové a filtrové vlastnosti

Třída `MarqueeControlRootDesigner` poskytuje implementaci pro kořenového návrháře. Kromě tohoto návrháře, který pracuje na `MarqueeControl`, budete potřebovat vlastního návrháře, který je konkrétně přidružen k ovládacímu prvku `MarqueeBorder`. Tento návrhář poskytuje vlastní chování, které je vhodné v kontextu vlastního kořenového návrháře.

Konkrétně `MarqueeBorderDesigner` bude "Stínová" a bude filtrovat určité vlastnosti ovládacího prvku `MarqueeBorder` a změnit jejich interakci s návrhovým prostředím.

Zachytávání volání vlastnosti objektu komponenty se označují jako "stíning". Umožňuje návrháři sledovat hodnotu nastavenou uživatelem a volitelně předat tuto hodnotu do navržené součásti.

V tomto příkladu budou vlastnosti <xref:System.Windows.Forms.Control.Visible%2A> a <xref:System.Windows.Forms.Control.Enabled%2A> vystínované `MarqueeBorderDesigner`, což brání uživateli v tom, aby během návrhu byl ovládací prvek `MarqueeBorder` neviditelný nebo zakázaný.

Návrháři mohou také přidávat a odebírat vlastnosti. V tomto příkladu bude vlastnost <xref:System.Windows.Forms.Control.Padding%2A> odebrána v době návrhu, protože ovládací prvek `MarqueeBorder` programově nastaví odsazení na základě velikosti světel určených vlastností `LightSize`.

Základní třída pro `MarqueeBorderDesigner` je <xref:System.ComponentModel.Design.ComponentDesigner>, která má metody, které mohou měnit atributy, vlastnosti a události vystavené ovládacím prvkem v době návrhu:

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

Při změně veřejného rozhraní komponenty pomocí těchto metod použijte tato pravidla:

- Přidat nebo odebrat položky pouze z `PreFilter`ch metod

- Upravit existující položky jenom v `PostFilter` metodách

- Vždy volejte základní implementaci nejprve v metodách `PreFilter`

- Vždy volat základní implementaci jako poslední v metodách `PostFilter`

Dodržování těchto pravidel zajišťuje, že všichni návrháři v prostředí návrhu mají konzistentní zobrazení všech navržených komponent.

Třída <xref:System.ComponentModel.Design.ComponentDesigner> poskytuje slovník pro správu hodnot stínových vlastností, což zbavuje nutnost vytváření specifických proměnných instance.

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Vytvoření vlastního návrháře pro vlastnosti stínu a filtru

1. Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu. Dejte zdrojovému souboru základní název **MarqueeBorderDesigner**.

2. Otevřete zdrojový soubor MarqueeBorderDesigner v **editoru kódu**. V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. Změňte deklaraci `MarqueeBorderDesigner`, aby dědila z <xref:System.Windows.Forms.Design.ParentControlDesigner>.

    Vzhledem k tomu, že ovládací prvek `MarqueeBorder` může obsahovat podřízené ovládací prvky, `MarqueeBorderDesigner` dědí z <xref:System.Windows.Forms.Design.ParentControlDesigner>, což zpracovává interakci nadřazený-podřízený.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. Přepsat základní implementaci <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. Implementujte vlastnosti <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A>. Tyto implementace nastínují vlastnosti ovládacího prvku.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a>Zpracovat změny součásti

Třída `MarqueeControlRootDesigner` poskytuje vlastní prostředí pro dobu návrhu pro vaše `MarqueeControl` instance. Většina funkcí návrhu je děděna z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy. Váš kód bude implementovat dvě konkrétní vlastní nastavení: zpracování změn součástí a přidávání operací návrháře.

Když uživatelé navrhují své `MarqueeControl` instance, váš kořenový Návrhář bude sledovat změny `MarqueeControl` a jeho podřízených ovládacích prvků. Prostředí pro dobu návrhu nabízí pohodlný službu, <xref:System.ComponentModel.Design.IComponentChangeService>pro sledování změn stavu komponent.

Odkaz na tuto službu získáte dotazem na prostředí pomocí metody <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>. Pokud je dotaz úspěšný, může váš návrhář připojit obslužnou rutinu pro událost <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> a provést jakékoli úkoly, aby zachovaly konzistentní stav v době návrhu.

V případě `MarqueeControlRootDesigner` třídy zavoláte metodu <xref:System.Windows.Forms.Control.Refresh%2A> na každý objekt `IMarqueeWidget` obsažený v `MarqueeControl`. Tím dojde k tomu, že objekt `IMarqueeWidget` pro překreslení sebe sama o sobě vhodně, když se změní vlastnosti, jako je jeho nadřazený <xref:System.Windows.Forms.Control.Size%2A>.

### <a name="to-handle-component-changes"></a>Zpracování změn součástí

1. Otevřete zdrojový soubor `MarqueeControlRootDesigner` v **editoru kódu** a přepište metodu <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>. Zavolejte základní implementaci <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> a dotaz na <xref:System.ComponentModel.Design.IComponentChangeService>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. Implementujte obslužnou rutinu události <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>. Otestujte typ odesílající komponenty, a pokud se jedná o `IMarqueeWidget`, zavolejte metodu <xref:System.Windows.Forms.Control.Refresh%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a>Přidání příkazů návrháře do vlastního návrháře

Příkaz návrháře je příkaz nabídky propojený s obslužnou rutinou události. Příkazy návrháře jsou přidány do místní nabídky součásti v době návrhu. Další informace naleznete v tématu <xref:System.ComponentModel.Design.DesignerVerb>.

Do návrháře přidáte dva příkazy návrháře: **Spusťte test** a **zastavte test**. Tyto příkazy vám umožní zobrazit v době návrhu chování `MarqueeControl` v době běhu. Tyto operace budou přidány do `MarqueeControlRootDesigner`.

Při vyvolání příkazu **Spustit test** bude obslužná rutina události příkazu volat metodu `StartMarquee` v `MarqueeControl`. Při vyvolání příkazu **zastavit test** obslužná rutina události vyvolá metodu `StopMarquee` v `MarqueeControl`. Implementace metod `StartMarquee` a `StopMarquee` volá tyto metody pro obsažené ovládací prvky, které implementují `IMarqueeWidget`, takže všechny obsažené `IMarqueeWidget` ovládací prvky se také účastní testu.

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Přidání příkazů návrháře do vlastních návrhářů

1. Ve třídě `MarqueeControlRootDesigner` přidejte obslužné rutiny událostí s názvem `OnVerbRunTest` a `OnVerbStopTest`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. Připojte tyto obslužné rutiny událostí ke svým odpovídajícím slovesům návrháře. `MarqueeControlRootDesigner` dědí <xref:System.ComponentModel.Design.DesignerVerbCollection> z jeho základní třídy. Vytvoříte dva nové objekty <xref:System.ComponentModel.Design.DesignerVerb> a přidáte je do této kolekce v metodě <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a>Vytvoření vlastního Editor UITypeEditor

Když pro uživatele vytvoříte vlastní prostředí pro dobu návrhu, často je žádoucí vytvořit vlastní interakci s okno Vlastnosti. To můžete provést vytvořením <xref:System.Drawing.Design.UITypeEditor>.

Ovládací prvek `MarqueeBorder` zpřístupňuje v okno Vlastnosti několik vlastností. Dvě z těchto vlastností `MarqueeSpinDirection` a `MarqueeLightShape` jsou reprezentovány výčty. Pro ilustraci použití Editoru typů uživatelského rozhraní bude mít vlastnost `MarqueeLightShape` přidruženou třídu <xref:System.Drawing.Design.UITypeEditor>.

### <a name="to-create-a-custom-ui-type-editor"></a>Vytvoření vlastního editoru typů uživatelského rozhraní

1. Otevřete zdrojový soubor `MarqueeBorder` v **editoru kódu**.

2. V definici třídy `MarqueeBorder` Deklarujte třídu nazvanou `LightShapeEditor`, která je odvozena z <xref:System.Drawing.Design.UITypeEditor>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance nazvanou `editorService`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. Přepsat metodu <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>. Tato implementace vrací <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, která oznamuje vývojovému prostředí, jak zobrazit `LightShapeEditor`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. Přepsat metodu <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>. Tato implementace se dotazuje návrhového prostředí pro objekt <xref:System.Windows.Forms.Design.IWindowsFormsEditorService>. V případě úspěchu vytvoří `LightShapeSelectionControl`. Metoda <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> je vyvolána pro spuštění `LightShapeEditor`. Návratová hodnota z tohoto vyvolání se vrátí do prostředí návrhu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a>Vytvoření ovládacího prvku zobrazení pro vlastní editor UITypeEditor

Vlastnost `MarqueeLightShape` podporuje dva typy lehkých tvarů: `Square` a `Circle`. Vytvoříte vlastní ovládací prvek, který bude použit výhradně pro účely grafického zobrazení těchto hodnot v okno Vlastnosti. Tento vlastní ovládací prvek bude použit vaším <xref:System.Drawing.Design.UITypeEditor> k interakci s okno Vlastnosti.

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Vytvoření ovládacího prvku zobrazení pro vlastní Editor typů uživatelského rozhraní

1. Přidejte novou <xref:System.Windows.Forms.UserControl>ovou položku do projektu `MarqueeControlLibrary`. Dejte novému zdrojovému souboru základní název **LightShapeSelectionControl**.

2. Přetáhněte dva ovládací prvky <xref:System.Windows.Forms.Panel> z **panelu nástrojů** na `LightShapeSelectionControl`. Pojmenujte je `squarePanel` a `circlePanel`. Uspořádejte je vedle sebe. Nastavte vlastnost <xref:System.Windows.Forms.Control.Size%2A> obou ovládacích prvků <xref:System.Windows.Forms.Panel> na **(60, 60)** . Nastavte vlastnost <xref:System.Windows.Forms.Control.Location%2A> ovládacího prvku `squarePanel` na **(8, 10)** . Nastavte vlastnost <xref:System.Windows.Forms.Control.Location%2A> ovládacího prvku `circlePanel` na **(80, 10)** . Nakonec nastavte vlastnost <xref:System.Windows.Forms.Control.Size%2A> `LightShapeSelectionControl` na **(150, 80)** .

3. Otevřete zdrojový soubor `LightShapeSelectionControl` v **editoru kódu**. V horní části souboru importujte <xref:System.Windows.Forms.Design?displayProperty=nameWithType> obor názvů:

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. Implementujte <xref:System.Windows.Forms.Control.Click> obslužných rutin událostí pro ovládací prvky `squarePanel` a `circlePanel`. Tyto metody vyvolávají <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> pro ukončení relace úprav vlastního <xref:System.Drawing.Design.UITypeEditor>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance nazvanou `editorService`.

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. Deklarujte `MarqueeLightShape` proměnnou instance nazvanou `lightShapeValue`.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. V konstruktoru `LightShapeSelectionControl` připojte obslužné rutiny události <xref:System.Windows.Forms.Control.Click> k <xref:System.Windows.Forms.Control.Click> událostem `squarePanel` a `circlePanel`ch ovládacích prvků. Také definujte přetížení konstruktoru, které přiřadí hodnotu `MarqueeLightShape` z návrhového prostředí do pole `lightShapeValue`.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. V metodě <xref:System.ComponentModel.Component.Dispose%2A> odpojte obslužné rutiny události <xref:System.Windows.Forms.Control.Click>.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** . Otevřete soubor LightShapeSelectionControl.Designer.cs nebo LightShapeSelectionControl. Designer. vb a odeberte výchozí definici metody <xref:System.ComponentModel.Component.Dispose%2A>.

10. Implementujte vlastnost `LightShape`.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. Přepsat metodu <xref:System.Windows.Forms.Control.OnPaint%2A>. Tato implementace Vykreslí vyplněný čtverec a kruh. Tím se také zvýrazní vybraná hodnota vykreslením ohraničení kolem jednoho obrazce nebo druhého.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a>Testování vlastního ovládacího prvku v Návrháři

V tomto okamžiku můžete sestavit `MarqueeControlLibrary` projekt. Otestujte implementaci vytvořením ovládacího prvku, který dědí z třídy `MarqueeControl` a použijete jej na formuláři.

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Vytvoření vlastní implementace MarqueeControl

1. Otevřete `DemoMarqueeControl` v Návrhář formulářů. Tím se vytvoří instance typu `DemoMarqueeControl` a zobrazí se v instanci `MarqueeControlRootDesigner` typu.

2. V **sadě nástrojů**otevřete kartu **součásti MarqueeControlLibrary** . Zobrazí se ovládací prvky `MarqueeBorder` a `MarqueeText` dostupné pro výběr.

3. Přetáhněte instanci ovládacího prvku `MarqueeBorder` na návrhovou plochu `DemoMarqueeControl`. Ukotvit tento ovládací prvek `MarqueeBorder` do nadřazeného ovládacího prvku.

4. Přetáhněte instanci ovládacího prvku `MarqueeText` na návrhovou plochu `DemoMarqueeControl`.

5. Sestavte řešení.

6. Klikněte pravým tlačítkem myši na `DemoMarqueeControl` a z místní nabídky vyberte možnost **Spustit test** . tím se spustí animace. Kliknutím na **zastavit test** zastavte animaci.

7. Otevřete **Form1** v zobrazení Návrh.

8. Do formuláře umístěte dva ovládací prvky <xref:System.Windows.Forms.Button>. Pojmenujte je `startButton` a `stopButton`a změňte hodnoty vlastností <xref:System.Windows.Forms.Control.Text%2A> na **Start** a **stop**v uvedeném pořadí.

9. Implementujte obslužné rutiny událostí <xref:System.Windows.Forms.Control.Click> pro ovládací prvky <xref:System.Windows.Forms.Button>.

10. V **sadě nástrojů**otevřete kartu **součásti MarqueeControlTest** . Zobrazí se `DemoMarqueeControl` k dispozici pro výběr.

11. Přetáhněte instanci `DemoMarqueeControl` na návrhovou plochu **Form1** .

12. V obslužných rutinách události <xref:System.Windows.Forms.Control.Click> volejte na `DemoMarqueeControl`metody `Start` a `Stop`.

    ```vb
    Private Sub startButton_Click(sender As Object, e As System.EventArgs)
        Me.demoMarqueeControl1.Start()
    End Sub 'startButton_Click

    Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Stop()
    End Sub 'stopButton_Click
    ```

    ```csharp
    private void startButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Start();
    }

    private void stopButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Stop();
    }
    ```

13. Nastavte projekt `MarqueeControlTest` jako spouštěný projekt a spusťte ho. Zobrazí se formulář zobrazující `DemoMarqueeControl`. Kliknutím na tlačítko **Start** spustíte animaci. Mělo by se zobrazit blikání textu a indikátory pohybu kolem ohraničení.

## <a name="next-steps"></a>Další kroky

`MarqueeControlLibrary` ukazuje jednoduchou implementaci vlastních ovládacích prvků a přidružených návrhářů. Tuto ukázku můžete udělat několika způsoby:

- Změňte hodnoty vlastností `DemoMarqueeControl` v návrháři. Chcete-li vytvořit vnořený efekt, přidejte další ovládací prvky `MarqueBorder` a ukotvěte je Dock v rámci jejich nadřazených instancí. Experimentujte s různými nastaveními `UpdatePeriod` a vlastností souvisejícími s osvětlením.

- Vytvořte vlastní implementace `IMarqueeWidget`. Mohli byste například vytvořit Flash "Neon Sign" nebo animované znaménko s více obrázky.

- Dále upravte prostředí pro dobu návrhu. Můžete vyzkoušet více vlastností stínové kopie než <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A>a můžete přidat nové vlastnosti. Přidejte nové příkazy návrháře, abyste zjednodušili běžné úkoly, jako je například ukotvení podřízených ovládacích prvků.

- License `MarqueeControl`.

- Určuje, jak jsou ovládací prvky serializovány a jak jsou pro ně generovány kódy. Další informace naleznete v tématu [generování a kompilace dynamického zdrojového kódu](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
