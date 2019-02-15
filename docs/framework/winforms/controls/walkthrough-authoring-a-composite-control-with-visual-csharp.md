---
title: 'Průvodce: Vytvoření složeného ovládacího prvku pomocí Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 357e001effe22f5e9603ebee63188ddff957d585
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305724"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a>Průvodce: Vytvoření složeného ovládacího prvku pomocí Visual C# #
Složené ovládací prvky poskytují způsob, kterým lze vytvořit vlastní grafické rozhraní a znovu použít. Složený ovládací prvek je v podstatě komponent pomocí vizuální reprezentace. V důsledku toho může obsahovat jeden nebo více Windows Forms ovládací prvky, komponenty nebo bloky kódu, který můžete rozšířit funkce ověřování uživatelského vstupu, změnou zobrazení vlastností nebo provádění jiných úloh vyžaduje autorem. Složené ovládací prvky mohou být umístěny ve Windows Forms stejným způsobem jako ostatní ovládací prvky. V první části tohoto návodu vytvoříte jednoduchou složeného ovládacího prvku volá `ctlClock`. V druhé části tohoto průvodce, které rozšiřují funkce nástroje `ctlClock` prostřednictvím dědičnosti.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Když vytvoříte nový projekt, zadejte její název na nastavit kořenový obor názvů, název sestavení a název projektu a ujistěte se, že součást výchozí bude v správný obor názvů.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Chcete-li vytvořit ctlClockLib Knihovna ovládacích prvků a ovládací prvek ctlClock  
  
1.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu** otevřete **nový projekt** dialogové okno.  
  
2.  V seznamu Projekty Visual C#, vyberte **Knihovna ovládacích prvků Windows Forms** šablony projektu, typ `ctlClockLib` v **název** pole a potom klikněte na tlačítko **OK**.  
  
     Název projektu `ctlClockLib`, je také přiřazený k oboru názvů root ve výchozím nastavení. Kořenový obor názvů se používá k určení názvů součástí sestavení. Například, pokud se dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete zadat vaše `ctlClock` pomocí komponenty `ctlClockLib.ctlClock.`  
  
3.  V Průzkumníku řešení klikněte pravým tlačítkem na **UserControl1.cs**a potom klikněte na tlačítko **přejmenovat**. Změňte název souboru, aby `ctlClock.cs`. Klikněte na tlačítko **Ano** tlačítko, pokud budete vyzváni, pokud chcete přejmenovat všechny odkazy na prvek kódu "UserControl1".  
  
    > [!NOTE]
    >  Ve výchozím nastavení, zdědí složeného ovládacího prvku <xref:System.Windows.Forms.UserControl> třídy poskytované systémem. <xref:System.Windows.Forms.UserControl> Třída poskytuje funkce vyžadované všech složených ovládacích prvků a implementuje standardní metody a vlastnosti.  
  
4.  Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Přidání Windows ovládacích prvků a komponent do složeného ovládacího prvku  
 Vizuální rozhraní je zásadní součástí složeného ovládacího prvku. Tento vizuální rozhraní je implementováno přidání jednoho nebo více ovládacích prvků Windows na plochu návrháře. V následující ukázce se začlenit ovládacích prvků Windows do složeného ovládacího prvku a napsat kód k implementaci funkcionality.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Přidejte popisek a časovač do složeného ovládacího prvku  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.cs**a potom klikněte na tlačítko **Návrhář zobrazení**.  
  
2.  V **nástrojů**, rozbalte **běžné ovládací prvky** uzel a poté dvojitým kliknutím **popisek**.  
  
     A <xref:System.Windows.Forms.Label> ovládací prvek s názvem `label1` se přidá do vašeho ovládacího prvku na návrhové ploše.  
  
3.  V návrháři, klikněte na tlačítko **label1**. V okně Vlastnosti nastavte následující vlastnosti.  
  
    |Vlastnost|Změňte na|  
    |--------------|---------------|  
    |**Název**|`lblDisplay`|  
    |**Text**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  V **nástrojů**, rozbalte **součásti** uzel a poté dvojitým kliknutím **časovače**.  
  
     Protože <xref:System.Windows.Forms.Timer> je komponenta, nemá žádný vizuální reprezentace v době běhu. Proto není zobrazen s ovládacími prvky na návrhové ploše, ale spíše v **návrháře komponent** (na hlavním panelu v dolní části na plochu návrháře).  
  
5.  V **návrháře komponent**, klikněte na tlačítko **timer1**a pak nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `1000` a <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true`.  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost řídí frekvenci, se kterým <xref:System.Windows.Forms.Timer> komponenty značky. Pokaždé, když `timer1` tiků, spustí kód, který `timer1_Tick` událostí. Interval představuje počet milisekund mezi značkami.  
  
6.  V **návrháře komponent**, dvakrát klikněte na panel **timer1** přejděte `timer1_Tick` událost pro `ctlClock`.  
  
7.  Upravte kód tak, aby vypadá podobně jako následující příklad kódu. Nezapomeňte změnit modifikátor přístupu z `private` k `protected`.  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     Tento kód způsobí, že aktuální čas v `lblDisplay`. Protože interval `timer1` byl nastaven na `1000`, dojde k této události každých tisíců milisekund, tedy aktualizuje aktuální čas každou sekundu.  
  
8.  Upravte metodu k možné overridable s `virtual` – klíčové slovo. Další informace naleznete v části "Dědění z uživatelského ovládacího prvku" níže.  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.  
  
## <a name="adding-properties-to-the-composite-control"></a>Přidání vlastnosti do složeného ovládacího prvku  
 Ovládací prvek hodiny nyní zapouzdřuje <xref:System.Windows.Forms.Label> ovládacího prvku a <xref:System.Windows.Forms.Timer> komponenty, každý s vlastní sadou vlastní vlastnosti. I když jednotlivé vlastnosti těchto ovládacích prvků nebudou přístupné uživatelům následné ovládacího prvku, můžete vytvořit a vystavit vlastní vlastnosti napsáním příslušné bloky kódu. V následujícím postupu přidejte vlastnosti do ovládacího prvku, který uživateli umožňuje změnit barvu pozadí a textu.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Přidání vlastnosti do složeného ovládacího prvku  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.cs**a potom klikněte na tlačítko **zobrazit kód**.  
  
     **Editor kódu** pro vaše ovládací prvek se otevře.  
  
2.  Vyhledejte `public partial class ctlClock` příkazu. Pod levou složenou závorku (`{)`, zadejte následující kód.  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     Tyto příkazy vytvořit soukromé proměnné, které budete používat k ukládání hodnot pro vlastnosti, které se chystáte vytvořit.  
  
3.  Zadejte následující kód pod deklarace proměnných z kroku 2.  
  
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
  
     Předchozí kód provede dvě vlastní vlastnosti `ClockForeColor` a `ClockBackColor`, která je dostupná uživatelům následné tohoto ovládacího prvku. `get` a `set` příkazy zajišťují pro ukládání a načítání hodnoty vlastnosti, jakož i kód k implementaci funkcionality odpovídající vlastnosti.  
  
4.  Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.  
  
## <a name="testing-the-control"></a>Testování ovládacího prvku  
 Ovládací prvky nejsou samostatné aplikace; musí být uložen v kontejneru. Chování ovládacího prvku za běhu testu přestal pracovat a s jeho vlastnosti **UserControl – kontejner testů**. Další informace najdete v tématu [jak: Testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-your-control"></a>Testování ovládacího prvku  
  
1.  Stisknutím klávesy F5 sestavte projekt a spusťte váš ovládací prvek **UserControl – kontejner testů**.  
  
2.  V mřížce vlastností kontejner testu, vyhledejte `ClockBackColor` vlastnost a potom vyberte vlastnost pro zobrazení palety barev.  
  
3.  Kliknutím zvolte barvu.  
  
     Barva pozadí ovládacího prvku změní barvu, kterou jste vybrali.  
  
4.  Ověřte, že pomocí podobně jako posloupnost událostí `ClockForeColor` vlastnost funguje podle očekávání.  
  
     V této části a v předchozích částech, jste viděli, jak mohou být kombinovány komponent a ovládacích prvků Windows s kódem a balení poskytují vlastní funkce v podobě složeného ovládacího prvku. Naučili jste se vystavení vlastností v složeného ovládacího prvku a po dokončení testování ovládacího prvku. V další části se dozvíte, jak vytvořit objekt zděděné složeného ovládacího prvku pomocí `ctlClock` jako základ.  
  
## <a name="inheriting-from-a-composite-control"></a>Dědění z složeného ovládacího prvku  
 V předchozích částech jste zjistili, jak zkombinovat ovládací prvky, komponenty a kódu Windows do opakovaně použitelného složených ovládacích prvků. Složený ovládací prvek je nyní možné jako základ, na kterém je možné sestavovat další ovládací prvky. Proces odvození třídy ze základní třídy se nazývá *dědičnosti*. V této části vytvoříte složeného ovládacího prvku volá `ctlAlarmClock`. Tento ovládací prvek bude odvozený z jeho nadřazenému ovládacímu prvku `ctlClock`. Se dozvíte, jak rozšířit funkce `ctlClock` nadřazené metody přepsání a přidáním nových metod a vlastností.  
  
 Prvním krokem při vytváření zděděný ovládací prvek je odvozen od svého nadřazeného objektu. Tato akce vytvoří nový ovládací prvek, který má všechny vlastnosti, metody a grafické vlastnosti nadřazeného ovládacího prvku, ale mohou chovat i jako základ pro přidání nové nebo upravené funkce.  
  
#### <a name="to-create-the-inherited-control"></a>Chcete-li vytvořit zděděný ovládací prvek  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**, přejděte na **přidat**a potom klikněte na tlačítko **uživatelský ovládací prvek**.  
  
     **Přidat novou položku** zobrazí se dialogové okno.  
  
2.  Vyberte **zděděné uživatelský ovládací prvek** šablony.  
  
3.  V **název** zadejte `ctlAlarmClock.cs`a potom klikněte na tlačítko **přidat**.  
  
     **Výběr dědičnosti** zobrazí se dialogové okno.  
  
4.  V části **název komponenty**, dvakrát klikněte na panel **ctlClock**.  
  
5.  V Průzkumníku řešení projděte si aktuální projekty.  
  
    > [!NOTE]
    >  Soubor s názvem **ctlAlarmClock.cs** byl přidán do aktuálního projektu.  
  
### <a name="adding-the-alarm-properties"></a>Přidání vlastností upozornění  
 Vlastnosti jsou přidány do zděděný ovládací prvek stejným způsobem, které se přidají do složeného ovládacího prvku. Teď použijete syntaxi deklarace vlastností přidat dvě vlastnosti do ovládacího prvku: `AlarmTime`, která bude uchovávat hodnotu Datum a čas vypnutí, a `AlarmSet`, která indikuje, jestli je nastavit alarm.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Přidání vlastnosti do složeného ovládacího prvku  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na tlačítko **zobrazit kód**.  
  
2.  Vyhledejte `public class` příkazu. Všimněte si, že ovládací prvek dědí z `ctlClockLib.ctlClock`. Pod levou složenou závorku (`{)` příkazu, zadejte následující kód.  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>Přidávání do rozhraní grafického ovládacího prvku  
 Zděděný ovládací prvek má grafické rozhraní, který je stejný jako ovládací prvek, který dědí z. Má stejné základní ovládací prvky jako jeho nadřazený ovládací prvek, ale vlastností základních ovládacích prvků nebude k dispozici, pokud výslovně vystavený. Můžete přidat grafické rozhraní zděděných složeného ovládacího prvku stejným způsobem jako můžete přidat do jakékoli složeného ovládacího prvku. Pokračujte v přidávání do vašeho budíku vizuální rozhraní, přidejte ovládací prvek popisku, který bude flash, když je zvukově alarm.  
  
##### <a name="to-add-the-label-control"></a>Chcete-li přidat ovládací prvek popisek  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na tlačítko **Návrhář zobrazení**.  
  
     Návrhář pro `ctlAlarmClock` otevře v hlavním okně.  
  
2.  Klikněte na část zobrazení ovládacího prvku a zobrazte v okně Vlastnosti.  
  
    > [!NOTE]
    >  Když se zobrazí všechny vlastnosti, jsou neaktivní. To znamená, že tyto vlastnosti jsou pro nativní `lblDisplay` a nelze změnit ani získat přístup v okně Vlastnosti. Ve výchozím nastavení, ovládacích prvcích obsažených složeného ovládacího prvku jsou `private`, a jejich vlastnosti nejsou dostupné žádné prostředky.  
  
    > [!NOTE]
    >  Pokud chcete mít přístup k jeho interní kontrolní mechanismy následné uživatelé složeného ovládacího prvku, je jako deklarovat `public` nebo `protected`. To vám umožní nastavit a změnit vlastnosti ovládacích prvků uvnitř složeného ovládacího prvku pomocí odpovídající kód.  
  
3.  Přidat <xref:System.Windows.Forms.Label> ovládacího prvku do složeného ovládacího prvku.  
  
4.  Pomocí myši přetáhnout <xref:System.Windows.Forms.Label> ovládací prvek bezprostředně pod rozevíracím seznamu zobrazit. V okně Vlastnosti nastavte následující vlastnosti.  
  
    |Vlastnost|Nastavení|  
    |--------------|-------------|  
    |**Název**|`lblAlarm`|  
    |**Text**|**Alarm!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Viditelné**|`false`|  
  
### <a name="adding-the-alarm-functionality"></a>Přidání funkce upozornění  
 V předchozích postupů jste přidali, vlastností a ovládací prvek, který vám umožní alarmů funkcí do složeného ovládacího prvku. V tomto postupu přidáte kód, který porovná aktuální čas na čas alarmu, a pokud se shodují, na flash alarm. Přepsáním `timer1_Tick` metoda `ctlClock` a do ní přidáte další kód, budou rozšíření možností objektu `ctlAlarmClock` při zachování všech funkcí inherentní `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>Chcete-li přepsat metodu timer1_Tick ctlClock  
  
1.  V **Editor kódu**, vyhledejte `private bool blnAlarmSet;` příkazu. Bezprostředně pod něj přidejte následující příkaz.  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  V **Editor kódu**, vyhledejte pravou složenou závorku (`})` na konci třídy. Těsně před složenou závorku přidejte následující kód.  
  
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
  
     Tento kód provede několik úloh. `override` Příkaz přesměruje ovládacího prvku, aby používali tuto metodu místo metody, která se dědí ze základního ovládacího prvku. Když tato metoda je volána, volá metodu přepíše vyvoláním `base.timer1_Tick` příkaz zajistí, že všechny funkce součástí původního ovládacího prvku je uveden v tomto ovládacím prvku. Pak spustí další kód začlenit funkce alarm. Blikající ovládací prvek popisku se zobrazí při výskytu varování.  
  
     Ovládací prvek budíku je skoro hotová. Jediné, co, která zůstává je implementace způsob, jak ji vypnout. K tomu přidáte kód, který `lblAlarm_Click` metody.  
  
##### <a name="to-implement-the-shutoff-method"></a>K implementaci přístupnými – metoda  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock.cs**a potom klikněte na tlačítko **Návrhář zobrazení**.  
  
     Otevře se Návrhář.  
  
2.  Přidání tlačítka pro ovládací prvek. Vlastnosti tlačítka nastavte následujícím způsobem.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Název**|`btnAlarmOff`|  
    |**Text**|**Zakázat upozornění**|  
  
3.  V Návrháři dvakrát klikněte na panel **btnAlarmOff**.  
  
     **Editor kódu** se otevře `private void btnAlarmOff_Click` řádku.  
  
4.  Upravte tuto metodu tak, aby vypadá podobně jako následující kód.  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Pomocí zděděný ovládací prvek ve formuláři  
 Zděděný ovládací prvek můžete otestovat stejným způsobem můžete otestovat základní třídy ovládacího prvku, `ctlClock`: Stisknutím klávesy F5 sestavte projekt a spusťte váš ovládací prvek **UserControl – kontejner testů**. Další informace najdete v tématu [jak: Testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Vložit ovládací prvek používat, musíte ho hostovat ve formuláři. Stejně jako u standardní složeného ovládacího prvku, zděděné složený ovládací prvek nemůže zůstat sama a musí být hostovaný ve formuláři nebo jiném kontejneru. Protože `ctlAlarmClock` větší hloubky funkce, je potřeba ji otestovat další kód. V tomto postupu budete psát jednoduchý program k otestování funkce `ctlAlarmClock`. Budete psát kód pro nastavení a zobrazení `AlarmTime` vlastnost `ctlAlarmClock`a testovat své vlastní funkce.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>K vytvoření a přidání ovládacího prvku na formulář testu  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**a potom klikněte na tlačítko **sestavení**.  
  
2.  Přidat nový **aplikace Windows** projektu do řešení a pojmenujte ho `Test`.  
  
3.  V Průzkumníku řešení klikněte pravým tlačítkem myši **odkazy** uzel pro testovací projekt. Klikněte na tlačítko **přidat odkaz** zobrazíte **přidat odkaz** dialogové okno. Klikněte na kartu **projekty**. Vaše `ctlClockLib` projektu budou uvedené v části **název projektu**. Dvakrát klikněte na projekt tak, aby do testovacího projektu přidejte odkaz.  
  
4.  V Průzkumníku řešení klikněte pravým tlačítkem na **testovací**a potom klikněte na tlačítko **sestavení**.  
  
5.  V **nástrojů**, rozbalte **ctlClockLib součásti** uzlu.  
  
6.  Dvakrát klikněte na panel **ctlAlarmClock** přidat kopii `ctlAlarmClock` do formuláře.  
  
7.  V **nástrojů**, vyhledejte a dvakrát klikněte na panel **ovládacího prvku DateTimePicker** přidat <xref:System.Windows.Forms.DateTimePicker> ovládací prvek do formuláře a poté přidejte <xref:System.Windows.Forms.Label> ovládací prvek dvojitým kliknutím **popisek**.  
  
8.  Pokud chcete umístit ovládací prvky v místě na formuláři pomocí myši.  
  
9. Následujícím způsobem nastavte vlastnosti těchto ovládacích prvků.  
  
    |Control|Vlastnost|Hodnota|  
    |-------------|--------------|-----------|  
    |`label1`|**Text**|`(blank space)`|  
    ||**Název**|`lblTest`|  
    |`dateTimePicker1`|**Název**|`dtpTest`|  
    ||**Formát**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. V Návrháři dvakrát klikněte na panel **dtpTest**.  
  
     **Editor kódu** otevře `private void dtpTest_ValueChanged`.  
  
11. Upravte kód tak, aby se podobá následující.  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. V Průzkumníku řešení klikněte pravým tlačítkem na **testovací**a potom klikněte na tlačítko **nastavit jako spouštěný projekt**.  
  
13. Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.  
  
     Testovací program spustí. Všimněte si, že aktuální čas je aktualizace v `ctlAlarmClock` ovládacího prvku a, počáteční čas je zobrazena ve <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku.  
  
14. Klikněte na tlačítko <xref:System.Windows.Forms.DateTimePicker> ve kterém se zobrazují minuty v hodině.  
  
15. Pomocí klávesnice, nastavte hodnotu minut, který je větší než aktuální čas zobrazí jednu minutu `ctlAlarmClock`.  
  
     Čas potřebný pro nastavení upozornění se zobrazí v `lblTest`. Počkejte zobrazeném čase k nastavení doby alarm. Čas, ke kterému je nastavit alarm, dosáhne zobrazeném čase `lblAlarm` bude flash.  
  
16. Vypnout alarmu, kliknutím na `btnAlarmOff`. Nyní může resetovat alarm.  
  
     Tento názorný postup zahrnují několik klíčových konceptů. Naučili jste se vytvoření složeného ovládacího prvku kombinací ovládacích prvků a komponent do složeného ovládacího prvku kontejneru. Jste se naučili přidání vlastnosti do ovládacího prvku a napsat kód k implementaci vlastních funkcí. V předchozí části jste se dozvěděli k rozšíření funkčnosti dané složeného ovládacího prvku prostřednictvím dědičnosti a změnit funkci metody hostitele tak, že přepíšete tyto metody.  
  
## <a name="see-also"></a>Viz také:
- [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
- [Postupy: Zobrazení ovládacího prvku v zvolit položky panelu nástrojů – dialogové okno](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
