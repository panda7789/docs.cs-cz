---
title: 'Návod: Lokalizace hybridní aplikace'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: b406d539f2446824027e9462c8ecbe20c18cfb27
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794131"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Návod: Lokalizace hybridní aplikace

V tomto návodu se dozvíte, jak lokalizovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky do model Windows Forms hybridní aplikace založené na.

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváří se projekt hostitele model Windows Forms.

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

Prvním krokem je vytvoření projektu model Windows Forms aplikace a přidání prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s obsahem, který budete lokalizovat.

### <a name="to-create-the-host-project"></a>Vytvoření hostitelského projektu

1. Vytvořte projekt **aplikace WPF** s názvem `LocalizingWpfInWf`.  (**Soubor** > **nové** > **projektu** > **vizuálu C#**  nebo **Visual Basic** > **klasické desktopové** > **WPF aplikace**).

2. Přidejte do projektu prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> s názvem `SimpleControl`.

3. Pomocí ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost> umístěte `SimpleControl` prvek do formuláře. Další informace najdete v tématu [Návod: hostování složeného ovládacího prvku 3D WPF v model Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Přidávání Lokalizovatelnýho obsahu

Dále přidáte ovládací prvek popisek model Windows Forms a nastavíte obsah elementu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na Lokalizovatelný řetězec.

### <a name="to-add-localizable-content"></a>Přidání lokalizovatelné obsahu

1. V **Průzkumník řešení**poklikejte na **SimpleControl. XAML** a otevře se v Návrháři WPF.

2. Obsah ovládacího prvku <xref:System.Windows.Controls.Button> nastavte pomocí následujícího kódu.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. V **Průzkumník řešení**dvakrát klikněte na **Form1** a otevřete ho v Návrhář formulářů.

4. Otevřete **sadu nástrojů** a dvojitým kliknutím na položku **popisek** přidejte ovládací prvek popisek do formuláře. Nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Text%2A> na `"Hello"`.

5. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

     Prvek `SimpleControl` i ovládací prvek popisek zobrazí text **"Hello"** .

## <a name="enabling-localization"></a>Povolení lokalizace

Návrhář formulářů poskytuje nastavení pro povolení lokalizace v satelitním sestavení.

### <a name="to-enable-localization"></a>Povolení lokalizace

1. V **Průzkumník řešení**dvakrát klikněte na **Form1.cs** a otevřete ji v Návrhář formulářů.

2. V okně **vlastnosti** nastavte hodnotu vlastnosti **localize** formuláře na `true`.

3. V okně **vlastnosti** nastavte hodnotu vlastnosti **Language** na **španělština (Španělsko)** .

4. V Návrhář formulářů vyberte ovládací prvek popisek.

5. V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Text%2A> na `"Hola"`.

     Do projektu se přidá nový soubor prostředků s názvem Form1.es-ES. resx.

6. V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1.cs** a kliknutím na **Zobrazit kód** ho otevřete v editoru kódu.

7. Zkopírujte následující kód do konstruktoru `Form1` před voláním `InitializeComponent`.

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

Lokalizovatelné obsahy můžete mapovat na sestavení prostředků pomocí identifikátorů prostředků. Když zadáte možnost `updateuid`, aplikace MsBuild. exe automaticky přiřadí identifikátory prostředků.

### <a name="to-assign-resource-identifiers"></a>Přiřazení identifikátorů prostředků

1. V nabídce Start otevřete Developer Command Prompt pro Visual Studio.

2. K přiřazení identifikátorů prostředků k lokalizovatelnýmu obsahu použijte následující příkaz.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. V **Průzkumník řešení**poklikejte na **SimpleControl. XAML** a otevře se v editoru kódu. Uvidíte, že příkaz `msbuild` přidal atribut `Uid` do všech prvků. To usnadňuje lokalizaci prostřednictvím přiřazení identifikátorů prostředků.

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

3. Otevřete soubor Temp. csv pomocí sady Visual Studio nebo jiného textového editoru. Nahraďte řetězec `"Hello"` jeho španělským překladem `"Hola"`.

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
- [Návod: lokalizace model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
