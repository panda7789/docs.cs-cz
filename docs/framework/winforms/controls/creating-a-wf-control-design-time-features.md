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
ms.openlocfilehash: 4d741beffa5649d1d1593ba3dbb7a1918b669b80
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882321"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu

Možnosti času návrhu pro vlastní ovládací prvek může taková instalace vylepšit pro vytváření přidružený vlastní designer.

Tento návod ukazuje, jak vytvořit vlastního návrháře pro vlastní ovládací prvek. Budete implementovat `MarqueeControl` typu a přidružené návrháře třídy, nazvané `MarqueeControlRootDesigner`.

`MarqueeControl` Typ implementuje podobný výběr celé obrazovky, s animovaný světla a blikající text zobrazení.

Návrhář pro tento ovládací prvek komunikuje s prostředím návrhu poskytnout vlastní možnosti času návrhu. Vlastní návrháři, můžete sestavit vlastní `MarqueeControl` implementaci animovaný světla a blikající text v mnoha kombinace. Můžete použít deskách ovládací prvek ve formuláři jako jakýkoli jiný ovládací prvek Windows Forms.

Úlohy v tomto návodu zahrnují:

- Vytvoření projektu

- Vytvoření projektu knihovny ovládacích prvků

- Odkazování na projekt vlastního ovládacího prvku

- Definování vlastního ovládacího prvku a jeho vlastní návrháři

- Vytvoření Instance vlastního ovládacího prvku

- Nastavení projektu pro ladění v době návrhu

- Implementace vlastního ovládacího prvku

- Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek

- Vytvoření MarqueeBorder podřízený ovládací prvek

- Vytvoření vlastního návrháře a stínové vlastnosti filtru

- Zpracování změny součásti

- Příkazy návrháře přidání do vlastního návrháře

- Vytvoření vlastního editoru UITypeEditor.

- Testování vlastní ovládací prvek v Návrháři

Až budete hotovi, vaše vlastní ovládací prvek bude vypadat podobně jako následující:

![Aplikaci zobrazující výběr říká Text a spouštění a zastavování tlačítka.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

Výpis úplného kódu naleznete v tématu [jak: Vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat Visual Studio.

## <a name="creating-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu aplikace. Tento projekt bude používat k sestavení aplikace, který je hostitelem vlastního ovládacího prvku.

Otevřete Visual Studio a vytvořte projekt Formulářové aplikace Windows s názvem "MarqueeControlTest" (**souboru** > **nový** > **projektu**  >  **Visual C#**  nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaciWindowsForms**).

## <a name="creating-a-control-library-project"></a>Vytvoření projektu knihovny ovládacích prvků

Dalším krokem je vytvoření projektu knihovny ovládacích prvků. Vytvořte nový vlastní ovládací prvek a jeho odpovídající vlastní návrháře.

### <a name="to-create-the-control-library-project"></a>Vytvoření projektu knihovny ovládacích prvků

1. Přidáte do řešení projekt Knihovna ovládacích prvků formulářů Windows. Pojmenujte projekt "MarqueeControlLibrary."

2. Pomocí **Průzkumníka řešení**, odstraňte výchozí ovládací prvek projektu tak, že odstraníte zdrojový soubor s názvem "UserControl1.cs" nebo "UserControl1.vb", v závislosti na vámi zvolený jazyk. Další informace najdete v tématu [jak: Odebrat, odstranit a vyloučit položky](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).

3. Přidat nový <xref:System.Windows.Forms.UserControl> položkou `MarqueeControlLibrary` projektu. Zadejte nový zdrojový soubor základní název typu "MarqueeControl."

4. Pomocí **Průzkumníka řešení**, vytvořte novou složku v `MarqueeControlLibrary` projektu. Další informace najdete v tématu [jak: Přidání nových položek projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)). Název nové složky "Návrhu."

5. Klikněte pravým tlačítkem myši **návrhu** složky a přidejte novou třídu. Zadejte zdrojový soubor základní název "MarqueeControlRootDesigner."

6. Budete muset používat typy ze sestavení System.Design, proto přidat tento odkaz `MarqueeControlLibrary` projektu.

    > [!NOTE]
    > Použití sestavení System.Design, musí váš projekt cílit na plnou verzi rozhraní .NET Framework není rozhraní .NET Framework Client Profile. Chcete-li změnit cílovou architekturu, [jak: Cílení na určitou verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

## <a name="referencing-the-custom-control-project"></a>Odkazování na projekt vlastního ovládacího prvku

Budete používat `MarqueeControlTest` projekt k testování vlastního ovládacího prvku. Projekt testů dozví o vlastní ovládací prvek přidáte odkaz na projekt `MarqueeControlLibrary` sestavení.

### <a name="to-reference-the-custom-control-project"></a>Chcete-li odkazovat na projekt, vlastní ovládací prvek

- V `MarqueeControlTest` projektu, přidejte odkaz na projekt `MarqueeControlLibrary` sestavení. Nezapomeňte použít **projekty** kartu **přidat odkaz** dialogové okno namísto odkazování `MarqueeControlLibrary` sestavení přímo.

## <a name="defining-a-custom-control-and-its-custom-designer"></a>Definování vlastního ovládacího prvku a jeho vlastní návrháři
 Vlastní ovládací prvek bude odvozovat <xref:System.Windows.Forms.UserControl> třídy. Díky tomu váš ovládací prvek obsahující další ovládací prvky a navíc nabízí spoustu výchozí funkce ovládacího prvku.

 Vlastní ovládací prvek bude mít přidružený vlastní designer. To umožňuje vytvořit jedinečný návrhové prostředí navržených speciálně pro vlastní ovládací prvek.

 Přidružte ovládací prvek pomocí jeho návrháře pomocí <xref:System.ComponentModel.DesignerAttribute> třídy. Vzhledem k tomu, že vyvíjíte celý chování vlastního ovládacího prvku v době návrhu, se implementovat vlastní návrháře <xref:System.ComponentModel.Design.IRootDesigner> rozhraní.

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Chcete-li definovat vlastní ovládací prvek a jeho vlastní návrháři

1. Otevřít `MarqueeControl` zdrojový soubor v **Editor kódu**. V horní části souboru importujte následující obory názvů:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. Přidat <xref:System.ComponentModel.DesignerAttribute> k `MarqueeControl` deklarace třídy. Tento návrhář přidruží vlastního ovládacího prvku.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. Otevřít `MarqueeControlRootDesigner` zdrojový soubor v **Editor kódu**. V horní části souboru importujte následující obory názvů:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. Změňte deklaraci `MarqueeControlRootDesigner` dědit z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy. Použít <xref:System.ComponentModel.ToolboxItemFilterAttribute> k určení návrháře interakci s **nástrojů**.

     **Poznámka:** definice `MarqueeControlRootDesigner` třídy byl uzavřený do obor názvů s názvem "MarqueeControlLibrary.Design." Toto prohlášení umístí návrháře speciální oboru názvů vyhrazený pro typy související s návrhem.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. Definovat konstruktor pro `MarqueeControlRootDesigner` třídy. Vložit <xref:System.Diagnostics.Trace.WriteLine%2A> příkaz v těle konstruktoru. To bude hodit pro účely ladění.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="creating-an-instance-of-your-custom-control"></a>Vytvoření Instance vlastního ovládacího prvku
 Sledovat vlastní chování ovládacího prvku v době návrhu, umístí instance ovládacího prvku na formulář v nástrojích pro `MarqueeControlTest` projektu.

### <a name="to-create-an-instance-of-your-custom-control"></a>K vytvoření instance vlastního ovládacího prvku

1. Přidat nový <xref:System.Windows.Forms.UserControl> položkou `MarqueeControlTest` projektu. Zadejte nový zdrojový soubor základní název "DemoMarqueeControl."

2. Otevřít `DemoMarqueeControl` soubor **Editor kódu**. V horní části souboru, importovat `MarqueeControlLibrary` obor názvů:

```vb
Imports MarqueeControlLibrary
```

```csharp
using MarqueeControlLibrary;
```

1. Změňte deklaraci `DemoMarqueeControl` dědit z `MarqueeControl` třídy.

2. Sestavte projekt.

3. Otevřít `Form1` v Návrháři formulářů Windows.

4. Najít **MarqueeControlTest součásti** kartu **nástrojů** a otevřete ho. Přetáhněte `DemoMarqueeControl` z **nástrojů** do formuláře.

5. Sestavte projekt.

## <a name="setting-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu

Pokud vyvíjíte vlastní možnosti času návrhu, bude potřeba ladění ovládacích prvků a komponent. Neexistuje jednoduchý způsob, jak nastavení projektu pro povolení ladění v době návrhu. Další informace najdete v tématu [názorný postup: Ovládací prvky ladění vlastního Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).

### <a name="to-set-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu

1. Klikněte pravým tlačítkem myši `MarqueeControlLibrary` projektu a vyberte **vlastnosti**.

2. V dialogovém okně "Stránky vlastností MarqueeControlLibrary" vyberte **ladění** stránky.

3. V **spustit akci** vyberte **spustit externí Program**. Bude ladění samostatnou instanci sady Visual Studio, proto klikněte na symbol tří teček (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) tlačítko Procházet pro Visual Studio IDE. Název spustitelného souboru devenv.exe, a pokud jste nainstalovali do výchozího umístění, její cesta 9.0\Common7\IDE\devenv.exe %programfiles%\Microsoft Visual Studio.

4. Kliknutím na OK zavřete dialogové okno.

5. Klikněte pravým tlačítkem myši `MarqueeControlLibrary` projektu a vyberte "Nastavit jako spouštěný projekt" Povolit této konfiguraci ladění.

## <a name="checkpoint"></a>CheckPoint

Nyní jste připraveni k ladění chování návrhu vlastního ovládacího prvku. Jakmile určíte, že je správně nastavené ladicího prostředí budete testovat přidružení mezi vlastního ovládacího prvku a vlastního návrháře.

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>K testování ladicí prostředí a návrháře přidružení

1. Otevřít `MarqueeControlRootDesigner` zdrojový soubor v **Editor kódu** a umístit zarážky na <xref:System.Diagnostics.Trace.WriteLine%2A> příkazu.

2. Stisknutím klávesy F5 pro spuštění relace ladění. Všimněte si, že je vytvořena nová instance sady Visual Studio.

3. V nové instanci sady Visual Studio otevřete řešení "MarqueeControlTest". Řešení můžete snadno vyhledat tak, že vyberete **posledních projektů** z **souboru** nabídky. Soubor řešení "MarqueeControlTest.sln", bude uveden jako naposledy použitých souborů.

4. Otevřít `DemoMarqueeControl` v návrháři. Všimněte si, že instanci ladění aplikace Visual Studio získá fokus a provádění zastaví na zarážku. Stisknutím klávesy F5 pokračovat v relaci ladění.

V tomto okamžiku všechno, co je v místo, kde můžete k vývoji a ladění vlastního ovládacího prvku a jeho přidružený vlastní designer. Zbývající část tohoto návodu bude soustředit se na podrobnosti implementace funkce ovládacího prvku a návrháře.

## <a name="implementing-your-custom-control"></a>Implementace vlastního ovládacího prvku

`MarqueeControl` Je <xref:System.Windows.Forms.UserControl> stačí nepatrné přizpůsobení. Poskytuje dvě metody: `Start`, která spustí animace běžícího textu a `Stop`, které zastaví animace. Protože `MarqueeControl` obsahuje podřízené ovládací prvky, které implementují `IMarqueeWidget` rozhraní, `Start` a `Stop` výčet každé podřízené ovládací prvky a volání `StartMarquee` a `StopMarquee` metody, v uvedeném pořadí, na všechny podřízené ovládací prvky který implementuje `IMarqueeWidget`.

Vzhled `MarqueeBorder` a `MarqueeText` ovládacích prvků je závislé na rozložení, tak `MarqueeControl` přepsání <xref:System.Windows.Forms.Control.OnLayout%2A> metoda a volání <xref:System.Windows.Forms.Control.PerformLayout%2A> na podřízené ovládací prvky tohoto typu.

Toto je rozsah `MarqueeControl` vlastní nastavení. Běhové funkce jsou implementované `MarqueeBorder` a `MarqueeText` ovládací prvky a funkce návrhu jsou implementované `MarqueeBorderDesigner` a `MarqueeControlRootDesigner` třídy.

### <a name="to-implement-your-custom-control"></a>Pro implementaci vlastního ovládacího prvku

1. Otevřít `MarqueeControl` zdrojový soubor v **Editor kódu**. Implementace `Start` a `Stop` metody.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. Přepsat <xref:System.Windows.Forms.Control.OnLayout%2A> metody.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="creating-a-child-control-for-your-custom-control"></a>Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek

`MarqueeControl` Bude hostovat dva druhy podřízeného ovládacího prvku: `MarqueeBorder` ovládacího prvku a `MarqueeText` ovládacího prvku.

- `MarqueeBorder`: Tento ovládací prvek vykreslí ohraničení "světla" kolem okraje. Indikátory flash v pořadí, takže se budou zobrazovat Přesun celého ohraničení. Rychlost, jakou světel flash řídí vlastnost s názvem `UpdatePeriod`. Několik dalších vlastních vlastností určují další aspekty vzhledu ovládacího prvku. Dvě metody volá `StartMarquee` a `StopMarquee`, řídit, kdy animace spouští a zastavuje.

- `MarqueeText`: Tento ovládací prvek vykreslí blikající řetězec. Podobně jako `MarqueeBorder` ovládacího prvku, rychlost, jakou začne blikat text je řízena `UpdatePeriod` vlastnost. `MarqueeText` Ovládací prvek má také `StartMarquee` a `StopMarquee` metody společně s `MarqueeBorder` ovládacího prvku.

V době návrhu `MarqueeControlRootDesigner` umožňuje typy těchto dvou ovládacích prvků mají být přidány do `MarqueeControl` v libovolné kombinaci.

Společné funkce dvou ovládacích prvků se promítnou do rozhraní volá `IMarqueeWidget`. Díky tomu `MarqueeControl` zjišťovat všechny Marquee související podřízené ovládací prvky a udělit jim zvláštní zacházení.

K implementaci funkce pravidelné animace, budete používat <xref:System.ComponentModel.BackgroundWorker> objekty z <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů. Můžete použít <xref:System.Windows.Forms.Timer> objekty, ale po mnoho `IMarqueeWidget` objekty jsou k dispozici, jedno vlákno uživatelského rozhraní, možná nebudete moct držet krok s animace.

### <a name="to-create-a-child-control-for-your-custom-control"></a>Chcete-li vytvořit podřízeného ovládacího prvku pro vlastní ovládací prvek

1. Přidat novou položku třídy a `MarqueeControlLibrary` projektu. Zadejte nový zdrojový soubor základní název "IMarqueeWidget."

2. Otevřít `IMarqueeWidget` zdrojový soubor v **Editor kódu** a změnit deklarace z `class` k `interface`:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. Přidejte následující kód, který `IMarqueeWidget` rozhraní ke zveřejnění dvě metody a vlastnosti, která manipulovat s animace běžícího textu:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. Přidat nový **vlastní ovládací prvek** položkou `MarqueeControlLibrary` projektu. Zadejte nový zdrojový soubor základní název "MarqueeText."

5. Přetáhněte <xref:System.ComponentModel.BackgroundWorker> z **nástrojů** do vaší `MarqueeText` ovládacího prvku. Tato součást vám umožní `MarqueeText` ovládací prvek aktualizovalo samo asynchronně.

6. V okně Vlastnosti nastavte <xref:System.ComponentModel.BackgroundWorker> komponenty `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastností `true`. Tato nastavení umožňují <xref:System.ComponentModel.BackgroundWorker> komponenty pravidelně zvýšit <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí a zrušení asynchronní aktualizace. Další informace najdete v tématu [BackgroundWorker – komponenta](backgroundworker-component.md).

7. Otevřít `MarqueeText` zdrojový soubor v **Editor kódu**. V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. Změňte deklaraci `MarqueeText` dědit z <xref:System.Windows.Forms.Label> a provádět `IMarqueeWidget` rozhraní:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. Deklarujte proměnné instance, které odpovídají vystavené vlastnosti a inicializace v konstruktoru. `isLit` Pole určuje, zda text je nutné překreslit barevně dána `LightColor` vlastnost.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. Implementujte rozhraní `IMarqueeWidget`.

    `StartMarquee` a `StopMarquee` vyvolání metody <xref:System.ComponentModel.BackgroundWorker> komponenty <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metod ke spuštění a ukončení animace.

    <xref:System.ComponentModel.CategoryAttribute.Category%2A> a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> atributy jsou použity `UpdatePeriod` vlastnost, aby se zobrazovalo ve vlastní části okna Vlastnosti volá "Marquee."

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. Implementujte přistupující objekty vlastnosti. Bude vystavovat dvě vlastnosti do klientů: `LightColor` a `DarkColor`. <xref:System.ComponentModel.CategoryAttribute.Category%2A> a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> atributy jsou použity tyto vlastnosti, takže vlastnosti se zobrazí v části vlastní okna Vlastnosti volá "Marquee."

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. Implementace obslužné rutiny <xref:System.ComponentModel.BackgroundWorker> komponenty <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události.

    <xref:System.ComponentModel.BackgroundWorker.DoWork> Počet milisekund, po prodlevě obslužná rutina události `UpdatePeriod` poté vyvolá <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události, dokud váš kód přestane animace voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Obslužná rutina události přepíná mezi stavu světlé a tmavé vzhled blikat text.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. Přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> způsob povolení animace.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. Sestavte řešení stisknutím klávesy F6.

## <a name="create-the-marqueeborder-child-control"></a>Vytvoření MarqueeBorder podřízený ovládací prvek

`MarqueeBorder` Je o něco složitější než ovládací prvek `MarqueeText` ovládacího prvku. Obsahuje více vlastností a animace v <xref:System.Windows.Forms.Control.OnPaint%2A> metoda je složitější. V zásadě je podobný tomu `MarqueeText` ovládacího prvku.

Vzhledem k tomu, `MarqueeBorder` ovládací prvek může mít podřízené ovládací prvky, musí se jednat o seznámen <xref:System.Windows.Forms.Control.Layout> události.

### <a name="to-create-the-marqueeborder-control"></a>Vytvoření ovládacího prvku MarqueeBorder

1. Přidat nový **vlastní ovládací prvek** položkou `MarqueeControlLibrary` projektu. Zadejte nový zdrojový soubor základní název "MarqueeBorder."

2. Přetáhněte <xref:System.ComponentModel.BackgroundWorker> z **nástrojů** do vaší `MarqueeBorder` ovládacího prvku. Tato součást vám umožní `MarqueeBorder` ovládací prvek aktualizovalo samo asynchronně.

3. V okně Vlastnosti nastavte <xref:System.ComponentModel.BackgroundWorker> komponenty `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastností `true`. Tato nastavení umožňují <xref:System.ComponentModel.BackgroundWorker> komponenty pravidelně zvýšit <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí a zrušení asynchronní aktualizace. Další informace najdete v tématu [BackgroundWorker – komponenta](backgroundworker-component.md).

4. V okně Vlastnosti klikněte na tlačítko události. Připojte obslužné rutiny pro <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události.

5. Otevřít `MarqueeBorder` zdrojový soubor v **Editor kódu**. V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. Změňte deklaraci `MarqueeBorder` dědit z <xref:System.Windows.Forms.Panel> a provádět `IMarqueeWidget` rozhraní.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. Deklarace výčtů dvě pro správu `MarqueeBorder` stav ovládacího prvku: `MarqueeSpinDirection`, který určuje směr, ve kterém světel "dokola" ohraničení, a `MarqueeLightShape`, která určuje tvar světla (čtvereček nebo cyklické). Tato deklarace před umístit `MarqueeBorder` deklarace třídy.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. Deklarujte proměnné instance, které odpovídají vystavené vlastnosti a inicializace v konstruktoru.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. Implementujte rozhraní `IMarqueeWidget`.

    `StartMarquee` a `StopMarquee` vyvolání metody <xref:System.ComponentModel.BackgroundWorker> komponenty <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metod ke spuštění a ukončení animace.

    Vzhledem k tomu, `MarqueeBorder` ovládacího prvku může obsahovat podřízené ovládací prvky, `StartMarquee` metoda výčet všech podřízených ovládacích prvků a volání `StartMarquee` na ty, které implementují `IMarqueeWidget`. `StopMarquee` Metoda má podobné implementace.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. Implementujte přistupující objekty vlastnosti. `MarqueeBorder` Ovládací prvek má několik vlastností pro řízení její vzhled.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. Implementace obslužné rutiny <xref:System.ComponentModel.BackgroundWorker> komponenty <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události.

    <xref:System.ComponentModel.BackgroundWorker.DoWork> Počet milisekund, po prodlevě obslužná rutina události `UpdatePeriod` poté vyvolá <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události, dokud váš kód přestane animace voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Zvýší pozice indikátor "základní", ze kterého je určen stav světlý/tmavý další indikátory, a volá obslužná rutina události <xref:System.Windows.Forms.Control.Refresh%2A> metoda způsobit repaint samotný ovládací prvek.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. Implementace pomocných metod `IsLit` a `DrawLight`.

    `IsLit` Metody určuje barvy světla na dané pozici. Světla, které jsou "lit" vykresleny barvou dána `LightColor` vlastnost a ty, které jsou "tmavě" jsou vykreslovány vedle barevně dána `DarkColor` vlastnost.

    `DrawLight` Metoda vykreslí světla odpovídající barvou, tvar a pozici.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. Přepsat <xref:System.Windows.Forms.Control.OnLayout%2A> a <xref:System.Windows.Forms.Control.OnPaint%2A> metody.

    <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda vykreslí světla podél okrajů `MarqueeBorder` ovládacího prvku.

    Vzhledem k tomu, <xref:System.Windows.Forms.Control.OnPaint%2A> metoda závisí na velikosti `MarqueeBorder` ovládací prvek, musíte ji volat pokaždé, když se změní rozložení. Za tím účelem přepsání <xref:System.Windows.Forms.Control.OnLayout%2A> a volat <xref:System.Windows.Forms.Control.Refresh%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>Vytvoření vlastního návrháře a stínové vlastnosti filtru

`MarqueeControlRootDesigner` Třída poskytuje implementaci pro Návrhář kořenových aktivit. Kromě tohoto návrháře, který pracuje `MarqueeControl`, budete potřebovat vlastní návrháře, který je speciálně přidružený `MarqueeBorder` ovládacího prvku. Tento návrhář obsahuje vlastní chování, které je vhodné v rámci vlastní kořenového návrháře.

Konkrétně `MarqueeBorderDesigner` "stínové", který se určité vlastnosti vyfiltrujte `MarqueeBorder` ovládacího prvku, změna jejich interakce s prostředím návrhu.

Zachycení volání přistupující objekt vlastnosti komponenty se označuje jako "stínováním." Umožňuje sledovat hodnotu nastavenou uživatelem designeru a volitelně předat tuto hodnotu na komponentu navržen.

V tomto příkladu <xref:System.Windows.Forms.Control.Visible%2A> a <xref:System.Windows.Forms.Control.Enabled%2A> vlastnosti se stínovaný podle `MarqueeBorderDesigner`, což zabrání uživateli v provádění `MarqueeBorder` ovládací prvek neviditelný nebo zakázaný v době návrhu.

Návrháři můžete také přidávat a odebírat vlastnosti. V tomto příkladu <xref:System.Windows.Forms.Control.Padding%2A> vlastnost bude odebrána v době návrhu, protože `MarqueeBorder` řízení prostřednictvím kódu programu nastavuje výplň na základě velikosti světla určené `LightSize` vlastnost.

Základní třída pro `MarqueeBorderDesigner` je <xref:System.ComponentModel.Design.ComponentDesigner>, který má metody, které můžete změnit atributy, vlastnosti a události, které jsou vystavené ovládací prvek v době návrhu:

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

Při změně veřejné rozhraní komponenty pomocí těchto metod, musí dodržovat tato pravidla:

- Přidat nebo odebrat položky `PreFilter` pouze metody

- Upravit existující položky v `PostFilter` pouze metody

- Vždy nejprve volat základní implementaci `PreFilter` metody

- Vždy volat základní implementaci poslední `PostFilter` metody

Týkajícími se tato pravidla zajišťuje, že všechny návrháře v prostředí návrhu mají konzistentní zobrazení všech součástí navržen.

<xref:System.ComponentModel.Design.ComponentDesigner> Třída obsahuje slovník pro správu hodnoty stínové vlastnosti, které která vás zbaví nutnosti vytvářet konkrétní instanci proměnné.

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Vytvoření vlastního návrháře na stínové a filtrovat vlastnosti

1. Klikněte pravým tlačítkem myši **návrhu** složky a přidejte novou třídu. Zadejte zdrojový soubor základní název "MarqueeBorderDesigner."

2. Otevřít `MarqueeBorderDesigner` zdrojový soubor v **Editor kódu**. V horní části souboru importujte následující obory názvů:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. Změňte deklaraci `MarqueeBorderDesigner` dědit z <xref:System.Windows.Forms.Design.ParentControlDesigner>.

    Vzhledem k tomu, `MarqueeBorder` ovládacího prvku může obsahovat podřízené ovládací prvky, `MarqueeBorderDesigner` dědí z <xref:System.Windows.Forms.Design.ParentControlDesigner>, která zpracovává interakce nadřazený podřízený.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. Přepsat základní implementaci <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. Implementace <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A> vlastnosti. Tato implementace stínové vlastnosti ovládacího prvku.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handling-component-changes"></a>Zpracování změny součásti
 `MarqueeControlRootDesigner` Třída poskytuje vlastní návrhové prostředí pro vaše `MarqueeControl` instancí. Většinu funkcí návrhu je zděděno od <xref:System.Windows.Forms.Design.DocumentDesigner> třída; se vašeho kódu implementovat úpravami dva: zpracování změny součásti a přidání příkazy návrháře.

 Uživatelé návrhu jejich `MarqueeControl` instancí, váš Návrhář kořenových aktivit budou sledovat změny `MarqueeControl` a jeho podřízených ovládacích prvků. Návrhové prostředí nabízí pohodlný služby <xref:System.ComponentModel.Design.IComponentChangeService>pro sledování se změní na stav součásti.

 Získat odkaz na tuto službu prostředí s dotazem <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> metody. Pokud je dotaz úspěšný, návrháře připojit obslužné rutiny pro <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> události a provádět libovolné kroky je třeba udržovat konzistentní stav v době návrhu.

 V případě třídy `MarqueeControlRootDesigner` třídu bude volat <xref:System.Windows.Forms.Control.Refresh%2A> metodu na každý `IMarqueeWidget` obsažen v objektu `MarqueeControl`. To způsobí, že `IMarqueeWidget` objektu samotného při vlastnosti svého nadřazeného objektu, jako jsou odpovídajícím způsobem repaint <xref:System.Windows.Forms.Control.Size%2A> se změní.

### <a name="to-handle-component-changes"></a>Pro případ změn komponenty

1. Otevřít `MarqueeControlRootDesigner` zdrojový soubor v **Editor kódu** a přepsat <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metody. Volat základní implementaci <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> a dotázat <xref:System.ComponentModel.Design.IComponentChangeService>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. Implementace <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> obslužné rutiny události. Test typ odeslání součásti, a pokud se jedná `IMarqueeWidget`, volání jeho <xref:System.Windows.Forms.Control.Refresh%2A> – metoda.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="adding-designer-verbs-to-your-custom-designer"></a>Příkazy návrháře přidání do vlastního návrháře

Návrháře příkaz je příkaz nabídky propojené s obslužnou rutinu události. Příkazy návrháře se přidají do komponenty nabídku v době návrhu. Další informace naleznete v tématu <xref:System.ComponentModel.Design.DesignerVerb>.

Ať už přidáte dva příkazy návrháře: **Spustit Test** a **zastavení testu**. Tato operace vám umožní zobrazit chování za běhu `MarqueeControl` v době návrhu. Tyto příkazy se přidají do `MarqueeControlRootDesigner`.

Když **spustit Test** je vyvolána, příkaz obslužná rutina události zavolá `StartMarquee` metodu na `MarqueeControl`. Když **zastavit testovací** je vyvolána, příkaz obslužná rutina události zavolá `StopMarquee` metodu na `MarqueeControl`. Provádění `StartMarquee` a `StopMarquee` metody volat tyto metody pro obsažené ovládací prvky, které implementují `IMarqueeWidget`, takže omezením `IMarqueeWidget` ovládací prvky se také účastní testu.

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Příkazy návrháře přidat do vlastní návrháři

1. V `MarqueeControlRootDesigner` třídy, přidejte obslužné rutiny události s názvem `OnVerbRunTest` a `OnVerbStopTest`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. Připojení těchto obslužných rutin událostí k jejich odpovídající příkazy návrháře. `MarqueeControlRootDesigner` dědí <xref:System.ComponentModel.Design.DesignerVerbCollection> ze své základní třídy. Vytvoříte dvě nové <xref:System.ComponentModel.Design.DesignerVerb> objekty a přidat je do této kolekce v <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metody.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="creating-a-custom-uitypeeditor"></a>Vytvoření vlastního editoru UITypeEditor.

Při vytváření vlastního návrhu prostředí pro uživatele, je často žádoucí, vytvořte vlastní interakci se v okně Vlastnosti. Můžete to udělat tak, že vytvoříte <xref:System.Drawing.Design.UITypeEditor>. Další informace najdete v tématu [jak: Vytvoření editoru typů uživatelského rozhraní](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120)).

`MarqueeBorder` Ovládacího prvku poskytuje několik vlastností v okně Vlastnosti. Dva z těchto vlastností `MarqueeSpinDirection` a `MarqueeLightShape` jsou reprezentovány výčty. Pro ilustraci použití Editoru typů uživatelského rozhraní, `MarqueeLightShape` vlastnost bude mít přiřazený <xref:System.Drawing.Design.UITypeEditor> třídy.

### <a name="to-create-a-custom-ui-type-editor"></a>Chcete-li vytvořit vlastní typ uživatelského rozhraní editoru

1. Otevřít `MarqueeBorder` zdrojový soubor v **Editor kódu**.

2. V definici `MarqueeBorder` třídy, deklarujte třídu s názvem `LightShapeEditor` , která je odvozena z <xref:System.Drawing.Design.UITypeEditor>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. Deklarovat <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance proměnné s názvem `editorService`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. Přepsat <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metody. Tato implementace vrátí <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, který informuje návrhové prostředí, jak má zobrazit `LightShapeEditor`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. Přepsat <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metody. Tato implementace dotazuje návrhové prostředí pro <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> objektu. Pokud úspěšné, vytvoří `LightShapeSelectionControl`. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Je vyvolána metoda pro spuštění `LightShapeEditor`. Hodnota vrácená z toto volání se vrátí do vývojového prostředí.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>Vytvoření ovládacího prvku zobrazení pro vaše vlastní editor UITypeEditor

1. `MarqueeLightShape` Vlastnost podporuje dva typy světla tvarů: `Square` a `Circle`. Můžete vytvořit vlastní ovládací prvek používat výhradně pro účely graficky zobrazení tyto hodnoty v okně Vlastnosti. Budou používat tento vlastní ovládací prvek vaše <xref:System.Drawing.Design.UITypeEditor> pracovat v okně Vlastnosti.

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Chcete-li vytvořit ovládací prvek zobrazení pro vaše vlastní uživatelské rozhraní editoru typů

1. Přidat nový <xref:System.Windows.Forms.UserControl> položkou `MarqueeControlLibrary` projektu. Zadejte nový zdrojový soubor základní název "LightShapeSelectionControl."

2. Přetáhněte dva <xref:System.Windows.Forms.Panel> ovládacích prvků z **nástrojů** na `LightShapeSelectionControl`. Pojmenujte je `squarePanel` a `circlePanel`. Uspořádejte je vedle sebe. Nastavte <xref:System.Windows.Forms.Control.Size%2A> vlastnost objektu i <xref:System.Windows.Forms.Panel> ovládacích prvků do (60, 60). Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost `squarePanel` ovládací prvek (8, 10). Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost `circlePanel` ovládací prvek (80, 10). Nastavte <xref:System.Windows.Forms.Control.Size%2A> vlastnost `LightShapeSelectionControl` do (150, 80).

3. Otevřít `LightShapeSelectionControl` zdrojový soubor v **Editor kódu**. V horní části souboru, importovat <xref:System.Windows.Forms.Design?displayProperty=nameWithType> obor názvů:

```vb
Imports System.Windows.Forms.Design
```

```csharp
using System.Windows.Forms.Design;
```

1. Implementace <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí pro `squarePanel` a `circlePanel` ovládací prvky. Tyto metody volat <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> na konec vlastního <xref:System.Drawing.Design.UITypeEditor> relace úprav.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

2. Deklarovat <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance proměnné s názvem `editorService`.

```vb
Private editorService As IWindowsFormsEditorService
```

```csharp
private IWindowsFormsEditorService editorService;
```

1. Deklarace `MarqueeLightShape` instance proměnné s názvem `lightShapeValue`.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

2. V `LightShapeSelectionControl` konstruktoru, připojte <xref:System.Windows.Forms.Control.Click> obslužných rutin událostí k `squarePanel` a `circlePanel` ovládacích prvků <xref:System.Windows.Forms.Control.Click> události. Navíc definovat přetížení konstruktoru, který přiřazuje `MarqueeLightShape` hodnotu z prostředí návrhu tak, aby `lightShapeValue` pole.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

3. V <xref:System.ComponentModel.Component.Dispose%2A> metoda, odpojit <xref:System.Windows.Forms.Control.Click> obslužných rutin událostí.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

4. V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory** tlačítko. Otevřete soubor LightShapeSelectionControl.Designer.cs nebo LightShapeSelectionControl.Designer.vb a odeberte výchozí definice <xref:System.ComponentModel.Component.Dispose%2A> metody.

5. Implementace `LightShape` vlastnost.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

6. Přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Tato implementace nakreslí plný čtvereček a kruh. Vybrané hodnoty se budou rovněž zvýrazněna kreslením ohraničení kolem jeden tvar nebo druhé.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="testing-your-custom-control-in-the-designer"></a>Testování vlastní ovládací prvek v Návrháři

V tomto okamžiku můžete vytvořit `MarqueeControlLibrary` projektu. Testování vaší implementace tak, že vytvoříte ovládací prvek, který dědí z `MarqueeControl` třídy a používat ho ve formuláři.

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Chcete-li vytvořit vlastní implementaci typu MarqueeControl

1. Otevřít `DemoMarqueeControl` v Návrháři formulářů Windows. Tím se vytvoří instance `DemoMarqueeControl` zadejte a zobrazí jej v instanci `MarqueeControlRootDesigner` typu.

2. V **nástrojů**, otevřete **MarqueeControlLibrary součásti** kartu. Zobrazí se `MarqueeBorder` a `MarqueeText` ovládací prvky, které jsou k dispozici pro výběr.

3. Přetáhněte instance `MarqueeBorder` na ovládací prvek `DemoMarqueeControl` návrhovou plochu. Ukotvit to `MarqueeBorder` ovládacího prvku na nadřazený ovládací prvek.

4. Přetáhněte instance `MarqueeText` na ovládací prvek `DemoMarqueeControl` návrhovou plochu.

5. Sestavte řešení.

6. Klikněte pravým tlačítkem myši `DemoMarqueeControl` a z místní nabídky vyberte **spustit Test** možnosti spuštění animace. Klikněte na tlačítko **zastavit testovací** k ukončení animace.

7. Otevřít **Form1** v návrhovém zobrazení.

8. Umístěte dvě <xref:System.Windows.Forms.Button> ovládacích prvků na formuláři. Pojmenujte je `startButton` a `stopButton`a změnit <xref:System.Windows.Forms.Control.Text%2A> hodnot vlastností do **Start** a **Zastavit**v uvedeném pořadí.

9. Implementace <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí pro obě <xref:System.Windows.Forms.Button> ovládacích prvků.

10. V **nástrojů**, otevřete **MarqueeControlTest součásti** kartu. Zobrazí se `DemoMarqueeControl` k dispozici pro výběr.

11. Přetáhněte instance `DemoMarqueeControl` na **Form1** návrhovou plochu.

12. V <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí, vyvolat `Start` a `Stop` metody `DemoMarqueeControl`.

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

1. Nastavte `MarqueeControlTest` projekt jako spouštěný projekt a potom ho spusťte. Zobrazení formuláře se zobrazí vaše `DemoMarqueeControl`. Klikněte na tlačítko **Start** tlačítko pro spuštění animace. Měli byste vidět začne blikat text a světla přesouvat ohraničení.

## <a name="next-steps"></a>Další kroky

`MarqueeControlLibrary` Ukazuje jednoduchý provádění vlastní ovládací prvky a přidružené designeru. Složitější této ukázky můžete provést několika způsoby:

- Změňte hodnoty vlastností `DemoMarqueeControl` v návrháři. Přidat další `MarqueBorder` ovládací prvky, ukotvit je v rámci jejich nadřazené instance k vytvoření efektu vnořené. Experiment s různými nastaveními pro `UpdatePeriod` a vlastnosti související s světla.

- Vytváření vlastních implementací `IMarqueeWidget`. Můžete například vytvořit blikající "neon přihlášení" nebo znak animovaný s více bitových kopií.

- Dále přizpůsobte možnosti času návrhu. Můžete zkusit stínováním více vlastností než <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A>, a můžete přidat nové vlastnosti. Přidáte nové příkazy návrháře pro zjednodušení běžné úkoly jako ukotvení podřízených ovládacích prvků.

- Licence `MarqueeControl`. Další informace najdete v tématu [jak: Licencování komponent a ovládacích prvků](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).

- Řídíte způsob, jakým vaše ovládací prvky serializují a jak vytvořit kód pro ně. Další informace najdete v tématu [dynamické generování zdrojového kódu a kompilace](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- [Postupy: Vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu aplikace](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
- [Rozšíření podpory během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Vlastní návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))
