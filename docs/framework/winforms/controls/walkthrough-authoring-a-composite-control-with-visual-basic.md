---
title: 'Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu'
ms.date: 03/30/2017
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
ms.openlocfilehash: cb54ef372e6da551b95f1edf61e3844b9dcba4c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950044"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu
Složené ovládací prvky poskytují prostředky, pomocí kterých lze vytvořit a znovu použít vlastní grafická rozhraní. Složený ovládací prvek je v podstatě součástí vizuální reprezentace. V takovém případě se může skládat z jednoho nebo více model Windows Forms ovládacích prvků, komponent nebo bloků kódu, které mohou rozšiřování funkcí pomocí ověření vstupu uživatele, změny vlastností zobrazení nebo provádění jiných úloh vyžadovaných autorem. Složené ovládací prvky lze umístit na model Windows Forms stejným způsobem jako jiné ovládací prvky. V první části tohoto návodu vytvoříte jednoduchý složený ovládací prvek s názvem `ctlClock`. V druhé části návodu rozšíříte funkce `ctlClock` nástroje prostřednictvím dědičnosti.

## <a name="creating-the-project"></a>Vytvoření projektu
 Při vytváření nového projektu zadáte jeho název pro nastavení kořenového oboru názvů, název sestavení a název projektu a zajistěte, aby byla výchozí komponenta ve správném oboru názvů.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Vytvoření knihovny ovládacích prvků ctlClockLib a ovládacího prvku ctlClock

1. V nabídce **soubor** přejděte na příkaz **Nový**a kliknutím na položku **projekt** otevřete dialogové okno **Nový projekt** .

2. V seznamu Visual Basic projektů vyberte šablonu projektu **Knihovna ovládacích prvků systému Windows** , zadejte `ctlClockLib` do pole **název** a klikněte na tlačítko **OK**.

     Název projektu, `ctlClockLib`, je ve výchozím nastavení přiřazen ke kořenovému oboru názvů. Kořenový obor názvů slouží k získání názvů komponent v sestavení. Například pokud dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete určit svou `ctlClock` komponentu pomocí`ctlClockLib.ctlClock.`

3. V Průzkumník řešení klikněte pravým tlačítkem na **UserControl1. vb**a pak klikněte na **Přejmenovat**. Změňte název souboru na `ctlClock.vb`. Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu "UserControl1", klikněte na tlačítko **Ano** .

    > [!NOTE]
    > Ve výchozím nastavení dědí složený ovládací prvek ze <xref:System.Windows.Forms.UserControl> třídy poskytované systémem. <xref:System.Windows.Forms.UserControl> Třída poskytuje funkce vyžadované všemi složenými ovládacími prvky a implementuje standardní metody a vlastnosti.

4. V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Přidávání ovládacích prvků a součástí systému Windows do složeného ovládacího prvku
 Vizuální rozhraní je podstatnou součástí složeného ovládacího prvku. Toto vizuální rozhraní je implementováno přidáním jednoho nebo více ovládacích prvků Windows na plochu návrháře. V následující ukázce zahrnete ovládací prvky Windows do složeného ovládacího prvku a napíšete kód pro implementaci funkcí.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Přidání popisku a časovače do složeného ovládacího prvku

1. V Průzkumník řešení klikněte pravým tlačítkem myši na **ctlClock. vb**a potom klikněte na tlačítko **Návrhář zobrazení**.

2. V sadě nástrojů rozbalte uzel **běžné ovládací prvky** a dvakrát klikněte na položku **popisek**.

     Ovládací prvek s `Label1` názvem je přidán k ovládacímu prvku na návrhové ploše. <xref:System.Windows.Forms.Label>

3. V návrháři klikněte na možnost **Label1**. V okno Vlastnosti nastavte následující vlastnosti.

    |Vlastnost|Změnit na|
    |--------------|---------------|
    |**Název**|`lblDisplay`|
    |**Text**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**Font. Size**|`14`|

4. V sadě **nástrojů**rozbalte uzel **komponenty** a dvakrát klikněte na položku **časovač**.

     Vzhledem k <xref:System.Windows.Forms.Timer> tomu, že se jedná o komponentu, nemá v době běhu žádná vizuální reprezentace. Proto se nezobrazí s ovládacími prvky na návrhové ploše, ale spíše v Návrháři komponent (zásobník na spodní straně návrhové plochy).

5. V Návrháři komponent klikněte na **Timer1**a pak nastavte <xref:System.Windows.Forms.Timer.Interval%2A> <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost na `1000`. `True`

     <xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost určuje četnost, se kterou se komponenta časovače zaškrtne. Každé časové `Timer1` impulsy spustí kód `Timer1_Tick` v události. Interval představuje počet milisekund mezi takty.

6. V Návrháři komponent poklikejte na **Timer1** a přejděte na `Timer1_Tick` událost pro. `ctlClock`

7. Upravte kód tak, aby vypadal jako následující ukázka kódu. Nezapomeňte změnit modifikátor přístupu z `Private` na. `Protected`

    ```vb
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles Timer1.Tick
        ' Causes the label to display the current time.
        lblDisplay.Text = Format(Now, "hh:mm:ss")
    End Sub
    ```

     Tento kód způsobí, že bude aktuální čas zobrazen v `lblDisplay`. Vzhledem k tomu, `Timer1` že interval byl `1000`nastaven na hodnotu, bude tato událost provedena každých tisíc milisekund, čímž se aktualizuje aktuální čas každou sekundu.

8. Upravte metodu, kterou chcete přepsat. Další informace najdete v části "dědění z uživatelského ovládacího prvku" níže.

    ```vb
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _
        e As System.EventArgs) Handles Timer1.Tick
    ```

9. V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.

## <a name="adding-properties-to-the-composite-control"></a>Přidání vlastností do složeného ovládacího prvku
 Ovládací prvek hodiny nyní zapouzdřuje <xref:System.Windows.Forms.Label> ovládací prvek <xref:System.Windows.Forms.Timer> a komponentu, z nichž každá má svou vlastní sadu vlastností. Přestože jednotlivé vlastnosti těchto ovládacích prvků nebudou k dispozici pro následné uživatele vašeho ovládacího prvku, můžete vytvořit a vystavit vlastní vlastnosti zápisem příslušných bloků kódu. V následujícím postupu přidáte vlastnosti ovládacího prvku, který uživateli umožňuje změnit barvu pozadí a textu.

### <a name="to-add-a-property-to-your-composite-control"></a>Přidání vlastnosti do složeného ovládacího prvku

1. V Průzkumník řešení klikněte pravým tlačítkem na **ctlClock. vb**a pak klikněte na **Zobrazit kód**.

     Otevře se Editor kódu pro váš ovládací prvek.

2. `Public Class ctlClock` Vyhledejte příkaz. Pod ní zadejte následující kód.

    ```vb
    Private colFColor as Color
    Private colBColor as Color
    ```

     Tyto příkazy vytvoří soukromé proměnné, které použijete k uložení hodnot pro vlastnosti, které se chystáte vytvořit.

3. Vložte následující kód pod deklarace proměnných z kroku 2.

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

     Předchozí kód vytvoří dvě vlastní vlastnosti `ClockForeColor` a `ClockBackColor`zpřístupní pro následné uživatele tohoto `Property` ovládacího prvku vyvoláním příkazu. Příkazy `Get` a`Set` poskytují úložiště a načtení hodnoty vlastnosti a také kód pro implementaci funkcí vhodných pro vlastnost.

4. V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.

## <a name="testing-the-control"></a>Testování ovládacího prvku
 Ovládací prvky nejsou samostatné projekty; musí být hostovány v kontejneru. Otestujte chování ovládacího prvku za běhu a využijte jeho vlastnosti pomocí **kontejneru testu UserControl**. Další informace najdete v tématu [jak: Otestuje chování prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)v době běhu.

### <a name="to-test-your-control"></a>Testování ovládacího prvku

1. Stisknutím klávesy F5 Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**.

2. V mřížce vlastností kontejneru testů vyberte `ClockBackColor` vlastnost a potom kliknutím na šipku rozevíracího seznamu zobrazte paletu barev.

3. Vyberte barvu kliknutím na ni.

     Barva pozadí ovládacího prvku se změní na barvu, kterou jste vybrali.

4. Pomocí podobné posloupnosti událostí ověřte, zda `ClockForeColor` vlastnost pracuje podle očekávání.

5. Kliknutím na tlačítko **Zavřít** zavřete **kontejner testu UserControl**.

     V této části a předchozích částech jste viděli, jak mohou být komponenty a ovládací prvky systému Windows kombinovány s kódem a balíčkem, aby poskytovaly vlastní funkce ve formě složeného ovládacího prvku. Naučili jste se vystavit vlastnosti ve složeném ovládacím prvku a jak otestovat ovládací prvek po jeho dokončení. V další části se dozvíte, jak vytvořit zděděný složený ovládací prvek pomocí `ctlClock` jako základu.

## <a name="inheriting-from-a-composite-control"></a>Dědění ze složeného ovládacího prvku
 V předchozích částech jste zjistili, jak zkombinovat ovládací prvky, komponenty a kód Windows do opakovaně použitelných složených ovládacích prvků. Složený ovládací prvek se teď dá použít jako základ, na kterém můžou být sestavené další ovládací prvky. Proces odvození třídy ze základní třídy se nazývá *Dědičnost*. V této části vytvoříte složený ovládací prvek, který se nazývá `ctlAlarmClock`. Tento ovládací prvek bude odvozen z jeho nadřazeného ovládacího prvku `ctlClock`. Naučíte se rozšíření funkcí `ctlClock` přepsáním nadřazených metod a přidáním nových metod a vlastností.

 Prvním krokem při vytváření zděděného ovládacího prvku je jeho odvození od jeho nadřazené položky. Tato akce vytvoří nový ovládací prvek, který obsahuje všechny vlastnosti, metody a grafické charakteristiky nadřazeného ovládacího prvku, ale může také sloužit jako základ pro přidání nových nebo upravených funkcí.

### <a name="to-create-the-inherited-control"></a>Vytvoření zděděného ovládacího prvku

1. V Průzkumník řešení klikněte pravým tlačítkem myši na **ctlClockLib**, přejděte na **Přidat**a pak klikněte na **uživatelský ovládací prvek**.

     **Přidat novou položku** zobrazí se dialogové okno.

2. Vyberte šablonu **zděděného uživatelského ovládacího prvku** .

3. Do pole **název** zadejte `ctlAlarmClock.vb`a pak klikněte na **Přidat**.

     Zobrazí se dialogové okno **Výběr dědičnosti** .

4. V části **název součásti**poklikejte na **ctlClock**.

5. V Průzkumník řešení Procházet aktuální projekty.

    > [!NOTE]
    > Do aktuálního projektu byl přidán soubor s názvem **ctlAlarmClock. vb** .

### <a name="adding-the-alarm-properties"></a>Přidání vlastností alarmu
 Vlastnosti jsou přidány do zděděného ovládacího prvku stejným způsobem jako přidaným do složeného ovládacího prvku. Nyní použijete syntaxi deklarace vlastností k přidání dvou vlastností do ovládacího prvku: `AlarmTime`, který bude uchovávat hodnotu data a času, kdy má alarm přejít, a `AlarmSet`, který bude označovat, zda je alarm nastaven.

#### <a name="to-add-properties-to-your-composite-control"></a>Přidání vlastností do složeného ovládacího prvku

1. V Průzkumník řešení klikněte pravým tlačítkem na **ctlAlarmClock**a pak klikněte na **Zobrazit kód**.

2. Vyhledejte deklaraci třídy pro ovládací prvek ctlAlarmClock, který se zobrazí `Public Class ctlAlarmClock`jako.  V deklaraci třídy vložte následující kód.

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

### <a name="adding-to-the-graphical-interface-of-the-control"></a>Přidání do grafického rozhraní ovládacího prvku
 Zděděný ovládací prvek má vizuální rozhraní, které je identické s ovládacím prvkem, ze kterého dědí. Má stejné ovládací prvky jako svůj nadřazený ovládací prvek, ale vlastnosti ovládacích prvků nebudou k dispozici, pokud nebyly výslovně zpřístupněny. Můžete přidat do grafického rozhraní zděděného složeného ovládacího prvku stejným způsobem, jako byste přidali do jakéhokoli složeného ovládacího prvku. Pokud chcete pokračovat v přidávání do vizuálního rozhraní pro budíky, přidejte ovládací prvek popisek, který bude při zvukovém alarmu blikat.

#### <a name="to-add-the-label-control"></a>Přidání ovládacího prvku popisek

1. V Průzkumník řešení klikněte pravým tlačítkem myši na **ctlAlarmClock**a pak klikněte na **Návrhář zobrazení**.

     Návrhář pro `ctlAlarmClock` se otevře v hlavním okně.

2. Klikněte `lblDisplay` na tlačítko (zobrazená část ovládacího prvku) a zobrazte okno Vlastnosti.

    > [!NOTE]
    > Všechny vlastnosti jsou zobrazeny šedě. To znamená, že tyto vlastnosti jsou nativní `lblDisplay` a nelze je upravovat nebo k nim nelze přicházet v okno Vlastnosti. Ve výchozím nastavení jsou `Private`ovládací prvky obsažené ve složeném ovládacím prvku a jejich vlastnosti přístupné žádným způsobem.

    > [!NOTE]
    > Pokud chcete, aby následující uživatelé složeného ovládacího prvku měli přístup k vnitřním ovládacím prvkům, deklarujte `Public` je `Protected`jako nebo. To vám umožní nastavit a upravit vlastnosti ovládacích prvků obsažených v rámci složeného ovládacího prvku pomocí příslušného kódu.

3. <xref:System.Windows.Forms.Label> Přidejte ovládací prvek do složeného ovládacího prvku.

4. Pomocí myši přetáhněte <xref:System.Windows.Forms.Label> ovládací prvek hned pod zobrazeným polem. V okno Vlastnosti nastavte následující vlastnosti.

    |Vlastnost|Nastavení|
    |--------------|-------------|
    |**Název**|`lblAlarm`|
    |**Text**|**Alarm!**|
    |**TextAlign**|`MiddleCenter`|
    |**Zobrazeny**|`False`|

### <a name="adding-the-alarm-functionality"></a>Přidání funkce alarmu
 V předchozích postupech jste přidali vlastnosti a ovládací prvek, který umožní funkci alarmu ve složeném ovládacím prvku. V tomto postupu přidáte kód, který bude porovnávat aktuální čas s časem alarmu, a pokud jsou stejné, budete chtít zvuk a přehrát alarm. Tím, že `ctlClock` `ctlClock`přepíšete `Timer1_Tick` metodu a přidáte do ní další kód, rozšíříte možnost azachováte`ctlAlarmClock` všechny podstatné funkce.

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>Přepsání metody Timer1_Tick pro ctlClock

1. V Průzkumník řešení klikněte pravým tlačítkem na **ctlAlarmClock. vb**a pak klikněte na **Zobrazit kód**.

2. `Private blnAlarmSet As Boolean` Vyhledejte příkaz. Hned pod ním přidejte následující příkaz.

    ```vb
    Dim blnColorTicker as Boolean
    ```

3. `End Class` Vyhledejte příkaz v dolní části stránky. Těsně před `End Class` příkazem přidejte následující kód.

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

     Přidání tohoto kódu dosahuje několika úloh. `Overrides` Příkaz nasměruje ovládací prvek na použití této metody místo metody, která byla zděděna ze základního ovládacího prvku. Při volání této metody volá metodu, kterou Přepisuje, vyvoláním `MyBase.Timer1_Tick` příkazu, čímž se zajistí, že všechny funkce zahrnuté v původním ovládacím prvku budou v tomto ovládacím prvku reprodukovány. Potom spustí další kód, který bude začlenit funkci alarmu. Pokud dojde k alarmu, zobrazí se ovládací prvek popisku, který se bude objevovat zvukovým signálem.

    > [!NOTE]
    > Vzhledem k tomu, že přepisujete zděděnou obslužnou rutinu události, nemusíte zadávat událost `Handles` s klíčovým slovem. Událost je již zapojena. Vše, co přepisujete, je implementace obslužné rutiny.

     Ovládací prvek hodiny budíku je skoro kompletní. Jediná věc, kterou zbývá, je implementovat způsob, jak ho vypnout. K tomu je třeba přidat kód do `lblAlarm_Click` metody.

#### <a name="to-implement-the-shutoff-method"></a>Implementace metody shutoff

1. V Průzkumník řešení klikněte pravým tlačítkem myši na **ctlAlarmClock. vb**a potom klikněte na tlačítko **Návrhář zobrazení**.

2. V Návrháři poklikejte na **lblAlarm**. Otevře se **Editor kódu** na `Private Sub lblAlarm_Click` řádku.

3. Upravte tuto metodu tak, aby vypadala jako následující kód.

    ```vb
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _
     System.EventArgs) Handles lblAlarm.Click
        ' Turns off the alarm.
        AlarmSet = False
        ' Hides the flashing label.
        lblAlarm.Visible = False
    End Sub
    ```

4. V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.

### <a name="using-the-inherited-control-on-a-form"></a>Použití zděděného ovládacího prvku na formuláři
 Zděděný ovládací prvek lze otestovat stejným způsobem jako ovládací prvek `ctlClock`základní třídy: Stisknutím klávesy F5 Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**. Další informace najdete v tématu [jak: Otestuje chování prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)v době běhu.

 Chcete-li ovládací prvek použít, budete ho muset hostovat na formuláři. Stejně jako u standardního složeného ovládacího prvku nemůže zděděný složený ovládací prvek samostatně a musí být hostovaný ve formuláři nebo jiném kontejneru. Vzhledem `ctlAlarmClock` k tomu, že má větší hloubku funkčnosti, je nutné k otestování dalšího kódu. V tomto postupu napíšete jednoduchý program, který bude testovat funkčnost `ctlAlarmClock`nástroje. Napíšete kód pro nastavení a zobrazení `AlarmTime` `ctlAlarmClock`vlastnosti a otestujete své své vlastní funkce.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Sestavení a přidání ovládacího prvku do formuláře testu

1. V Průzkumník řešení klikněte pravým tlačítkem na **ctlClockLib**a pak klikněte na **sestavit**.

2. V nabídce **soubor** přejděte na příkaz **Přidat**a poté klikněte na možnost **Nový projekt**.

3. Přidejte do řešení nový projekt **aplikace pro Windows** a pojmenujte ho `Test`.

     **Testovací** projekt je přidán do Průzkumník řešení.

4. V Průzkumník řešení klikněte pravým tlačítkem myši `Test` na uzel projektu a potom klikněte na tlačítko **Přidat odkaz** . zobrazí se dialogové okno **Přidat odkaz** .

5. Klikněte na kartu s označením **projekty**. Projekt **ctlClockLib** bude uveden v části **název projektu**. Dvojím kliknutím na **ctlClockLib** přidejte odkaz na testovací projekt.

6. V Průzkumník řešení klikněte pravým tlačítkem na **test**a pak klikněte na **sestavit**.

7. V **sadě nástrojů**rozbalte uzel **součásti ctlClockLib** .

8. Dvojím kliknutím na **ctlAlarmClock** přidejte instanci `ctlAlarmClock` do formuláře.

9. V **sadě nástrojů**Najděte a dvakrát klikněte na **DateTimePicker** a přidejte <xref:System.Windows.Forms.DateTimePicker> ovládací prvek do <xref:System.Windows.Forms.Label> formuláře a pak přidejte ovládací prvek dvojitým kliknutím na **popisek**.

10. Pomocí myši umístěte ovládací prvky na vhodné místo na formuláři.

11. Následujícím způsobem nastavte vlastnosti těchto ovládacích prvků.

    |Control|Vlastnost|Value|
    |-------------|--------------|-----------|
    |`label1`|**Text**|`(blank space)`|
    ||**Název**|`lblTest`|
    |`dateTimePicker1`|**Název**|`dtpTest`|
    ||**Formátovat**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

12. V Návrháři poklikejte na **dtpTest**.

     Otevře`Private Sub dtpTest_ValueChanged`se **Editor kódu** .

13. Upravte kód tak, aby vypadal takto:

    ```vb
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles dtpTest.ValueChanged
        ctlAlarmClock1.AlarmTime = dtpTest.Value
        ctlAlarmClock1.AlarmSet = True
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _
            "hh:mm")
    End Sub
    ```

14. V Průzkumník řešení klikněte pravým tlačítkem na **test**a pak klikněte na **nastavit jako spouštěný projekt**.

15. Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.

     Spustí se testovací program. Všimněte si, že aktuální čas je aktualizován v `ctlAlarmClock` ovládacím prvku a že počáteční čas je zobrazen <xref:System.Windows.Forms.DateTimePicker> v ovládacím prvku.

16. Klikněte na <xref:System.Windows.Forms.DateTimePicker> místo, kde se zobrazují minuty hodiny.

17. Pomocí klávesnice nastavte hodnotu minuty, která je 1 minutou větší než aktuální čas zobrazený v `ctlAlarmClock`.

     Čas pro nastavení alarmu je zobrazen v `lblTest`. Počkejte, až zobrazený čas dorazí na čas nastavení alarmu. Když zobrazený čas dosáhne doby, po kterou je nastavené alarmu, bude zvukový signál zvuk `lblAlarm` a bude blikat.

18. Vypněte alarm kliknutím na tlačítko `lblAlarm`. Nyní můžete resetovat alarm.

     Tento návod pokrývá řadu klíčových konceptů. Naučili jste se vytvořit složený ovládací prvek kombinováním ovládacích prvků a součástí do složeného kontejneru ovládacích prvků. Seznámili jste se s přidáním vlastností do ovládacího prvku a při psaní kódu pro implementaci vlastních funkcí. V poslední části jste se dozvěděli o rozšíření funkcí daného složeného ovládacího prvku prostřednictvím dědičnosti a ke změně funkčnosti metod hostitele přepsáním těchto metod.

## <a name="see-also"></a>Viz také:

- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
- [Postupy: Vytváření složených ovládacích prvků](how-to-author-composite-controls.md)
- [Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
