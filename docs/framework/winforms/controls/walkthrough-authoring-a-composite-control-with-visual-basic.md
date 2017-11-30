---
title: "Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basic"
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
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c86a3d420b85c1287597cda738c6d72f0433d0f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basic
Složené ovládací prvky poskytují prostředky, pomocí kterého lze vytvořit vlastní grafické rozhraní a znovu použít. Složeného ovládacího prvku je v podstatě součást s vizuální reprezentace. Takto může obsahovat jeden nebo více Windows Forms – ovládací prvky, komponenty nebo bloky kódu, který můžete rozšířit funkce ověřování uživatelského vstupu, změnou vlastností zobrazení nebo provádění jiných úloh vyžaduje autorem. Složené ovládací prvky můžete umístit v rozhraní Windows Forms stejným způsobem jako další ovládací prvky. V první části tohoto návodu, vytvořte jednoduché složeného ovládacího prvku názvem `ctlClock`. V druhé části tohoto průvodce, můžete rozšířit funkce `ctlClock` prostřednictvím dědičnosti.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Když vytvoříte nový projekt, je třeba zadat jeho název nastavení kořenového oboru názvů, název sestavení a název projektu a ujistěte se, že komponentu výchozí bude ve správném oboru názvů.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>K vytvoření knihovny řízení ctlClockLib a ctlClock ovládací prvek  
  
1.  Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu** otevřete **nový projekt** dialogové okno.  
  
2.  Ze seznamu [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projekty, vyberte **knihovny ovládacích prvků Windows** šablona projektu, typ `ctlClockLib` v **název** pole a pak klikněte na **OK**.  
  
     Název projektu `ctlClockLib`, je také přiřazený k oboru názvů root ve výchozím nastavení. Kořenový obor názvů se použijí pro kvalifikaci názvy součásti v sestavení. Například, pokud dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete zadat vaše `ctlClock` pomocí součásti`ctlClockLib.ctlClock.`  
  
3.  V Průzkumníku řešení klikněte pravým tlačítkem na **UserControl1.vb**a potom klikněte na **přejmenovat**. Změňte název souboru `ctlClock.vb`. Klikněte **Ano** tlačítko po zobrazení dotazu, pokud chcete přejmenovat všechny odkazy na tento element kódu "UserControl1".  
  
    > [!NOTE]
    >  Ve výchozím nastavení, zdědí složeného ovládacího prvku <xref:System.Windows.Forms.UserControl> třída poskytuje systém. <xref:System.Windows.Forms.UserControl> Třída poskytuje funkce, které vyžadují všechny složené ovládací prvky a implementuje standardní metody a vlastnosti.  
  
4.  Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Přidání Windows ovládací prvky a součásti složeného ovládacího prvku  
 Vizuální rozhraní je zásadní součástí vaší složeného ovládacího prvku. Toto visual rozhraní je implementováno modulem přidání jednoho nebo více ovládacích prvků Windows na plochu návrháře. V následující ukázce se ovládací prvky Windows začlenit do vaší složeného ovládacího prvku a napsat kód pro implementaci funkcí.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Přidat k vaší složeného ovládacího prvku popisek a časovač  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.vb**a potom klikněte na **Návrhář zobrazení**.  
  
2.  V sadě nástrojů, rozbalte **běžné ovládací prvky** uzel a poté dvojitým kliknutím **popisek**.  
  
     A <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1` se přidá do vašeho ovládacího prvku na plochu návrháře.  
  
3.  V návrháři, klikněte na tlačítko **Label1**. V okně vlastností nastavte následující vlastnosti.  
  
    |Vlastnost|Změňte na|  
    |--------------|---------------|  
    |**Jméno**|`lblDisplay`|  
    |**Text**|`(blank space)`|  
    |**Zarovnání textu**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  V **sada nástrojů**, rozbalte **součásti** uzel a poté dvojitým kliknutím **časovače**.  
  
     Protože <xref:System.Windows.Forms.Timer> je komponenta, nemá žádné vizuální znázornění za běhu. Proto se nezobrazí s ovládacími prvky na plochu návrháře, ale v Návrháři součástí (panelu v dolní části plochu návrháře).  
  
5.  V Návrháři součástí, klikněte na tlačítko **Timer1**a poté nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `1000` a <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `True`.  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost řídí frekvenci, se kterým komponenta časovač značek. Pokaždé, když `Timer1` rysky, spuštěním kódu `Timer1_Tick` událostí. Interval představuje počet milisekund, po mezi značky.  
  
6.  V Návrháři součástí, klikněte dvakrát na **Timer1** přejít na `Timer1_Tick` událost pro `ctlClock`.  
  
7.  Upravte kód tak, aby je podobná následující ukázka kódu. Ujistěte se, chcete-li změnit – modifikátor přístupu z `Private` k `Protected`.  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     Tento kód způsobí, že aktuální čas zobrazený v `lblDisplay`. Protože interval `Timer1` byla nastavena na `1000`, tato událost se stane každých tisíc milisekund, proto aktualizace aktuální čas každou sekundu.  
  
8.  Změňte metodu být přepisovatelné. Další informace najdete v části ", která dědí z uživatelského ovládacího prvku" níže.  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.  
  
## <a name="adding-properties-to-the-composite-control"></a>Přidání vlastnosti do složeného ovládacího prvku  
 Vlastní ovládací prvek hodiny nyní zapouzdří <xref:System.Windows.Forms.Label> řízení a <xref:System.Windows.Forms.Timer> součást, každou s vlastní sadou vyplývajících vlastnosti. Zatímco jednotlivé vlastnosti těchto ovládacích prvků nebude přístupný uživatelům následné ovládacího prvku, můžete vytvořit a vystavení vlastní vlastnosti napsáním odpovídající bloky kódu. V následujícím postupu bude přidávat vlastnosti pro vaše ovládací prvek, který uživateli umožňuje změnit barvu pozadí a text.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Přidání vlastnosti do vašeho složeného ovládacího prvku  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.vb**a potom klikněte na **kód zobrazení**.  
  
     Otevře se Editor kódu pro ovládací prvek.  
  
2.  Vyhledejte `Public Class ctlClock` příkaz. Pod, zadejte následující kód.  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     Tyto příkazy vytvářet soukromé proměnné, které budete používat k ukládání hodnoty pro vlastnosti, které se chystáte vytvořit.  
  
3.  Vložte následující kód pod deklarace proměnných z kroku 2.  
  
    ```vb  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     Předchozí kód vytvoří dvě vlastní vlastnosti `ClockForeColor` a `ClockBackColor`, k dispozici pro další uživatelé tohoto ovládacího prvku vyvoláním `Property` příkaz. `Get` a `Set` příkazy zadat pro ukládání a načítání hodnotu vlastnosti, jakož i kód implementovat funkce, které jsou vhodné pro vlastnost.  
  
4.  Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.  
  
## <a name="testing-the-control"></a>Testování ovládacího prvku  
 Ovládací prvky nejsou samostatné projekty; musí být hostované v kontejneru. Testování chování ovládacího prvku a jeho vlastnosti s vykonávat **UserControl – kontejner testů**. Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-your-control"></a>K otestování ovládacího prvku  
  
1.  Stiskněte klávesu F5, aby se projekt sestavil a spuštění vlastního ovládacího prvku v **UserControl – kontejner testů**.  
  
2.  V mřížce vlastnost kontejner testů, vyberte `ClockBackColor` vlastnost a potom klikněte na šipku rozevíracího seznamu zobrazíte paletu barev.  
  
3.  Vyberte barvu kliknutím.  
  
     Barva pozadí ovládacího prvku změny barev, které jste vybrali.  
  
4.  Ověřte, že pomocí posloupnost událostí, podobně jako `ClockForeColor` vlastnost funguje podle očekávání.  
  
5.  Klikněte na tlačítko **zavřete** zavřete **UserControl – kontejner testů**.  
  
     V této části a v předchozích částech, jste viděli, jak mohou být kombinovány komponenty a ovládací prvky Windows s kódem a balení vlastní nakonfigurovánu ve formě složeného ovládacího prvku. Naučili jste se vystavení vlastností ve vaší složeného ovládacího prvku a po dokončení testování vlastního ovládacího prvku. V další části se dozvíte, jak vytvořit k zděděné složeného ovládacího prvku pomocí `ctlClock` jako základ.  
  
## <a name="inheriting-from-a-composite-control"></a>Dědění z složeného ovládacího prvku  
 V předchozích částech jste zjistili, jak kombinovat ovládací prvky systému Windows, komponent a kód do opakovatelně použitelných složené ovládací prvky. Vaše složeného ovládacího prvku nyní slouží jako základ, na kterém se dají vytvářet další ovládací prvky. Proces odvození třídy z základní třídy se nazývá *dědičnosti*. V této části vytvoříte složeného ovládacího prvku názvem `ctlAlarmClock`. Tento ovládací prvek bude odvozena z jeho nadřazenému ovládacímu prvku `ctlClock`. Naučíte se rozšířit funkce `ctlClock` přepsání metody nadřazené a přidáním nových metod a vlastností.  
  
 Prvním krokem při vytvoření ovládacího prvku zděděné je odvozena z nadřazené. Tato akce vytvoří nový ovládací prvek, který má všechny vlastnosti, metod a grafické vlastnosti nadřazeného ovládacího prvku, ale mohou chovat i jako základ pro přidání nové nebo změněné funkce.  
  
#### <a name="to-create-the-inherited-control"></a>Vytvoření zděděné ovládacího prvku  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**, přejděte na příkaz **přidat**a potom klikněte na **uživatelský ovládací prvek**.  
  
     **Přidat novou položku** otevře se dialogové okno.  
  
2.  Vyberte **zděděná uživatelský ovládací prvek** šablony.  
  
3.  V **název** zadejte `ctlAlarmClock.vb`a potom klikněte na **přidat**.  
  
     **Výběr dědičnosti** zobrazí se dialogové okno.  
  
4.  V části **název komponenty**, dvakrát klikněte na **ctlClock**.  
  
5.  V Průzkumníku řešení procházet aktuální projekty.  
  
    > [!NOTE]
    >  Soubor nazývá **ctlAlarmClock.vb** byla přidána do aktuálního projektu.  
  
### <a name="adding-the-alarm-properties"></a>Přidání vlastnosti výstrahy  
 Vlastnosti jsou přidány do ovládacího prvku zděděné stejným způsobem, které budou přidány do složeného ovládacího prvku. Teď použijete syntaxe deklarace vlastnost přidat dvě vlastnosti do vlastního ovládacího prvku: `AlarmTime`, který uloží hodnotu data a je čas vypnutí, a `AlarmSet`, který udává, zda je nastaven na upozornění.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Přidání vlastnosti do složených prvků  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na **kód zobrazení**.  
  
2.  Vyhledejte deklaraci třídy pro řízení ctlAlarmClock, které se zobrazí jako `Public Class ctlAlarmClock`.  V deklaraci třídy vložte následující kód.  
  
    ```vb  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>Přidávání do grafické rozhraní ovládacího prvku  
 Vizuální rozhraní, který je stejný jako ovládací prvek, který dědí z má vlastní zděděné ovládací prvek. Má k dispozici stejný základní ovládací prvky jako jeho nadřazenému ovládacímu prvku, ale vlastností základních ovládacích prvků nebudete mít k dispozici, pokud byly konkrétně vystavené. Můžete přidat na grafické rozhraní zděděné složeného ovládacího prvku stejným způsobem jako přidáváte do jakékoli složeného ovládacího prvku. Chcete-li pokračovat, přidávání do rozhraní visual alarmů hodiny, přidáte ovládacího prvku popisek, který bude flash, když je zvukově na upozornění.  
  
##### <a name="to-add-the-label-control"></a>Přidání ovládacího prvku popisek  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a klikněte na tlačítko **Návrhář zobrazení**.  
  
     Návrhář pro `ctlAlarmClock` otevře v hlavním okně.  
  
2.  Klikněte na tlačítko `lblDisplay` (část zobrazení ovládacího prvku) a zobrazte okno vlastností.  
  
    > [!NOTE]
    >  Když se zobrazí všechny vlastnosti, jsou neaktivní. To znamená, že tyto vlastnosti jsou nativní pro `lblDisplay` a nelze změnit ani získat přístup v okně Vlastnosti. Ve výchozím nastavení, jsou součástí složeného ovládacího prvku – ovládací prvky `Private`, a jejich vlastnosti nejsou dostupné žádné prostředky.  
  
    > [!NOTE]
    >  Pokud chcete další uživatelé složeného ovládacího prvku tak, aby měl přístup k jeho interní kontrolní mechanismy, deklarovat je jako `Public` nebo `Protected`. To vám umožní nastavit a úpravy vlastností ovládacích prvků, které jsou obsažené v rámci vaší složeného ovládacího prvku pomocí správný kód.  
  
3.  Přidat <xref:System.Windows.Forms.Label> řízení pro vaše složeného ovládacího prvku.  
  
4.  Pomocí myši, přetáhněte <xref:System.Windows.Forms.Label> ovládací prvek bezprostředně pod rozevíracím seznamu zobrazit. V okně vlastností nastavte následující vlastnosti.  
  
    |Vlastnost|Nastavení|  
    |--------------|-------------|  
    |**Jméno**|`lblAlarm`|  
    |**Text**|**Varování!**|  
    |**Zarovnání textu**|`MiddleCenter`|  
    |**Viditelné**|`False`|  
  
### <a name="adding-the-alarm-functionality"></a>Přidání funkce výstrahy  
 V předchozích postupech jste přidali, vlastnosti a ovládací prvek, který vám umožní alarmů funkce ve vašem složeného ovládacího prvku. V tomto postupu přidáte kód, který porovná aktuální čas je čas alarmů a, pokud jsou stejné, a zvukových flash alarm. Přepsáním `Timer1_Tick` metodu `ctlClock` a přidání další kód do, bude rozšířit schopnosti produktu `ctlAlarmClock` při zachování všech vyplývajících funkce `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>Chcete-li přepsat metodě Timer1_Tick ctlClock  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock.vb**a potom klikněte na **kód zobrazení**.  
  
2.  Vyhledejte `Private blnAlarmSet As Boolean` příkaz. Bezprostředně pod něj přidejte následující příkaz.  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  Vyhledejte `End Class` příkaz v dolní části stránky. Těsně před `End Class` prohlášení, přidejte následující kód.  
  
    ```vb  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     Přidání tento kód provede několik úloh. `Overrides` Příkaz přesměruje ovládací prvek, který chcete použít tuto metodu místo metody, která byla zděděna od základního ovládacího prvku. Když tato metoda je volána, zavolá metodu přepíše vyvoláním `MyBase.Timer1_Tick` prohlášení, zajistíte, že všechny funkce součástí původní ovládací prvek je uveden v tomto ovládacím prvku. Pak spustí další kód pro výstrahy funkce součástí. Blikající ovládací prvek popisek se zobrazí při výskytu varování a zvukových zvukový signál bude buďte vyslyšeni.  
  
    > [!NOTE]
    >  Vzhledem k tomu, že přepíšete zděděné obslužnou rutinu, není nutné zadat událost s `Handles` – klíčové slovo. Události je již připojili. Všechny, které jsou přepisování je implementace obslužné rutiny.  
  
     Vlastní ovládací prvek alarmů hodiny je téměř dokončena. Jediné, co zůstane je implementace způsob, jak ho vypnout. K tomuto účelu přidáte kód, který `lblAlarm_Click` metoda.  
  
##### <a name="to-implement-the-shutoff-method"></a>Chcete-li implementovat metodu přístupnými  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock.vb**a potom klikněte na **Návrhář zobrazení**.  
  
2.  V návrháři, klikněte dvakrát na **lblAlarm**. **Editor kódu** se otevře `Private Sub lblAlarm_Click` řádku.  
  
3.  Upravte tuto metodu tak, aby je podobná následující kód.  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Použití zděděné ovládacího prvku ve formuláři  
 Můžete otestovat zděděné kontrolu nad stejným způsobem jako otestovat základní třída prvku, `ctlClock`: stisknutím klávesy F5 se projekt sestavil a spuštění vlastního ovládacího prvku v **UserControl Test kontejneru**. Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Vložit ovládací prvek použít, musíte ji hostovat ve formuláři. Stejně jako u standardní složeného ovládacího prvku, zděděné složeného ovládacího prvku nelze samostatná a musí být uloženy ve formuláři nebo jiných kontejneru. Vzhledem k tomu `ctlAlarmClock` má větší hloubky funkcí, je potřeba otestovat další kód. V tomto postupu budete psát jednoduché program k testování funkčnosti `ctlAlarmClock`. Budete psát kód k nastavení a zobrazit `AlarmTime` vlastnost `ctlAlarmClock`a testovat své vyplývajících funkce.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>Sestavení a přidat do formuláře testu  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**a potom klikněte na **sestavení**.  
  
2.  Na **soubor** nabídky, přejděte na příkaz **přidat**a potom klikněte na **nový projekt**.  
  
3.  Přidejte nový **aplikace Windows** projektu k řešení a pojmenujte ji `Test`.  
  
     **Test** projekt je přidán do Průzkumníka řešení.  
  
4.  V Průzkumníku řešení klikněte pravým tlačítkem myši `Test` uzel projektu a pak klikněte na **přidat odkaz na** zobrazíte **přidat odkaz na** dialogové okno.  
  
5.  Klikněte na kartu s názvem bez přípony **projekty**. Projekt **ctlClockLib** bude uvedena v **název projektu**. Klikněte dvakrát na **ctlClockLib** se přidat odkaz na projekt test.  
  
6.  V Průzkumníku řešení klikněte pravým tlačítkem na **Test**a potom klikněte na **sestavení**.  
  
7.  V **sada nástrojů**, rozbalte **ctlClockLib součásti** uzlu.  
  
8.  Klikněte dvakrát na **ctlAlarmClock** přidat instanci `ctlAlarmClock` do svého formuláře.  
  
9. V **sada nástrojů**, vyhledejte a dvakrát klikněte na **DateTimePicker** přidat <xref:System.Windows.Forms.DateTimePicker> řízení do svého formuláře a poté přidejte <xref:System.Windows.Forms.Label> řízení dvojitým kliknutím na soubor **popisek**.  
  
10. Umístění ovládacích prvků na vhodné místo na formuláři pomocí myši.  
  
11. Nastavte vlastnosti tyto ovládací prvky následujícím způsobem.  
  
    |Ovládací prvek|Vlastnost|Hodnota|  
    |-------------|--------------|-----------|  
    |`label1`|**Text**|`(blank space)`|  
    ||**Jméno**|`lblTest`|  
    |`dateTimePicker1`|**Jméno**|`dtpTest`|  
    ||**Formát**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. V návrháři, klikněte dvakrát na **dtpTest**.  
  
     **Editor kódu** otevře `Private Sub dtpTest_ValueChanged`.  
  
13. Upravte kód tak, aby vypadá přibližně takto.  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. V Průzkumníku řešení klikněte pravým tlačítkem na **Test**a potom klikněte na **nastavit jako spouštěný projekt**.  
  
15. Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.  
  
     Test program spustí. Všimněte si, že je aktuální čas aktualizován v `ctlAlarmClock` ovládací prvek, a že počáteční čas je zobrazen v nabídce <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku.  
  
16. Klikněte <xref:System.Windows.Forms.DateTimePicker> kde se zobrazují počet minut za hodinu.  
  
17. Pomocí klávesnice, nastavte hodnotu pro počet minut, který je větší než aktuální čas zobrazí jednu minutu `ctlAlarmClock`.  
  
     Čas pro nastavení upozornění se zobrazí v `lblTest`. Počkejte, než zobrazených dobu dosáhnout alarmů nastavení času. Když zobrazených čas dosáhne čas, ke kterému je nastaven na upozornění, bude zvukový signál zvukových a `lblAlarm` bude flash.  
  
18. Vypnout varování kliknutím `lblAlarm`. Teď může resetovat na upozornění.  
  
     Tento názorný postup obsahuje zahrnutých počet klíčových konceptů. Jste se naučili vytvoření složeného ovládacího prvku kombinací ovládací prvky a součásti do kontejneru složeného ovládacího prvku. Jste se naučili přidání vlastnosti do vlastního ovládacího prvku a napsat kód pro implementaci vlastní funkce. V poslední části jste se dozvěděli rozšířit funkce dané složeného ovládacího prvku prostřednictvím dědičnosti a změnit funkce hostitele metody přepsání těchto metod.  
  
## <a name="see-also"></a>Viz také  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Postupy: vytváření složených ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [Postupy: zobrazení ovládacího prvku v výběr položek sady nástrojů – dialogové okno](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Součást pro vytváření obsahu návody](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
