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
ms.openlocfilehash: 3ad9aad026a1a6a1266845736d7651db77fd5d5c
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546721"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a>Návod: Vytvoření složeného ovládacího prvku pomocí c\#

Složené ovládací prvky poskytují prostředky, kterými lze vytvořit a znovu použít vlastní grafická rozhraní. Složený ovládací prvek je v podstatě součást s vizuální reprezentací. Jako takový může sestávat z jednoho nebo více ovládacích prvků, součástí nebo bloků kódu ve formulářích Systému Windows, které mohou rozšířit funkce ověřením vstupu uživatele, úpravou vlastností zobrazení nebo provedením dalších úloh vyžadovaných autorem. Složené ovládací prvky lze umístit do formulářů Windows stejným způsobem jako ostatní ovládací prvky. V první části tohoto návodu vytvoříte jednoduchý `ctlClock`složený ovládací prvek s názvem . V druhé části návodu rozšířit funkce prostřednictvím `ctlClock` dědičnosti.

## <a name="create-the-project"></a>Vytvoření projektu

Při vytváření nového projektu zadáte jeho název, chcete-li nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, aby výchozí součást byla ve správném oboru názvů.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Vytvoření knihovny ovládacích prvku ctlClockLib a ovládacího prvku ctlClock

1. V sadě Visual Studio vytvořte nový projekt **knihovny windows forms control** a pojmenujte jej **ctlClockLib**.

     Název projektu `ctlClockLib`, je také přiřazen kořenovému oboru názvů ve výchozím nastavení. Kořenový obor názvů se používá ke kvalifikaci názvů součástí v sestavě. Pokud například dvě sestavy poskytují `ctlClock`součásti s `ctlClock` názvem , můžete určit součást pomocí`ctlClockLib.ctlClock.`

2. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **UserControl1.cs**a potom klepněte na příkaz **Přejmenovat**. Změňte název `ctlClock.cs`souboru na . Klepněte na tlačítko **Ano,** když budete dotázáni, zda chcete přejmenovat všechny odkazy na prvek kódu "UserControl1".

    > [!NOTE]
    > Ve výchozím nastavení zdědí <xref:System.Windows.Forms.UserControl> složený ovládací prvek z třídy poskytované systémem. Třída <xref:System.Windows.Forms.UserControl> poskytuje funkce vyžadované všemi složenými ovládacími prvky a implementuje standardní metody a vlastnosti.

3. V nabídce **Soubor** kliknutím na **Uložit vše** projekt uložte.

## <a name="add-windows-controls-and-components-to-the-composite-control"></a>Přidání ovládacích prvků a součástí systému Windows do složeného ovládacího prvku

Vizuální rozhraní je nezbytnou součástí vašeho kompozitního ovládacího prvku. Toto vizuální rozhraní je implementováno přidáním jednoho nebo více ovládacích prvků systému Windows na povrch návrháře. V následující ukázce začleníte ovládací prvky systému Windows do složeného ovládacího prvku a napíšete kód pro implementaci funkcí.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Přidání popisku a časovače do složeného ovládacího prvku

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **ctlClock.cs**a potom klepněte na příkaz **Návrhář zobrazení**.

2. V **panelu nástrojů**rozbalte uzel **Běžné ovládací prvky** a poklepejte na **popisek**.

     Ovládací <xref:System.Windows.Forms.Label> prvek `label1` s názvem je přidán do ovládacího prvku na povrchu návrháře.

3. V návrháři klepněte na **popisek1**. V okně Vlastnosti nastavte následující vlastnosti.

    |Vlastnost|Změňte na|
    |--------------|---------------|
    |**Název**|`lblDisplay`|
    |**Text**|`(blank space)`|
    |**Textalign**|`MiddleCenter`|
    |**Písmo.Velikost**|`14`|

4. V **panelu nástrojů**rozbalte uzel **Součásti** a poklepejte na **tlačítko Časovač**.

     Vzhledem <xref:System.Windows.Forms.Timer> k tomu, že a je součást, nemá žádné vizuální reprezentace za běhu. Proto se nezobrazí s ovládacími prvky na povrchu návrháře, ale spíše v **Návrhář komponent** (zásobník v dolní části povrchu návrháře).

5. V **Návrháři komponent**klepněte na **tlačítko timer1** <xref:System.Windows.Forms.Timer.Enabled%2A> a `true`nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `1000` a vlastnost na .

     Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> určuje frekvenci, s <xref:System.Windows.Forms.Timer> jakou komponenta značky. Pokaždé, `timer1` když zaškrtne, spustí `timer1_Tick` kód v události. Interval představuje počet milisekund mezi značkami.

6. V **Návrháři komponent**poklepáním **na timer1** přejděte na `timer1_Tick` událost pro . `ctlClock`

7. Upravte kód tak, aby se podobal následující ukázce kódu. Nezapomeňte změnit modifikátor `private` přístupu z na `protected`.

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     Tento kód způsobí, že aktuální `lblDisplay`čas se zobrazí v . Vzhledem k `timer1` tomu, `1000`že interval byl nastaven na , bude tato událost nastat každých tisíc milisekund, tedy aktualizace aktuální čas každou sekundu.

8. Upravte metodu tak, aby `virtual` byla overridable s klíčovým slovem. Další informace naleznete v části "Dědění z uživatelského ovládacího prvku" níže.

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. V nabídce **Soubor** kliknutím na **Uložit vše** projekt uložte.

## <a name="add-properties-to-the-composite-control"></a>Přidání vlastností do složeného ovládacího prvku

Ovládací prvek hodiny nyní zapouzdřuje <xref:System.Windows.Forms.Label> ovládací prvek a <xref:System.Windows.Forms.Timer> součást, každý s vlastní sadou vlastních vlastností. Zatímco jednotlivé vlastnosti těchto ovládacích prvků nebudou přístupné pro následné uživatele ovládacího prvku, můžete vytvořit a vystavit vlastní vlastnosti napsáním příslušné bloky kódu. V následujícím postupu přidáte do ovládacího prvku vlastnosti, které uživateli umožní změnit barvu pozadí a textu.

### <a name="to-add-a-property-to-your-composite-control"></a>Přidání vlastnosti do složeného ovládacího prvku

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **ctlClock.cs**a potom klepněte na příkaz **Zobrazit kód**.

     Otevře se **Editor kódu** pro váš ovládací prvek.

2. Vyhledejte `public partial class ctlClock` příkaz. Pod otevírací složenou`{)`závorku ( zadejte následující kód.

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     Tyto příkazy vytvořit soukromé proměnné, které budete používat k uložení hodnoty pro vlastnosti, které se chystáte vytvořit.

3. Zadejte nebo vložte následující kód pod deklarace proměnných z kroku 2.

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

     Předchozí kód zpřístupní dvě `ClockForeColor` `ClockBackColor`vlastní vlastnosti a , k dispozici pro následné uživatele tohoto ovládacího prvku. `get` Příkazy `set` a poskytují úložiště a načítání hodnoty vlastnosti, stejně jako kód pro implementaci funkce vhodné pro vlastnost.

4. V nabídce **Soubor** kliknutím na **Uložit vše** projekt uložte.

## <a name="test-the-control"></a>Otestujte ovládací prvek

Ovládací prvky nejsou samostatné aplikace; musí být umístěny v kontejneru. Otestujte chování ovládacího prvku za běhu a jeho vlastnosti můžete používat pomocí **testovacího kontejneru UserControl**. Další informace naleznete v [tématu How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

### <a name="to-test-your-control"></a>Testování ovládacího prvku

1. Stisknutím **klávesy F5** vytvořte projekt a spusťte ovládací prvek v **testovacím kontejneru UserControl**.

2. V mřížce vlastností testovacího kontejneru vyhledejte `ClockBackColor` vlastnost a pak vyberte vlastnost, která zobrazí paletu barev.

3. Kliknutím zvolte barvu.

   Barva pozadí ovládacího prvku se změní na vybranou barvu.

4. Použijte podobnou posloupnost událostí `ClockForeColor` k ověření, že vlastnost funguje podle očekávání.

   V této části a v předchozích částech jste viděli, jak lze součásti a ovládací prvky systému Windows kombinovat s kódem a balením a poskytovat vlastní funkce ve formě složeného ovládacího prvku. Naučili jste se vystavit vlastnosti v složené ovládací prvek a jak otestovat ovládací prvek po dokončení. V další části se dozvíte, jak vytvořit `ctlClock` zděděný složený ovládací prvek pomocí jako základ.

## <a name="inherit-from-a-composite-control"></a>Dědit z složeného ovládacího prvku

V předchozích částech jste se naučili kombinovat ovládací prvky systému Windows, součásti a kód do opakovaně použitelných složených ovládacích prvků. Složený ovládací prvek lze nyní použít jako základ, na kterém lze sestavit další ovládací prvky. Proces odvození třídy ze základní třídy se nazývá *dědičnost*. V této části vytvoříte složený `ctlAlarmClock`ovládací prvek s názvem . Tento ovládací prvek bude odvozen z `ctlClock`nadřazeného ovládacího prvku . Naučíte se rozšířit funkce `ctlClock` přepsáním nadřazených metod a přidáním nových metod a vlastností.

Prvním krokem při vytváření zděděného ovládacího prvku je jeho odvození z nadřazeného prvku. Tato akce vytvoří nový ovládací prvek, který má všechny vlastnosti, metody a grafické charakteristiky nadřazeného ovládacího prvku, ale může také sloužit jako základ pro přidání nové nebo upravené funkce.

### <a name="to-create-the-inherited-control"></a>Vytvoření zděděného ovládacího prvku

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku ctlClockLib**, přejděte na **tlačítko Přidat**a klepněte na příkaz Uživatelské **řízení**.

     Otevře se dialogové okno **Přidat novou položku.**

2. Vyberte šablonu **Zděděný uživatelský ovládací prvek.**

3. Do pole **Název** `ctlAlarmClock.cs`zadejte a klikněte na **Přidat**.

     Zobrazí se dialogové okno **Výběr dědičnosti.**

4. V **části Název součásti**poklepejte na **položku ctlClock**.

5. V **Průzkumníku řešení**projděte aktuální projekty.

    > [!NOTE]
    > Do aktuálního projektu byl přidán soubor s názvem **ctlAlarmClock.cs.**

### <a name="add-the-alarm-properties"></a>Přidání vlastností alarmu

Vlastnosti jsou přidány do zděděného ovládacího prvku stejným způsobem, jakým jsou přidány do složeného ovládacího prvku. Nyní použijete syntaxi deklarace vlastnosti k `AlarmTime`přidání dvou vlastností do ovládacího prvku: , který `AlarmSet`uloží hodnotu data a času, kdy má alarm zhasnout, a , která bude označovat, zda je budík nastaven.

#### <a name="to-add-properties-to-your-composite-control"></a>Přidání vlastností do složeného ovládacího prvku

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **příkaz ctlAlarmClock**a potom klepněte na příkaz **Zobrazit kód**.

2. Vyhledejte `public class` příkaz. Všimněte si, že `ctlClockLib.ctlClock`ovládací prvek dědí z . Pod otevírací složenou`{)` závorku ( příkaz zadejte následující kód.

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

Zděděný ovládací prvek má vizuální rozhraní, které je shodné s ovládacím prvkem, který dědí z. Má stejné základní ovládací prvky jako jeho nadřazený ovládací prvek, ale vlastnosti základní ovládací prvky nebudou k dispozici, pokud nebyly konkrétně vystaveny. Do grafického rozhraní zděděného složeného ovládacího prvku můžete přidat stejným způsobem, jako byste jej přidali do libovolného složeného ovládacího prvku. Chcete-li pokračovat v přidávání do vizuálního rozhraní budíku, přidáte ovládací prvek štítku, který bude blikat, když budík zazní.

#### <a name="to-add-the-label-control"></a>Přidání ovládacího prvku popisek

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **příkaz ctlAlarmClock**a potom klepněte na příkaz **Zobrazit návrháře**.

     Návrhář pro `ctlAlarmClock` otevírá v hlavním okně.

2. Klepněte na zobrazovanou část ovládacího prvku a zobrazte okno Vlastnosti.

    > [!NOTE]
    > Zatímco jsou zobrazeny všechny vlastnosti, jsou ztlumené. To znamená, že tyto `lblDisplay` vlastnosti jsou nativní pro a nelze změnit nebo přistupovat v okně Vlastnosti. Ve výchozím nastavení jsou `private`ovládací prvky obsažené ve složeném ovládacím prvku a jejich vlastnosti nejsou žádným způsobem přístupné.

    > [!NOTE]
    > Pokud chcete, aby další uživatelé složeného ovládacího prvku `public` měli `protected`přístup k jeho vnitřním ovládacím prvkům, deklarujte je jako nebo . To vám umožní nastavit a upravit vlastnosti ovládacích prvků obsažených v složeném ovládacím prvku pomocí příslušného kódu.

3. Přidejte <xref:System.Windows.Forms.Label> ovládací prvek do složeného ovládacího prvku.

4. Pomocí myši přetáhněte <xref:System.Windows.Forms.Label> ovládací prvek bezprostředně pod pole displeje. V okně Vlastnosti nastavte následující vlastnosti.

    |Vlastnost|Nastavení|
    |--------------|-------------|
    |**Název**|`lblAlarm`|
    |**Text**|**Alarm!**|
    |**Textalign**|`MiddleCenter`|
    |**Visible**|`false`|

### <a name="add-the-alarm-functionality"></a>Přidání funkce alarmu

V předchozích postupech jste přidali vlastnosti a ovládací prvek, který umožní funkce alarmu ve složeném ovládacím prvku. V tomto postupu přidáte kód pro porovnání aktuálního času s časem alarmu a pokud jsou stejné, pro blikání alarmu. Přepsáním `timer1_Tick` metody `ctlClock` a přidáním dalšího kódu do něj `ctlAlarmClock` rozšíříte možnost i zachování `ctlClock`všech vlastních funkcí aplikace .

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>Chcete-li přepsat timer1_Tick metodu ctlClock

1. V **Editoru kódu** `private bool blnAlarmSet;` vyhledejte příkaz. Okamžitě pod něj přidejte následující příkaz.

    ```csharp
    private bool blnColorTicker;
    ```

2. V **Editoru kódu**vyhledejte`})` uzavírací složenou závorku ( na konci třídy. Těsně před složenou závorku přidejte následující kód.

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

     Přidání tohoto kódu provádí několik úkolů. Příkaz `override` řídí ovládací prvek použít tuto metodu namísto metody, která byla zděděna ze základního ovládacího prvku. Při volání této metody volá metodu, kterou přepíše `base.timer1_Tick` vyvoláním příkazu, zajištěním, že všechny funkce obsažené v původním ovládacím prvku jsou reprodukovány v tomto ovládacím prvku. Potom spustí další kód začlenit funkce alarmu. Když dojde k poplachu, zobrazí se blikající ovládací prvek štítku.

     Ovládání budíku je téměř dokončeno. Jediná věc, která zůstává, je implementovat způsob, jak ji vypnout. Chcete-li to provést, přidáte `lblAlarm_Click` kód k metodě.

#### <a name="to-implement-the-shutoff-method"></a>Implementace metody vypnutí

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **ctlAlarmClock.cs**a potom klepněte na příkaz **Návrhář zobrazení**.

     Návrhář otevře.

2. Přidejte tlačítko do ovládacího prvku. Nastavte vlastnosti tlačítka následujícím způsobem.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|`btnAlarmOff`|
    |**Text**|**Zakázat alarm**|

3. V návrháři poklepejte na **btnAlarmOff**.

     **Editor kódu** se `private void btnAlarmOff_Click` otevře na řádku.

4. Upravte tuto metodu tak, aby se podobala následujícímu kódu.

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. V nabídce **Soubor** kliknutím na **Uložit vše** projekt uložte.

### <a name="use-the-inherited-control-on-a-form"></a>Použití zděděného ovládacího prvku ve formuláři

Zděděný ovládací prvek můžete otestovat stejným způsobem, `ctlClock`jakým jste testovali ovládací prvek základní třídy: Stisknutím **klávesy F5** vytvořte projekt a spusťte ovládací prvek v **testovacím kontejneru UserControl**. Další informace naleznete v [tématu How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

Chcete-li ovládací prvek použít, budete jej muset hostovat ve formuláři. Stejně jako u standardního složeného ovládacího prvku zděděný složený ovládací prvek nemůže samostatně a musí být hostován ve formuláři nebo jiném kontejneru. Vzhledem k tomu, `ctlAlarmClock` že má větší hloubku funkčnosti, další kód je nutné otestovat. V tomto postupu napíšete jednoduchý program pro `ctlAlarmClock`testování funkčnosti aplikace . Napíšete kód pro nastavení `AlarmTime` a `ctlAlarmClock`zobrazení vlastnosti aplikace a otestujete jeho vlastní funkce.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Vytvoření a přidání ovládacího prvku do testovacího formuláře

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **příkaz ctlClockLib**a potom klepněte na příkaz **Sestavit**.

2. Přidejte do řešení nový projekt **aplikace Windows Forms Application** a pojmenujte jej **Test**.

3. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Reference** pro testovací projekt. Kliknutím na **Přidat odkaz** zobrazíte dialogové okno **Přidat odkaz.** Klikněte na kartu s názvem **Projekty**. Projekt `ctlClockLib` bude uveden v části **Název projektu**. Poklepáním na projekt přidejte odkaz na testovací projekt.

4. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **tlačítko Testovat**a potom klepněte na příkaz **Sestavit**.

5. V **panelu nástrojů**rozbalte uzel **komponenty ctlClockLib.**

6. Poklepáním na **ctlAlarmClock** přidejte kopii `ctlAlarmClock` formuláře.

7. V **panelu nástrojů**vyhledejte a poklepejte na <xref:System.Windows.Forms.DateTimePicker> <xref:System.Windows.Forms.Label> **položku DateTimePicker,** chcete-li do formuláře přidat ovládací prvek, a potom přidejte ovládací prvek poklepáním na **popisek**.

8. Pomocí myši umístěte ovládací prvky na vhodné místo ve formuláři.

9. Nastavte vlastnosti těchto ovládacích prvků následujícím způsobem.

    |Řízení|Vlastnost|Hodnota|
    |-------------|--------------|-----------|
    |`label1`|**Text**|`(blank space)`|
    ||**Název**|`lblTest`|
    |`dateTimePicker1`|**Název**|`dtpTest`|
    ||**Formát**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. V návrháři poklepejte na **dtpTest**.

     **Editor kódu** se `private void dtpTest_ValueChanged`otevře do aplikace .

11. Upravte kód tak, aby se podobal následujícím.

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **tlačítko Testovat**a potom klepněte na příkaz Nastavit jako **počáteční projekt**.

13. V nabídce **Ladit** klikněte na **Spustit ladění**.

     Spustí se testovací program. Všimněte si, že aktuální `ctlAlarmClock` čas je aktualizován v ovládacím <xref:System.Windows.Forms.DateTimePicker> prvku a že počáteční čas je zobrazen v ovládacím prvku.

14. Klikněte <xref:System.Windows.Forms.DateTimePicker> na místo, kde se zobrazí minuty hodiny.

15. Pomocí klávesnice nastavte hodnotu pro minuty, která je o `ctlAlarmClock`jednu minutu větší než aktuální čas zobrazený aplikacem .

     Čas nastavení alarmu je `lblTest`zobrazen v . Počkejte, až zobrazený čas dosáhne doby nastavení alarmu. Když zobrazený čas dosáhne času, na který je `lblAlarm` budík nastaven, bude blikat.

16. Vypněte budík `btnAlarmOff`kliknutím na tlačítko . Nyní můžete resetovat alarm.

Tento článek se vztahuje na řadu klíčových pojmů. Naučili jste se vytvořit složený ovládací prvek kombinací ovládacích prvků a součástí do kontejneru složených ovládacích prvků. Naučili jste se přidat vlastnosti do ovládacího prvku a napsat kód pro implementaci vlastních funkcí. V poslední části jste se naučili rozšířit funkce daného složeného ovládacího prvku prostřednictvím dědičnosti a změnit funkce hostitelských metod přepsáním těchto metod.

## <a name="see-also"></a>Viz také

- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
- [Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
