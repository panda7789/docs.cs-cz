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
ms.openlocfilehash: 10905df76f2b638c10b14c1dd8c181b9652ea963
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu
Možnosti návrhu vlastního ovládacího prvku se dá vylepšit vytvářením přidružený vlastní designer.  
  
 Tento návod ukazuje, jak vytvořit vlastní návrháře vlastního ovládacího prvku. Budete implementovat `MarqueeControl` typu a přidruženou třídu návrháře, názvem `MarqueeControlRootDesigner`.  
  
 `MarqueeControl` Typ implementuje podobná běžící kina text s animovaný indikátory a blikající text zobrazení.  
  
 Komunikuje se službou prostředí návrhu a poskytuje vlastní prostředí návrhu návrháře pro tento ovládací prvek. Pomocí vlastních návrháře můžete sestavit vlastní `MarqueeControl` implementace s animovaný indikátory a blikající text v počet kombinací. Můžete použít sestavený prvek na formuláři, stejně jako jakýkoli jiný ovládací prvek Windows Forms.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytvoření projektu  
  
-   Vytvoření projektu knihovny ovládacího prvku  
  
-   Odkazování na projekt vlastního ovládacího prvku  
  
-   Definování vlastní ovládací prvek a jeho vlastní návrháře  
  
-   Vytvoření Instance vlastního ovládacího prvku  
  
-   Nastavení projektu pro ladění v době návrhu  
  
-   Implementace vlastního ovládacího prvku  
  
-   Vytvoření ovládacího prvku podřízené pro váš vlastní ovládací prvek  
  
-   Vytvoření ovládacího prvku MarqueeBorder podřízené  
  
-   Vytváření vlastních návrháře stínové a vlastnosti filtru  
  
-   Zpracování změny součásti  
  
-   Přidání návrháře příkazy k vaší vlastní Designer  
  
-   Vytvoření vlastního editoru UITypeEditor.  
  
-   Testování vlastního ovládacího prvku v Návrháři  
  
 Jakmile budete hotovi, vlastní ovládací prvek bude vypadat podobně jako následující:  
  
 ![Možné uspořádání typu MarqueeControl](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "DemoMarqueeControl")  
  
 Výpis úplného kódu, najdete v části [postupy: vytvoření funkce systému Windows Forms ovládací prvek, trvá výhod z návrhu](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, budete potřebovat:  
  
-   Dostatečná oprávnění, abyste mohli vytvořit a spustit projekty aplikací Windows Forms v počítači, kde je nainstalován Visual Studio.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu aplikace. Tento projekt použije k vytvoření aplikace, který je hostitelem vlastního ovládacího prvku.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte projekt Formulářové aplikace Windows s názvem "MarqueeControlTest." Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
## <a name="creating-a-control-library-project"></a>Vytvoření projektu knihovny ovládacího prvku  
 Dalším krokem je vytvoření projektu knihovny ovládacího prvku. Vytvořte nové vlastní ovládací prvek a jeho odpovídající vlastní designer.  
  
#### <a name="to-create-the-control-library-project"></a>Vytvoření projektu knihovny ovládacího prvku  
  
1.  Přidejte projektu knihovny ovládacích prvků Windows Forms k řešení. Název projektu "MarqueeControlLibrary."  
  
2.  Pomocí **Průzkumníku**, odstraňte výchozí řízení projektu odstraněním zdrojového souboru s názvem "UserControl1.cs" nebo "UserControl1.vb", v závislosti na vámi zvolený jazyk. Další informace najdete v tématu [NIB: postupy: odebrání, odstranění a vyloučit položky](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
3.  Přidejte nový <xref:System.Windows.Forms.UserControl> položkou `MarqueeControlLibrary` projektu. Zadejte nový zdrojový soubor základní název typu "MarqueeControl".  
  
4.  Pomocí **Průzkumníku řešení**, vytvořte novou složku v `MarqueeControlLibrary` projektu. Další informace najdete v tématu [NIB: postupy: Přidání nové položky projektu](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce). Název nové složky "Návrhu."  
  
5.  Klikněte pravým tlačítkem myši **návrhu** složky a přidejte novou třídu. Zadejte zdrojový soubor základní název "MarqueeControlRootDesigner."  
  
6.  Budete muset použít typy ze sestavení System.Design, takže přidat tento odkaz na `MarqueeControlLibrary` projektu.  
  
    > [!NOTE]
    >  Pokud chcete používat sestavení System.Design, musí být projektu plnou verzi rozhraní .NET Framework, není profil klienta rozhraní .NET Framework. Chcete-li změnit cílový framework, [postupy: cílení na verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).  
  
## <a name="referencing-the-custom-control-project"></a>Odkazování na projekt vlastního ovládacího prvku  
 Budete používat `MarqueeControlTest` projektu pro testování vlastního ovládacího prvku. K testovacímu projektu bude vědět, vlastní ovládací prvek, když přidáte odkaz na projekt `MarqueeControlLibrary` sestavení.  
  
#### <a name="to-reference-the-custom-control-project"></a>Chcete-li projekt vlastního ovládacího prvku  
  
-   V `MarqueeControlTest` projekt, přidejte odkaz na projekt `MarqueeControlLibrary` sestavení. Nezapomeňte použít **projekty** ve **přidat odkaz na** dialogové okno místo odkazující na `MarqueeControlLibrary` sestavení přímo.  
  
## <a name="defining-a-custom-control-and-its-custom-designer"></a>Definování vlastní ovládací prvek a jeho vlastní návrháře  
 Vlastní ovládací prvek odvodí z <xref:System.Windows.Forms.UserControl> třídy. To umožňuje vaší řídit tak, aby obsahovala další ovládací prvky a poskytuje výrazně výchozí funkce vlastního ovládacího prvku.  
  
 Vlastní ovládací prvek bude mít přidružený vlastní designer. Umožňuje vytvořit jedinečný návrhu prostředí upravená speciálně pro vaše vlastní ovládací prvek.  
  
 Přidružení ovládacího prvku pomocí jeho návrháře pomocí <xref:System.ComponentModel.DesignerAttribute> třídy. Vzhledem k tomu, že vyvíjíte celý chování návrhu vlastního ovládacího prvku, bude implementovat vlastní návrháře <xref:System.ComponentModel.Design.IRootDesigner> rozhraní.  
  
#### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Chcete-li definovat vlastní ovládací prvek a jeho vlastní designer  
  
1.  Otevřete `MarqueeControl` zdrojový soubor v **Editor kódu**. V horní části souboru importujte následujících oborů názvů:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]  
  
2.  Přidat <xref:System.ComponentModel.DesignerAttribute> k `MarqueeControl` deklarace třídy. Tato vlastní ovládací prvek přidruží jeho designer.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]  
  
3.  Otevřete `MarqueeControlRootDesigner` zdrojový soubor v **Editor kódu**. V horní části souboru importujte následujících oborů názvů:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]  
  
4.  Změňte deklaraci `MarqueeControlRootDesigner` dědění z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy. Použít <xref:System.ComponentModel.ToolboxItemFilterAttribute> k určení návrháře interakci s **sada nástrojů**.  
  
     **Poznámka:** definici `MarqueeControlRootDesigner` třída má byla uzavřena v obor názvů s názvem "MarqueeControlLibrary.Design." Toto prohlášení umístí návrháře v oboru názvů speciální vyhrazené pro návrh související typy.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]  
  
5.  Definování v konstruktoru pro `MarqueeControlRootDesigner` třídy. Vložení <xref:System.Diagnostics.Trace.WriteLine%2A> příkaz v těle konstruktor. To bude hodit pro účely ladění.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]  
  
## <a name="creating-an-instance-of-your-custom-control"></a>Vytvoření Instance vlastního ovládacího prvku  
 Abyste mohli pozorovat chování vlastní návrhu ovládacího prvku, umístí instance ovládacího prvku na formuláři v `MarqueeControlTest` projektu.  
  
#### <a name="to-create-an-instance-of-your-custom-control"></a>K vytvoření instance vlastního ovládacího prvku  
  
1.  Přidejte nový <xref:System.Windows.Forms.UserControl> položkou `MarqueeControlTest` projektu. Pojmenujte nový zdrojový soubor základní služby "DemoMarqueeControl."  
  
2.  Otevřete `DemoMarqueeControl` v soubor **Editor kódu**. V horní části souboru, importujte `MarqueeControlLibrary` obor názvů:  
  
```vb  
Imports MarqueeControlLibrary  
```  
  
```csharp  
using MarqueeControlLibrary;  
```  
  
1.  Změňte deklaraci `DemoMarqueeControl` dědění z `MarqueeControl` třídy.  
  
2.  Sestavte projekt.  
  
3.  Otevřete `Form1` v Návrháři formulářů.  
  
4.  Najít **MarqueeControlTest součásti** ve **sada nástrojů** a otevřete ji. Přetáhněte `DemoMarqueeControl` z **sada nástrojů** do formuláře.  
  
5.  Sestavte projekt.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu  
 Při vývoji vlastní možnosti návrhu, bude potřeba k ladění ovládací prvky a součásti. Je jednoduchý způsob, jak nastavit projektu a povolit ladění v době návrhu. Další informace najdete v tématu [návod: ladění vlastních ovládacích prvků Windows Forms v době návrhu](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu  
  
1.  Klikněte pravým tlačítkem myši `MarqueeControlLibrary` projektu a vyberte **vlastnosti**.  
  
2.  V dialogovém okně "Stránky vlastností MarqueeControlLibrary" vyberte **ladění** stránky.  
  
3.  V **spustit akci** vyberte **spustit externí Program**. Bude ladění samostatné instanci sady Visual Studio, proto klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko procházení pro Visual Studio IDE. Název spustitelného souboru je devenv.exe, a pokud jste nainstalovali do výchozího umístění, jeho cesta je 9.0\Common7\IDE\devenv.exe %programfiles%\Microsoft Visual Studio.  
  
4.  Kliknutím na OK zavřete dialogové okno.  
  
5.  Klikněte pravým tlačítkem myši `MarqueeControlLibrary` projektu a vyberte možnost "Nastavit jako spouštěný projekt" Chcete-li povolit tuto konfiguraci ladění.  
  
## <a name="checkpoint"></a>Kontrolní bod  
 Nyní jste připraveni k ladění chování návrhu vlastního ovládacího prvku. Jakmile zjistíte, že ladění prostředí je nastavit správně, budete testovat přidružení mezi vlastního ovládacího prvku a vlastní návrháře.  
  
#### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>K testování ladění prostředí a návrháře přidružení  
  
1.  Otevřete `MarqueeControlRootDesigner` zdrojový soubor v **Editor kódu** a umístěte zarážku na <xref:System.Diagnostics.Trace.WriteLine%2A> příkaz.  
  
2.  Stisknutím klávesy F5 spusťte relaci ladění. Všimněte si, že je vytvořena nová instance sady Visual Studio.  
  
3.  V nové instanci sady Visual Studio otevřete řešení "MarqueeControlTest". Budete moci snadno najít řešení výběrem **poslední projekty** z **souboru** nabídky. Soubor řešení "MarqueeControlTest.sln" se objeví jako naposledy použitých souborů.  
  
4.  Otevřete `DemoMarqueeControl` v návrháři. Upozorňujeme, že ladění instanci sady Visual Studio získá fokus a spuštění zastaví na vaší zarážce. Stisknutím klávesy F5 pokračovat relaci ladění.  
  
 V tomto okamžiku všechno, co se vám při vývoji a ladění vlastního ovládacího prvku a jeho přidružený vlastní designer. Zbývající část tohoto návodu se zaměří na podrobnosti implementace funkce ovládacího prvku a návrháře.  
  
## <a name="implementing-your-custom-control"></a>Implementace vlastního ovládacího prvku  
 `MarqueeControl` Je <xref:System.Windows.Forms.UserControl> s chvilku přizpůsobení. Zpřístupňuje dvě metody: `Start`, který spustí animace běžícího textu a `Stop`, která zastaví animace. Protože `MarqueeControl` obsahuje podřízené ovládací prvky, které implementují `IMarqueeWidget` rozhraní, `Start` a `Stop` výčet každý podřízený ovládací prvek a volání `StartMarquee` a `StopMarquee` metody, v uvedeném pořadí, na všechny podřízené ovládací prvky která implementuje `IMarqueeWidget`.  
  
 Vzhled `MarqueeBorder` a `MarqueeText` ovládací prvky je závislý na rozložení, tak `MarqueeControl` přepsání <xref:System.Windows.Forms.Control.OnLayout%2A> metoda a volání <xref:System.Windows.Forms.Control.PerformLayout%2A> na podřízené ovládací prvky tohoto typu.  
  
 Jedná se rozsah `MarqueeControl` přizpůsobení. Běhové funkce jsou implementované `MarqueeBorder` a `MarqueeText` ovládací prvky a funkce návrhu jsou implementované `MarqueeBorderDesigner` a `MarqueeControlRootDesigner` třídy.  
  
#### <a name="to-implement-your-custom-control"></a>K implementaci vlastního ovládacího prvku  
  
1.  Otevřete `MarqueeControl` zdrojový soubor v **Editor kódu**. Implementace `Start` a `Stop` metody.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]  
  
2.  Přepsání <xref:System.Windows.Forms.Control.OnLayout%2A> metoda.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]  
  
## <a name="creating-a-child-control-for-your-custom-control"></a>Vytvoření ovládacího prvku podřízené pro váš vlastní ovládací prvek  
 `MarqueeControl` Bude hostitelem dva druhy podřízeného ovládacího prvku: `MarqueeBorder` řízení a `MarqueeText` ovládacího prvku.  
  
-   `MarqueeBorder`: Tento ovládací prvek vybarví ohraničení "světla" jeho okrajů. Indikátory flash v pořadí, aby se zobrazily jako možné manipulaci se ohraničení. Rychlost, jakou světla flash řídí vlastnost s názvem `UpdatePeriod`. Několik dalších vlastních vlastností určit další aspekty vzhledu ovládacího prvku. Dvě metody, nazývá `StartMarquee` a `StopMarquee`, řídit, kdy animace spuštění a zastavení.  
  
-   `MarqueeText`: Tento ovládací prvek vybarví blikající řetězec. Podobně jako `MarqueeBorder` řízení, se řídí rychlost, jakou text bliká `UpdatePeriod` vlastnost. `MarqueeText` Řízení má také `StartMarquee` a `StopMarquee` metody společně s `MarqueeBorder` ovládacího prvku.  
  
 V době návrhu `MarqueeControlRootDesigner` umožňuje tyto typy dvou ovládacích prvků mají být přidány do `MarqueeControl` v libovolné kombinace.  
  
 Běžné funkce dvou ovládacích prvků se promítnou do rozhraní nazvané `IMarqueeWidget`. Díky tomu `MarqueeControl` ke zjištění všech souvisejících výběr podřízených ovládacích prvků a jim poskytnout speciální zacházení.  
  
 Pokud chcete implementovat funkci pravidelné animace, budete používat <xref:System.ComponentModel.BackgroundWorker> objekty z <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů. Můžete použít <xref:System.Windows.Forms.Timer> objekty, ale po mnoho `IMarqueeWidget` dostupné objekty, nemusí být možné udržovat tempo s animace jednoho vlákna uživatelského rozhraní.  
  
#### <a name="to-create-a-child-control-for-your-custom-control"></a>Chcete-li vytvořit podřízený ovládací prvek pro váš vlastní ovládací prvek  
  
1.  Přidat novou položku – třída k `MarqueeControlLibrary` projektu. Pojmenujte nový zdrojový soubor základní služby "IMarqueeWidget."  
  
2.  Otevřete `IMarqueeWidget` zdrojový soubor v **Editor kódu** a změňte deklaraci ze `class` k `interface`:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]  
  
3.  Přidejte následující kód, který `IMarqueeWidget` rozhraní vystavit dvě metody a vlastnosti, která manipulaci s animace běžícího textu:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]  
  
4.  Přidejte nový **vlastní ovládací prvek** položkou `MarqueeControlLibrary` projektu. Pojmenujte nový zdrojový soubor základní služby "MarqueeText."  
  
5.  Přetáhněte <xref:System.ComponentModel.BackgroundWorker> součásti z **sada nástrojů** do vaší `MarqueeText` ovládacího prvku. Tato součást bude možné `MarqueeText` řízení sám aktualizoval asynchronně.  
  
6.  V okně vlastnosti nastavit <xref:System.ComponentModel.BackgroundWorker> součásti `WorkerReportsProgess` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti, které chcete `true`. Tato nastavení umožňují <xref:System.ComponentModel.BackgroundWorker> součást, kterou pravidelně vyvolat <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí a zrušit asynchronní aktualizace. Další informace najdete v tématu [BackgroundWorker – komponenta](../../../../docs/framework/winforms/controls/backgroundworker-component.md).  
  
7.  Otevřete `MarqueeText` zdrojový soubor v **Editor kódu**. V horní části souboru importujte následujících oborů názvů:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]  
  
8.  Změňte deklaraci `MarqueeText` dědění z <xref:System.Windows.Forms.Label> a implementovat `IMarqueeWidget` rozhraní:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]  
  
9. Deklarujte proměnné instance, které odpovídají vystavené vlastnosti a inicializace je v konstruktoru. `isLit` Pole určuje, zda text k se vykresluje v barvu poskytují `LightColor` vlastnost.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]  
  
10. Implementace `IMarqueeWidget` rozhraní.  
  
     `StartMarquee` a `StopMarquee` vyvolání metody <xref:System.ComponentModel.BackgroundWorker> součásti <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody spuštění a ukončení animace.  
  
     <xref:System.ComponentModel.CategoryAttribute.Category%2A> a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> atributy jsou použity `UpdatePeriod` vlastnost, zobrazí se v části vlastní okno Vlastnosti názvem "běžící text".  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]  
  
11. Implementace přístupových objektů vlastnost. Zveřejní dvě vlastnosti klientům: `LightColor` a `DarkColor`. <xref:System.ComponentModel.CategoryAttribute.Category%2A> a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> atributy jsou použity tyto vlastnosti, takže vlastnosti se zobrazí v části vlastní okno Vlastnosti názvem "běžící text".  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]  
  
12. Implementace obslužné rutiny <xref:System.ComponentModel.BackgroundWorker> součásti <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události.  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> Obslužné rutiny události v režimu spánku počet milisekund, `UpdatePeriod` poté vyvolá <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí, dokud kódu zastaví animace voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Obslužné rutiny události přepíná mezi stav světlým a tmavým umožnit vzhled blikat text.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]  
  
13. Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> způsob povolení animace.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]  
  
14. Stiskněte klávesu F6 sestavte řešení.  
  
## <a name="create-the-marqueeborder-child-control"></a>Vytvoření ovládacího prvku MarqueeBorder podřízené  
 `MarqueeBorder` Ovládací prvek je trochu složitější než `MarqueeText` ovládacího prvku. Obsahuje více vlastností a animace v <xref:System.Windows.Forms.Control.OnPaint%2A> metoda je složitější. V zásadě, je velmi podobný `MarqueeText` ovládacího prvku.  
  
 Protože `MarqueeBorder` řízení může mít podřízené ovládací prvky, musí se jednat o vědět <xref:System.Windows.Forms.Control.Layout> události.  
  
#### <a name="to-create-the-marqueeborder-control"></a>Vytvoření ovládacího prvku MarqueeBorder  
  
1.  Přidejte nový **vlastní ovládací prvek** položkou `MarqueeControlLibrary` projektu. Pojmenujte nový zdrojový soubor základní služby "MarqueeBorder."  
  
2.  Přetáhněte <xref:System.ComponentModel.BackgroundWorker> součásti z **sada nástrojů** do vaší `MarqueeBorder` ovládacího prvku. Tato součást bude možné `MarqueeBorder` řízení sám aktualizoval asynchronně.  
  
3.  V okně vlastnosti nastavit <xref:System.ComponentModel.BackgroundWorker> součásti `WorkerReportsProgess` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti, které chcete `true`. Tato nastavení umožňují <xref:System.ComponentModel.BackgroundWorker> součást, kterou pravidelně vyvolat <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí a zrušit asynchronní aktualizace. Další informace najdete v tématu [BackgroundWorker – komponenta](../../../../docs/framework/winforms/controls/backgroundworker-component.md).  
  
4.  V okně vlastností klikněte na tlačítko události. Obslužné rutiny pro připojení <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události.  
  
5.  Otevřete `MarqueeBorder` zdrojový soubor v **Editor kódu**. V horní části souboru importujte následujících oborů názvů:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]  
  
6.  Změňte deklaraci `MarqueeBorder` dědění z <xref:System.Windows.Forms.Panel> a implementovat `IMarqueeWidget` rozhraní.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]  
  
7.  Deklarace výčtů dva pro správu `MarqueeBorder` stavu ovládacího prvku: `MarqueeSpinDirection`, která určuje směr, ve kterém světla "otočit" kolem ohraničení, a `MarqueeLightShape`, který určuje tvar indikátory (odmocnina nebo cyklické). Umístěte tyto deklarace před `MarqueeBorder` deklarace třídy.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]  
  
8.  Deklarujte proměnné instance, které odpovídají vystavené vlastnosti a inicializace je v konstruktoru.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]  
  
9. Implementace `IMarqueeWidget` rozhraní.  
  
     `StartMarquee` a `StopMarquee` vyvolání metody <xref:System.ComponentModel.BackgroundWorker> součásti <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody spuštění a ukončení animace.  
  
     Protože `MarqueeBorder` ovládacího prvku může obsahovat podřízených ovládacích prvků, `StartMarquee` metoda zobrazí všechny podřízené ovládací prvky a volání `StartMarquee` na ty, které implementují `IMarqueeWidget`. `StopMarquee` Metoda má podobné implementace.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]  
  
10. Implementace přístupových objektů vlastnost. `MarqueeBorder` Ovládací prvek má několik vlastností pro řízení její vzhled.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]  
  
11. Implementace obslužné rutiny <xref:System.ComponentModel.BackgroundWorker> součásti <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události.  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> Obslužné rutiny události v režimu spánku počet milisekund, `UpdatePeriod` poté vyvolá <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí, dokud kódu zastaví animace voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Obslužné rutiny události zvýší pozici "základní" světlým, ze kterého je určen stav světlý nebo tmavý další indikátory, a počet volání <xref:System.Windows.Forms.Control.Refresh%2A> metodu pro ovládací prvek, aby překreslit sám sebe.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]  
  
12. Implementace metody helper `IsLit` a `DrawLight`.  
  
     `IsLit` Metoda určuje barvu světla na dané pozici. Indikátory, které jsou "lit" jsou vykreslovány v barvu poskytují `LightColor` vlastnost a ty, které jsou "tmavý" jsou vykreslovány v barvu poskytují `DarkColor` vlastnost.  
  
     `DrawLight` Metoda nevykresluje lehkým pomocí příslušné barvu, tvar a pozice.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]  
  
13. Přepsání <xref:System.Windows.Forms.Control.OnLayout%2A> a <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda nevykresluje indikátory podél okrajů `MarqueeBorder` ovládacího prvku.  
  
     Protože <xref:System.Windows.Forms.Control.OnPaint%2A> metoda závisí na rozměry `MarqueeBorder` ovládací prvek, musíte ji volat při každé změně rozložení. Chcete-li dosáhnout, přepište <xref:System.Windows.Forms.Control.OnLayout%2A> a volání <xref:System.Windows.Forms.Control.Refresh%2A>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]  
  
## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>Vytváření vlastních návrháře stínové a vlastnosti filtru  
 `MarqueeControlRootDesigner` Třída poskytuje implementaci pro kořenové návrháře. Kromě Tento návrhář, který funguje na `MarqueeControl`, budete potřebovat vlastního návrháře, který je konkrétně přidružený `MarqueeBorder` ovládacího prvku. Tento návrhář poskytuje vlastní chování, který je vhodný v kontextu vlastní kořenového návrháře.  
  
 Konkrétně `MarqueeBorderDesigner` bude "stínové" a filtrovat některé vlastnosti `MarqueeBorder` řízení, změna jejich interakci s prostředím návrhu.  
  
 Brání volání přistupujícího objektu vlastnosti součásti se označuje jako "stínováním." Ji umožňuje návrháře sledovat hodnotu nastavenou uživatelem a volitelně komponentu navrženy předat tuto hodnotu.  
  
 V tomto příkladu <xref:System.Windows.Forms.Control.Visible%2A> a <xref:System.Windows.Forms.Control.Enabled%2A> vlastnosti bude stínovaný podle `MarqueeBorderDesigner`, což zabrání uživateli v provádění `MarqueeBorder` řízení skryté a zakázané během doby návrhu.  
  
 Návrháři můžete také přidávat a odebírat vlastnosti. V tomto příkladu <xref:System.Windows.Forms.Control.Padding%2A> vlastnost odeberou v době návrhu, protože `MarqueeBorder` řízení prostřednictvím kódu programu Nastaví odsazení na základě velikosti indikátory určeného `LightSize` vlastnost.  
  
 Základní třída pro `MarqueeBorderDesigner` je <xref:System.ComponentModel.Design.ComponentDesigner>, která obsahuje metody, které můžete změnit atributy, vlastnosti a události vystavené ovládacího prvku v době návrhu:  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>  
  
 Při změně veřejné rozhraní součásti pomocí těchto metod, je třeba provést tato pravidla:  
  
-   Přidání nebo odebrání položek v `PreFilter` pouze metody  
  
-   Změnit existující položky v `PostFilter` pouze metody  
  
-   Volat základní implementaci vždy nejprve `PreFilter` metody  
  
-   Vždy volat základní implementaci poslední `PostFilter` metody  
  
 Se tato pravidla zajistí, že všechny Designer v prostředí návrhu konzistentní zobrazení všech součástí navrženy.  
  
 <xref:System.ComponentModel.Design.ComponentDesigner> Třída poskytuje slovník pro správu hodnoty stíněné vlastností, což sníží můžete potřebu vytvářet konkrétní instanci proměnné.  
  
#### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Chcete-li vytvořit vlastní návrháře stínové a filtr vlastností  
  
1.  Klikněte pravým tlačítkem myši **návrhu** složky a přidejte novou třídu. Zadejte zdrojový soubor základní název "MarqueeBorderDesigner."  
  
2.  Otevřete `MarqueeBorderDesigner` zdrojový soubor v **Editor kódu**. V horní části souboru importujte následujících oborů názvů:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]  
  
3.  Změňte deklaraci `MarqueeBorderDesigner` dědění z <xref:System.Windows.Forms.Design.ParentControlDesigner>.  
  
     Protože `MarqueeBorder` ovládacího prvku může obsahovat podřízené ovládací prvky, `MarqueeBorderDesigner` dědí z <xref:System.Windows.Forms.Design.ParentControlDesigner>, která zpracovává interakci nadřazený podřízený.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]  
  
4.  Přepsání základní implementace <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]  
  
5.  Implementace <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A> vlastnosti. Tato implementace stínové vlastností ovládacího prvku.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]  
  
## <a name="handling-component-changes"></a>Zpracování změny součásti  
 `MarqueeControlRootDesigner` Třída poskytuje možnosti návrhu vlastní vaší `MarqueeControl` instance. Většinu funkcí návrhu je zděděn z <xref:System.Windows.Forms.Design.DocumentDesigner> třída; váš kód bude implementovat dvě konkrétní přizpůsobení: zpracování změny součásti a přidání návrháře příkazy.  
  
 Jako uživatelé návrhu jejich `MarqueeControl` instancí kořenového návrháře bude sledovat změny `MarqueeControl` a jeho podřízených ovládacích prvků. V prostředí návrhu nabízí pohodlný službu, <xref:System.ComponentModel.Design.IComponentChangeService>pro sledování se změní na stav komponenty.  
  
 Získat odkaz na tuto službu dotazováním prostředí s <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> metoda. Pokud je dotaz úspěšný, vašeho návrháře můžete připojit obslužnou rutinu pro <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> události a provádět jakékoli úlohy je potřeba udržovat konzistentně v době návrhu.  
  
 U `MarqueeControlRootDesigner` třídu bude volat <xref:System.Windows.Forms.Control.Refresh%2A> metoda na každém `IMarqueeWidget` objekt obsažený `MarqueeControl`. To způsobí, že `IMarqueeWidget` chcete překreslit samotné správně, když vlastnosti, jako je jeho nadřazený objekt <xref:System.Windows.Forms.Control.Size%2A> došlo ke změně.  
  
#### <a name="to-handle-component-changes"></a>Zpracovat změny v součásti  
  
1.  Otevřete `MarqueeControlRootDesigner` zdrojový soubor v **Editor kódu** a přepsat <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metoda. Volat základní implementaci <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> a dotazu <xref:System.ComponentModel.Design.IComponentChangeService>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]  
  
2.  Implementace <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> obslužné rutiny události. Test typu odesílání komponenty, a pokud je `IMarqueeWidget`, volání jeho <xref:System.Windows.Forms.Control.Refresh%2A> metoda.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]  
  
## <a name="adding-designer-verbs-to-your-custom-designer"></a>Přidání návrháře příkazy k vaší vlastní Designer  
 Návrhář operaci je příkaz nabídky propojené s obslužné rutiny události. Návrhář příkazy se přidají do komponenty místní nabídky v době návrhu. Další informace naleznete v tématu <xref:System.ComponentModel.Design.DesignerVerb>.  
  
 Dva příkazy návrháře přidá do vašeho návrháři: **spustit Test** a **zastavit testovací**. Tyto příkazy vám umožní zobrazit chování běhové `MarqueeControl` v době návrhu. Tyto příkazy bude přidán do `MarqueeControlRootDesigner`.  
  
 Když **spustit Test** je vyvolána, bude volat operaci obslužné rutiny události `StartMarquee` metodu `MarqueeControl`. Při **zastavit testovací** je vyvolána, obslužné rutiny události příkaz zavolá `StopMarquee` metodu `MarqueeControl`. Implementace `StartMarquee` a `StopMarquee` metody volat tyto metody na obsažené ovládací prvky, které implementují `IMarqueeWidget`, takže všechny obsažené `IMarqueeWidget` ovládací prvky bude také podílet na test.  
  
#### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Chcete-li přidat návrháře příkazy k vaší vlastní Designer  
  
1.  V `MarqueeControlRootDesigner` třídy, přidejte obslužné rutiny událostí s názvem `OnVerbRunTest` a `OnVerbStopTest`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]  
  
2.  Připojení těchto obslužných rutin událostí na jejich odpovídající návrháře příkazy. `MarqueeControlRootDesigner` dědí <xref:System.ComponentModel.Design.DesignerVerbCollection> ze své základní třídy. Vytvoříte dva nové <xref:System.ComponentModel.Design.DesignerVerb> objekty a přidat je do této kolekce v <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metoda.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]  
  
## <a name="creating-a-custom-uitypeeditor"></a>Vytvoření vlastního editoru UITypeEditor.  
 Když vytvoříte vlastní prostředí návrhu pro uživatele, je často žádoucí, chcete-li vytvořit vlastní interakci s okno vlastností. To můžete udělat tak, že vytvoříte <xref:System.Drawing.Design.UITypeEditor>. Další informace najdete v tématu [postupy: vytvoření Editor typů uživatelského rozhraní](http://msdn.microsoft.com/library/292c6e33-8d85-4012-9b51-05835a6f6dfd).  
  
 `MarqueeBorder` Řízení poskytuje několik vlastností, v okně Vlastnosti. Dva z těchto vlastností `MarqueeSpinDirection` a `MarqueeLightShape` jsou reprezentované pomocí výčty. Pro ilustraci použití editor typů uživatelského rozhraní, `MarqueeLightShape` vlastnost budou mít přidružené <xref:System.Drawing.Design.UITypeEditor> třídy.  
  
#### <a name="to-create-a-custom-ui-type-editor"></a>Chcete-li vytvořit vlastní typ uživatelského rozhraní editoru  
  
1.  Otevřete `MarqueeBorder` zdrojový soubor v **Editor kódu**.  
  
2.  V definici `MarqueeBorder` třídy, deklarovat třídy s názvem `LightShapeEditor` která je odvozena od <xref:System.Drawing.Design.UITypeEditor>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]  
  
3.  Deklarace <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance proměnné s názvem `editorService`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]  
  
4.  Přepsání <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metoda. Tato implementace vrátí <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, která informuje prostředí návrhu, jak má zobrazit `LightShapeEditor`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]  
  
5.  Přepsání <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metoda. Tato implementace dotazuje prostředí návrhu pro <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> objektu. Pokud úspěšné, vytvoří `LightShapeSelectionControl`. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Metoda je volána spustit `LightShapeEditor`. Vrácená hodnota z toto volání se vrátí do prostředí návrhu.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]  
  
## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>Vytvoření ovládacího prvku zobrazení pro vaše vlastní typu UITypeEditor  
  
1.  `MarqueeLightShape` Vlastnost podporuje dva typy světla tvarů: `Square` a `Circle`. Vytvoříte vlastní ovládací prvek použitý výhradně pro účely graficky zobrazení tyto hodnoty v okně Vlastnosti. Tento vlastní ovládací prvek použije vaše <xref:System.Drawing.Design.UITypeEditor> k interakci se okno Vlastnosti.  
  
#### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Vytvoření ovládacího prvku zobrazení pro vlastní uživatelské rozhraní editor typů  
  
1.  Přidejte nový <xref:System.Windows.Forms.UserControl> položkou `MarqueeControlLibrary` projektu. Pojmenujte nový zdrojový soubor základní služby "LightShapeSelectionControl."  
  
2.  Přetáhněte dva <xref:System.Windows.Forms.Panel> z ovládací prvky **sada nástrojů** na `LightShapeSelectionControl`. Název je `squarePanel` a `circlePanel`. Umožňuje uspořádejte je vedle sebe. Nastavte <xref:System.Windows.Forms.Control.Size%2A> vlastnost objektu i <xref:System.Windows.Forms.Panel> prvky (60, 60). Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost `squarePanel` řídit k (8, 10). Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost `circlePanel` řídit k (80, 10). Nakonec nastavte <xref:System.Windows.Forms.Control.Size%2A> vlastnost `LightShapeSelectionControl` k (150, 80).  
  
3.  Otevřete `LightShapeSelectionControl` zdrojový soubor v **Editor kódu**. V horní části souboru, importujte <xref:System.Windows.Forms.Design?displayProperty=nameWithType> obor názvů:  
  
```vb  
Imports System.Windows.Forms.Design  
```  
  
```csharp  
using System.Windows.Forms.Design;  
```  
  
1.  Implementace <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `squarePanel` a `circlePanel` ovládací prvky. Tyto metody vyvolání <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> na konec vlastní <xref:System.Drawing.Design.UITypeEditor> úpravy relace.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]  
  
2.  Deklarace <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance proměnné s názvem `editorService`.  
  
```vb  
Private editorService As IWindowsFormsEditorService  
```  
  
```csharp  
private IWindowsFormsEditorService editorService;  
```  
  
1.  Deklarace `MarqueeLightShape` instance proměnné s názvem `lightShapeValue`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]  
  
2.  V `LightShapeSelectionControl` konstruktor, připojte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí k `squarePanel` a `circlePanel` ovládací prvky <xref:System.Windows.Forms.Control.Click> události. Navíc definovat přetížení konstruktor, který přiřazuje `MarqueeLightShape` hodnotu z prostředí návrhu tak, aby `lightShapeValue` pole.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]  
  
3.  V <xref:System.ComponentModel.Component.Dispose%2A> metoda, odpojte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]  
  
4.  V **Průzkumníku řešení**, klikněte **zobrazit všechny soubory** tlačítko. Otevřete soubor LightShapeSelectionControl.Designer.cs nebo LightShapeSelectionControl.Designer.vb a odeberte výchozí definice <xref:System.ComponentModel.Component.Dispose%2A> metoda.  
  
5.  Implementace `LightShape` vlastnost.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]  
  
6.  Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> metoda. Tato implementace bude zakreslit vyplněný čtvereček a kruh. Pomocí kreslení ohraničení tvaru jeden nebo druhý ho bude také zvýrazněte vybrané hodnoty.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]  
  
## <a name="testing-your-custom-control-in-the-designer"></a>Testování vlastního ovládacího prvku v Návrháři  
 V tomto okamžiku můžete vytvořit `MarqueeControlLibrary` projektu. Testování vaší implementace vytvořením ovládacího prvku, který dědí z `MarqueeControl` třídy a použití ve formuláři.  
  
#### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Chcete-li vytvořit vlastní implementaci typu MarqueeControl  
  
1.  Otevřete `DemoMarqueeControl` v Návrháři formulářů. Tím se vytvoří instance `DemoMarqueeControl` zadejte a zobrazí v instanci systému `MarqueeControlRootDesigner` typu.  
  
2.  V **sada nástrojů**, otevřete **MarqueeControlLibrary součásti** kartě. Zobrazí se `MarqueeBorder` a `MarqueeText` ovládací prvky, které jsou k dispozici pro výběr.  
  
3.  Přetáhněte instanci `MarqueeBorder` na ovládací prvek `DemoMarqueeControl` návrhovou plochu. Ukotvení – to `MarqueeBorder` ovládacího prvku do nadřazeného ovládacího prvku.  
  
4.  Přetáhněte instanci `MarqueeText` na ovládací prvek `DemoMarqueeControl` návrhovou plochu.  
  
5.  Sestavte řešení.  
  
6.  Klikněte pravým tlačítkem myši `DemoMarqueeControl` a z místní nabídky vyberte možnost **spustit Test** možnost spustit animace. Klikněte na tlačítko **zastavit testovací** zastavit animace.  
  
7.  Otevřete **Form1** v zobrazení návrhu.  
  
8.  Umístěte dva <xref:System.Windows.Forms.Button> ovládací prvky na formuláři. Název je `startButton` a `stopButton`a změňte <xref:System.Windows.Forms.Control.Text%2A> vlastnosti hodnoty k **spustit** a **Zastavit**, v uvedeném pořadí.  
  
9. Implementace <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro obě <xref:System.Windows.Forms.Button> ovládací prvky.  
  
10. V **sada nástrojů**, otevřete **MarqueeControlTest součásti** kartě. Zobrazí se `DemoMarqueeControl` k dispozici pro výběr.  
  
11. Přetáhněte instanci `DemoMarqueeControl` na **Form1** návrhovou plochu.  
  
12. V <xref:System.Windows.Forms.Control.Click> vyvolání obslužné rutiny událostí, `Start` a `Stop` metody `DemoMarqueeControl`.  
  
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
  
1.  Nastavte `MarqueeControlTest` projekt jako spouštěný projekt a spusťte ho. Uvidíte formulář zobrazení vaší `DemoMarqueeControl`. Klikněte **spustit** tlačítko pro spuštění animace. Měli byste vidět text blikající a světla pohyb ohraničení.  
  
## <a name="next-steps"></a>Další kroky  
 `MarqueeControlLibrary` Ukazuje jednoduchou implementaci vlastní ovládací prvky a přidružené designeru. Složitější této ukázky můžete provést několika způsoby:  
  
-   Změnit vlastnosti hodnoty `DemoMarqueeControl` v návrháři. Přidat další `MarqueBorder` ovládací prvky a dokování je v rámci jejich nadřazené instance vytvořit vnořené efekt. Experiment s různá nastavení pro `UpdatePeriod` a vlastnosti související s light.  
  
-   Vytvořit vlastní implementace `IMarqueeWidget`. Může například vytvořit blikající "Neónová znaménkem" nebo symbolem animovaný s více bitových kopií.  
  
-   Přizpůsobíte možnosti návrhu. Mohou zkuste stínový provoz více vlastností než <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A>, a můžete přidat nové vlastnosti. Přidáte nové návrháře příkazy ke zjednodušení běžné úkoly, jako ukotvení podřízených ovládacích prvků.  
  
-   Licence `MarqueeControl`. Další informace najdete v tématu [postup: komponenty licence a ovládací prvky](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57).  
  
-   Řídí, jak vaše ovládací prvky jsou serializovány a jak se generuje kód pro ně. Další informace najdete v tématu [dynamické generování zdrojového kódu a kompilace](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Design.ParentControlDesigner>  
 <xref:System.Windows.Forms.Design.DocumentDesigner>  
 <xref:System.ComponentModel.Design.IRootDesigner>  
 <xref:System.ComponentModel.Design.DesignerVerb>  
 <xref:System.Drawing.Design.UITypeEditor>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)  
 [Rozšíření podpory návrhu](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Vlastní Designer](http://msdn.microsoft.com/library/ca11988e-d38e-44d8-a05d-71362ae7844d)  
 [Knihovna .NET tvar: Ukázka návrháře](http://windowsforms.net/articles/shapedesigner.aspx)
