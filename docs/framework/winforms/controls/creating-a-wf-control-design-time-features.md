---
title: Vytvoření ovládacího prvku, který využívá výhod funkcí nástroje Visual Studio pro dobu návrhu
description: Naučte se, jak vytvořit vlastního návrháře vlastního ovládacího prvku v model Windows Forms, který využívá funkce pro dobu návrhu.
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
ms.openlocfilehash: 03c04578ecb01b689f58d41a46eef5793fb1182c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613907"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a>Návod: vytvoření ovládacího prvku, který bude využívat funkce pro dobu návrhu

Prostředí pro návrh vlastního ovládacího prvku lze zvýšit vytvořením přidruženého vlastního návrháře.

Tento článek ukazuje, jak vytvořit vlastního návrháře vlastního ovládacího prvku. Implementujete `MarqueeControl` typ a přidruženou třídu návrháře s názvem `MarqueeControlRootDesigner` .

`MarqueeControl`Typ implementuje zobrazení podobné textu v kino s animovanými indikátory a blikající text.

Návrhář pro tento ovládací prvek komunikuje s vývojovým prostředím, aby poskytoval vlastní prostředí pro dobu návrhu. Pomocí vlastního návrháře můžete sestavit vlastní `MarqueeControl` implementaci s animovanými indikátory a blikající text v mnoha kombinacích. Můžete použít sestavený ovládací prvek na formuláři, stejně jako jakýkoli jiný ovládací prvek model Windows Forms.

Až budete s tímto návodem hotový, váš vlastní ovládací prvek bude vypadat přibližně takto:

![Aplikace, která zobrazuje text a tlačítka Spustit a zastavit](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

Úplný výpis kódu naleznete v tématu [How to: Create a model Windows Forms Control, který využívá funkce pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).

## <a name="prerequisites"></a>Požadavky

Aby bylo možné dokončit tento návod, budete potřebovat aplikaci Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu aplikace. Pomocí tohoto projektu sestavíte aplikaci, která je hostitelem vlastního ovládacího prvku.

V aplikaci Visual Studio vytvořte nový projekt aplikace model Windows Forms a pojmenujte jej **MarqueeControlTest**.

## <a name="create-the-control-library-project"></a>Vytvořit projekt knihovny ovládacích prvků

1. Přidejte do řešení projekt knihovny ovládacích prvků model Windows Forms. Pojmenujte projekt **MarqueeControlLibrary**.

2. Pomocí **Průzkumník řešení**odstraňte výchozí ovládací prvek projektu odstraněním zdrojového souboru s názvem "UserControl1.cs" nebo "UserControl1. vb" v závislosti na zvoleném jazyce.

3. Přidejte <xref:System.Windows.Forms.UserControl> do projektu novou položku `MarqueeControlLibrary` . Dejte novému zdrojovému souboru základní název **MarqueeControl**.

4. Pomocí **Průzkumník řešení**vytvořte v projektu novou složku `MarqueeControlLibrary` .

5. Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu. Pojmenujte ho **MarqueeControlRootDesigner**.

6. Budete muset použít typy ze sestavení System. design, takže přidejte tento odkaz do `MarqueeControlLibrary` projektu.

## <a name="reference-the-custom-control-project"></a>Odkaz na projekt vlastního ovládacího prvku

`MarqueeControlTest`K otestování vlastního ovládacího prvku použijete projekt. Testovací projekt se při přidání odkazu na projekt do sestavení změní na vlastní ovládací prvek `MarqueeControlLibrary` .

V `MarqueeControlTest` projektu přidejte odkaz na projekt do `MarqueeControlLibrary` sestavení. Nezapomeňte použít kartu **projekty** v dialogovém okně **Přidat odkaz** namísto odkazování na `MarqueeControlLibrary` sestavení přímo.

## <a name="define-a-custom-control-and-its-custom-designer"></a>Definování vlastního ovládacího prvku a jeho vlastního návrháře

Vlastní ovládací prvek bude odvozen z <xref:System.Windows.Forms.UserControl> třídy. To umožňuje vašemu ovládacímu prvku, aby obsahoval další ovládací prvky, a poskytuje vašemu ovládacímu prvku skvělou výchozí funkčnost.

Vlastní ovládací prvek bude mít přidružený vlastní Návrhář. To vám umožní vytvořit jedinečné vývojové prostředí, které se přizpůsobí speciálně pro váš vlastní ovládací prvek.

K přidružení ovládacího prvku ke svému návrháři použijte <xref:System.ComponentModel.DesignerAttribute> třídu. Vzhledem k tomu, že vyvíjíte celé chování vlastního ovládacího prvku v době návrhu, bude vlastní Návrhář implementovat <xref:System.ComponentModel.Design.IRootDesigner> rozhraní.

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Definování vlastního ovládacího prvku a jeho vlastního návrháře

1. Otevřete `MarqueeControl` zdrojový soubor v **editoru kódu**. V horní části souboru importujte následující obory názvů:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. Přidejte <xref:System.ComponentModel.DesignerAttribute> do `MarqueeControl` deklarace třídy. Tím přiřadíte vlastní ovládací prvek ke svému návrháři.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. Otevřete `MarqueeControlRootDesigner` zdrojový soubor v **editoru kódu**. V horní části souboru importujte následující obory názvů:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. Změňte deklaraci `MarqueeControlRootDesigner` na dědění z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy. Použijte <xref:System.ComponentModel.ToolboxItemFilterAttribute> pro určení interakce návrháře pomocí **sady nástrojů**.

   > [!NOTE]
   > Definice pro třídu byla `MarqueeControlRootDesigner` uzavřená v oboru názvů s názvem MarqueeControlLibrary. Design. Tato deklarace umístí návrháře ve speciálním oboru názvů vyhrazeném pro typy související s návrhem.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. Definujte konstruktor pro `MarqueeControlRootDesigner` třídu. Vloží <xref:System.Diagnostics.Trace.WriteLine%2A> příkaz do těla konstruktoru. To bude užitečné pro ladění.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a>Vytvoření instance vlastního ovládacího prvku

1. Přidejte <xref:System.Windows.Forms.UserControl> do projektu novou položku `MarqueeControlTest` . Dejte novému zdrojovému souboru základní název **DemoMarqueeControl**.

2. Otevřete `DemoMarqueeControl` soubor v **editoru kódu**. V horní části souboru importujte `MarqueeControlLibrary` obor názvů:

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. Změňte deklaraci `DemoMarqueeControl` na dědění z `MarqueeControl` třídy.

4. Sestavte projekt.

5. Otevřete Form1 v Návrhář formulářů.

6. V **sadě nástrojů** Najděte kartu **komponenty MarqueeControlTest** a otevřete ji. Přetáhněte `DemoMarqueeControl` z **panelu nástrojů** do formuláře.

7. Sestavte projekt.

## <a name="set-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu

Při vývoji vlastního prostředí v době návrhu bude nutné ladit ovládací prvky a komponenty. Existuje jednoduchý způsob, jak nastavit projekt tak, aby umožňoval ladění v době návrhu. Další informace naleznete v tématu [Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).

1. Klikněte pravým tlačítkem na `MarqueeControlLibrary` projekt a vyberte **vlastnosti**.

2. V dialogovém okně **stránky vlastností MarqueeControlLibrary** vyberte stránku **ladění** .

3. V části **spouštěcí akce** vyberte **spustit externí program**. Budete ladit samostatnou instanci sady Visual Studio, takže kliknutím na tlačítko se třemi tečkami ( ![ ...) v okno Vlastnosti sady Visual Studio ](./media/visual-studio-ellipsis-button.png) ) můžete procházet prostředí IDE sady Visual Studio. Název spustitelného souboru je devenv.exe a pokud jste nainstalovali do výchozího umístění, jeho cesta je *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019 \\ \<edition>\Common7\IDE\devenv.exe*.

4. Kliknutím na **tlačítko OK** zavřete dialogové okno.

5. Klikněte pravým tlačítkem na projekt MarqueeControlLibrary a vyberte **nastavit jako spouštěný projekt** , abyste mohli tuto konfiguraci ladění povolit.

## <a name="checkpoint"></a>CheckPoint

Nyní jste připraveni ladit chování vlastního ovládacího prvku v době návrhu. Jakmile zjistíte, že je prostředí ladění správně nastavené, otestujete přidružení mezi vlastním ovládacím prvkem a vlastním návrhářem.

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Otestování ladicího prostředí a přidružení návrháře

1. Otevřete zdrojový soubor MarqueeControlRootDesigner v **editoru kódu** a umístěte zarážku na <xref:System.Diagnostics.Trace.WriteLine%2A> příkaz.

2. Stisknutím klávesy **F5** spusťte relaci ladění.

   Vytvoří se nová instance sady Visual Studio.

3. V nové instanci aplikace Visual Studio otevřete řešení MarqueeControlTest. Řešení můžete snadno najít výběrem položky **Poslední projekty** v nabídce **soubor** . Soubor řešení MarqueeControlTest. sln bude uveden jako naposledy použitý soubor.

4. Otevřete `DemoMarqueeControl` v návrháři.

   Instance ladění aplikace Visual Studio získá fokus a provádění se zastaví na zarážce. Stisknutím klávesy **F5** pokračujte v relaci ladění.

V tomto okamžiku je vše pro vývoj a ladění vlastního ovládacího prvku a jeho přidruženého vlastního návrháře. Zbývající část tohoto článku se zaměřuje na podrobnosti o implementaci funkcí ovládacího prvku a návrháře.

## <a name="implement-the-custom-control"></a>Implementace vlastního ovládacího prvku

`MarqueeControl`Je a <xref:System.Windows.Forms.UserControl> s malým počtem přizpůsobení. Zveřejňuje dvě metody: `Start` , který spustí animaci běžící na hranice a `Stop` , která zastaví animaci. Protože `MarqueeControl` obsahuje podřízené ovládací prvky, které implementují rozhraní a vyčíslení `IMarqueeWidget` `Start` každého podřízeného ovládacího prvku a `Stop` volání `StartMarquee` `StopMarquee` metod a, v uvedeném pořadí, v každém podřízeném ovládacím prvku, který implementuje `IMarqueeWidget` .

Vzhled `MarqueeBorder` `MarqueeText` ovládacích prvků a je závislý na rozložení, takže `MarqueeControl` přepíše <xref:System.Windows.Forms.Control.OnLayout%2A> metodu a volání <xref:System.Windows.Forms.Control.PerformLayout%2A> podřízených ovládacích prvků tohoto typu.

Toto je rozsah `MarqueeControl` úprav. Funkce modulu runtime jsou implementovány `MarqueeBorder` `MarqueeText` ovládacími prvky a a funkce v době návrhu jsou implementovány `MarqueeBorderDesigner` `MarqueeControlRootDesigner` třídami a.

### <a name="to-implement-your-custom-control"></a>Implementace vlastního ovládacího prvku

1. Otevřete `MarqueeControl` zdrojový soubor v **editoru kódu**. Implementujte `Start` `Stop` metody a.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. Přepsat <xref:System.Windows.Forms.Control.OnLayout%2A> metodu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a>Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek

`MarqueeControl`Bude hostovat dva druhy podřízeného ovládacího prvku: `MarqueeBorder` ovládací prvek a `MarqueeText` ovládací prvek.

- `MarqueeBorder`: Tento ovládací prvek vykreslí ohraničení "světel" kolem jeho okrajů. Světla se zobrazí v sekvenci, takže se zdají kolem ohraničení pohybovat. Rychlost, s níž jsou indikátory blesku ovládány vlastností s názvem `UpdatePeriod` . Některé další vlastní vlastnosti určují další aspekty vzhledu ovládacího prvku. Dvě metody, které jsou volány `StartMarquee` a `StopMarquee` , určují, kdy se animace spouští a zastavuje.

- `MarqueeText`: Tento ovládací prvek vykreslí blikající řetězec. Podobně jako u `MarqueeBorder` ovládacího prvku je rychlost, s jakou je text blikající, ovládána `UpdatePeriod` vlastností. `MarqueeText`Ovládací prvek má také `StartMarquee` `StopMarquee` společné metody a s `MarqueeBorder` ovládacím prvkem.

V době návrhu umožňuje, aby `MarqueeControlRootDesigner` tyto dva typy ovládacích prvků byly přidány do `MarqueeControl` jakékoli kombinace.

Společné funkce těchto dvou ovládacích prvků jsou přihlédnuto do rozhraní s názvem `IMarqueeWidget` . To umožňuje, `MarqueeControl` aby se zjistily podřízené ovládací prvky související s rámečkem a přidávají jim speciální zacházení.

K implementaci funkce periodické animace budete používat <xref:System.ComponentModel.BackgroundWorker> objekty z <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů. Můžete použít <xref:System.Windows.Forms.Timer> objekty, ale `IMarqueeWidget` v případě, že je přítomen velký počet objektů, nemusí být jedno vlákno uživatelského rozhraní schopno s animací zůstat.

### <a name="to-create-a-child-control-for-your-custom-control"></a>Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek

1. Přidejte do projektu novou položku třídy `MarqueeControlLibrary` . Dejte novému zdrojovému souboru základní název "IMarqueeWidget".

2. Otevřete `IMarqueeWidget` zdrojový soubor v **editoru kódu** a změňte deklaraci z `class` na `interface` :

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. Přidejte následující kód do rozhraní, `IMarqueeWidget` aby bylo možné vystavit dvě metody a vlastnost, která zpracovává animaci běžícího výběru:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. Přidejte do projektu novou položku **vlastního ovládacího prvku** `MarqueeControlLibrary` . Dejte novému zdrojovému souboru základní název "MarqueeText".

5. Přetáhněte <xref:System.ComponentModel.BackgroundWorker> komponentu z **panelu nástrojů** na `MarqueeText` ovládací prvek. Tato součást umožní, aby se `MarqueeText` ovládací prvek sám aktualizoval asynchronně.

6. V okně **vlastnosti** nastavte <xref:System.ComponentModel.BackgroundWorker> komponentu `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti na **hodnotu true**. Tato nastavení umožňují, <xref:System.ComponentModel.BackgroundWorker> aby součást pravidelně vyvolala <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událost a zrušila asynchronní aktualizace.

   Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).

7. Otevřete `MarqueeText` zdrojový soubor v **editoru kódu**. V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. Změňte deklaraci `MarqueeText` na dědění z <xref:System.Windows.Forms.Label> a k implementaci `IMarqueeWidget` rozhraní:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru. `isLit`Pole určuje, zda má být text vykreslen v barvě dané `LightColor` vlastností.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. Implementujte rozhraní `IMarqueeWidget`.

    `StartMarquee`Metody a `StopMarquee` vyvolají <xref:System.ComponentModel.BackgroundWorker> komponentu <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody pro spuštění a zastavení animace.

    <xref:System.ComponentModel.CategoryAttribute.Category%2A>Atributy a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> se aplikují na `UpdatePeriod` vlastnost, takže se zobrazí ve vlastní části okno Vlastnosti nazvané "výběr".

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. Implementujte přistupující objekty vlastnosti. Pro klienty vystavíte dvě vlastnosti: `LightColor` a `DarkColor` . <xref:System.ComponentModel.CategoryAttribute.Category%2A>Atributy a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> se aplikují na tyto vlastnosti, takže se vlastnosti zobrazí ve vlastní části okno Vlastnosti s názvem "výběr".

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. Implementujte obslužné rutiny pro <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.DoWork> události komponenty a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> .

    <xref:System.ComponentModel.BackgroundWorker.DoWork>Obslužná rutina události v režimu spánku po dobu určenou v milisekundách `UpdatePeriod` vyvolá <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událost, dokud váš kód nezastaví animaci voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> .

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>Obslužná rutina události přepíná text mezi jeho světlý a tmavý stav, aby bylo možné podobu blikání.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. Přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metodu pro povolení animace.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. Stisknutím klávesy **F6** Sestavte řešení.

## <a name="create-the-marqueeborder-child-control"></a>Vytvoření podřízeného ovládacího prvku MarqueeBorder

`MarqueeBorder`Ovládací prvek je poněkud složitější než `MarqueeText` ovládací prvek. Má více vlastností a další animace v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě je více zapojena. V zásadě je poměrně podobný `MarqueeText` ovládacímu prvku.

Vzhledem k tomu `MarqueeBorder` , že ovládací prvek může mít podřízené ovládací prvky, musí znát <xref:System.Windows.Forms.Control.Layout> události.

### <a name="to-create-the-marqueeborder-control"></a>Vytvoření ovládacího prvku MarqueeBorder

1. Přidejte do projektu novou položku **vlastního ovládacího prvku** `MarqueeControlLibrary` . Dejte novému zdrojovému souboru základní název "MarqueeBorder".

2. Přetáhněte <xref:System.ComponentModel.BackgroundWorker> komponentu z **panelu nástrojů** na `MarqueeBorder` ovládací prvek. Tato součást umožní, aby se `MarqueeBorder` ovládací prvek sám aktualizoval asynchronně.

3. V okně **vlastnosti** nastavte <xref:System.ComponentModel.BackgroundWorker> komponentu `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti na **hodnotu true**. Tato nastavení umožňují, <xref:System.ComponentModel.BackgroundWorker> aby součást pravidelně vyvolala <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událost a zrušila asynchronní aktualizace. Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).

4. V okně **vlastnosti** vyberte tlačítko **události** . Připojte obslužné rutiny <xref:System.ComponentModel.BackgroundWorker.DoWork> pro <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události a.

5. Otevřete `MarqueeBorder` zdrojový soubor v **editoru kódu**. V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. Změňte deklaraci `MarqueeBorder` na dědění z <xref:System.Windows.Forms.Panel> a k implementaci `IMarqueeWidget` rozhraní.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. Deklarujete dva výčty pro správu `MarqueeBorder` stavu ovládacího prvku: `MarqueeSpinDirection` , který určuje směr otočení světla kolem ohraničení a `MarqueeLightShape` určuje tvar světel (čtvercové nebo kruhové). Tyto deklarace umístěte před `MarqueeBorder` deklaraci třídy.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. Implementujte rozhraní `IMarqueeWidget`.

    `StartMarquee`Metody a `StopMarquee` vyvolají <xref:System.ComponentModel.BackgroundWorker> komponentu <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody pro spuštění a zastavení animace.

    Vzhledem k tomu `MarqueeBorder` , že ovládací prvek může obsahovat podřízené ovládací prvky, `StartMarquee` Metoda vytvoří výčet všech podřízených ovládacích prvků a volání `StartMarquee` , která implementují `IMarqueeWidget` . `StopMarquee`Metoda má podobnou implementaci.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. Implementujte přistupující objekty vlastnosti. `MarqueeBorder`Ovládací prvek má několik vlastností pro řízení jeho vzhledu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. Implementujte obslužné rutiny pro <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.DoWork> události komponenty a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> .

    <xref:System.ComponentModel.BackgroundWorker.DoWork>Obslužná rutina události v režimu spánku po dobu určenou v milisekundách `UpdatePeriod` vyvolá <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událost, dokud váš kód nezastaví animaci voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> .

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>Obslužná rutina události zvýší pozici "základního" světla, ze kterého je stanoven světlý nebo tmavý stav ostatních světel, a volá <xref:System.Windows.Forms.Control.Refresh%2A> metodu, která způsobí, že ovládací prvek provede překreslení sám sebe.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. Implementujte pomocné metody `IsLit` a `DrawLight` .

    `IsLit`Metoda určuje barvu světla na dané pozici. Indikátory, které jsou "osvětlené" jsou vykresleny barvou dané `LightColor` vlastností a ty, které jsou "tmavé" jsou vykresleny v barvě dané `DarkColor` vlastností.

    `DrawLight`Metoda nakreslí světlo pomocí příslušné barvy, tvaru a pozice.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. Přepište <xref:System.Windows.Forms.Control.OnLayout%2A> <xref:System.Windows.Forms.Control.OnPaint%2A> metody a.

    <xref:System.Windows.Forms.Control.OnPaint%2A>Metoda kreslí světla podél okrajů `MarqueeBorder` ovládacího prvku.

    Vzhledem k tomu <xref:System.Windows.Forms.Control.OnPaint%2A> , že metoda závisí na rozměrech `MarqueeBorder` ovládacího prvku, je nutné jej zavolat při každé změně rozložení. Chcete-li toho dosáhnout, přepište <xref:System.Windows.Forms.Control.OnLayout%2A> a zavolejte <xref:System.Windows.Forms.Control.Refresh%2A> .

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a>Vytvoření vlastního návrháře pro stínové a filtrové vlastnosti

`MarqueeControlRootDesigner`Třída poskytuje implementaci pro kořenového návrháře. Kromě tohoto návrháře, který pracuje na `MarqueeControl` , budete potřebovat vlastního návrháře, který je konkrétně přidružen k `MarqueeBorder` ovládacímu prvku. Tento návrhář poskytuje vlastní chování, které je vhodné v kontextu vlastního kořenového návrháře.

Konkrétně `MarqueeBorderDesigner` bude "stínem" a filtrovat určité vlastnosti `MarqueeBorder` ovládacího prvku, změnou jejich interakce s návrhovým prostředím.

Zachytávání volání vlastnosti objektu komponenty se označují jako "stíning". Umožňuje návrháři sledovat hodnotu nastavenou uživatelem a volitelně předat tuto hodnotu do navržené součásti.

V tomto příkladu <xref:System.Windows.Forms.Control.Visible%2A> <xref:System.Windows.Forms.Control.Enabled%2A> budou vlastnosti a nastínované pomocí `MarqueeBorderDesigner` , což brání uživateli v tom, aby `MarqueeBorder` během návrhu byl ovládací prvek neviditelný nebo zakázán.

Návrháři mohou také přidávat a odebírat vlastnosti. V tomto příkladu <xref:System.Windows.Forms.Control.Padding%2A> bude vlastnost odebrána v době návrhu, protože `MarqueeBorder` ovládací prvek programově nastaví odsazení na základě velikosti světla určených `LightSize` vlastností.

Základní třída pro `MarqueeBorderDesigner` je <xref:System.ComponentModel.Design.ComponentDesigner> , která má metody, které mohou měnit atributy, vlastnosti a události vystavené ovládacím prvkem v době návrhu:

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

Při změně veřejného rozhraní komponenty pomocí těchto metod použijte tato pravidla:

- Přidat nebo odebrat položky pouze v `PreFilter` metodách

- Upravit existující položky pouze v `PostFilter` metodách

- Vždy volat základní implementaci nejprve v `PreFilter` metodách

- Vždy volat základní implementaci jako poslední v `PostFilter` metodách

Dodržování těchto pravidel zajišťuje, že všichni návrháři v prostředí návrhu mají konzistentní zobrazení všech navržených komponent.

<xref:System.ComponentModel.Design.ComponentDesigner>Třída poskytuje slovník pro správu hodnot stínových vlastností, což zbavuje nutnost vytváření specifických proměnných instance.

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Vytvoření vlastního návrháře pro vlastnosti stínu a filtru

1. Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu. Dejte zdrojovému souboru základní název **MarqueeBorderDesigner**.

2. Otevřete zdrojový soubor MarqueeBorderDesigner v **editoru kódu**. V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. Změňte deklaraci `MarqueeBorderDesigner` na dědění z <xref:System.Windows.Forms.Design.ParentControlDesigner> .

    Vzhledem k tomu, že `MarqueeBorder` ovládací prvek může obsahovat podřízené ovládací prvky, `MarqueeBorderDesigner` dědí z <xref:System.Windows.Forms.Design.ParentControlDesigner> , který zpracovává interakci nadřazený-podřízený.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. Přepsat základní implementaci <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A> .

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. Implementujte <xref:System.Windows.Forms.Control.Enabled%2A> <xref:System.Windows.Forms.Control.Visible%2A> vlastnosti a. Tyto implementace nastínují vlastnosti ovládacího prvku.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a>Zpracovat změny součásti

`MarqueeControlRootDesigner`Třída poskytuje vlastní prostředí pro dobu návrhu pro vaše `MarqueeControl` instance. Většina funkcí návrhu je děděna z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy. Váš kód bude implementovat dvě konkrétní vlastní nastavení: zpracování změn součástí a přidávání operací návrháře.

Když uživatelé navrhují své `MarqueeControl` instance, váš kořenový Návrhář bude sledovat změny `MarqueeControl` a jeho podřízené ovládací prvky. Prostředí pro dobu návrhu nabízí pohodlný službu, která umožňuje <xref:System.ComponentModel.Design.IComponentChangeService> sledovat změny stavu součásti.

Odkaz na tuto službu získáte dotazem na prostředí pomocí <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> metody. Pokud je dotaz úspěšný, může Návrhář k události připojit obslužnou rutinu <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> a provést jakékoli úkoly, aby zachovaly konzistentní stav v době návrhu.

V případě `MarqueeControlRootDesigner` třídy zavoláte <xref:System.Windows.Forms.Control.Refresh%2A> metodu pro každý `IMarqueeWidget` objekt obsažený v `MarqueeControl` . To způsobí, že se `IMarqueeWidget` objekt znovu překreslí, pokud dojde ke změně vlastností, jako je jeho nadřazený prvek <xref:System.Windows.Forms.Control.Size%2A> .

### <a name="to-handle-component-changes"></a>Zpracování změn součástí

1. Otevřete `MarqueeControlRootDesigner` zdrojový soubor v **editoru kódu** a přepište <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodu. Zavolejte základní implementaci <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> a dotaz na <xref:System.ComponentModel.Design.IComponentChangeService> .

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. Implementujte <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> obslužnou rutinu události. Otestujte typ odesílající komponenty a v případě, že se jedná o `IMarqueeWidget` , zavolejte svou <xref:System.Windows.Forms.Control.Refresh%2A> metodu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a>Přidání příkazů návrháře do vlastního návrháře

Příkaz návrháře je příkaz nabídky propojený s obslužnou rutinou události. Příkazy návrháře jsou přidány do místní nabídky součásti v době návrhu. Další informace naleznete v tématu <xref:System.ComponentModel.Design.DesignerVerb>.

Do návrháře přidáte dva příkazy návrháře: **Spusťte test** a **zastavte test**. Tyto příkazy vám umožní zobrazit chování za běhu v době `MarqueeControl` návrhu. Tyto operace budou přidány do `MarqueeControlRootDesigner` .

Při vyvolání příkazu **Spustit test** , obslužná rutina události vyvolá `StartMarquee` metodu na `MarqueeControl` . Při vyvolání příkazu **zastavit test** obslužná rutina události vyvolá `StopMarquee` metodu na `MarqueeControl` . Implementace `StartMarquee` `StopMarquee` metod a volá tyto metody pro obsažené ovládací prvky, které implementují `IMarqueeWidget` , takže všechny obsažené `IMarqueeWidget` ovládací prvky se také účastní testu.

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Přidání příkazů návrháře do vlastních návrhářů

1. Ve `MarqueeControlRootDesigner` třídě přidejte obslužné rutiny události s názvem `OnVerbRunTest` a `OnVerbStopTest` .

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. Připojte tyto obslužné rutiny událostí ke svým odpovídajícím slovesům návrháře. `MarqueeControlRootDesigner`dědí <xref:System.ComponentModel.Design.DesignerVerbCollection> z své základní třídy. Vytvoříte dva nové <xref:System.ComponentModel.Design.DesignerVerb> objekty a přidáte je do této kolekce v <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodě.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a>Vytvoření vlastního Editor UITypeEditor

Když pro uživatele vytvoříte vlastní prostředí pro dobu návrhu, často je žádoucí vytvořit vlastní interakci s okno Vlastnosti. To můžete provést vytvořením <xref:System.Drawing.Design.UITypeEditor> .

`MarqueeBorder`Ovládací prvek zveřejňuje v okno Vlastnosti několik vlastností. Dvě z těchto vlastností `MarqueeSpinDirection` a `MarqueeLightShape` jsou reprezentovány výčty. K ilustraci použití Editoru typů uživatelského rozhraní `MarqueeLightShape` bude mít vlastnost přidruženou <xref:System.Drawing.Design.UITypeEditor> třídu.

### <a name="to-create-a-custom-ui-type-editor"></a>Vytvoření vlastního editoru typů uživatelského rozhraní

1. Otevřete `MarqueeBorder` zdrojový soubor v **editoru kódu**.

2. V definici `MarqueeBorder` třídy Deklarujte třídu `LightShapeEditor` s názvem, která je odvozena z <xref:System.Drawing.Design.UITypeEditor> .

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance s názvem `editorService` .

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. Přepsat <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metodu. Tato implementace vrátí <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown> , což oznamuje vývojovému prostředí, jak zobrazit `LightShapeEditor` .

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. Přepsat <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metodu. Tato implementace se dotazuje návrhového prostředí pro <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> objekt. V případě úspěchu vytvoří `LightShapeSelectionControl` . <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A>Metoda je vyvolána pro spuštění `LightShapeEditor` . Návratová hodnota z tohoto vyvolání se vrátí do prostředí návrhu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a>Vytvoření ovládacího prvku zobrazení pro vlastní editor UITypeEditor

`MarqueeLightShape`Vlastnost podporuje dva typy lehkých tvarů: `Square` a `Circle` . Vytvoříte vlastní ovládací prvek, který bude použit výhradně pro účely grafického zobrazení těchto hodnot v okno Vlastnosti. Váš vlastní ovládací prvek bude použit <xref:System.Drawing.Design.UITypeEditor> pro interakci s okno Vlastnosti.

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Vytvoření ovládacího prvku zobrazení pro vlastní Editor typů uživatelského rozhraní

1. Přidejte <xref:System.Windows.Forms.UserControl> do projektu novou položku `MarqueeControlLibrary` . Dejte novému zdrojovému souboru základní název **LightShapeSelectionControl**.

2. Přetáhněte dva <xref:System.Windows.Forms.Panel> ovládací prvky ze **sady nástrojů** na `LightShapeSelectionControl` . Pojmenujte je `squarePanel` a `circlePanel` . Uspořádejte je vedle sebe. Nastavte <xref:System.Windows.Forms.Control.Size%2A> vlastnost obou <xref:System.Windows.Forms.Panel> ovládacích prvků na **(60, 60)**. Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost `squarePanel` ovládacího prvku na **(8, 10)**. Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost `circlePanel` ovládacího prvku na **(80, 10)**. Nakonec nastavte vlastnost na <xref:System.Windows.Forms.Control.Size%2A> `LightShapeSelectionControl` **(150, 80)**.

3. Otevřete `LightShapeSelectionControl` zdrojový soubor v **editoru kódu**. V horní části souboru importujte <xref:System.Windows.Forms.Design?displayProperty=nameWithType> obor názvů:

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. Implementujte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí pro `squarePanel` `circlePanel` ovládací prvky a. Tyto metody <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> se volají k ukončení vlastní <xref:System.Drawing.Design.UITypeEditor> relace úprav.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance s názvem `editorService` .

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. Deklarujte `MarqueeLightShape` proměnnou instance nazvanou `lightShapeValue` .

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. V `LightShapeSelectionControl` konstruktoru připojte <xref:System.Windows.Forms.Control.Click> obslužné rutiny události k `squarePanel` `circlePanel` událostem ovládacích prvků a <xref:System.Windows.Forms.Control.Click> . Také definujte přetížení konstruktoru, které přiřadí `MarqueeLightShape` hodnotu z prostředí návrhu k `lightShapeValue` poli.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. V <xref:System.ComponentModel.Component.Dispose%2A> metodě odpojte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** . Otevřete soubor LightShapeSelectionControl.Designer.cs nebo LightShapeSelectionControl. Designer. vb a odeberte výchozí definici <xref:System.ComponentModel.Component.Dispose%2A> metody.

10. Implementujte `LightShape` vlastnost.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. Přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metodu. Tato implementace Vykreslí vyplněný čtverec a kruh. Tím se také zvýrazní vybraná hodnota vykreslením ohraničení kolem jednoho obrazce nebo druhého.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a>Testování vlastního ovládacího prvku v Návrháři

V tomto okamžiku můžete sestavit `MarqueeControlLibrary` projekt. Otestujte implementaci vytvořením ovládacího prvku, který dědí z `MarqueeControl` třídy a jeho použitím na formuláři.

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Vytvoření vlastní implementace MarqueeControl

1. Otevřete `DemoMarqueeControl` v Návrhář formulářů. Tím se vytvoří instance `DemoMarqueeControl` typu a zobrazí se v instanci `MarqueeControlRootDesigner` typu.

2. V **sadě nástrojů**otevřete kartu **součásti MarqueeControlLibrary** . Zobrazí se `MarqueeBorder` ovládací prvky a, které `MarqueeText` jsou k dispozici pro výběr.

3. Přetáhněte instanci `MarqueeBorder` ovládacího prvku na `DemoMarqueeControl` návrhovou plochu. Ukotvit tento `MarqueeBorder` ovládací prvek nadřazenému ovládacímu prvku.

4. Přetáhněte instanci `MarqueeText` ovládacího prvku na `DemoMarqueeControl` návrhovou plochu.

5. Sestavte řešení.

6. Kliknutím pravým tlačítkem myši na `DemoMarqueeControl` a z místní nabídky vyberte možnost **Spustit test** a spusťte animaci. Kliknutím na **zastavit test** zastavte animaci.

7. Otevřete **Form1** v zobrazení Návrh.

8. Umístěte dva <xref:System.Windows.Forms.Button> ovládací prvky do formuláře. Pojmenujte je `startButton` a `stopButton` změňte <xref:System.Windows.Forms.Control.Text%2A> hodnoty vlastností na **Start** a **zastavit**v uvedeném pořadí.

9. Implementujte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí pro oba <xref:System.Windows.Forms.Button> ovládací prvky.

10. V **sadě nástrojů**otevřete kartu **součásti MarqueeControlTest** . Zobrazí se `DemoMarqueeControl` dostupná pro výběr.

11. Přetáhněte instanci `DemoMarqueeControl` na návrhovou plochu **Form1** .

12. V <xref:System.Windows.Forms.Control.Click> obslužných rutinách události volejte `Start` `Stop` metody a na `DemoMarqueeControl` .

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

13. Nastavte `MarqueeControlTest` projekt jako spouštěný projekt a spusťte ho. Zobrazí se formulář, ve kterém se zobrazuje vaše `DemoMarqueeControl` . Kliknutím na tlačítko **Start** spustíte animaci. Mělo by se zobrazit blikání textu a indikátory pohybu kolem ohraničení.

## <a name="next-steps"></a>Další kroky

`MarqueeControlLibrary`Ukazuje jednoduchou implementaci vlastních ovládacích prvků a přidružených návrhářů. Tuto ukázku můžete udělat několika způsoby:

- Změňte hodnoty vlastností `DemoMarqueeControl` v návrháři. `MarqueBorder`Chcete-li vytvořit vnořený efekt, přidejte další ovládací prvky a ukotvěte je Dock v rámci jejich nadřazených instancí. Experimentujte s různými nastaveními pro `UpdatePeriod` a vlastnosti související s osvětlením.

- Vytvořte vlastní implementace `IMarqueeWidget` . Mohli byste například vytvořit Flash "Neon Sign" nebo animované znaménko s více obrázky.

- Dále upravte prostředí pro dobu návrhu. Můžete zkusit vytvořit stín více vlastností než <xref:System.Windows.Forms.Control.Enabled%2A> a a <xref:System.Windows.Forms.Control.Visible%2A> můžete přidat nové vlastnosti. Přidejte nové příkazy návrháře, abyste zjednodušili běžné úkoly, jako je například ukotvení podřízených ovládacích prvků.

- Licenci `MarqueeControl` .

- Určuje, jak jsou ovládací prvky serializovány a jak jsou pro ně generovány kódy. Další informace naleznete v tématu [generování a kompilace dynamického zdrojového kódu](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
