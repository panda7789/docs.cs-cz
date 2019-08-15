---
title: 'Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu'
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
ms.openlocfilehash: 733f22c122dd6acdad41371419375e55e977c016
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039934"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu

Prostředí pro návrh vlastního ovládacího prvku lze zvýšit vytvořením přidruženého vlastního návrháře.

Tento návod ukazuje, jak vytvořit vlastního návrháře vlastního ovládacího prvku. Budete implementovat `MarqueeControl` typ a přidruženou třídu návrháře, která je volána `MarqueeControlRootDesigner`.

`MarqueeControl` Typ implementuje zobrazení podobné textu v kino s animovanými indikátory a blikající text.

Návrhář pro tento ovládací prvek komunikuje s vývojovým prostředím, aby poskytoval vlastní prostředí pro dobu návrhu. Pomocí vlastního návrháře můžete sestavit vlastní `MarqueeControl` implementaci s animovanými indikátory a blikající text v mnoha kombinacích. Můžete použít sestavený ovládací prvek na formuláři, stejně jako jakýkoli jiný ovládací prvek model Windows Forms.

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytvoření projektu

- Vytvoření projektu knihovny ovládacích prvků

- Odkazování na projekt vlastního ovládacího prvku

- Definování vlastního ovládacího prvku a jeho vlastního návrháře

- Vytvoření instance vlastního ovládacího prvku

- Nastavení projektu pro ladění v době návrhu

- Implementace vlastního ovládacího prvku

- Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek

- Vytvoření podřízeného ovládacího prvku MarqueeBorder

- Vytvoření vlastního návrháře pro vlastnosti stínu a filtru

- Zpracování změn součástí

- Přidávání operací návrháře do vlastního návrháře

- Vytvoření vlastního Editor UITypeEditor

- Testování vlastního ovládacího prvku v Návrháři

Až budete hotovi, váš vlastní ovládací prvek bude vypadat přibližně takto:

![Aplikace, která zobrazuje text a tlačítka Spustit a zastavit](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

Úplný výpis kódu naleznete v tématu [How to: Vytvořte model Windows Forms ovládací prvek, který bude využívat funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))pro dobu návrhu.


## <a name="prerequisites"></a>Požadavky

Aby bylo možné dokončit tento návod, budete potřebovat aplikaci Visual Studio.

## <a name="creating-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu aplikace. Pomocí tohoto projektu sestavíte aplikaci, která je hostitelem vlastního ovládacího prvku.

Otevřete Visual Studio a vytvořte projekt model Windows Forms aplikace s názvem "MarqueeControlTest" (**souborový** > **vizuál C#**  **Nový** > **projekt** > nebo **Visual Basic**  >  **Klasický stolní počítač** **Model Windows Forms aplikace).**  > 

## <a name="creating-a-control-library-project"></a>Vytvoření projektu knihovny ovládacích prvků

Dalším krokem je vytvoření projektu knihovny ovládacích prvků. Vytvoří se nový vlastní ovládací prvek a jeho odpovídající vlastní Návrhář.

### <a name="to-create-the-control-library-project"></a>Vytvoření projektu knihovny ovládacích prvků

1. Přidejte do řešení projekt knihovny ovládacích prvků model Windows Forms. Pojmenujte projekt "MarqueeControlLibrary".

2. Pomocí **Průzkumník řešení**odstraňte výchozí ovládací prvek projektu odstraněním zdrojového souboru s názvem "UserControl1.cs" nebo "UserControl1. vb" v závislosti na zvoleném jazyce. Další informace najdete v tématu [jak: Odebere, odstraní a vyloučí položky](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).

3. <xref:System.Windows.Forms.UserControl> Přidejte`MarqueeControlLibrary` do projektu novou položku. Dejte novému zdrojovému souboru základní název "MarqueeControl".

4. Pomocí **Průzkumník řešení**vytvořte v `MarqueeControlLibrary` projektu novou složku. Další informace najdete v tématu [jak: Přidejte nové položky](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))projektu. Pojmenujte novou složku "design".

5. Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu. Udělte zdrojovému souboru základní název "MarqueeControlRootDesigner".

6. Budete muset použít typy ze sestavení System. design, takže přidejte tento odkaz do `MarqueeControlLibrary` projektu.

    > [!NOTE]
    > Chcete-li použít sestavení System. design, musí projekt cílit na plnou verzi .NET Framework, nikoli .NET Framework profil klienta. Chcete-li změnit cílovou architekturu [, přečtěte si téma How to: Cílí na verzi .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

## <a name="referencing-the-custom-control-project"></a>Odkazování na projekt vlastního ovládacího prvku

K otestování vlastního ovládacího prvku použijete projekt.`MarqueeControlTest` Testovací projekt se při přidání odkazu na projekt do `MarqueeControlLibrary` sestavení změní na vlastní ovládací prvek.

### <a name="to-reference-the-custom-control-project"></a>Odkazování na projekt vlastního ovládacího prvku

- V projektu přidejte odkaz na projekt do `MarqueeControlLibrary` sestavení. `MarqueeControlTest` Nezapomeňte použít kartu **projekty** v dialogovém okně **Přidat odkaz** namísto odkazování na `MarqueeControlLibrary` sestavení přímo.

## <a name="defining-a-custom-control-and-its-custom-designer"></a>Definování vlastního ovládacího prvku a jeho vlastního návrháře
 Vlastní ovládací prvek bude odvozen z <xref:System.Windows.Forms.UserControl> třídy. To umožňuje vašemu ovládacímu prvku, aby obsahoval další ovládací prvky, a poskytuje vašemu ovládacímu prvku skvělou výchozí funkčnost.

 Vlastní ovládací prvek bude mít přidružený vlastní Návrhář. To vám umožní vytvořit jedinečné vývojové prostředí, které se přizpůsobí speciálně pro váš vlastní ovládací prvek.

 K přidružení ovládacího prvku ke svému návrháři použijte <xref:System.ComponentModel.DesignerAttribute> třídu. Vzhledem k tomu, že vyvíjíte celé chování vlastního ovládacího prvku v době návrhu, bude vlastní Návrhář implementovat <xref:System.ComponentModel.Design.IRootDesigner> rozhraní.

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Definování vlastního ovládacího prvku a jeho vlastního návrháře

1. Otevřete zdrojový soubor v **editoru kódu.** `MarqueeControl` V horní části souboru importujte následující obory názvů:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <xref:System.ComponentModel.DesignerAttribute> Přidejte`MarqueeControl` do deklarace třídy. Tím přiřadíte vlastní ovládací prvek ke svému návrháři.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. Otevřete zdrojový soubor v **editoru kódu.** `MarqueeControlRootDesigner` V horní části souboru importujte následující obory názvů:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. Změňte deklaraci `MarqueeControlRootDesigner` na dědění <xref:System.Windows.Forms.Design.DocumentDesigner> z třídy. Použijte pro určení interakce návrháře pomocí **sady nástrojů.** <xref:System.ComponentModel.ToolboxItemFilterAttribute>

     **Poznámka:** Definice pro `MarqueeControlRootDesigner` třídu byla uzavřená v oboru názvů s názvem "MarqueeControlLibrary. Design". Tato deklarace umístí návrháře ve speciálním oboru názvů vyhrazeném pro typy související s návrhem.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. Definujte konstruktor pro `MarqueeControlRootDesigner` třídu. <xref:System.Diagnostics.Trace.WriteLine%2A> Vloží příkaz do těla konstruktoru. To bude užitečné pro účely ladění.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="creating-an-instance-of-your-custom-control"></a>Vytvoření instance vlastního ovládacího prvku
 Chcete-li sledovat vlastní chování ovládacího prvku v době návrhu, umístěte instanci ovládacího prvku do formuláře v `MarqueeControlTest` projektu.

### <a name="to-create-an-instance-of-your-custom-control"></a>Vytvoření instance vlastního ovládacího prvku

1. <xref:System.Windows.Forms.UserControl> Přidejte`MarqueeControlTest` do projektu novou položku. Dejte novému zdrojovému souboru základní název "DemoMarqueeControl".

2. Otevřete soubor v **editoru kódu.** `DemoMarqueeControl` V horní části souboru importujte `MarqueeControlLibrary` obor názvů:

```vb
Imports MarqueeControlLibrary
```

```csharp
using MarqueeControlLibrary;
```

1. Změňte deklaraci `DemoMarqueeControl` na dědění `MarqueeControl` z třídy.

2. Sestavte projekt.

3. Otevřete `Form1` v Návrhář formulářů.

4. V **sadě nástrojů** Najděte kartu **komponenty MarqueeControlTest** a otevřete ji. Přetáhněte z panelu nástrojů do formuláře. `DemoMarqueeControl`

5. Sestavte projekt.

## <a name="setting-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu

Při vývoji vlastního prostředí v době návrhu bude nutné ladit ovládací prvky a komponenty. Existuje jednoduchý způsob, jak nastavit projekt tak, aby umožňoval ladění v době návrhu. Další informace najdete v tématu [Návod: Ladění vlastních ovládacích prvků model Windows Forms v době](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)návrhu.

### <a name="to-set-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu

1. Klikněte pravým tlačítkem `MarqueeControlLibrary` na projekt a vyberte **vlastnosti**.

2. V dialogovém okně "MarqueeControlLibrary stránky vlastností" vyberte stránku **ladění** .

3. V části **spouštěcí akce** vyberte **spustit externí program**. Budete ladit samostatnou instanci sady Visual Studio, proto klikněte na tlačítko se třemi![tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) a vyhledejte integrované vývojové prostředí (IDE) sady Visual Studio. Název spustitelného souboru je devenv. exe a pokud jste nainstalovali do výchozího umístění, jeho cesta je%programfiles%\Microsoft Visual Studio 9.0 \ Common7\IDE\devenv.exe.

4. Kliknutím na tlačítko OK zavřete dialogové okno.

5. Klikněte pravým tlačítkem `MarqueeControlLibrary` na projekt a vyberte nastavit jako spouštěný projekt, abyste mohli tuto konfiguraci ladění povolit.

## <a name="checkpoint"></a>CheckPoint

Nyní jste připraveni ladit chování vlastního ovládacího prvku v době návrhu. Jakmile zjistíte, že je prostředí ladění správně nastaveno, budete testovat přidružení mezi vlastním ovládacím prvkem a vlastním návrhářem.

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Otestování ladicího prostředí a přidružení návrháře

1. Otevřete zdrojový soubor v **editoru kódu** a umístěte zarážku na <xref:System.Diagnostics.Trace.WriteLine%2A> příkaz. `MarqueeControlRootDesigner`

2. Stisknutím klávesy F5 spusťte relaci ladění. Všimněte si, že je vytvořena nová instance aplikace Visual Studio.

3. V nové instanci aplikace Visual Studio otevřete řešení "MarqueeControlTest". Řešení můžete snadno najít výběrem položky **Poslední projekty** v nabídce **soubor** . Soubor řešení "MarqueeControlTest. sln" bude uveden jako naposledy použitý soubor.

4. `DemoMarqueeControl` Otevřete v návrháři. Všimněte si, že instance ladění sady Visual Studio získá fokus a provádění se zastaví na zarážce. Stisknutím klávesy F5 pokračujte v relaci ladění.

V tomto okamžiku je vše pro vývoj a ladění vlastního ovládacího prvku a jeho přidruženého vlastního návrháře. Zbývající část tohoto návodu se soustředí na podrobnosti o implementaci funkcí ovládacího prvku a návrháře.

## <a name="implementing-your-custom-control"></a>Implementace vlastního ovládacího prvku

`MarqueeControl` Je a<xref:System.Windows.Forms.UserControl> s malým počtem přizpůsobení. Zveřejňuje dvě metody: `Start`, který spustí animaci běžící na hranice a `Stop`, která zastaví animaci. `StartMarquee` `IMarqueeWidget` `StopMarquee` `Stop` `Start` Protože obsahuje podřízené ovládací prvky, které implementují rozhraní, a vyčíslení každého podřízeného ovládacího prvku a volání metod a v každém podřízeném ovládacím prvku, v uvedeném pořadí. `MarqueeControl` , který `IMarqueeWidget`implementuje.

Vzhled `MarqueeBorder` ovládacích prvků a `MarqueeText` je závislý na <xref:System.Windows.Forms.Control.OnLayout%2A> rozložení, takže `MarqueeControl` přepíše metodu a volání <xref:System.Windows.Forms.Control.PerformLayout%2A> podřízených ovládacích prvků tohoto typu.

Toto je rozsah `MarqueeControl` úprav. Funkce modulu runtime jsou implementovány `MarqueeBorder` ovládacími prvky a `MarqueeText` a `MarqueeBorderDesigner` funkce v době návrhu jsou implementovány třídami a `MarqueeControlRootDesigner` .

### <a name="to-implement-your-custom-control"></a>Implementace vlastního ovládacího prvku

1. Otevřete zdrojový soubor v **editoru kódu.** `MarqueeControl` Implementujte metody `Stop`a. `Start`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. Přepsat <xref:System.Windows.Forms.Control.OnLayout%2A> metody.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="creating-a-child-control-for-your-custom-control"></a>Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek

Bude hostovat dva druhy podřízeného ovládacího prvku `MarqueeBorder` : ovládací prvek a `MarqueeText` ovládací prvek. `MarqueeControl`

- `MarqueeBorder`: Tento ovládací prvek vykreslí ohraničení "světel" kolem jeho okrajů. Světla se zobrazí v sekvenci, takže se zdají kolem ohraničení pohybovat. Rychlost, s níž jsou indikátory blesku ovládány vlastností s `UpdatePeriod`názvem. Některé další vlastní vlastnosti určují další aspekty vzhledu ovládacího prvku. Dvě metody, které `StartMarquee` jsou `StopMarquee`volány a, určují, kdy se animace spouští a zastavuje.

- `MarqueeText`: Tento ovládací prvek vykreslí blikající řetězec. Podobně jako `MarqueeBorder` u ovládacího prvku je rychlost, s jakou je text blikající, ovládána `UpdatePeriod` vlastností. Ovládací prvek `StopMarquee` `MarqueeBorder` má také společné metody asovládacímprvkem.`StartMarquee` `MarqueeText`

V době návrhu `MarqueeControlRootDesigner` umožňuje, aby tyto dva typy ovládacích prvků byly přidány `MarqueeControl` do jakékoli kombinace.

Společné funkce těchto dvou ovládacích prvků jsou přihlédnuto do rozhraní s názvem `IMarqueeWidget`. To umožňuje, `MarqueeControl` aby se zjistily podřízené ovládací prvky související s rámečkem a přidávají jim speciální zacházení.

K implementaci funkce periodické animace budete používat <xref:System.ComponentModel.BackgroundWorker> objekty <xref:System.ComponentModel?displayProperty=nameWithType> z oboru názvů. Můžete použít <xref:System.Windows.Forms.Timer> objekty, ale v případě, `IMarqueeWidget` že je přítomen velký počet objektů, nemusí být jedno vlákno uživatelského rozhraní schopno s animací zůstat.

### <a name="to-create-a-child-control-for-your-custom-control"></a>Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek

1. Přidejte do `MarqueeControlLibrary` projektu novou položku třídy. Dejte novému zdrojovému souboru základní název "IMarqueeWidget".

2. Otevřete zdrojový soubor v **editoru kódu** a změňte deklaraci z `class` na: `interface` `IMarqueeWidget`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. Přidejte následující kód do `IMarqueeWidget` rozhraní, aby bylo možné vystavit dvě metody a vlastnost, která zpracovává animaci běžícího výběru:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. Přidejte do `MarqueeControlLibrary` projektu novou položku **vlastního ovládacího prvku** . Dejte novému zdrojovému souboru základní název "MarqueeText".

5. Přetáhněte komponentu z **panelu nástrojů** na ovládacíprvek.`MarqueeText` <xref:System.ComponentModel.BackgroundWorker> Tato součást umožní, aby `MarqueeText` se ovládací prvek sám aktualizoval asynchronně.

6. V okno Vlastnosti nastavte <xref:System.ComponentModel.BackgroundWorker> vlastnosti `WorkerReportsProgress` komponenty a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> na `true`. Tato nastavení umožňují, <xref:System.ComponentModel.BackgroundWorker> aby součást pravidelně <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> vyvolala událost a zrušila asynchronní aktualizace. Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).

7. Otevřete zdrojový soubor v **editoru kódu.** `MarqueeText` V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. Změňte deklaraci `MarqueeText` na dědění z <xref:System.Windows.Forms.Label> a k implementaci `IMarqueeWidget` rozhraní:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru. Pole určuje, zda má být text vykreslen v barvě dané `LightColor` vlastností. `isLit`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. Implementujte rozhraní `IMarqueeWidget`.

    `StartMarquee` Metodya`StopMarquee` vyvolají<xref:System.ComponentModel.BackgroundWorker> komponentu a<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>metody pro spuštění a zastavení animace. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>

    Atributy a se<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> aplikují na vlastnost,takžesezobrazívevlastníčástioknoVlastnostinazvané"výběr".`UpdatePeriod` <xref:System.ComponentModel.CategoryAttribute.Category%2A>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. Implementujte přistupující objekty vlastnosti. Pro klienty budete vystavovat dvě vlastnosti `LightColor` : `DarkColor`a. Atributy <xref:System.ComponentModel.CategoryAttribute.Category%2A> a<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> se aplikují na tyto vlastnosti, takže se vlastnosti zobrazí ve vlastní části okno Vlastnosti s názvem "výběr".

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. Implementujte obslužné rutiny <xref:System.ComponentModel.BackgroundWorker> pro události <xref:System.ComponentModel.BackgroundWorker.DoWork> komponenty <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a.

    Obslužná rutina `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>události v režimu spánku po dobu určenou v milisekundách vyvolá událost, dokud váš kód nezastaví animaci voláním. <xref:System.ComponentModel.BackgroundWorker.DoWork>

    Obslužná <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> rutina události přepíná text mezi jeho světlý a tmavý stav, aby bylo možné podobu blikání.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <xref:System.Windows.Forms.Control.OnPaint%2A> Přepsat metodu pro povolení animace.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. Stisknutím klávesy F6 Sestavte řešení.

## <a name="create-the-marqueeborder-child-control"></a>Vytvoření podřízeného ovládacího prvku MarqueeBorder

Ovládací prvek je poněkud složitější `MarqueeText` než ovládací prvek. `MarqueeBorder` Má více vlastností a další animace v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě je více zapojena. V zásadě je poměrně podobný `MarqueeText` ovládacímu prvku.

Vzhledem k tomu, že <xref:System.Windows.Forms.Control.Layout> ovládacíprvekmůžemítpodřízenéovládacíprvky,musíznátudálosti.`MarqueeBorder`

### <a name="to-create-the-marqueeborder-control"></a>Vytvoření ovládacího prvku MarqueeBorder

1. Přidejte do `MarqueeControlLibrary` projektu novou položku **vlastního ovládacího prvku** . Dejte novému zdrojovému souboru základní název "MarqueeBorder".

2. Přetáhněte komponentu z **panelu nástrojů** na ovládacíprvek.`MarqueeBorder` <xref:System.ComponentModel.BackgroundWorker> Tato součást umožní, aby `MarqueeBorder` se ovládací prvek sám aktualizoval asynchronně.

3. V okno Vlastnosti nastavte <xref:System.ComponentModel.BackgroundWorker> vlastnosti `WorkerReportsProgress` komponenty a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> na `true`. Tato nastavení umožňují, <xref:System.ComponentModel.BackgroundWorker> aby součást pravidelně <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> vyvolala událost a zrušila asynchronní aktualizace. Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).

4. V okno Vlastnosti klikněte na tlačítko události. Připojte obslužné rutiny <xref:System.ComponentModel.BackgroundWorker.DoWork> pro <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události a.

5. Otevřete zdrojový soubor v **editoru kódu.** `MarqueeBorder` V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. Změňte deklaraci `MarqueeBorder` na dědění z <xref:System.Windows.Forms.Panel> a k implementaci `IMarqueeWidget` rozhraní.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. Deklarujete dva výčty pro správu `MarqueeBorder` stavu ovládacího prvku: `MarqueeSpinDirection`, který určuje směr otočení světla kolem ohraničení a `MarqueeLightShape`určuje tvar světel (čtvercové nebo kruhové). Tyto deklarace umístěte před `MarqueeBorder` deklaraci třídy.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. Implementujte rozhraní `IMarqueeWidget`.

    `StartMarquee` Metodya`StopMarquee` vyvolají<xref:System.ComponentModel.BackgroundWorker> komponentu a<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>metody pro spuštění a zastavení animace. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>

    Vzhledem k `MarqueeBorder` `StartMarquee` tomu, že ovládací prvek může obsahovat podřízené ovládací prvky, metoda vytvoří výčet všech `StartMarquee` podřízených ovládacích prvků `IMarqueeWidget`a volání, která implementují. `StopMarquee` Metoda má podobnou implementaci.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. Implementujte přistupující objekty vlastnosti. `MarqueeBorder` Ovládací prvek má několik vlastností pro řízení jeho vzhledu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. Implementujte obslužné rutiny <xref:System.ComponentModel.BackgroundWorker> pro události <xref:System.ComponentModel.BackgroundWorker.DoWork> komponenty <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a.

    Obslužná rutina `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>události v režimu spánku po dobu určenou v milisekundách vyvolá událost, dokud váš kód nezastaví animaci voláním. <xref:System.ComponentModel.BackgroundWorker.DoWork>

    Obslužná rutina <xref:System.Windows.Forms.Control.Refresh%2A>událostizvýší pozici "základního" světla, ze kterého je stanoven světlý nebo tmavý stav ostatních světel, a volá metodu, která způsobí, že ovládací prvek provede překreslení sám sebe. <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. Implementujte pomocné metody `IsLit` a `DrawLight`.

    `IsLit` Metoda určuje barvu světla na dané pozici. Indikátory, které jsou "osvětlené" jsou vykresleny barvou `LightColor` dané vlastností a ty, které jsou "tmavé" jsou vykresleny v barvě dané `DarkColor` vlastností.

    `DrawLight` Metoda nakreslí světlo pomocí příslušné barvy, tvaru a pozice.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. Přepište metody <xref:System.Windows.Forms.Control.OnPaint%2A>a. <xref:System.Windows.Forms.Control.OnLayout%2A>

    Metoda kreslí světla podél okrajů `MarqueeBorder` ovládacího prvku. <xref:System.Windows.Forms.Control.OnPaint%2A>

    Vzhledem k tomu, že `MarqueeBorder` metodazávisínarozměrechovládacíhoprvku,jenutnéjejzavolatpřikaždézměněrozložení.<xref:System.Windows.Forms.Control.OnPaint%2A> Chcete-li toho dosáhnout <xref:System.Windows.Forms.Control.OnLayout%2A> , přepište a zavolejte. <xref:System.Windows.Forms.Control.Refresh%2A>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>Vytvoření vlastního návrháře pro vlastnosti stínu a filtru

`MarqueeControlRootDesigner` Třída poskytuje implementaci pro kořenového návrháře. Kromě tohoto návrháře, který pracuje na `MarqueeControl`, budete potřebovat vlastního návrháře, který je konkrétně přidružen `MarqueeBorder` k ovládacímu prvku. Tento návrhář poskytuje vlastní chování, které je vhodné v kontextu vlastního kořenového návrháře.

Konkrétně bude "stínem" a filtrovat určité vlastnosti `MarqueeBorder` ovládacího prvku, změnou jejich interakce s návrhovým prostředím. `MarqueeBorderDesigner`

Zachytávání volání vlastnosti objektu komponenty se označují jako "stíning". Umožňuje návrháři sledovat hodnotu nastavenou uživatelem a volitelně předat tuto hodnotu do navržené součásti.

V tomto příkladu <xref:System.Windows.Forms.Control.Visible%2A> budou vlastnosti a <xref:System.Windows.Forms.Control.Enabled%2A> nastínované pomocí `MarqueeBorderDesigner`, což brání uživateli v tom, aby během návrhu byl `MarqueeBorder` ovládací prvek neviditelný nebo zakázán.

Návrháři mohou také přidávat a odebírat vlastnosti. V tomto příkladu <xref:System.Windows.Forms.Control.Padding%2A> bude vlastnost odebrána v době návrhu, `MarqueeBorder` protože ovládací prvek programově nastaví odsazení na základě velikosti světla určených `LightSize` vlastností.

Základní třída pro `MarqueeBorderDesigner` je <xref:System.ComponentModel.Design.ComponentDesigner>, která má metody, které mohou měnit atributy, vlastnosti a události vystavené ovládacím prvkem v době návrhu:

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

Při změně veřejného rozhraní komponenty pomocí těchto metod je nutné dodržovat tato pravidla:

- Přidat nebo odebrat položky pouze v `PreFilter` metodách

- Upravit existující položky pouze v `PostFilter` metodách

- Vždy volat základní implementaci nejprve v `PreFilter` metodách

- Vždy volat základní implementaci jako poslední v `PostFilter` metodách

Dodržování těchto pravidel zajišťuje, že všichni návrháři v prostředí návrhu mají konzistentní zobrazení všech navržených komponent.

<xref:System.ComponentModel.Design.ComponentDesigner> Třída poskytuje slovník pro správu hodnot stínových vlastností, což zbavuje nutnost vytváření specifických proměnných instance.

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Vytvoření vlastního návrháře pro vlastnosti stínu a filtru

1. Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu. Udělte zdrojovému souboru základní název "MarqueeBorderDesigner".

2. Otevřete zdrojový soubor v **editoru kódu.** `MarqueeBorderDesigner` V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. Změňte deklaraci `MarqueeBorderDesigner` na dědění z <xref:System.Windows.Forms.Design.ParentControlDesigner>.

    Vzhledem k `MarqueeBorder` tomu, že ovládací prvek může `MarqueeBorderDesigner` obsahovat podřízené <xref:System.Windows.Forms.Design.ParentControlDesigner>ovládací prvky, dědí z, který zpracovává interakci nadřazený-podřízený.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. Přepsat základní implementaci <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. Implementujte vlastnosti <xref:System.Windows.Forms.Control.Visible%2A>a. <xref:System.Windows.Forms.Control.Enabled%2A> Tyto implementace nastínují vlastnosti ovládacího prvku.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handling-component-changes"></a>Zpracování změn součástí
 Třída poskytuje vlastní prostředí pro dobu návrhu pro vaše `MarqueeControl` instance. `MarqueeControlRootDesigner` Většina funkcí návrhu je děděna z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy; váš kód implementuje dvě konkrétní vlastní nastavení: zpracování změn součástí a přidávání operací návrháře.

 Když uživatelé navrhují `MarqueeControl` své instance, váš kořenový Návrhář bude sledovat změny `MarqueeControl` a jeho podřízené ovládací prvky. Prostředí pro dobu návrhu nabízí pohodlný službu, <xref:System.ComponentModel.Design.IComponentChangeService>která umožňuje sledovat změny stavu součásti.

 Odkaz na tuto službu získáte dotazem na prostředí pomocí <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> metody. Pokud je dotaz úspěšný, může Návrhář k <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> události připojit obslužnou rutinu a provést jakékoli úkoly, aby zachovaly konzistentní stav v době návrhu.

 V případě `MarqueeControlRootDesigner` třídy <xref:System.Windows.Forms.Control.Refresh%2A> zavoláte metodu pro každý `IMarqueeWidget` objekt obsažený v `MarqueeControl`. To způsobí, že `IMarqueeWidget` se objekt znovu překreslí, pokud dojde ke změně vlastností, jako <xref:System.Windows.Forms.Control.Size%2A> je jeho nadřazený prvek.

### <a name="to-handle-component-changes"></a>Zpracování změn součástí

1. Otevřete zdrojový soubor v **editoru kódu** a přepište <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodu. `MarqueeControlRootDesigner` Zavolejte základní implementaci <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> a dotaz <xref:System.ComponentModel.Design.IComponentChangeService>na.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. Implementujte obslužnou rutinu události. <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> Otestujte typ odesílající komponenty a v případě, že se jedná o `IMarqueeWidget`, zavolejte svou <xref:System.Windows.Forms.Control.Refresh%2A> metodu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="adding-designer-verbs-to-your-custom-designer"></a>Přidávání operací návrháře do vlastního návrháře

Příkaz návrháře je příkaz nabídky propojený s obslužnou rutinou události. Příkazy návrháře jsou přidány do místní nabídky součásti v době návrhu. Další informace naleznete v tématu <xref:System.ComponentModel.Design.DesignerVerb>.

Do návrháře přidáte dva příkazy návrháře: **Spusťte test** a **zastavte test**. Tyto příkazy vám umožní zobrazit chování `MarqueeControl` za běhu v době návrhu. Tyto operace budou přidány do `MarqueeControlRootDesigner`.

Při vyvolání příkazu **Spustit test** , obslužná rutina `StartMarquee` události vyvolá metodu na `MarqueeControl`. Při vyvolání příkazu **zastavit test** obslužná rutina `StopMarquee` události vyvolá metodu na `MarqueeControl`. Implementace `StartMarquee` metod a `StopMarquee` volá tyto metody pro obsažené ovládací prvky, které implementují `IMarqueeWidget`, takže všechny obsažené `IMarqueeWidget` ovládací prvky se také účastní testu.

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Přidání příkazů návrháře do vlastních návrhářů

1. Ve třídě přidejte obslužné rutiny události s `OnVerbRunTest` názvem `OnVerbStopTest`a. `MarqueeControlRootDesigner`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. Připojte tyto obslužné rutiny událostí ke svým odpovídajícím slovesům návrháře. `MarqueeControlRootDesigner`<xref:System.ComponentModel.Design.DesignerVerbCollection> dědí z své základní třídy. Vytvoříte dva nové <xref:System.ComponentModel.Design.DesignerVerb> objekty a přidáte je do této kolekce <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> v metodě.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="creating-a-custom-uitypeeditor"></a>Vytvoření vlastního Editor UITypeEditor

Když pro uživatele vytvoříte vlastní prostředí pro dobu návrhu, často je žádoucí vytvořit vlastní interakci s okno Vlastnosti. To můžete provést vytvořením <xref:System.Drawing.Design.UITypeEditor>. Další informace najdete v tématu [jak: Vytvoří Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120))typů uživatelského rozhraní.

`MarqueeBorder` Ovládací prvek zveřejňuje v okno Vlastnosti několik vlastností. Dvě z těchto vlastností `MarqueeSpinDirection` a `MarqueeLightShape` jsou reprezentovány výčty. K ilustraci použití editoru `MarqueeLightShape` typů uživatelského rozhraní bude mít vlastnost přidruženou <xref:System.Drawing.Design.UITypeEditor> třídu.

### <a name="to-create-a-custom-ui-type-editor"></a>Vytvoření vlastního editoru typů uživatelského rozhraní

1. Otevřete zdrojový soubor v **editoru kódu.** `MarqueeBorder`

2. V definici `MarqueeBorder` třídy Deklarujte třídu s názvem `LightShapeEditor` , která je odvozena z <xref:System.Drawing.Design.UITypeEditor>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance s `editorService`názvem.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. Přepsat <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metody. Tato implementace vrátí <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, což oznamuje vývojovému prostředí, jak `LightShapeEditor`zobrazit.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. Přepsat <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metody. Tato implementace se dotazuje návrhového prostředí <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> pro objekt. V případě úspěchu vytvoří `LightShapeSelectionControl`. Metoda je vyvolána pro `LightShapeEditor`spuštění. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Návratová hodnota z tohoto vyvolání se vrátí do prostředí návrhu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>Vytvoření ovládacího prvku zobrazení pro vlastní editor UITypeEditor

1. Vlastnost podporuje dva typy lehkých tvarů: `Square` a `Circle`. `MarqueeLightShape` Vytvoříte vlastní ovládací prvek, který bude použit výhradně pro účely grafického zobrazení těchto hodnot v okno Vlastnosti. Váš <xref:System.Drawing.Design.UITypeEditor> vlastní ovládací prvek bude použit pro interakci s okno Vlastnosti.

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Vytvoření ovládacího prvku zobrazení pro vlastní Editor typů uživatelského rozhraní

1. <xref:System.Windows.Forms.UserControl> Přidejte`MarqueeControlLibrary` do projektu novou položku. Dejte novému zdrojovému souboru základní název "LightShapeSelectionControl".

2. Přetáhněte dva <xref:System.Windows.Forms.Panel> ovládací prvky ze `LightShapeSelectionControl` **sady nástrojů** na. `squarePanel` Pojmenujte `circlePanel`je a. Uspořádejte je vedle sebe. Nastavte vlastnost obou <xref:System.Windows.Forms.Panel> ovládacích prvků na (60, 60). <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> Nastavte vlastnost `squarePanel` ovládacího prvku na (8, 10). <xref:System.Windows.Forms.Control.Location%2A> Nastavte vlastnost `circlePanel` ovládacího prvku na (80, 10). Nakonec nastavte <xref:System.Windows.Forms.Control.Size%2A> vlastnost `LightShapeSelectionControl` na (150, 80).

3. Otevřete zdrojový soubor v **editoru kódu.** `LightShapeSelectionControl` V horní části souboru importujte <xref:System.Windows.Forms.Design?displayProperty=nameWithType> obor názvů:

```vb
Imports System.Windows.Forms.Design
```

```csharp
using System.Windows.Forms.Design;
```

1. Implementujte <xref:System.Windows.Forms.Control.Click> obslužné rutiny `squarePanel` událostí `circlePanel` pro ovládací prvky a. Tyto metody se <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> volají k ukončení vlastní <xref:System.Drawing.Design.UITypeEditor> relace úprav.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

2. Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance s `editorService`názvem.

```vb
Private editorService As IWindowsFormsEditorService
```

```csharp
private IWindowsFormsEditorService editorService;
```

1. Deklarujte proměnnou `lightShapeValue`instance nazvanou. `MarqueeLightShape`

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

2. `squarePanel` `circlePanel` V konstruktoru připojte obslužné rutiny <xref:System.Windows.Forms.Control.Click> události<xref:System.Windows.Forms.Control.Click> k událostem ovládacích prvků a. `LightShapeSelectionControl` Také definujte přetížení konstruktoru, které přiřadí `MarqueeLightShape` hodnotu z prostředí návrhu `lightShapeValue` k poli.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

3. V metodě odpojte obslužné rutiny <xref:System.Windows.Forms.Control.Click>událostí. <xref:System.ComponentModel.Component.Dispose%2A>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

4. V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** . Otevřete soubor LightShapeSelectionControl.Designer.cs nebo LightShapeSelectionControl. Designer. vb a odeberte výchozí definici <xref:System.ComponentModel.Component.Dispose%2A> metody.

5. Implementujte `LightShape` vlastnost.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

6. Přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Tato implementace Vykreslí vyplněný čtverec a kruh. Tím se také zvýrazní vybraná hodnota vykreslením ohraničení kolem jednoho obrazce nebo druhého.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="testing-your-custom-control-in-the-designer"></a>Testování vlastního ovládacího prvku v Návrháři

V tomto okamžiku můžete sestavit `MarqueeControlLibrary` projekt. Otestujte implementaci vytvořením ovládacího prvku, který dědí z `MarqueeControl` třídy a jeho použitím na formuláři.

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Vytvoření vlastní implementace MarqueeControl

1. Otevřete `DemoMarqueeControl` v Návrhář formulářů. Tím se `DemoMarqueeControl` vytvoří instance typu a zobrazí se v instanci `MarqueeControlRootDesigner` typu.

2. V **sadě nástrojů**otevřete kartu **součásti MarqueeControlLibrary** . Zobrazí se `MarqueeBorder` ovládací prvky a `MarqueeText` , které jsou k dispozici pro výběr.

3. Přetáhněte instanci `MarqueeBorder` ovládacího prvku `DemoMarqueeControl` na návrhovou plochu. Ukotvit tento `MarqueeBorder` ovládací prvek nadřazenému ovládacímu prvku.

4. Přetáhněte instanci `MarqueeText` ovládacího prvku `DemoMarqueeControl` na návrhovou plochu.

5. Sestavte řešení.

6. Kliknutím `DemoMarqueeControl` pravým tlačítkem myši na a z místní nabídky vyberte možnost **Spustit test** a spusťte animaci. Kliknutím na **zastavit test** zastavte animaci.

7. Otevřete **Form1** v zobrazení Návrh.

8. Umístěte dva <xref:System.Windows.Forms.Button> ovládací prvky do formuláře. `startButton` Pojmenujte `stopButton`je a změňte <xref:System.Windows.Forms.Control.Text%2A> hodnoty vlastností na **Start** a **zastavit**v uvedeném pořadí.

9. Implementujte <xref:System.Windows.Forms.Control.Click> obslužné rutiny <xref:System.Windows.Forms.Button> událostí pro oba ovládací prvky.

10. V **sadě nástrojů**otevřete kartu **součásti MarqueeControlTest** . Zobrazí se `DemoMarqueeControl` dostupná pro výběr.

11. Přetáhněte instanci `DemoMarqueeControl` na návrhovou plochu **Form1** .

12. V obslužných rutinách `Start` `Stop` `DemoMarqueeControl`události volejte metody a na. <xref:System.Windows.Forms.Control.Click>

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

1. `MarqueeControlTest` Nastavte projekt jako spouštěný projekt a spusťte ho. Zobrazí se formulář, ve kterém se `DemoMarqueeControl`zobrazuje vaše. Kliknutím na tlačítko **Start** spustíte animaci. Mělo by se zobrazit blikání textu a indikátory pohybu kolem ohraničení.

## <a name="next-steps"></a>Další kroky

`MarqueeControlLibrary` Ukazuje jednoduchou implementaci vlastních ovládacích prvků a přidružených návrhářů. Tuto ukázku můžete udělat několika způsoby:

- Změňte hodnoty `DemoMarqueeControl` vlastností v návrháři. Chcete- `MarqueBorder` li vytvořit vnořený efekt, přidejte další ovládací prvky a ukotvěte je Dock v rámci jejich nadřazených instancí. Experimentujte s různými nastaveními `UpdatePeriod` pro a vlastnosti související s osvětlením.

- Vytvořte vlastní implementace `IMarqueeWidget`. Mohli byste například vytvořit Flash "Neon Sign" nebo animované znaménko s více obrázky.

- Dále upravte prostředí pro dobu návrhu. Můžete zkusit vytvořit stín více vlastností než <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A>a můžete přidat nové vlastnosti. Přidejte nové příkazy návrháře, abyste zjednodušili běžné úkoly, jako je například ukotvení podřízených ovládacích prvků.

- `MarqueeControl`Licenci. Další informace najdete v tématu [jak: Licenční komponenty a ovládací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))prvky.

- Určuje, jak jsou ovládací prvky serializovány a jak jsou pro ně generovány kódy. Další informace naleznete v tématu [generování a kompilace dynamického zdrojového kódu](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- [Postupy: Vytvoření model Windows Formsho ovládacího prvku, který bude využívat funkce pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
- [Rozšíření podpory pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Vlastní návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))
