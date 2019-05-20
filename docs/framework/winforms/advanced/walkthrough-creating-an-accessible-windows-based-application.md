---
title: 'Návod: Vytvoření aplikace systému Windows s usnadněním přístupu'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: 7dec86c724479fde78fcb2e2881dce40b1bf747a
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877107"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>Návod: Vytvoření aplikace systému Windows s usnadněním přístupu

Vytvoření přístupné aplikace má vliv na důležitá obchodní. Mnoha vlád mají usnadnění předpisy pro nákup softwaru. Logo Certified pro Windows obsahuje požadavky na usnadnění přístupu. Odhadované pobytem 30 milionů amerických samostatně, mnoho z nich potenciálních zákazníků, jsou ovlivněny usnadnění softwaru.

Tento názorný postup bude zabývat pět požadavků usnadnění přístupu pro logo Certified pro Windows. Podle těchto požadavků se dostupné aplikace:

- Podpora velikost ovládacích panelů, barvy, písma a vstupní nastavení. Řádku nabídek, záhlaví, ohraničení a stavový řádek všechny velikost se sami když uživatel změní nastavení ovládacího panelu. Nevyžaduje žádné další změny ovládací prvky nebo kód v této aplikaci.

- Podporovat režim s vysokým kontrastem.

- Zadejte zdokumentovaných klávesnici přístup ke všem funkcím.

- Vizuálně a programově zpřístupnit umístění fokus klávesnice.

- Vyhněte se předávání důležitých informací zvukovou samostatně.

Další informace najdete v tématu [prostředky pro návrh aplikace přístupné](/visualstudio/ide/reference/resources-for-designing-accessible-applications).

Informace o podpoře proměnlivé rozložení klávesnice, naleznete v tématu [osvědčené postupy pro vývoj globalizovaných aplikací](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).

## <a name="creating-the-project"></a>Vytvoření projektu

Tento návod vytvoří uživatelské rozhraní pro aplikace, která přebírá pizza objednávky. Skládá se z <xref:System.Windows.Forms.TextBox> pro jméno zákazníka <xref:System.Windows.Forms.RadioButton> skupina a vyberte velikost pizza <xref:System.Windows.Forms.CheckedListBox> pro výběr toppings, dva ovládací prvky tlačítek označené jako pořadí a zrušit a nabídky pomocí příkazu pro ukončení.

Uživatel zadá název zákazníka, velikost pizza a toppings potřeby. Když uživatel klikne na tlačítko pořadí, souhrn pořadí a její náklady jsou zobrazeny v okně se zprávou a ovládací prvky se vymažou a připravené pro další objednávku. Když uživatel klikne na tlačítko Storno, ovládací prvky se vymažou a připravené pro další objednávku. Když uživatel klikne na položku nabídky ukončení, program se ukončí.

Zvýraznění tohoto názorného postupu není kód systému prodejní objednávky, ale usnadnění přístupu uživatelského rozhraní. Návodu ukazuje, že funkce pro usnadnění přístupu z několika často používané ovládací prvky, včetně tlačítek, přepínacích tlačítek, textová pole a popisky.

#### <a name="to-begin-making-the-application"></a>Chcete-li začít vytvářet aplikace

- Vytvoření nové aplikace Windows v jazyce Visual Basic nebo Visual C#. Pojmenujte projekt **PizzaOrder**. (Podrobnosti najdete v tématu [vytváří se nová řešení a projekty](/visualstudio/ide/creating-solutions-and-projects).)

## <a name="adding-the-controls-to-the-form"></a>Přidání ovládacích prvků do formuláře

Když přidáváte ovládací prvky do formuláře, mějte na paměti následující pokyny, aby dostupné aplikace:

- Nastavte <xref:System.Windows.Forms.Control.AccessibleDescription%2A> a <xref:System.Windows.Forms.Control.AccessibleName%2A> vlastnosti. V tomto příkladu ve výchozím nastavení <xref:System.Windows.Forms.Control.AccessibleRole%2A> je dostačující. Další informace o vlastnostech usnadnění, naleznete v tématu [poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).

- Nastavte velikost písma 10 bodů nebo větší.

  > [!NOTE]
  > Pokud nastavíte velikost písma formuláře na 10 při spuštění, bude mít všechny ovládací prvky do formuláře přidán následně velikost písma 10.

- Zajistěte, aby libovolný ovládací prvek popisek, který popisuje ovládací prvek textového pole bezprostředně předchází ovládacího prvku textového pole v pořadí.

- Přidat přístupový kód, používat "&" znak <xref:System.Windows.Forms.Control.Text%2A> vlastnost libovolný ovládací prvek, uživatel může chtít přejít na.

- Přidat přístupový kód, používat "&" znak <xref:System.Windows.Forms.Control.Text%2A> popisku, který předchází ovládací prvek, který uživatel může chtít přejít na. Nastavit jmenovky <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `true`, tak, aby fokus na další ovládací prvek v pořadí karet při stisknutí přístupové klávesy.

- Přidáte všechny položky nabídky přístupové klíče.

#### <a name="to-make-your-windows-application-accessible"></a>Chcete-li zpřístupnit svoji aplikaci Windows

- Přidat ovládací prvky do formuláře a nastavte vlastnosti, jak je popsáno níže. Podívejte se na obrázku na konec tabulky modelu o tom, jak uspořádat ovládací prvky ve formuláři.

   |Objekt|Vlastnost|Value|
   |------------|--------------|-----------|
   |Form1|AccessibleDescription|Formulář objednávky|
   ||AccessibleName|Formulář objednávky|
   ||Velikost písma|10|
   ||Text|Formulář objednávky pizza|
   |PictureBox|Name|logo|
   ||AccessibleDescription|Řez pizza|
   ||AccessibleName|Logo společnosti|
   ||Image|Žádné ikona nebo rastrový obrázek|
   |Popisek|Name|companyLabel|
   ||Text|Good Pizza|
   ||TabIndex|1|
   ||AccessibleDescription|Název společnosti|
   ||AccessibleName|Název společnosti|
   ||Barva pozadí|Modrá|
   ||Barva popředí|Žlutá|
   ||Velikost písma|18|
   |Popisek|Name|customerLabel|
   ||Text|& název|
   ||TabIndex|2|
   ||AccessibleDescription|Popisek názvu zákazníka|
   ||AccessibleName|Popisek názvu zákazníka|
   ||Usemnemonic –|Pravda|
   |TextBox|Name|customerName|
   ||Text|(žádné)|
   ||TabIndex|3|
   ||AccessibleDescription|Jméno zákazníka|
   ||AccessibleName|Jméno zákazníka|
   |GroupBox|Name|sizeOptions|
   ||AccessibleDescription|Možnosti velikosti pizza|
   ||AccessibleName|Možnosti velikosti pizza|
   ||Text|Velikost pizza|
   ||TabIndex|4|
   |RadioButton|Name|smallPizza|
   ||Text|& malé $6.00|
   ||Zaškrtnuto|Pravda|
   ||TabIndex|0|
   ||AccessibleDescription|Malé pizza|
   ||AccessibleName|Malé pizza|
   |RadioButton|Name|largePizza|
   ||Text|& velké 10,00 USD|
   ||TabIndex|1|
   ||AccessibleDescription|Velké pizza|
   ||AccessibleName|Velké pizza|
   |Popisek|Name|toppingsLabel|
   ||Text|& toppings ($0,75 každý)|
   ||TabIndex|5|
   ||AccessibleDescription|Popisek toppings|
   ||AccessibleName|Popisek toppings|
   ||Usemnemonic –|Pravda|
   |CheckedListBox|Name|toppings|
   ||TabIndex|6|
   ||AccessibleDescription|K dispozici toppings|
   ||AccessibleName|K dispozici toppings|
   ||Položky|Pepperoni salám, hub|
   |Tlačítko|Name|pořadí|
   ||Text|& pořadí|
   ||TabIndex|7|
   ||AccessibleDescription|Celkový počet pořadí|
   ||AccessibleName|Celkový počet pořadí|
   |Tlačítko|Name|Zrušit|
   ||Text|& Zrušit|
   ||TabIndex|8|
   ||AccessibleDescription|Zrušit pořadí|
   ||AccessibleName|Zrušit objednávku|
   |MainMenu|Name|theMainMenu|
   |Položku nabídky|Name|fileCommands|
   ||Text|& soubor|
   |Položku nabídky|Name|exitApp|
   ||Text|U & končit|

   Formulář bude vypadat podobně jako na následujícím obrázku:

   ![Formulář objednávky pizza s názvem textového pole a velikost a toppings výběru.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)

## <a name="supporting-high-contrast-mode"></a>Podporující režim s vysokým kontrastem

Vysoký kontrast je nastavení systému Windows, který zlepšuje čitelnost pomocí kontrastní barvy a velikosti písem, které jsou užitečné pro uživatele se zrakovým postižením. <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Vlastnost je k dispozici k určení, zda je nastaven režim s vysokým kontrastem.

Pokud je SystemInformation.HighContrast `true`, by měla aplikace:

- Zobrazit všechny prvky uživatelského rozhraní pomocí systému barevné schéma

- Oznamují vizuální prvky nebo zvuk veškeré informace, které se předávají prostřednictvím barvu. Například pokud pomocí red písma jsou zvýrazněny konkrétní seznam položek, můžete také přidat tučné písmo, tak, aby uživatel měl jiné barvy upozornění, že jsou zvýrazněné položky.

- Vynechat všechny obrázky nebo vzory za text

Aplikace by měla kontrolovat nastavení <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> když aplikaci spustí a reagovat na událost systému <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Událost se vyvolá vždy, když hodnota <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> změny.

V naší aplikaci, je jediným prvkem, který se nepoužívá nastavení systému pro barvu `lblCompanyName`. <xref:System.Drawing.SystemColors> Třída se používá, chcete-li změnit nastavení barev popisku uživatel vybral systémových barev.

#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Povolit režim s vysokým kontrastem účinným způsobem

1. Vytvořte metodu pro nastavení barvy popisku na systémových barev.

    ```vb
    ' Visual Basic
    Private Sub SetColorScheme()
       If SystemInformation.HighContrast Then
          companyLabel.BackColor = SystemColors.Window
          companyLabel.ForeColor = SystemColors.WindowText
       Else
          companyLabel.BackColor = Color.Blue
          companyLabel.ForeColor = Color.Yellow
       End If
    End Sub
    ```

    ```csharp
    // C#
    private void SetColorScheme()
    {
       if (SystemInformation.HighContrast)
       {
          companyLabel.BackColor = SystemColors.Window;
          companyLabel.ForeColor = SystemColors.WindowText;
       }
       else
       {
          companyLabel.BackColor = Color.Blue;
          companyLabel.ForeColor = Color.Yellow;
       }
    }
    ```

2. Volání `SetColorScheme` postup v konstruktoru formuláře (`Public Sub New()` v jazyce Visual Basic a `public class Form1` ve Vizuálu C#). Pro přístup k konstruktoru v jazyce Visual Basic, budete muset rozbalit oblast s názvem **kód generovaný návrhářem formulářů Windows**.

    ```vb
    ' Visual Basic
    Public Sub New()
       MyBase.New()
       InitializeComponent()
       SetColorScheme()
    End Sub
    ```

    ```csharp
    // C#
    public Form1()
    {
       InitializeComponent();
       SetColorScheme();
    }
    ```

3. Vytvořit procedury události s odpovídajícím podpisem na <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> událostí.

    ```vb
    ' Visual Basic
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)
       SetColorScheme()
    End Sub
    ```

    ```csharp
    // C#
    public void UserPreferenceChanged(object sender,
    Microsoft.Win32.UserPreferenceChangedEventArgs e)
    {
       SetColorScheme();
    }
    ```

4. Přidejte kód konstruktoru formuláře po volání `InitializeComponents`, k připojení události postup systémové události. Tato metoda volá `SetColorScheme` postup.

    ```vb
    ' Visual Basic
    Public Sub New()
       MyBase.New()
       InitializeComponent()
       SetColorScheme()
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
          AddressOf Me.UserPreferenceChanged
    End Sub
    ```

    ```csharp
    // C#
    public Form1()
    {
       InitializeComponent();
       SetColorScheme();
       Microsoft.Win32.SystemEvents.UserPreferenceChanged
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(
          this.UserPreferenceChanged);
    }
    ```

5. Přidejte kód do formuláře <xref:System.Windows.Forms.Control.Dispose%2A> metoda před voláním <xref:System.Windows.Forms.Control.Dispose%2A> metody základní třídy k uvolnění události po zavření aplikace. Pro přístup <xref:System.Windows.Forms.Control.Dispose%2A> metody v jazyce Visual Basic, budete muset rozbalit oblast s názvem kód generovaný návrhářem formulářů Windows.

    > [!NOTE]
    > Kód události systému běží vlákno oddělená od hlavní aplikace. Pokud vydané události, spustí kód, který jste připojili k této události i po ukončení programu.

    ```vb
    ' Visual Basic
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)
       If disposing Then
          If Not (components Is Nothing) Then
             components.Dispose()
          End If
       End If
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
          AddressOf Me.UserPreferenceChanged
       MyBase.Dispose(disposing)
    End Sub
    ```

    ```csharp
    // C#
    protected override void Dispose( bool disposing )
    {
       if( disposing )
       {
          if (components != null)
          {
             components.Dispose();
          }
       }
       Microsoft.Win32.SystemEvents.UserPreferenceChanged
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(
          this.UserPreferenceChanged);
       base.Dispose( disposing );
    }
    ```

6. Stisknutím klávesy F5 spusťte aplikaci.

## <a name="conveying-important-information-by-means-other-than-sound"></a>Předávání důležitých informací prostředky než zvuku

V této aplikaci žádné informace předávají zvukovou samostatně. Pokud používáte zvuku ve vaší aplikaci, by měl jiným způsobem a zadejte informace.

#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Slouží k poskytování informací jiným způsobem než zvuku

1. Vytvoření záhlaví flash pomocí funkce rozhraní Windows API FlashWindow. Příklad toho, jak volat funkce rozhraní API Windows, naleznete v tématu [názorný postup: Volání rozhraní API Windows](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

    > [!NOTE]
    > Uživatel může mít povoleno, službu Windows Popis zvuku, která také způsobí, že v okně tak, aby při přehrávání zvuků systému prostřednictvím vestavěné reproduktorů počítače.

2. Zobrazení důležitých informací v nemodálním okně tak, aby uživatel může odpovědět na ni.

3. Zobrazí okno se zprávou, která získá fokus klávesnice. Tato metoda vyhněte, když uživatel může být psaní.

4. Zobrazte indikátor stavu v oznamovací oblasti na hlavním panelu Stav. Podrobnosti najdete v tématu [přidání ikon aplikací do TaskBar s komponentou Windows Forms NotifyIcon](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).

## <a name="testing-the-application"></a>Testování aplikace

Před nasazením aplikace, měli byste otestovat funkce pro usnadnění přístupu, které jste implementovali.

#### <a name="to-test-accessibility-features"></a>K otestování funkce pro usnadnění přístupu

1. K otestování klávesnice, myš odpojte a Navigovat v uživatelském rozhraní pro každou funkci pouze pomocí klávesnice. Ujistěte se, že všechny úlohy lze provádět pomocí klávesnice pouze.

2. K otestování podpory vysoký kontrast, zvolte ikonu možností usnadnění přístupu v Ovládacích panelech. Klikněte na kartu zobrazení a použití vysoký kontrast – zaškrtnutím políčka. Procházejte všechny prvky uživatelského rozhraní k zajištění, že se projeví změny barev a písma. Také se ujistěte, že jsou vynechány Image nebo vzorce vykreslit za text.

    > [!NOTE]
    > Windows NT 4 nemá ikonu možností usnadnění přístupu v Ovládacích panelech. Tento postup pro změnu nastavení SystemInformation.HighContrast proto nebude fungovat v systému Windows NT 4.

3. Další nástroje jsou snadno dostupné pro testování přístupnosti aplikace.

4. Pokud chcete otestovat, vystavení fokus klávesnice, spusťte Lupa. (Pokud chcete soubor otevřít, klikněte na tlačítko **Start** nabídky, přejděte k **programy**, přejděte na **Příslušenství**, přejděte na **usnadnění**a potom klikněte na tlačítko  **Lupa**). Navigovat v uživatelském rozhraní pomocí tabulátor klávesnice a myši. Ujistěte se, že je správně v sledovat všechny navigační **Lupa**.

5. K otestování zpřístupňuje prvky na obrazovce, spusťte zkontrolujte, jestli se a pomocí myši a klávesu TAB k dosažení jednotlivých prvků. Ujistěte se, že informace uváděné v pole název, stav, Role, umístění a hodnota okna zkontrolujte, jestli se má smysl pro uživatele pro každý objekt v uživatelském rozhraní.
