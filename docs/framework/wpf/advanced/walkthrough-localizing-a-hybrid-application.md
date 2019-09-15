---
title: 'Návod: Lokalizace hybridní aplikace'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: b98bf7b3f0aa4e7698a5c0ca7c8ae16051ce6300
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991784"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Návod: Lokalizace hybridní aplikace

V tomto návodu se dozvíte, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizovat prvky do hybridníaplikacezaloženénabázi.[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváření projektu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hostitele.

- Přidává se Lokalizovatelný obsah.

- Povoluje se lokalizace.

- Přiřazení identifikátorů prostředků.

- Použití nástroje LocBaml k vytvoření satelitního sestavení.

Úplný výpis kódu úloh, které jsou znázorněné v tomto návodu, najdete v tématu [lokalizace ukázky hybridní aplikace](https://go.microsoft.com/fwlink/?LinkID=160015).

Po dokončení budete mít lokalizovanou hybridní aplikaci.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Vytváří se projekt hostitele model Windows Forms.

Prvním krokem je vytvoření [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projektu aplikace a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přidání prvku s obsahem, který budete lokalizovat.

### <a name="to-create-the-host-project"></a>Vytvoření hostitelského projektu

1. Vytvořte projekt **aplikace WPF** s názvem `LocalizingWpfInWf`.  (**Soubor** > **Nový** **projekt vizuál C#**  aplikace Visual BasicClassic > DesktopWPF) > . >  > 

2. Přidejte element s názvem`SimpleControl` do projektu. <xref:System.Windows.Controls.UserControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

3. Ovládací prvek slouží k `SimpleControl` umístění prvku do formuláře. <xref:System.Windows.Forms.Integration.ElementHost> Další informace najdete v tématu [Návod: Hostování složeného ovládacího prvku 3D WPF v model Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Přidávání Lokalizovatelnýho obsahu

Dále přidáte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek popisek a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavíte obsah elementu na Lokalizovatelný řetězec.

### <a name="to-add-localizable-content"></a>Přidání lokalizovatelné obsahu

1. V **Průzkumník řešení**dvakrát klikněte na **SimpleControl. XAML** a otevřete [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]ho v.

2. Nastavte obsah <xref:System.Windows.Controls.Button> ovládacího prvku pomocí následujícího kódu.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. V **Průzkumník řešení**dvakrát klikněte na **Form1** a otevřete ho v Návrhář formulářů.

4. Otevřete **sadu nástrojů** a dvojitým kliknutím na položku **popisek** přidejte ovládací prvek popisek do formuláře. Nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> vlastnosti na `"Hello"`.

5. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

     Prvek i ovládací prvek popisek zobrazí text **"Hello".** `SimpleControl`

## <a name="enabling-localization"></a>Povolení lokalizace

Návrhář formulářů poskytuje nastavení pro povolení lokalizace v satelitním sestavení.

### <a name="to-enable-localization"></a>Povolení lokalizace

1. V **Průzkumník řešení**dvakrát klikněte na **Form1.cs** a otevřete ji v Návrhář formulářů.

2. V okně **vlastnosti** nastavte hodnotu vlastnosti **Localize** formuláře na `true`.

3. V okně **vlastnosti** nastavte hodnotu vlastnosti **Language** na **španělština (Španělsko)** .

4. V Návrhář formulářů vyberte ovládací prvek popisek.

5. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> vlastnosti na `"Hola"`.

     Do projektu se přidá nový soubor prostředků s názvem Form1.es-ES. resx.

6. V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1.cs** a kliknutím na **Zobrazit kód** ho otevřete v editoru kódu.

7. Zkopírujte následující kód do `Form1` konstruktoru před `InitializeComponent`voláním.

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **LocalizingWpfInWf** a klikněte na **Uvolnit projekt**.

     Název projektu je označený **(není k dispozici)** .

9. Klikněte pravým tlačítkem na **LocalizingWpfInWf**a pak klikněte na **Upravit LocalizingWpfInWf. csproj**.

     Soubor projektu se otevře v editoru kódu.

10. Zkopírujte následující řádek do prvního `PropertyGroup` v souboru projektu.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Uložte soubor projektu a zavřete ho.

12. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **LocalizingWpfInWf** a klikněte na **znovu načíst projekt**.

## <a name="assigning-resource-identifiers"></a>Přiřazení identifikátorů prostředků

Lokalizovatelné obsahy můžete mapovat na sestavení prostředků pomocí identifikátorů prostředků. Když zadáte `updateuid` možnost, aplikace MSBuild. exe automaticky přiřadí identifikátory prostředků.

### <a name="to-assign-resource-identifiers"></a>Přiřazení identifikátorů prostředků

1. V nabídce Start otevřete Developer Command Prompt pro Visual Studio.

2. K přiřazení identifikátorů prostředků k lokalizovatelnýmu obsahu použijte následující příkaz.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. V **Průzkumník řešení**poklikejte na **SimpleControl. XAML** a otevře se v editoru kódu. Uvidíte, že `msbuild` příkaz `Uid` přidal atribut všem prvkům. To usnadňuje lokalizaci prostřednictvím přiřazení identifikátorů prostředků.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Stisknutím klávesy **F6** Sestavte řešení.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Použití LocBaml k vytvoření satelitního sestavení

Lokalizovaný obsah je uložený v *satelitním sestavení*pouze pro prostředky. Použijte nástroj příkazového řádku LocBaml. exe k vytvoření lokalizovaného sestavení pro váš [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.

### <a name="to-produce-a-satellite-assembly"></a>Vytvoření satelitního sestavení

1. Zkopírujte LocBaml. exe do složky obj\Debug vašeho projektu. Další informace najdete v tématu [lokalizace aplikace](how-to-localize-an-application.md).

2. V okně příkazového řádku použijte následující příkaz k extrakci řetězců prostředků do dočasného souboru.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Otevřete soubor Temp. csv pomocí sady Visual Studio nebo jiného textového editoru. Nahraďte řetězec `"Hello"` jeho španělským `"Hola"`překladem.

4. Uložte soubor Temp. csv.

5. K vygenerování lokalizovaného souboru prostředků použijte následující příkaz.

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     Soubor LocalizingWpfInWf.g.es-ES. Resources se vytvoří ve složce obj\Debug.

6. K sestavení lokalizovaného satelitního sestavení použijte následující příkaz.

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     Ve složce obj\Debug se vytvoří soubor LocalizingWpfInWf. Resources. dll.

7. Zkopírujte soubor LocalizingWpfInWf. Resources. dll do složky bin\Debug\es-ES projektu. Nahraďte existující soubor.

8. Spusťte LocalizingWpfInWf. exe, který je umístěný ve složce bin\Debug vašeho projektu. Znovu sestavte aplikaci nebo satelitní sestavení bude přepsáno.

     Aplikace zobrazuje lokalizované řetězce místo anglických řetězců.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Lokalizace aplikace](how-to-localize-an-application.md)
- [Návod: Lokalizace model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
