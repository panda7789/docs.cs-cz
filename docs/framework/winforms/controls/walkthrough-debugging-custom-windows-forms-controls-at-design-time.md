---
title: 'Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
ms.openlocfilehash: b5c54acc89317104eddc3b1f5b350edcb263d208
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213686"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a>Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu
Při vytváření vlastního ovládacího prvku často zjistíte to potřebné k ladění jeho chování během návrhu. To platí zejména pokud vytváříte vlastní návrháře pro vlastní ovládací prvek. Podrobnosti najdete v tématu [názorný postup: Vytváření Windows Forms ovládací prvek, který využívá funkce sady Visual Studio Design-Time](creating-a-wf-control-design-time-features.md).  
  
 Vlastní ovládací prvky pomocí sady Visual Studio, můžete ladit stejně, jako by ladění jiných tříd rozhraní .NET Framework. Rozdíl spočívá v tom, že ladíte samostatnou instanci sady Visual Studio, na kterém běží vaše vlastní ovládací prvek kódu  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření projektu Windows Forms k hostování vlastního ovládacího prvku  
  
-   Vytvoření projektu knihovny ovládacích prvků  
  
-   Přidání vlastnosti do vlastního ovládacího prvku  
  
-   Přidání vlastního ovládacího prvku na formulář hostitele  
  
-   Nastavení projektu pro ladění v době návrhu  
  
-   Ladění vlastního ovládacího prvku v době návrhu  
  
 Až budete hotovi, budete mít porozumění úloh nezbytných pro ladění chování návrhu vlastního ovládacího prvku.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu aplikace. Tento projekt bude používat k sestavení aplikace, který je hostitelem vlastního ovládacího prvku.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte projekt aplikace Windows s názvem "DebuggingExample" (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).  
  
## <a name="creating-a-control-library-project"></a>Vytvoření projektu knihovny ovládacích prvků  
 Dalším krokem je vytvoření projektu knihovny ovládacích prvků a nastavení vlastního ovládacího prvku.  
  
#### <a name="to-create-the-control-library-project"></a>Vytvoření projektu knihovny ovládacích prvků  
  
1.  Přidat **Knihovna ovládacích prvků Windows** projektu do řešení.  
  
2.  Přidat nový **UserControl** položky do projektu DebugControlLibrary. Podrobnosti najdete v tématu [jak: Přidání nových položek projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)). Zadejte základní název "DebugControl" nového zdrojového souboru.  
  
3.  Použití **Průzkumníku řešení**, odstranění výchozího projektu ovládacího prvku tak, že odstraníte soubor kódu základní název s "`UserControl1`". Podrobnosti najdete v tématu [jak: Odebrat, odstranit a vyloučit položky](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).  
  
4.  Sestavte řešení.  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku budete moct zobrazit vaše vlastní ovládací prvky **nástrojů**.  
  
#### <a name="to-check-your-progress"></a>Chcete-li zkontrolovat průběh  
  
-   Vyhledejte novou kartu **DebugControlLibrary součásti** a kliknutím ji vyberte. Když se otevře, zobrazí se váš ovládací prvek zobrazí jako **DebugControl** s výchozí ikona vedle něj.  
  
## <a name="adding-a-property-to-your-custom-control"></a>Přidání vlastnosti do vlastního ovládacího prvku  
 Abychom si předvedli, že kód vlastní ovládací prvek je spuštěný v době návrhu, se přidat vlastnost a nastavte zarážku v kódu, který implementuje vlastnost.  
  
#### <a name="to-add-a-property-to-your-custom-control"></a>Přidání vlastnosti do vlastního ovládacího prvku  
  
1.  Otevřít **DebugControl** v **Editor kódu**. Přidejte následující kód do definice třídy:  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  Sestavte řešení.  
  
## <a name="adding-your-custom-control-to-the-host-form"></a>Přidání vlastního ovládacího prvku na formulář hostitele  
 Chcete-li ladit chování návrhu vlastního ovládacího prvku, umístíte instance třídy vlastní ovládací prvek ve formuláři hostitele.  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a>Přidání vlastního ovládacího prvku do formuláře hostitele  
  
1.  V projektu "DebuggingExample" otevřete Form1 v **Návrháře formulářů Windows**.  
  
2.  V **nástrojů**, otevřete **DebugControlLibrary součásti** kartu a přetáhnout **DebugControl** instance na formulář.  
  
3.  Najít `DemoString` vlastní vlastnost v **vlastnosti** okna. Všimněte si, že stejně jako jakoukoli jinou vlastnosti můžete změnit jeho hodnotu. Všimněte si také, že `DemoString` vybrána vlastnost, řetězce popisu vlastnosti se zobrazí v dolní části **vlastnosti** okna.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu  
 Chcete-li ladit chování vašeho vlastního ovládacího prvku návrhu, bude ladit samostatnou instanci sady Visual Studio, na kterém běží vaše vlastní ovládací prvek kódu.  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu  
  
1.  Klikněte pravým tlačítkem na **DebugControlLibrary** projekt **Průzkumníka řešení** a vyberte **vlastnosti**.  
  
2.  V **DebugControlLibrary** seznam vlastností, vyberte **ladění** kartu.  
  
     V **spustit akci** vyberte **externí program Start**. Bude ladění samostatnou instanci sady Visual Studio, proto klikněte na symbol tří teček (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Procházet pro Visual Studio IDE. Název spustitelného souboru, který je **devenv.exe**, a pokud jste nainstalovali do výchozího umístění, je jeho cesta 9.0\Common7\IDE\devenv.exe %programfiles%\Microsoft Visual Studio.  
  
3.  Kliknutím na **OK** zavřete dialogové okno.  
  
4.  Klikněte pravým tlačítkem myši **DebugControlLibrary** projektu a vyberte **nastavit jako spouštěný projekt** k povolení této konfiguraci ladění.  
  
## <a name="debugging-your-custom-control-at-design-time"></a>Ladění vlastního ovládacího prvku v době návrhu  
 Nyní jste připraveni k ladění vlastního ovládacího prvku při jeho spuštění v režimu návrhu. Když spustíte relaci ladění, bude vytvořena nová instance sady Visual Studio a použije k načtení řešení "DebuggingExample". Když otevřete Form1 v **Návrháře formulářů**, instance vašeho vlastního ovládacího prvku se vytvoří a spustí se systémem.  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a>Chcete-li ladit vlastního ovládacího prvku v době návrhu  
  
1.  Otevřít **DebugControl** zdrojový soubor v **Editor kódu** a umístit zarážky na `Set` přistupující objekt `DemoString` vlastnost.  
  
2.  Stisknutím klávesy F5 pro spuštění relace ladění. Všimněte si, že je vytvořena nová instance sady Visual Studio. Možné rozlišit mezi instancemi dvěma způsoby:  
  
    -   Ladění instance obsahuje slovo **systémem** v záhlaví  
  
    -   Ladění instance má **Start** tlačítko na jeho **ladění** nástrojů zakázáno  
  
     Vaše zarážka je nastavena v instanci ladění.  
  
3.  V nové instanci sady Visual Studio otevřete řešení "DebuggingExample". Řešení můžete snadno vyhledat tak, že vyberete **posledních projektů** z **souboru** nabídky. Soubor řešení "DebuggingExample.sln", bude uveden jako naposledy použitých souborů.  
  
4.  Otevřete Form1 v **Návrháře formulářů** a vyberte **DebugControl** ovládacího prvku.  
  
5.  Změňte hodnotu `DemoString` vlastnost. Všimněte si, že když změny potvrdíte, instanci ladění aplikace Visual Studio získá fokus a provádění zastaví na zarážku. Můžete si krokování přistupující objekt vlastnosti stejně jako vaše by jakýkoli jiný kód.  
  
6.  Až budete hotovi s vaší relace ladění, můžete ukončit zrušením hostované instance sady Visual Studio nebo kliknutím **Zastavit ladění** tlačítko v instanci ladění.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když vaše vlastní ovládací prvky můžete ladit v době návrhu, existuje mnoho možností pro rozbalení ovládacího prvku interakce s integrovaným vývojovým prostředím sady Visual Studio.  
  
-   Můžete použít <xref:System.ComponentModel.Component.DesignMode%2A> vlastnost <xref:System.ComponentModel.Component> třídy psaní kódu, který se spustí pouze v době návrhu. Podrobnosti najdete v tématu <xref:System.ComponentModel.Component.DesignMode%2A>.  
  
-   Několik atributů můžete provést u vlastností ovládacího prvku k manipulaci s vlastní ovládací prvek interakce s návrhářem. Tyto atributy v můžete najít <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů.  
  
-   Můžete napsat vlastního návrháře pro vlastní ovládací prvek. To vám plnou kontrolu nad komfortem při návrhu extensible návrháře infrastruktury zpřístupněný nástrojem Visual Studio. Podrobnosti najdete v tématu [názorný postup: Vytváření Windows Forms ovládací prvek, který využívá funkce sady Visual Studio Design-Time](creating-a-wf-control-design-time-features.md).  
  
## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md)
- [Postupy: Přístup ke službám během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171822(v=vs.120))
- [Postupy: Podpora návrhu přístupu ve Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171827(v=vs.120))
