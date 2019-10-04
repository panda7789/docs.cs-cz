---
title: 'Návod: Vytvoření aplikace systému Windows s usnadněnou obsluhou'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
dev_langs:
- csharp
- vb
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: b8f0c7c4584505d382e78aca68e2e99c9fa7748f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834628"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>Návod: Vytvoření aplikace systému Windows s usnadněnou obsluhou

Vytváření přístupných aplikací má zásadní dopad na firmu. Mnoho vlád má předpisy pro usnadnění nákupu softwaru. Logo Certified for Windows zahrnuje požadavky na usnadnění přístupu. Dostupnost softwaru má vliv na odhadované 30 000 000 obyvatele samotného USA, mnoho z nich potenciálních zákazníků.

Tento návod bude řešit pět požadavků na přístupnost pro logo Certified for Windows. V souladu s těmito požadavky bude dostupná aplikace:

- Podporuje nastavení velikosti, barvy, písma a vstupu ovládacích panelů. Panel nabídek, záhlaví, ohraničení a stavový řádek se změní, když uživatel změní nastavení ovládacího panelu. V této aplikaci nejsou vyžadovány žádné další změny ovládacích prvků nebo kódu.

- Podpora režimu Vysoký kontrast.

- Poskytněte zdokumentovanému přístupu ke všem funkcím klávesnici.

- Vizuálně a programově vystavit polohu fokusu klávesnice

- Nevytvářejte důležité informace pouhým zvukem.

Další informace najdete v tématu [prostředky pro návrh aplikací, které jsou k dispozici](/visualstudio/ide/reference/resources-for-designing-accessible-applications).

Informace o podpoře různých rozložení klávesnice najdete v tématu [osvědčené postupy pro vývoj aplikací připravených pro použití ve světě](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).

## <a name="creating-the-project"></a>Vytvoření projektu

Tento návod vytvoří uživatelské rozhraní pro aplikaci, která přijímá Pizza objednávky. Skládá se z <xref:System.Windows.Forms.TextBox> pro jméno zákazníka, skupinu <xref:System.Windows.Forms.RadioButton> pro výběr velikosti Pizza, <xref:System.Windows.Forms.CheckedListBox> pro výběr toppings, dvou ovládacích prvků tlačítko s popiskem pořadí a zrušení a nabídka s příkazem Exit.

Uživatel zadá jméno zákazníka, velikost Pizza a požadované toppings. Když uživatel klikne na tlačítko objednávka, v okně se zprávou se zobrazí souhrn objednávky a jeho nákladů a ovládací prvky budou vymazány a připraveny pro další objednávku. Když uživatel klikne na tlačítko Storno, ovládací prvky se vymažou a připraví k dalšímu pořadí. Když uživatel klikne na položku nabídky Exit, program se zavře.

Důrazem na tento návod není kód pro systém maloobchodních objednávek, ale přístupnost uživatelského rozhraní. Návod ukazuje funkce přístupnosti několika často používaných ovládacích prvků, včetně tlačítek, přepínačů, textových polí a popisků.

#### <a name="to-begin-making-the-application"></a>Zahájení provádění aplikace

- Vytvořte novou aplikaci pro Windows v Visual Basic nebo vizuálu C#. Pojmenujte projekt **PizzaOrder**. Podrobnosti najdete v tématu [vytváření nových řešení a projektů](/visualstudio/ide/creating-solutions-and-projects).

## <a name="adding-the-controls-to-the-form"></a>Přidání ovládacích prvků do formuláře

Při přidávání ovládacích prvků do formuláře mějte na paměti následující pokyny, jak zpřístupnit aplikaci, která je k dispozici:

- Nastavte vlastnosti <xref:System.Windows.Forms.Control.AccessibleDescription%2A> a <xref:System.Windows.Forms.Control.AccessibleName%2A>. V tomto příkladu je výchozí nastavení pro <xref:System.Windows.Forms.Control.AccessibleRole%2A> dostatečné. Další informace o vlastnostech přístupnosti najdete v tématu [poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).

- Nastavte velikost písma na 10 bodů nebo větší.

  > [!NOTE]
  > Pokud nastavíte velikost písma formuláře na hodnotu 10 při spuštění, budou mít všechny ovládací prvky následně přidané do formuláře velikost písma 10.

- Ujistěte se, že všechny ovládací prvky popisek, které popisují ovládací prvek TextBox, bezprostředně předcházejí ovládacímu prvku TextBox v pořadí prvků.

- Přidejte přístupový klíč pomocí znaku "&" na vlastnost <xref:System.Windows.Forms.Control.Text%2A> libovolného ovládacího prvku, na který uživatel může chtít přejít.

- Přidejte přístupový klíč pomocí znaku "&" do vlastnosti <xref:System.Windows.Forms.Control.Text%2A> popisku, který předchází ovládacímu prvku, na který uživatel může chtít přejít. Nastavte vlastnost Labels ' <xref:System.Windows.Forms.Label.UseMnemonic%2A> ' na `true`, aby se fokus nastavil na další ovládací prvek v pořadí prvků, když uživatel stiskne přístupový klíč.

- Přidejte přístupové klíče do všech položek nabídky.

#### <a name="to-make-your-windows-application-accessible"></a>Zpřístupnění aplikace pro Windows

- Přidejte ovládací prvky do formuláře a nastavte vlastnosti, jak je popsáno níže. Podívejte se na obrázek na konci tabulky, kde najdete model uspořádání ovládacích prvků ve formuláři.

   |Objekt|Vlastnost|Hodnota|
   |------------|--------------|-----------|
   |Form1|AccessibleDescription|Formulář objednávky|
   ||Přístupný|Formulář objednávky|
   ||Velikost písma|10pruhový|
   ||Text|Formulář objednávky Pizza|
   |PictureBox|Name|Symbol|
   ||AccessibleDescription|Řez Pizza|
   ||Přístupný|Logo společnosti|
   ||Image|Libovolná ikona nebo rastrový obrázek|
   |Popisek|Name|companyLabel|
   ||Text|Dobrá pizza|
   ||Prvku|první|
   ||AccessibleDescription|Název společnosti|
   ||Přístupný|Název společnosti|
   ||BackColor|Novák|
   ||ForeColor|Opatřen|
   ||Velikost písma|let|
   |Popisek|Name|customerLabel|
   ||Text|Název &|
   ||Prvku|odst|
   ||AccessibleDescription|Popisek názvu zákazníka|
   ||Přístupný|Popisek názvu zákazníka|
   ||UseMnemonic|Podmínka|
   |TextBox|Name|customerName|
   ||Text|nTato|
   ||Prvku|3|
   ||AccessibleDescription|Jméno zákazníka|
   ||Přístupný|Jméno zákazníka|
   |GroupBox|Name|sizeOptions|
   ||AccessibleDescription|Pizza možnosti velikosti|
   ||Přístupný|Pizza možnosti velikosti|
   ||Text|Velikost Pizza|
   ||Prvku|4|
   |RadioButton|Name|smallPizza|
   ||Text|& malý $6,00|
   ||kontrolovaný|Podmínka|
   ||Prvku|0,8|
   ||AccessibleDescription|Malé Pizza|
   ||Přístupný|Malé Pizza|
   |RadioButton|Name|largePizza|
   ||Text|& velký $10,00|
   ||Prvku|první|
   ||AccessibleDescription|Velké Pizza|
   ||Přístupný|Velké Pizza|
   |Popisek|Name|toppingsLabel|
   ||Text|& toppings ($0,75)|
   ||Prvku|5|
   ||AccessibleDescription|Popisek toppings|
   ||Přístupný|Popisek toppings|
   ||UseMnemonic|Podmínka|
   |CheckedListBox|Name|toppings|
   ||Prvku|6|
   ||AccessibleDescription|Dostupné toppings|
   ||Přístupný|Dostupné toppings|
   ||Položky|Pepperoni, Uzenec, žampiony|
   |Tlačítko|Name|pořadí|
   ||Text|Pořadí &|
   ||Prvku|čl|
   ||AccessibleDescription|Celková objednávka|
   ||Přístupný|Celková objednávka|
   |Tlačítko|Name|Operaci|
   ||Text|Zrušit &|
   ||Prvku|8|
   ||AccessibleDescription|Zrušit pořadí|
   ||Přístupný|Zrušit pořadí|
   |MainMenu|Name|theMainMenu|
   |MenuItem|Name|Příkazy příkazů|
   ||Text|Soubor &|
   |MenuItem|Name|exitApp|
   ||Text|Konec E &|

   Formulář bude vypadat přibližně jako na následujícím obrázku:

   ![Formulář pořadí Pizza s textovým polem názvu a velikostí a toppingsm výběrem.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)

## <a name="supporting-high-contrast-mode"></a>Podpora režimu Vysoký kontrast

Režim Vysoký kontrast je nastavení systému Windows, které zlepšuje čitelnost pomocí kontrastních barev a velikostí písem, které jsou užitečné pro uživatele s vadami postiženými uživateli. K určení, zda je nastaven režim Vysoký kontrast, je k dispozici vlastnost <xref:System.Windows.Forms.SystemInformation.HighContrast%2A>.

Pokud SystemInformation. HighContrast je `true`, aplikace by měla:

- Zobrazit všechny prvky uživatelského rozhraní pomocí barevného schématu systému

- Vyjádření pomocí vizuálních pomůcek nebo zvuku jakékoli informace, které jsou předány barevně. Například pokud jsou konkrétní položky seznamu zvýrazněny pomocí červeného písma, můžete také přidat tučné písmo, aby měl uživatel nebarevnou hromádku, že se položky zvýrazní.

- Vynechat všechny obrázky nebo vzory za textem

Aplikace by měla kontrolovat nastavení <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> při spuštění aplikace a reagovat na událost systému <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>. Událost <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> se vyvolá vždy, když se změní hodnota <xref:System.Windows.Forms.SystemInformation.HighContrast%2A>.

V naší aplikaci je jediným prvkem, který nepoužívá nastavení systému pro barvy, `lblCompanyName`. Třída <xref:System.Drawing.SystemColors> se používá ke změně nastavení barev popisku na systémové barvy vybrané uživatelem.

#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Postup povolení režimu Vysoký kontrast účinným způsobem

1. Vytvořte metodu pro nastavení barev popisku na systémové barvy.

    ```vb
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

2. Zavolejte proceduru `SetColorScheme` v konstruktoru formuláře (`Public Sub New()` v Visual Basic a `public Form1()` v vizuálu C#). Chcete-li získat přístup k konstruktoru v Visual Basic, bude nutné rozšířit oblast označený jako **kód vygenerovaný návrhářem Windows Form**.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
    }
    ```

3. Pokud chcete reagovat na událost <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>, vytvořte proceduru události s odpovídajícím podpisem.

    ```vb
    Protected Sub UserPreferenceChanged(sender As Object, _
    e As Microsoft.Win32.UserPreferenceChangedEventArgs)
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public void UserPreferenceChanged(object sender,
    Microsoft.Win32.UserPreferenceChangedEventArgs e)
    {
        SetColorScheme();
    }
    ```

4. Přidejte kód do konstruktoru formuláře po volání metody `InitializeComponents`, chcete-li připojit proceduru události k systémové události. Tato metoda volá proceduru `SetColorScheme`.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
        AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           += new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
    }
    ```

5. Přidejte kód do formuláře metoda <xref:System.Windows.Forms.Control.Dispose%2A> před voláním metody <xref:System.Windows.Forms.Control.Dispose%2A> základní třídy k uvolnění události při zavření aplikace. Chcete-li získat přístup k metodě <xref:System.Windows.Forms.Control.Dispose%2A> v Visual Basic, budete muset rozbalit oblast s popiskem Windows Form Designer generovaný kód.

    > [!NOTE]
    > Kód systémové události spouští vlákno oddělené od hlavní aplikace. Pokud událost neuvolníte, kód, který zaznamenáte do události, bude spuštěn i po zavření programu.

    ```vb
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)
        If disposing AndAlso components IsNot Nothing Then
            components.Dispose()
        End If
        RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
        MyBase.Dispose(disposing)
    End Sub
    ```

    ```csharp
    protected override void Dispose(bool disposing)
    {
        if(disposing && components != null)
        {
            components.Dispose();
        }
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           -= new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
        base.Dispose( disposing );
    }
    ```

6. Stisknutím klávesy F5 spusťte aplikaci.

## <a name="conveying-important-information-by-means-other-than-sound"></a>Předávání důležitých informací jiným způsobem než zvuk

V této aplikaci nejsou žádné informace přenášeny samotným zvukem. Pokud používáte zvuk v aplikaci, měli byste informace zadat také jinými způsoby.

#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Poskytnutí informací jiným způsobem než zvuk

1. Pomocí funkce rozhraní Windows API FlashWindow nastavte záhlaví na flash. Příklad volání funkcí rozhraní API systému Windows naleznete v tématu [Návod: volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

    > [!NOTE]
    > Uživatel může mít povolenou službu Windows Popis systému Windows, což způsobí, že se okno při přehrání systémových zvuků prostřednictvím integrovaného mluvčího počítače změní také na flash.

2. Zobrazí důležité informace v nemodálním okně, aby na ni uživatel mohl reagovat.

3. Zobrazí okno se zprávou, které získá fokus klávesnice. Vyhněte se této metodě, když uživatel může napsat.

4. Zobrazí v oznamovací oblasti hlavního panelu stavový indikátor. Podrobnosti najdete v tématu [Přidání ikon aplikace na hlavní panel se součástí model Windows Forms NotifyIcon](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).

## <a name="testing-the-application"></a>Testování aplikace

Před nasazením aplikace byste měli otestovat funkce přístupnosti, které jste implementovali.

#### <a name="to-test-accessibility-features"></a>Test funkcí pro usnadnění přístupu

1. Chcete-li otestovat přístup k klávesnici, odpojte myš a procházejte uživatelské rozhraní pro každou funkci pouze pomocí klávesnice. Ujistěte se, že všechny úlohy mohou být provedeny pouze pomocí klávesnice.

2. Chcete-li otestovat podporu Vysoký kontrast, vyberte v Ovládacích panelech ikonu Možnosti usnadnění. Klikněte na kartu zobrazení a zaškrtněte políčko použít Vysoký kontrast. Procházejte všemi prvky uživatelského rozhraní, abyste měli jistotu, že se projeví změny barev a písem. Také se ujistěte, že jsou vynechány obrázky nebo vzory vykreslené za textem.

    > [!NOTE]
    > Systém Windows NT 4 nemá ikonu možností přístupnosti v Ovládacích panelech. Proto tato procedura pro změnu nastavení SystemInformation. HighContrast nefunguje v systému Windows NT 4.

3. Další nástroje jsou snadno dostupné pro testování dostupnosti aplikace.

4. Chcete-li otestovat vystavení fokusu klávesnice, spusťte program Lupa. (Pokud ho chcete otevřít, klikněte na nabídku **Start** , přejděte na **programy**, přejděte na položku **příslušenství**, přejděte na položku **usnadnění**a potom klikněte na tlačítko **Lupa**). Navigace v uživatelském rozhraní pomocí klávesových zkratek klávesnice a myši. Ujistěte se, že je veškerá navigace správně sledována v **programu Lupa**.

5. Chcete-li otestovat vystavení prvků obrazovky, spusťte kontrolu a k dosažení každého elementu použijte myš i klávesu TAB. Ujistěte se, že informace uvedené v polích název, stav, role, umístění a hodnota v okně Kontrola mají význam pro uživatele pro každý objekt v uživatelském rozhraní.
