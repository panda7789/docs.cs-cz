---
title: "Návod: Vytvoření aplikace systému Windows s usnadněnou obsluhou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5b52f9f06e2a4adf401367e337be81684f661e1
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>Návod: Vytvoření aplikace systému Windows s usnadněnou obsluhou
Vytváření přístupné aplikací má zásadní obchodní dopad. Mnoho vlády mají požadavky na usnadnění nákup softwaru. Logo Certified for Windows obsahuje požadavky na usnadnění přístupu. Usnadnění softwaru se vztahuje odhadované 30 milionů obyvatele samostatně, USA, kolika z nich potenciální zákazníky.  
  
 Tento názorný postup vyřeší pět požadavky na usnadnění přístupu pro logo Certified for Windows. Dostupné aplikace se podle těchto požadavků:  
  
-   Podporovat velikost ovládacích panelů, barvy, písma a zadejte nastavení. Panel nabídek, záhlaví, ohraničení a stavového řádku změní všechny velikost sami když uživatel změní nastavení ovládacího panelu. V této aplikaci se nevyžadují žádné další změny ovládací prvky nebo kódu.  
  
-   Podpora režimu vysokého kontrastu.  
  
-   Zadejte zdokumentovaných klávesnice přístup ke všem funkcím.  
  
-   Vystavení umístění fokus klávesnice vizuálně a programově.  
  
-   Vyhněte se předávání důležitých informací zvukovou samostatně.  
  
 Další informace najdete v tématu [prostředky pro navrhování přístupné aplikace](/visualstudio/ide/reference/resources-for-designing-accessible-applications).  
  
 Informace na podporu různých rozložení klávesnice najdete v tématu [osvědčené postupy pro vývoj aplikací připravených](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Tento návod vytvoří uživatelské rozhraní pro aplikaci, která přebírá pizza objednávky. Skládá se z <xref:System.Windows.Forms.TextBox> pro název zákazníka, <xref:System.Windows.Forms.RadioButton> skupina a vyberte velikost pizza <xref:System.Windows.Forms.CheckedListBox> pro výběr toppings, dvou ovládacích prvků tlačítko s názvem bez přípony pořadí a zrušit a nabídky pomocí příkazu pro ukončení.  
  
 Uživatel zadá název zákazníka, velikost pizza a toppings potřeby. Když uživatel klikne na tlačítko pořadí, souhrn pořadí a jeho náklady jsou zobrazeny v okně se zprávou a ovládací prvky jsou nezaškrtnuté a připravené pro další pořadí. Když uživatel klikne na tlačítko Storno, ovládací prvky jsou nezaškrtnuté a připravené pro další pořadí. Když uživatel klikne na položku nabídky ukončení, program se ukončí.  
  
 Zvýraznění tohoto návodu není kód pro maloobchodní pořadí systému, ale usnadnění uživatelského rozhraní. Průvodce ukazuje, že funkce pro usnadnění přístupu několik často používané ovládací prvky, včetně tlačítka, přepínače, textových polí a popisky.  
  
#### <a name="to-begin-making-the-application"></a>Chcete-li začít vytvářet aplikace  
  
-   Vytvoření nové aplikace Windows v [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]. Název projektu **PizzaOrder**. (Podrobnosti najdete v tématu [vytváření nových řešení a projekty](/visualstudio/ide/creating-solutions-and-projects).)  
  
## <a name="adding-the-controls-to-the-form"></a>Přidání ovládacích prvků formuláře  
 Při přidávání ovládacích prvků na formuláři, mějte na paměti následující pokyny, aby se aplikace dostupné:  
  
-   Nastavte <xref:System.Windows.Forms.Control.AccessibleDescription%2A> a <xref:System.Windows.Forms.Control.AccessibleName%2A> vlastnosti. V tomto příkladu výchozí nastavení <xref:System.Windows.Forms.Control.AccessibleRole%2A> je dostačující. Další informace o vlastnostech usnadnění přístupu najdete v tématu [poskytuje informace o usnadnění pro ovládací prvky na formuláři Windows](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).  
  
-   Nastavení velikosti písma 10 bodů nebo větší.  
  
    > [!NOTE]
    >  Pokud nastavíte velikost písma formuláře na 10, při spuštění, bude mít všechny ovládací prvky, později přidané do formuláře velikost písma 10.  
  
-   Ujistěte se, že libovolný ovládací prvek popisek, který popisuje ovládacím prvku TextBox okamžitě předchází TextBox – ovládací prvek v pořadí.  
  
-   Přidat přístupový klíč, pomocí znaku "&" na <xref:System.Windows.Forms.Control.Text%2A> vlastnosti libovolného ovládacího prvku, uživatel může chtít přejděte do.  
  
-   Přidat přístupový klíč, pomocí znaku "&", položky <xref:System.Windows.Forms.Control.Text%2A> vlastnost štítek, který předchází ovládacího prvku, který uživatel může chtít přejděte do. Nastavit zobrazí popisky <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `true`, tak, aby fokus je nastavena na další ovládací prvek v pořadí, když uživatel stiskne přístupový klíč.  
  
-   Přidejte přístupové klíče pro všechny položky nabídky.  
  
#### <a name="to-make-your-windows-application-accessible"></a>Pro zpřístupnění aplikací pro Windows  
  
-   Přidání ovládacích prvků formuláře a nastavte vlastnosti, jak je popsáno níže. Zobrazí se obrázek na konci v tabulce pro model, jak k uspořádání ovládacích prvků na formuláři.  
  
    |Objekt|Vlastnost|Hodnota|  
    |------------|--------------|-----------|  
    |Form1|AccessibleDescription|Pořadí formuláře|  
    ||AccessibleName|Pořadí formuláře|  
    ||Velikost písma|10|  
    ||Text|Formulář pro objednání pizzy|  
    |PictureBox|Název|Logo|  
    ||AccessibleDescription|Řez pizza|  
    ||AccessibleName|Logo společnosti|  
    ||Image|Všechny ikony nebo rastrového obrázku|  
    |Popisek|Název|companyLabel|  
    ||Text|Dobrý Pizza|  
    ||Pořadové číslo prvku|1|  
    ||AccessibleDescription|Název společnosti|  
    ||AccessibleName|Název společnosti|  
    ||Barva pozadí|modrá|  
    ||ForeColor|žlutý|  
    ||Velikost písma|18|  
    |Popisek|Název|customerLabel|  
    ||Text|& název|  
    ||Pořadové číslo prvku|2|  
    ||AccessibleDescription|Popisek názvu zákazníka|  
    ||AccessibleName|Popisek názvu zákazníka|  
    ||Usemnemonic –|Hodnota TRUE|  
    |TextBox|Název|JménoZákazníka|  
    ||Text|(žádný)|  
    ||Pořadové číslo prvku|3|  
    ||AccessibleDescription|Jméno zákazníka|  
    ||AccessibleName|Jméno zákazníka|  
    |GroupBox|Název|sizeOptions|  
    ||AccessibleDescription|Možnosti velikosti pizza|  
    ||AccessibleName|Možnosti velikosti pizza|  
    ||Text|Velikost pizza|  
    ||Pořadové číslo prvku|4|  
    |RadioButton|Název|smallPizza|  
    ||Text|& malé $6.00|  
    ||Zaškrtnutí|Hodnota TRUE|  
    ||Pořadové číslo prvku|0|  
    ||AccessibleDescription|Malé pizza|  
    ||AccessibleName|Malé pizza|  
    |RadioButton|Název|largePizza|  
    ||Text|& velké 10,00 USD|  
    ||Pořadové číslo prvku|1|  
    ||AccessibleDescription|Velké pizza|  
    ||AccessibleName|Velké pizza|  
    |Popisek|Název|toppingsLabel|  
    ||Text|& toppings ($0,75 každý)|  
    ||Pořadové číslo prvku|5|  
    ||AccessibleDescription|Popisek toppings|  
    ||AccessibleName|Popisek toppings|  
    ||Usemnemonic –|Hodnota TRUE|  
    |CheckedListBox|Název|toppings|  
    ||Pořadové číslo prvku|6|  
    ||AccessibleDescription|K dispozici toppings|  
    ||AccessibleName|K dispozici toppings|  
    ||Položky|Pepperoni salám, hub|  
    |Tlačítko|Název|pořadí|  
    ||Text|& pořadí|  
    ||Pořadové číslo prvku|7|  
    ||AccessibleDescription|Celkový počet pořadí|  
    ||AccessibleName|Celkové pořadí|  
    |Tlačítko|Název|Zrušit|  
    ||Text|& Zrušit|  
    ||Pořadové číslo prvku|8|  
    ||AccessibleDescription|Zrušit pořadí|  
    ||AccessibleName|Zrušit pořadí|  
    |MainMenu|Název|theMainMenu|  
    |Položka nabídky|Název|fileCommands|  
    ||Text|& souboru|  
    |Položka nabídky|Název|exitApp|  
    ||Text|& Konec|  
  
     ![Formulář pro objednání pizzy](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")  
Formulář bude vypadat přibližně takto:  
  
## <a name="supporting-high-contrast-mode"></a>Podpora režimu vysokého kontrastu  
 V režimu Vysoký kontrast je nastavení systému Windows, který zlepšuje čitelnosti pomocí kontrastní barvy a velikosti písma, které jsou užitečné pro uživatele se zrakovým postižením. <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Vlastnost je poskytována k určení, zda je nastaven režimu vysokého kontrastu.  
  
 Pokud je SystemInformation.HighContrast `true`, by měla aplikace:  
  
-   Zobrazit všechny prvky uživatelského rozhraní pomocí barevného schématu systému  
  
-   Oznamují vizuální upozornění nebo zvukových veškeré informace, které se bude předávat přes barvu. Například pokud konkrétní seznam položek se zvýrazní pomocí red písmo, můžete také přidat tučné písmo, tak, aby uživatel má jiný color upozornění, že jsou vyznačené položky.  
  
-   Vynechat všechny bitové kopie nebo vzory za text  
  
 Aplikace by se mělo zjistit nastavením <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> když aplikaci spustí a reagovat na systémové události <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Událost se vyvolá, vždy, když hodnota <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> změny.  
  
 V naší aplikaci, je jediným prvkem, který nepoužívá nastavení systému pro barvu `lblCompanyName`. <xref:System.Drawing.SystemColors> Třída se používá k změňte nastavení barvu popisku na barvy vybraných uživatelem systému.  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Chcete-li povolit režimu vysokého kontrastu účinným způsobem  
  
1.  Vytvořte metodu a nastavit barvy popisku pro barev systému.  
  
    ```  
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
  
2.  Volání `SetColorScheme` postup v konstruktoru formuláře (`Public Sub New()` v jazyce Visual Basic a `public class Form1` v jazyce Visual C#). Pro přístup k konstruktoru v jazyce Visual Basic, budete muset rozbalte oblast s názvem bez přípony **Windows Form Designer generovaného kódu**.  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3.  Vytvořit procedury události s odpovídajícím podpisem, aby odpovídal na <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> událostí.  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4.  Přidejte do konstruktoru formuláře kód po volání `InitializeComponents`, spojit události postup systémové události. Tato metoda volá `SetColorScheme` postupu.  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
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
  
5.  Přidejte kód pro formulář <xref:System.Windows.Forms.Control.Dispose%2A> metody před volání <xref:System.Windows.Forms.Control.Dispose%2A> metoda základní třídy, chcete-li uvolnit událostí po ukončení aplikace. Abyste měli přístup <xref:System.Windows.Forms.Control.Dispose%2A> metody v jazyce Visual Basic, budete muset rozbalte oblast s názvem bez přípony Windows Form Designer vygenerovat kód.  
  
    > [!NOTE]
    >  Spustí kód událostí systému vlákno odděleně od hlavní aplikace. Pokud není verze události, kód, který spojit události se spustí i po ukončení programu.  
  
    ```  
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
  
6.  Stisknutím klávesy F5 spusťte aplikaci.  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a>Předávání důležitých informací jiným způsobem než zvuk  
 V této aplikaci žádné informace předávají zvukovou samostatně. Pokud používáte zvuku ve vaší aplikaci, musí jiným způsobem a zadejte informace.  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a>K poskytování informací jiným způsobem než zvuk  
  
1.  Zkontrolujte záhlaví s použitím funkce rozhraní API systému Windows FlashWindow, flash. Příklad toho, jak volat funkce rozhraní API systému Windows, naleznete v části [návod: volání rozhraní API systému Windows](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
    > [!NOTE]
    >  Uživatel může mít povoleno, službu Popis zvuku Windows, která způsobí také okno na flash po přehrání zvuku systému prostřednictvím předdefinované mluvčího počítače.  
  
2.  Důležité informace zobrazí v nemodálním okně, tak, aby uživatel může odpovědět na ni.  
  
3.  Zobrazte okno se zprávou, který získá fokus klávesnice. Tato metoda Vyhněte se při uživatel může být psaní.  
  
4.  Zobrazí indikátor stavu v oznamovací oblasti stav na hlavním panelu. Podrobnosti najdete v tématu [přidání ikon aplikací do TaskBar se součástí Windows Forms NotifyIcon](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Před nasazením aplikace, měli byste otestovat funkce usnadnění, které jste implementovali.  
  
#### <a name="to-test-accessibility-features"></a>Testování funkce pro usnadnění přístupu  
  
1.  Test přístupu k klávesnice, myš odpojte a Navigovat v uživatelském rozhraní pro každou funkci pouze pomocí klávesnice. Zajistěte, aby všechny úlohy mohou být provedeny pomocí klávesnice jenom.  
  
2.  K otestování podpory vysoký kontrast, zvolte ikonu Možnosti usnadnění v Ovládacích panelech. Klikněte na kartu zobrazení a zaškrtněte políčko použití vysokého kontrastu. Procházejte všechny prvky uživatelského rozhraní pro zajištění, že barev a písem změny se projeví. Ujistěte se také, vynechání bitové kopie nebo vzory vykreslovat za text.  
  
    > [!NOTE]
    >  Systém Windows NT 4 nemá ikonu Možnosti usnadnění v Ovládacích panelech. Tento postup pro změnu nastavení SystemInformation.HighContrast proto nefunguje v systému Windows NT 4.  
  
3.  Další nástroje jsou snadno dostupné pro testování usnadnění aplikace.  
  
4.  Chcete-li otestovat vystavení fokus klávesnice, spusťte Lupa. (Otevřete ho kliknutím na **spustit** nabídky, přejděte na příkaz **programy**, přejděte na příkaz **Příslušenství**, přejděte na **usnadnění**a pak klikněte na tlačítko  **Lupa**). Navigovat v uživatelském rozhraní, pomocí procházení tabulátorem klávesnice a myši. Ujistěte se, že je správně sledovat všechny navigační **Lupa**.  
  
5.  K testování zpřístupňuje prvky obrazovky, spusťte kontroly a použít k dosažení každý prvek myši a klávesy TAB. Zajistěte, aby byl informace uvedené v polích pro název, stav, Role, umístění a hodnota okna kontroly srozumitelné pro uživatele pro každý objekt v uživatelském rozhraní.
