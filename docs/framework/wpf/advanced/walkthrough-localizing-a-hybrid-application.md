---
title: 'Návod: Lokalizace hybridní aplikace'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 685c68967f69e8933ff3dd2cd062e0893c7e2da6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076807"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Návod: Lokalizace hybridní aplikace

Tento návod ukazuje, jak lokalizovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvků v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]– hybridní aplikace.

Úlohy v tomto návodu zahrnují:

-   Vytváří [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projektu hostitel.

-   Přidání lokalizovatelné obsahu.

-   Povoluje se lokalizace.

-   Přiřazení identifikátory prostředků.

-   Chcete-li vytvořit satelitní sestavení pomocí locbaml – nástroj.

Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [lokalizace ukázkové aplikace hybridní](https://go.microsoft.com/fwlink/?LinkID=160015).

Až skončíte, bude mít lokalizované hybridní aplikace.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

-   Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Vytvoření projektu Windows Forms hostitele

Prvním krokem je vytvoření [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace projekt a přidejte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu s obsahem, který bude lokalizovat.

### <a name="to-create-the-host-project"></a>Chcete-li vytvořit projekt hostitele

1.  Vytvoření **aplikace WPF** projekt s názvem `LocalizingWpfInWf`.  (**Souboru** > **nové** > **projektu** > **Visual C#** nebo **jazyka Visual Basic**   >  **Klasický desktopový** > **aplikace WPF**).

2.  Přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> prvek s názvem `SimpleControl` do projektu.

3.  Použití <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek umístit `SimpleControl` prvek na formuláři. Další informace najdete v tématu [návod: hostování 3D složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Přidání lokalizovatelné obsahu

V dalším kroku přidáte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacímu prvku popisek a nastavte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] reprezentace obsahu elementu do zdrojů lokalizovatelných řetězců.

### <a name="to-add-localizable-content"></a>Chcete-li přidat lokalizovatelné obsahu

1.  V **Průzkumníka řešení**, dvakrát klikněte na panel **SimpleControl.xaml** a otevřete tak [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

2.  Nastavení obsahu prvku <xref:System.Windows.Controls.Button> řídit pomocí následujícího kódu.

     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3.  V **Průzkumníka řešení**, dvakrát klikněte na panel **Form1** ho otevřete v Návrháři formulářů Windows.

4.  Otevřít **nástrojů** a dvakrát klikněte na panel **popisek** přidání ovládacího prvku popisek do formuláře. Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `"Hello"`.

5.  Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.

     Oba `SimpleControl` elementu a ovládací prvek popisku se zobrazí text **"Hello"**.

## <a name="enabling-localization"></a>Povoluje se lokalizace

Návrhář formulářů Windows poskytuje nastavení pro povolení lokalizace v satelitním sestavení.

### <a name="to-enable-localization"></a>Chcete-li povolit lokalizaci

1.  V **Průzkumníka řešení**, dvakrát klikněte na panel **Form1.cs** ho otevřete v Návrháři formulářů Windows.

2.  V **vlastnosti** okno, nastavte hodnotu vlastnosti formuláře **Localizable** vlastnost `true`.

3.  V **vlastnosti** okno, nastavte hodnotu **jazyk** vlastnost **Španělština (Španělsko)**.

4.  V Návrháři formulářů Windows vyberte ovládací prvek popisku.

5.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> vlastnost `"Hola"`.

     Do projektu se přidá nový soubor prostředků s názvem Form1.es ES.resx.

6.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1.cs** a klikněte na tlačítko **zobrazit kód** ho otevřete v editoru kódu.

7.  Zkopírujte následující kód do `Form1` konstruktoru, předchozí volání `InitializeComponent`.

     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **LocalizingWpfInWf** a klikněte na tlačítko **uvolnit projekt**.

     Název projektu je označené jako **(není k dispozici)**.

9. Klikněte pravým tlačítkem na **LocalizingWpfInWf**a klikněte na tlačítko **upravit LocalizingWpfInWf.csproj**.

     Soubor projektu se otevře v editoru kódu.

10. Zkopírujte následující řádek do první `PropertyGroup` v souboru projektu.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Uložte soubor projektu a zavřete ho.

12. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **LocalizingWpfInWf** a klikněte na tlačítko **znovu načíst projekt**.

## <a name="assigning-resource-identifiers"></a>Přiřazuje se identifikátory prostředků

Můžete namapovat lokalizovatelné obsah sestavení prostředků s použitím identifikátory prostředků. Při zadávání MsBuild.exe aplikace automaticky přiřadí identifikátory prostředků `updateuid` možnost.

### <a name="to-assign-resource-identifiers"></a>K přiřazení identifikátory prostředků

1.  Z nabídky Start otevřete příkazový řádek sady Visual Studio.

2.  Použijte následující příkaz k přiřazení identifikátory prostředků lokalizovatelných obsah.

    ```
    msbuild /t:updateuid LocalizingWpfInWf.csproj
    ```

3.  V **Průzkumníka řešení**, dvakrát klikněte na panel **SimpleControl.xaml** ho otevřete v editoru kódu. Uvidíte, že `msbuild` příkaz má přidat `Uid` atribut na všechny prvky. To usnadňuje lokalizaci prostřednictvím přiřazení identifikátory prostředků.

     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4.  Stisknutím klávesy **F6** k sestavení řešení.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Pomocí locbaml – Chcete-li vytvořit satelitní sestavení

Lokalizovaný obsah uložený v pouze prostředky *satelitní sestavení*. Pomocí nástroje příkazového řádku LocBaml.exe k vytvoření lokalizovaných sestavení pro vaši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.

### <a name="to-produce-a-satellite-assembly"></a>Chcete-li vytvořit satelitní sestavení

1.  Zkopírujte do složky vašeho projektu obj\Debug LocBaml.exe. Další informace najdete v tématu [lokalizace aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).

2.  V okně příkazového řádku použijte následující příkaz k extrakci zdrojové řetězce do dočasného souboru.

    ```
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3.  Otevřete soubor temp.csv pomocí sady Visual Studio nebo jiného textového editoru. Nahraďte řetězec `"Hello"` spolu s překladem Španělština `"Hola"`.

4.  Uložte soubor temp.csv.

5.  Použijte následující příkaz k vygenerování lokalizované soubory prostředků.

    ```
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     Soubor LocalizingWpfInWf.g.es ES.resources se vytvoří ve složce obj\Debug.

6.  Použijte následující příkaz k vytvoření lokalizované satelitní sestavení.

    ```
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     Soubor LocalizingWpfInWf.resources.dll se vytvoří ve složce obj\Debug.

7.  Zkopírujte soubor LocalizingWpfInWf.resources.dll do složky projektu bin\Debug\es-ES. Nahraďte existující soubor.

8.  Spusťte LocalizingWpfInWf.exe, který je umístěn ve složce bin\Debug vašeho projektu. Znovu sestavit aplikaci nebo do satelitního sestavení se přepíšou.

     Aplikace se zobrazí lokalizované řetězce místo anglické řetězce.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Lokalizace aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
- [Návod: Lokalizace Windows Forms](https://msdn.microsoft.com/library/9a96220d-a19b-4de0-9f48-01e5d82679e5)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
