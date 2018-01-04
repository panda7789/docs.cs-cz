---
title: "Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fd38f6246d44bd24753d9c86a5b0b08819d3db7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a>Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu
Při vytváření vlastního ovládacího prvku často zjistíte, je nezbytné k ladění její chování v době návrhu. To platí hlavně vytváříte-li vlastní návrháře pro vaše vlastní ovládací prvek. Podrobnosti najdete v tématu [návod: vytváření funkce systému Windows Forms ovládací prvek, trvá využít nástroje Visual Studio návrhu](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
 Vlastní ovládací prvky pomocí sady Visual Studio, můžete ladit, stejně jako ostatní třídy rozhraní .NET Framework by ladění. Rozdíl je, že ladíte samostatnou instanci Visual Studia, která běží kód vlastní ovládací prvek  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytvoření projektu pro hostování vašeho vlastního ovládacího prvku Windows Forms  
  
-   Vytvoření projektu knihovny ovládacího prvku  
  
-   Přidání vlastnosti do vlastního ovládacího prvku  
  
-   Přidání vlastního ovládacího prvku na formulář hostitele  
  
-   Nastavení projektu pro ladění v době návrhu  
  
-   Ladění vlastního ovládacího prvku v době návrhu  
  
 Jakmile budete hotovi, budete mít k pochopení úlohy plánování pro ladění v době návrhu chování vlastního ovládacího prvku.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu aplikace. Tento projekt použije k vytvoření aplikace, který je hostitelem vlastního ovládacího prvku.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte projekt aplikace pro systém Windows s názvem "DebuggingExample". Podrobnosti najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
## <a name="creating-a-control-library-project"></a>Vytvoření projektu knihovny ovládacího prvku  
 Dalším krokem je vytvoření projektu knihovny řízení a nastavení vlastního ovládacího prvku.  
  
#### <a name="to-create-the-control-library-project"></a>Vytvoření projektu knihovny ovládacího prvku  
  
1.  Přidat **knihovny ovládacích prvků Windows** projektu k řešení.  
  
2.  Přidejte nový **UserControl** položky k DebugControlLibrary projektu. Podrobnosti najdete v tématu [NIB: postupy: Přidání nové položky projektu](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce). Zadejte základní název "DebugControl" nové zdrojový soubor.  
  
3.  Pomocí **Průzkumníku řešení**, odstraňte výchozí řízení projektu odstraněním souboru kódu s základní název "`UserControl1`". Podrobnosti najdete v tématu [NIB: postupy: odebrání, odstranění a vyloučit položky](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
4.  Sestavte řešení.  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku bude moci zobrazit vaše vlastní ovládací prvek v **sada nástrojů**.  
  
#### <a name="to-check-your-progress"></a>Chcete-li zkontrolovat průběh  
  
-   Najít novou kartu názvem **DebugControlLibrary součásti** a kliknutím vyberte ho. Když se otevře, zobrazí se vlastní ovládací prvek uveden jako **DebugControl** s výchozí ikonu vedle ní.  
  
## <a name="adding-a-property-to-your-custom-control"></a>Přidání vlastnosti do vlastního ovládacího prvku  
 K prokázání, že vlastní řídicí kód běží v době návrhu, bude přidání vlastnosti a nastavení zarážky v kódu, který implementuje vlastnost.  
  
#### <a name="to-add-a-property-to-your-custom-control"></a>Přidání vlastnosti do vlastního ovládacího prvku  
  
1.  Otevřete **DebugControl** v **Editor kódu**. Přidejte následující kód v definici třídy:  
  
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
 Ladění chování návrhu vlastního ovládacího prvku, umístí instance třídy vlastního ovládacího prvku ve formuláři hostitele.  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a>Přidání vlastního ovládacího prvku do formuláře hostitele  
  
1.  V projektu "DebuggingExample" otevřete Form1 v **Návrhář formulářů Windows**.  
  
2.  V **sada nástrojů**, otevřete **DebugControlLibrary součásti** kartě a přetáhněte ji **DebugControl** instance do formuláře.  
  
3.  Najít `DemoString` vlastní vlastnost **vlastnosti** okno. Všimněte si, že stejně jako všechny ostatní vlastnosti můžete změnit jeho hodnotu. Všimněte si, že pokud `DemoString` vlastnost je vybraná, řetězec popisu vlastnosti se zobrazí v dolní části **vlastnosti** okno.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu  
 K ladění chování vlastního ovládacího prvku v době návrhu, bude ladění samostatnou instanci Visual Studia, která běží vlastní řídicí kód.  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu  
  
1.  Klikněte pravým tlačítkem na **DebugControlLibrary** v projektu **Průzkumníku řešení** a vyberte **vlastnosti**.  
  
2.  V **DebugControlLibrary** seznamu vlastností, vyberte **ladění** kartě.  
  
     V **spustit akci** vyberte **počáteční vnějšímu programu**. Bude ladění samostatné instanci sady Visual Studio, proto klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko procházení pro Visual Studio IDE. Název spustitelného souboru je **devenv.exe**, a pokud jste nainstalovali do výchozího umístění, je jeho cestu 9.0\Common7\IDE\devenv.exe %programfiles%\Microsoft Visual Studio.  
  
3.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
4.  Klikněte pravým tlačítkem myši **DebugControlLibrary** projektu a vyberte **nastavit jako spouštěný projekt** Chcete-li povolit tuto konfiguraci ladění.  
  
## <a name="debugging-your-custom-control-at-design-time"></a>Ladění vlastního ovládacího prvku v době návrhu  
 Nyní jste připraveni k ladění vlastního ovládacího prvku při jeho spuštění v režimu návrhu. Když spustíte relaci ladění, vytvoří novou instanci sady Visual Studio a použije ho k načtení řešení "DebuggingExample". Když otevřete Form1 v **Návrhář formulářů**, instanci vlastního ovládacího prvku se vytvoří a spustí systémem.  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a>Chcete-li ladit vlastního ovládacího prvku v době návrhu  
  
1.  Otevřete **DebugControl** zdrojový soubor v **Editor kódu** a umístěte zarážku na `Set` přistupujícího `DemoString` vlastnost.  
  
2.  Stisknutím klávesy F5 spusťte relaci ladění. Všimněte si, že je vytvořena nová instance sady Visual Studio. Možné rozlišit mezi instancemi dvěma způsoby:  
  
    -   Ladění instance má slovo **systémem** v jeho záhlaví  
  
    -   Ladění instance má **spustit** tlačítko na jeho **ladění** zakázáno panelu nástrojů  
  
     Vaší zarážce se nastavuje v ladění instance.  
  
3.  V nové instanci sady Visual Studio otevřete řešení "DebuggingExample". Budete moci snadno najít řešení výběrem **poslední projekty** z **souboru** nabídky. Soubor řešení "DebuggingExample.sln" se objeví jako naposledy použitých souborů.  
  
4.  Otevřete Form1 v **Návrhář formulářů** a vyberte **DebugControl** ovládacího prvku.  
  
5.  Změňte hodnotu `DemoString` vlastnost. Upozorňujeme, že pokud provedete změny, získá fokus ladění instanci sady Visual Studio a spuštění zastaví na vaší zarážce. Můžete krokování prostřednictvím přistupující objekt vlastnosti stejně jako vaše by jakýkoli jiný kód.  
  
6.  Když skončíte s vaší relace ladění, můžete ukončit zrušením hostované instanci sady Visual Studio nebo kliknutím **Zastavte ladění** tlačítka na ladění instance.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když ladíte vlastní ovládací prvky v době návrhu existuje mnoho možností pro rozšíření interakci ovládacího prvku s Visual Studio IDE.  
  
-   Můžete použít <xref:System.ComponentModel.Component.DesignMode%2A> vlastnost <xref:System.ComponentModel.Component> třídu k zápisu kódu, který spustí, pouze v době návrhu. Podrobnosti najdete v tématu <xref:System.ComponentModel.Component.DesignMode%2A>.  
  
-   Několik atributů můžete provést u vlastnosti ovládacího prvku k manipulaci s interakce vlastního ovládacího prvku pomocí návrháře. Můžete najít v těchto atributů <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů.  
  
-   Můžete napsat vlastní návrháře pro vaše vlastní ovládací prvek. To vám dává úplnou kontrolu nad prostředí návrhu pomocí extensible návrháře infrastruktury vystavené Visual Studio. Podrobnosti najdete v tématu [návod: vytváření funkce systému Windows Forms ovládací prvek, trvá využít nástroje Visual Studio návrhu](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [Postupy: přístup ke službám v době návrhu](http://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [Postupy: přístup k podpoře návrhu v systému Windows Forms](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
