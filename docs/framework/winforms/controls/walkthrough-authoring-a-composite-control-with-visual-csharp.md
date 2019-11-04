---
title: 'Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#'
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c1d9be77550b1255a24120c68f20d25640e0ebdf
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460627"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a>Návod: Vytvoření složeného ovládacího prvku pomocí jazyka C\#

Složené ovládací prvky poskytují prostředky, pomocí kterých lze vytvořit a znovu použít vlastní grafická rozhraní. Složený ovládací prvek je v podstatě součástí vizuální reprezentace. V takovém případě se může skládat z jednoho nebo více model Windows Forms ovládacích prvků, komponent nebo bloků kódu, které mohou rozšiřování funkcí pomocí ověření vstupu uživatele, změny vlastností zobrazení nebo provádění jiných úloh vyžadovaných autorem. Složené ovládací prvky lze umístit na model Windows Forms stejným způsobem jako jiné ovládací prvky. V první části tohoto návodu vytvoříte jednoduchý složený ovládací prvek s názvem `ctlClock`. V druhé části návodu rozšíříte funkci `ctlClock` prostřednictvím dědičnosti.

## <a name="create-the-project"></a>Vytvoření projektu

Při vytváření nového projektu zadáte jeho název pro nastavení kořenového oboru názvů, název sestavení a název projektu a zajistěte, aby byla výchozí komponenta ve správném oboru názvů.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Vytvoření knihovny ovládacích prvků ctlClockLib a ovládacího prvku ctlClock

1. V aplikaci Visual Studio vytvořte nový projekt **knihovny ovládacích prvků model Windows Forms** a pojmenujte jej **ctlClockLib**.

     Název projektu, `ctlClockLib`, je ve výchozím nastavení přiřazen také kořenovému oboru názvů. Kořenový obor názvů slouží k získání názvů komponent v sestavení. Například pokud dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete určit `ctlClock` komponentu pomocí `ctlClockLib.ctlClock.`

2. V **Průzkumník řešení**klikněte pravým tlačítkem na **UserControl1.cs**a pak klikněte na **Přejmenovat**. Změňte název souboru na `ctlClock.cs`. Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu "UserControl1", klikněte na tlačítko **Ano** .

    > [!NOTE]
    > Ve výchozím nastavení dědí složený ovládací prvek z <xref:System.Windows.Forms.UserControl> třídy poskytované systémem. Třída <xref:System.Windows.Forms.UserControl> poskytuje funkce vyžadované všemi složenými ovládacími prvky a implementuje standardní metody a vlastnosti.

3. V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.

## <a name="add-windows-controls-and-components-to-the-composite-control"></a>Přidat ovládací prvky a součásti systému Windows do složeného ovládacího prvku

Vizuální rozhraní je podstatnou součástí složeného ovládacího prvku. Toto vizuální rozhraní je implementováno přidáním jednoho nebo více ovládacích prvků Windows na plochu návrháře. V následující ukázce zahrnete ovládací prvky Windows do složeného ovládacího prvku a napíšete kód pro implementaci funkcí.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Přidání popisku a časovače do složeného ovládacího prvku

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlClock.cs**a potom klikněte na **Návrhář zobrazení**.

2. V sadě **nástrojů**rozbalte uzel **běžné ovládací prvky** a dvakrát klikněte na položku **popisek**.

     Ovládací prvek <xref:System.Windows.Forms.Label> s názvem `label1` je přidán k ovládacímu prvku na návrhové ploše.

3. V návrháři klikněte na možnost **Label1**. V okno Vlastnosti nastavte následující vlastnosti.

    |Vlastnost|Změnit na|
    |--------------|---------------|
    |**Jméno**|`lblDisplay`|
    |**Text**|`(blank space)`|
    |**Textu**|`MiddleCenter`|
    |**Font. Size**|`14`|

4. V sadě **nástrojů**rozbalte uzel **komponenty** a dvakrát klikněte na položku **časovač**.

     Vzhledem k tomu, že <xref:System.Windows.Forms.Timer> je komponenta, nemá v době běhu žádná vizuální reprezentace. Proto se nezobrazí s ovládacími prvky na návrhové ploše, ale spíše v **Návrháři komponent** (zásobník na spodní straně návrhové plochy).

5. V **Návrháři komponent**klikněte na **Timer1**a pak nastavte vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> na `1000` a vlastnost <xref:System.Windows.Forms.Timer.Enabled%2A> na `true`.

     Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> řídí frekvenci, se kterou <xref:System.Windows.Forms.Timer> komponenta se zaškrtne. Pokaždé, když `timer1`, spustí kód v události `timer1_Tick`. Interval představuje počet milisekund mezi takty.

6. V **Návrháři komponent**poklikejte na **Timer1** a přejděte na událost `timer1_Tick` pro `ctlClock`.

7. Upravte kód tak, aby vypadal jako následující ukázka kódu. Nezapomeňte změnit modifikátor přístupu z `private` na `protected`.

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     Tento kód způsobí, že se aktuální čas zobrazí v `lblDisplay`. Vzhledem k tomu, že interval `timer1` byl nastaven na hodnotu `1000`, bude tato událost provedena každých tisíc milisekund, čímž se aktualizuje aktuální čas každou sekundu.

8. Upravte metodu, kterou chcete přepsat pomocí klíčového slova `virtual`. Další informace najdete v části "dědění z uživatelského ovládacího prvku" níže.

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.

## <a name="add-properties-to-the-composite-control"></a>Přidat vlastnosti do složeného ovládacího prvku

Ovládací prvek hodiny nyní zapouzdřuje ovládací prvek <xref:System.Windows.Forms.Label> a <xref:System.Windows.Forms.Timer> komponentu, z nichž každá má vlastní sadu vlastních vlastností. Přestože jednotlivé vlastnosti těchto ovládacích prvků nebudou k dispozici pro následné uživatele vašeho ovládacího prvku, můžete vytvořit a vystavit vlastní vlastnosti zápisem příslušných bloků kódu. V následujícím postupu přidáte vlastnosti ovládacího prvku, který uživateli umožňuje změnit barvu pozadí a textu.

### <a name="to-add-a-property-to-your-composite-control"></a>Přidání vlastnosti do složeného ovládacího prvku

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlClock.cs**a pak klikněte na **Zobrazit kód**.

     Otevře se **Editor kódu** pro váš ovládací prvek.

2. Vyhledejte příkaz `public partial class ctlClock`. Pod levou složenou závorku (`{)`zadejte následující kód.

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     Tyto příkazy vytvoří soukromé proměnné, které použijete k uložení hodnot pro vlastnosti, které se chystáte vytvořit.

3. Zadejte nebo vložte následující kód pod deklaracemi proměnných z kroku 2.

    ```csharp
    // Declares the name and type of the property.
    public Color ClockBackColor
    {
        // Retrieves the value of the private variable colBColor.
        get
        {
            return colBColor;
        }
        // Stores the selected value in the private variable colBColor, and
        // updates the background color of the label control lblDisplay.
        set
        {
            colBColor = value;
            lblDisplay.BackColor = colBColor;
        }
    }
    // Provides a similar set of instructions for the foreground color.
    public Color ClockForeColor
    {
        get
        {
            return colFColor;
        }
        set
        {
            colFColor = value;
            lblDisplay.ForeColor = colFColor;
        }
    }
    ```

     Předchozí kód zpřístupňuje dvě vlastní vlastnosti, `ClockForeColor` a `ClockBackColor`, k dispozici dalším uživatelům tohoto ovládacího prvku. Příkazy `get` a `set` poskytují úložiště a načtení hodnoty vlastnosti a také kód pro implementaci funkcí vhodných pro vlastnost.

4. V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.

## <a name="test-the-control"></a>Testování ovládacího prvku

Ovládací prvky nejsou samostatné aplikace; musí být hostovány v kontejneru. Otestujte chování ovládacího prvku za běhu a využijte jeho vlastnosti pomocí **kontejneru testu UserControl**. Další informace naleznete v tématu [How to: test runtime Behavior prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

### <a name="to-test-your-control"></a>Testování ovládacího prvku

1. Stisknutím klávesy **F5** Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**.

2. V mřížce vlastností kontejneru testu Najděte vlastnost `ClockBackColor` a potom vyberte vlastnost, která zobrazí paletu barev.

3. Vyberte barvu kliknutím na ni.

   Barva pozadí ovládacího prvku se změní na barvu, kterou jste vybrali.

4. Pomocí podobné posloupnosti událostí ověřte, zda vlastnost `ClockForeColor` pracuje podle očekávání.

   V této části a předchozích částech jste viděli, jak mohou být komponenty a ovládací prvky systému Windows kombinovány s kódem a balíčkem, aby poskytovaly vlastní funkce ve formě složeného ovládacího prvku. Naučili jste se vystavit vlastnosti ve složeném ovládacím prvku a jak otestovat ovládací prvek po jeho dokončení. V další části se dozvíte, jak vytvořit zděděný složený ovládací prvek pomocí `ctlClock` jako základu.

## <a name="inherit-from-a-composite-control"></a>Zdědit ze složeného ovládacího prvku

V předchozích částech jste zjistili, jak zkombinovat ovládací prvky, komponenty a kód Windows do opakovaně použitelných složených ovládacích prvků. Složený ovládací prvek se teď dá použít jako základ, na kterém můžou být sestavené další ovládací prvky. Proces odvození třídy ze základní třídy se nazývá *Dědičnost*. V této části vytvoříte složený ovládací prvek s názvem `ctlAlarmClock`. Tento ovládací prvek bude odvozen z jeho nadřazeného ovládacího prvku `ctlClock`. Naučíte se rozšíření funkcí `ctlClock` přepsáním nadřazených metod a přidáním nových metod a vlastností.

Prvním krokem při vytváření zděděného ovládacího prvku je jeho odvození od jeho nadřazené položky. Tato akce vytvoří nový ovládací prvek, který obsahuje všechny vlastnosti, metody a grafické charakteristiky nadřazeného ovládacího prvku, ale může také sloužit jako základ pro přidání nových nebo upravených funkcí.

### <a name="to-create-the-inherited-control"></a>Vytvoření zděděného ovládacího prvku

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **ctlClockLib**, přejděte na **Přidat**a pak klikněte na **uživatelský ovládací prvek**.

     Otevře se dialogové okno **Přidat novou položku** .

2. Vyberte šablonu **zděděného uživatelského ovládacího prvku** .

3. Do pole **název** zadejte `ctlAlarmClock.cs`a pak klikněte na **Přidat**.

     Zobrazí se dialogové okno **Výběr dědičnosti** .

4. V části **název součásti**poklikejte na **ctlClock**.

5. V **Průzkumník řešení**Procházet aktuální projekty.

    > [!NOTE]
    > Do aktuálního projektu byl přidán soubor s názvem **ctlAlarmClock.cs** .

### <a name="add-the-alarm-properties"></a>Přidání vlastností alarmu

Vlastnosti jsou přidány do zděděného ovládacího prvku stejným způsobem jako přidaným do složeného ovládacího prvku. Nyní použijete syntaxi deklarace vlastností k přidání dvou vlastností do ovládacího prvku: `AlarmTime`, který uloží hodnotu data a času, kdy má alarm přejít, a `AlarmSet`, který označuje, zda je alarm nastaven.

#### <a name="to-add-properties-to-your-composite-control"></a>Přidání vlastností do složeného ovládacího prvku

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlAlarmClock**a pak klikněte na **Zobrazit kód**.

2. Vyhledejte příkaz `public class`. Všimněte si, že ovládací prvek dědí z `ctlClockLib.ctlClock`. Pod levou složenou závorku (příkaz`{)` zadejte následující kód.

    ```csharp
    private DateTime dteAlarmTime;
    private bool blnAlarmSet;
    // These properties will be declared as public to allow future
    // developers to access them.
    public DateTime AlarmTime
    {
        get
        {
            return dteAlarmTime;
        }
        set
        {
            dteAlarmTime = value;
        }
    }
    public bool AlarmSet
    {
        get
        {
            return blnAlarmSet;
        }
        set
        {
            blnAlarmSet = value;
        }
    }
    ```

### <a name="add-to-the-graphical-interface-of-the-control"></a>Přidat do grafického rozhraní ovládacího prvku

Zděděný ovládací prvek má vizuální rozhraní, které je identické s ovládacím prvkem, ze kterého dědí. Má stejné ovládací prvky jako svůj nadřazený ovládací prvek, ale vlastnosti ovládacích prvků nebudou k dispozici, pokud nebyly výslovně zpřístupněny. Můžete přidat do grafického rozhraní zděděného složeného ovládacího prvku stejným způsobem, jako byste přidali do jakéhokoli složeného ovládacího prvku. Pokud chcete pokračovat v přidávání do vizuálního rozhraní pro budíky, přidejte ovládací prvek popisek, který bude při zvukovém alarmu blikat.

#### <a name="to-add-the-label-control"></a>Přidání ovládacího prvku popisek

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na **Návrhář zobrazení**.

     V hlavním okně se otevře Návrhář pro `ctlAlarmClock`.

2. Klikněte na zobrazenou část ovládacího prvku a zobrazte okno Vlastnosti.

    > [!NOTE]
    > Všechny vlastnosti jsou zobrazeny šedě. To značí, že tyto vlastnosti jsou nativní pro `lblDisplay` a nelze je upravit nebo použít v okno Vlastnosti. Ve výchozím nastavení jsou ovládací prvky obsažené ve složeném ovládacím prvku `private`a jejich vlastnosti nejsou přístupné žádným způsobem.

    > [!NOTE]
    > Pokud chcete, aby následující uživatelé složeného ovládacího prvku měli přístup k vnitřním ovládacím prvkům, deklarujte je jako `public` nebo `protected`. To vám umožní nastavit a upravit vlastnosti ovládacích prvků obsažených v rámci složeného ovládacího prvku pomocí příslušného kódu.

3. Přidejte ovládací prvek <xref:System.Windows.Forms.Label> do složeného ovládacího prvku.

4. Pomocí myši přetáhněte ovládací prvek <xref:System.Windows.Forms.Label> hned pod pole zobrazení. V okno Vlastnosti nastavte následující vlastnosti.

    |Vlastnost|Nastavením|
    |--------------|-------------|
    |**Jméno**|`lblAlarm`|
    |**Text**|**Požární!**|
    |**Textu**|`MiddleCenter`|
    |**Zobrazeny**|`false`|

### <a name="add-the-alarm-functionality"></a>Přidání funkce alarm

V předchozích postupech jste přidali vlastnosti a ovládací prvek, který umožní funkci alarmu ve složeném ovládacím prvku. V tomto postupu přidáte kód, který bude porovnávat aktuální čas s časem alarmu, a pokud se jedná o stejnou dobu, aby se pomohlo zablikat alarm. Přepsáním metody `timer1_Tick` `ctlClock` a přidáním dalšího kódu do něj rozšíříte schopnost `ctlAlarmClock` a zároveň zachováte všechny podstatné funkce `ctlClock`.

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>Přepsání metody timer1_Tick pro ctlClock

1. V **editoru kódu**vyhledejte příkaz `private bool blnAlarmSet;`. Hned pod ním přidejte následující příkaz.

    ```csharp
    private bool blnColorTicker;
    ```

2. V **editoru kódu**vyhledejte pravou složenou závorku (`})` na konci třídy. Těsně před složenou závorku přidejte následující kód.

    ```csharp
    protected override void timer1_Tick(object sender, System.EventArgs e)
    {
        // Calls the Timer1_Tick method of ctlClock.
        base.timer1_Tick(sender, e);
        // Checks to see if the alarm is set.
        if (AlarmSet == false)
            return;
        else
            // If the date, hour, and minute of the alarm time are the same as
            // the current time, flash an alarm.
        {
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)
            {
                // Sets lblAlarmVisible to true, and changes the background color based on
                // the value of blnColorTicker. The background color of the label
                // will flash once per tick of the clock.
                lblAlarm.Visible = true;
                if (blnColorTicker == false)
                {
                    lblAlarm.BackColor = Color.Red;
                    blnColorTicker = true;
                }
                else
                {
                    lblAlarm.BackColor = Color.Blue;
                    blnColorTicker = false;
                }
            }
            else
            {
                // Once the alarm has sounded for a minute, the label is made
                // invisible again.
                lblAlarm.Visible = false;
            }
        }
    }
    ```

     Přidání tohoto kódu dosahuje několika úloh. Příkaz `override` přesměruje ovládací prvek na použití této metody místo metody, která byla zděděna ze základního ovládacího prvku. Při volání této metody volá metodu, kterou Přepisuje, vyvoláním příkazu `base.timer1_Tick`, aby se zajistilo, že všechny funkce zahrnuté v původním ovládacím prvku budou v tomto ovládacím prvku reprodukovány. Potom spustí další kód, který bude začlenit funkci alarmu. Pokud dojde k alarmu, zobrazí se ovládací prvek popisku, který bude blikat.

     Ovládací prvek hodiny budíku je skoro kompletní. Jediná věc, kterou zbývá, je implementovat způsob, jak ho vypnout. K tomu je třeba přidat kód do metody `lblAlarm_Click`.

#### <a name="to-implement-the-shutoff-method"></a>Implementace metody shutoff

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlAlarmClock.cs**a potom klikněte na **Návrhář zobrazení**.

     Otevře se Návrhář.

2. Přidejte k ovládacímu prvku tlačítko. Nastavte vlastnosti tlačítka následujícím způsobem.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Jméno**|`btnAlarmOff`|
    |**Text**|**Zakázat alarm**|

3. V Návrháři poklikejte na **btnAlarmOff**.

     Otevře se **Editor kódu** na `private void btnAlarmOff_Click` řádek.

4. Upravte tuto metodu tak, aby vypadala jako následující kód.

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.

### <a name="use-the-inherited-control-on-a-form"></a>Použití zděděného ovládacího prvku na formuláři

Zděděný ovládací prvek lze otestovat stejným způsobem jako ovládací prvek základní třídy, `ctlClock`: stisknutím klávesy **F5** sestavíte projekt a spustíte ovládací prvek v **kontejneru testu UserControl**. Další informace naleznete v tématu [How to: test runtime Behavior prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

Chcete-li ovládací prvek použít, budete ho muset hostovat na formuláři. Stejně jako u standardního složeného ovládacího prvku nemůže zděděný složený ovládací prvek samostatně a musí být hostovaný ve formuláři nebo jiném kontejneru. Vzhledem k tomu, že `ctlAlarmClock` má větší hloubku funkčnosti, je nutné k otestování dalšího kódu. V tomto postupu napíšete jednoduchý program, který bude testovat funkčnost `ctlAlarmClock`. Napíšete kód pro nastavení a zobrazení `AlarmTime` vlastnosti `ctlAlarmClock`a otestujete jeho své vlastní funkce.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Sestavení a přidání ovládacího prvku do formuláře testu

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlClockLib**a pak klikněte na **sestavit**.

2. Přidejte do řešení nový projekt **aplikace pro Windows** a pojmenujte ho **test**.

3. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro projekt testů. Kliknutím na tlačítko **Přidat odkaz** zobrazíte dialogové okno **Přidat odkaz** . Klikněte na kartu s označením **projekty**. Váš `ctlClockLib` projekt bude uveden v části **název projektu**. Dvojím kliknutím na projekt přidejte odkaz na testovací projekt.

4. V **Průzkumník řešení**klikněte pravým tlačítkem na **test**a pak klikněte na **sestavit**.

5. V **sadě nástrojů**rozbalte uzel **součásti ctlClockLib** .

6. Dvojím kliknutím na **ctlAlarmClock** přidáte kopii `ctlAlarmClock` do formuláře.

7. Na **panelu nástrojů**vyhledejte **DateTimePicker** a dvakrát klikněte na položku a přidejte ovládací prvek <xref:System.Windows.Forms.DateTimePicker> do formuláře a poté přidejte ovládací prvek <xref:System.Windows.Forms.Label> dvojitým kliknutím na položku **Label**.

8. Pomocí myši umístěte ovládací prvky na vhodné místo na formuláři.

9. Následujícím způsobem nastavte vlastnosti těchto ovládacích prvků.

    |Control|Vlastnost|Hodnota|
    |-------------|--------------|-----------|
    |`label1`|**Text**|`(blank space)`|
    ||**Jméno**|`lblTest`|
    |`dateTimePicker1`|**Jméno**|`dtpTest`|
    ||**Formátovat**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. V Návrháři poklikejte na **dtpTest**.

     Otevře se **Editor kódu** pro `private void dtpTest_ValueChanged`.

11. Upravte kód tak, aby vypadal takto:

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. V **Průzkumník řešení**klikněte pravým tlačítkem na **test**a pak klikněte na **nastavit jako spouštěný projekt**.

13. V nabídce **ladit** klikněte na **Spustit ladění**.

     Spustí se testovací program. Všimněte si, že aktuální čas je aktualizován v ovládacím prvku `ctlAlarmClock` a že počáteční čas je zobrazen v ovládacím prvku <xref:System.Windows.Forms.DateTimePicker>.

14. Klikněte na <xref:System.Windows.Forms.DateTimePicker>, kde se zobrazí minuty z hodiny.

15. Pomocí klávesnice nastavte hodnotu minuty, která je o jednu minutu větší než aktuální čas zobrazený `ctlAlarmClock`.

     Čas nastavení alarmu se zobrazí v `lblTest`. Počkejte, až zobrazený čas dorazí na čas nastavení alarmu. Když zobrazený čas dosáhne doby, na kterou je nastavené alarm, `lblAlarm` bude blikat.

16. Vypněte alarm kliknutím na `btnAlarmOff`. Nyní můžete resetovat alarm.

Tento článek pojednává o řadě klíčových konceptů. Naučili jste se vytvořit složený ovládací prvek kombinováním ovládacích prvků a součástí do složeného kontejneru ovládacích prvků. Seznámili jste se s přidáním vlastností do ovládacího prvku a při psaní kódu pro implementaci vlastních funkcí. V poslední části jste se dozvěděli o rozšíření funkcí daného složeného ovládacího prvku prostřednictvím dědičnosti a ke změně funkčnosti metod hostitele přepsáním těchto metod.

## <a name="see-also"></a>Viz také:

- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
- [Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
