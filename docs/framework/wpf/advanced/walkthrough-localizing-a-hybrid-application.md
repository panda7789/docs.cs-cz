---
title: 'Návod: Lokalizace hybridní aplikace'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111111"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Návod: Lokalizace hybridní aplikace

Tento návod ukazuje, jak lokalizovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky v hybridní aplikaci založené na formulářích Windows Forms.

Mezi úkoly znázorněné v tomto návodu patří:

- Vytvoření hostitelského projektu windows forms.

- Přidání lokalizovatelného obsahu.

- Povolení lokalizace.

- Přiřazení identifikátorů prostředků.

- Použití nástroje LocBaml k vytvoření satelitní sestavy.

Úplný seznam kódu úkolů znázorněných v tomto návodu naleznete v [tématu Lokalizace ukázky hybridní aplikace](https://go.microsoft.com/fwlink/?LinkID=160015).

Po dokončení budete mít lokalizované hybridní aplikace.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Vytvoření hostitelského projektu formulářů Windows Forms

Prvním krokem je vytvoření projektu aplikace Windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Forms a přidání prvku s obsahem, který budete lokalizovat.

### <a name="to-create-the-host-project"></a>Vytvoření hostitelského projektu

1. Vytvořte projekt aplikace `LocalizingWpfInWf` **WPF** s názvem .  (File**New** > **New** > **Project** > **Visual C#** nebo Visual **Basic** > **Classic Desktop** > **WPF Application**).

2. Přidejte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> prvek `SimpleControl` volaný do projektu.

3. Pomocí <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku `SimpleControl` umístěte prvek do formuláře. Další informace naleznete [v tématu Návod: Hostování kompozitního ovládacího prvku 3D WPF ve formulářích systému Windows](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Přidání lokalizovatelného obsahu

Dále přidáte ovládací prvek popisku formuláře [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému Windows a nastavíte obsah prvku na lokalizovatelný řetězec.

### <a name="to-add-localizable-content"></a>Přidání lokalizovatelného obsahu

1. V **Průzkumníku řešení**poklepejte na **soubor SimpleControl.xaml** a otevřete jej v Návrháři WPF.

2. Nastavte obsah ovládacího <xref:System.Windows.Controls.Button> prvku pomocí následujícího kódu.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. V **Průzkumníku řešení**poklepejte na **Formulář1** a otevřete jej v Návrháři formulářů systému Windows.

4. Otevřete **panel nástrojů** a poklepáním na **Popisek** přidejte do formuláře ovládací prvek popisku. Nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> její `"Hello"`vlastnosti na .

5. Stisknutím **klávesy F5** vytvořte a spusťte aplikaci.

     `SimpleControl` Prvek i ovládací prvek popisku zobrazují text **"Hello"**.

## <a name="enabling-localization"></a>Povolení lokalizace

Návrhář formulářů systému Windows poskytuje nastavení pro povolení lokalizace v satelitním sestavení.

### <a name="to-enable-localization"></a>Povolení lokalizace

1. V **Průzkumníku řešení**poklepejte na **Form1.cs** a otevřete jej v Návrháři formulářů systému Windows.

2. V okně **Vlastnosti** nastavte hodnotu **lokalizovatelné vlastnosti** formuláře na `true`.

3. V okně **Vlastnosti** nastavte hodnotu **Language** vlastnost **španělština (Španělsko)**.

4. V Návrháři formulářů systému Windows vyberte ovládací prvek popisků.

5. V okně **Vlastnosti** nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> `"Hola"`vlastnosti na .

     Do projektu je přidán nový soubor prostředků s názvem Form1.es-ES.resx.

6. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na **Form1.cs** a kliknutím na **Zobrazit kód** jej otevřete v Editoru kódu.

7. Zkopírujte následující kód `Form1` do konstruktoru před `InitializeComponent`voláním .

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku LocalizingWpfInWf** a klepněte na příkaz **Uvolnit projekt**.

     Název projektu je označen **(není k dispozici).**

9. Klepněte pravým tlačítkem myši na **localizingWpfInWf**a klepněte na příkaz **Upravit lokalizaciWpfInWf.csproj**.

     Soubor projektu se otevře v Editoru kódu.

10. Zkopírujte následující řádek `PropertyGroup` do prvního v souboru projektu.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Uložte soubor projektu a zavřete jej.

12. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku LocalizingWpfInWf** a klepněte na příkaz **Znovu načíst projekt**.

## <a name="assigning-resource-identifiers"></a>Přiřazení identifikátorů prostředků

Lokalizovatelný obsah můžete namapovat na sestavení prostředků pomocí identifikátorů prostředků. Aplikace MsBuild.exe automaticky přiřadí identifikátory prostředků, když zadáte `updateuid` možnost.

### <a name="to-assign-resource-identifiers"></a>Přiřazení identifikátorů prostředků

1. V nabídce Start otevřete příkazový řádek pro vývojáře pro Visual Studio.

2. Pomocí následujícího příkazu přiřaďte identifikátory prostředků k lokalizovatelnému obsahu.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. V **Průzkumníku řešení**poklepejte na **soubor SimpleControl.xaml** a otevřete jej v Editoru kódu. Uvidíte, že `msbuild` příkaz přidal `Uid` atribut do všech prvků. To usnadňuje lokalizaci prostřednictvím přiřazení identifikátorů prostředků.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Stisknutím klávesy **F6** sestavíte řešení.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Použití LocBaml k vytvoření satelitní hospo-

Lokalizovaný obsah je uložen v *satelitním sestavení*pouze pro prostředky . Pomocí nástroje příkazového řádku LocBaml.exe můžete vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizované sestavení pro váš obsah.

### <a name="to-produce-a-satellite-assembly"></a>Chcete-li vytvořit satelitní sestavení

1. Zkopírujte soubor LocBaml.exe do složky obj\Debug projektu. Další informace naleznete v [tématu Localize aplikace](how-to-localize-an-application.md).

2. V okně příkazového řádku extrahujte řetězce prostředků do dočasného souboru pomocí následujícího příkazu.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Otevřete soubor temp.csv pomocí sady Visual Studio nebo jiného textového editoru. Nahraďte `"Hello"` řetězec jeho `"Hola"`španělským překladem .

4. Uložte soubor temp.csv.

5. Ke generování lokalizovaného souboru prostředků použijte následující příkaz.

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     Soubor LocalizingWpfInWf.g.es-ES.resources je vytvořen ve složce obj\Debug.

6. K vytvoření lokalizovaného satelitního sestavení použijte následující příkaz.

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     Soubor LocalizingWpfInWf.resources.dll je vytvořen ve složce obj\Debug.

7. Zkopírujte soubor LocalizingWpfInWf.resources.dll do složky bin\Debug\es. Nahraďte existující soubor.

8. Spusťte soubor LocalizingWpfInWf.exe, který je umístěn ve složce bin\Ladění projektu. Neobnovovat aplikaci nebo satelitní sestavení bude přepsáno.

     Aplikace zobrazuje lokalizované řetězce namísto anglických řetězců.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Lokalizace aplikace](how-to-localize-an-application.md)
- [Návod: Lokalizace formulářů systému Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
