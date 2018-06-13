---
title: 'Návod: Lokalizace hybridní aplikace'
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 010c8f75a1151f5606be5ffa63d60fca364bdb59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549169"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Návod: Lokalizace hybridní aplikace
Tento návod ukazuje, jak k lokalizaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementů v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]– na základě hybridní aplikace.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytváření [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hostitele projektu.  
  
-   Přidávání lokalizovatelný obsahu.  
  
-   Povolení lokalizace.  
  
-   Přiřazení identifikátory prostředků.  
  
-   Pomocí nástroje LocBaml k vytvoření satelitní sestavení.  
  
 Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [lokalizace ukázku hybridní aplikace](http://go.microsoft.com/fwlink/?LinkID=160015).  
  
 Jakmile budete hotovi, budete mít lokalizované hybridní aplikace.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-windows-forms-host-project"></a>Vytváření projektu hostitele Windows Forms  
 Prvním krokem je vytvoření [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace projekt a přidejte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element s obsahem, který bude lokalizaci.  
  
#### <a name="to-create-the-host-project"></a>Vytvoření projektu hostitele  
  
1.  Vytvořte projekt aplikace WPF s názvem `LocalizingWpfInWf`. Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> prvek s názvem `SimpleControl` do projektu.  
  
3.  Použití <xref:System.Windows.Forms.Integration.ElementHost> řízení umístit `SimpleControl` prvek na formuláři. Další informace najdete v tématu [návod: hostování 3D složených prvků grafického subsystému WPF v rozhraní Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).  
  
## <a name="adding-localizable-content"></a>Přidávání lokalizovatelný obsahu  
 V dalším kroku přidáte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] popisku ovládacího prvku a nastavte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu elementu lokalizovatelný řetězec.  
  
#### <a name="to-add-localizable-content"></a>Přidání možnosti lokalizace obsahu  
  
1.  V Průzkumníku řešení klikněte dvakrát na **SimpleControl.xaml** otevřít v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
2.  Nastavit obsah <xref:System.Windows.Controls.Button> řízení pomocí následujícího kódu.  
  
     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  V Průzkumníku řešení klikněte dvakrát na **Form1** a otevře se v Návrháři formulářů Windows.  
  
4.  Otevřete panel a dvakrát klikněte na **popisek** přidání ovládacího prvku popisek do formuláře. Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `"Hello"`.  
  
5.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
     Obě `SimpleControl` elementu a ovládací prvek popisek zobrazit text **"Hello"**.  
  
## <a name="enabling-localization"></a>Povolení lokalizace  
 Návrhář formulářů Windows poskytuje nastavení pro povolení lokalizace v satelitní sestavení.  
  
#### <a name="to-enable-localization"></a>Chcete-li povolit lokalizace  
  
1.  V Průzkumníku řešení klikněte dvakrát na **Form1.cs** a otevře se v Návrháři formulářů Windows.  
  
2.  V okně vlastnosti nastavit hodnotu formuláře **Localizable** vlastnost `true`.  
  
3.  V okně vlastností nastavte hodnotu **jazyk** vlastnost **Španělština (Španělsko)**.  
  
4.  V Návrháři formulářů Windows vyberte ovládací prvek popisek.  
  
5.  V okně vlastností nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> vlastnost `"Hola"`.  
  
     Nový soubor prostředků s názvem Form1.es ES.resx se přidá do projektu.  
  
6.  V Průzkumníku řešení klikněte pravým tlačítkem na **Form1.cs** a klikněte na tlačítko **kód zobrazení** a otevře se v editoru kódu.  
  
7.  Zkopírujte následující kód do `Form1` konstruktoru, předchozích volání `InitializeComponent`.  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  V Průzkumníku řešení klikněte pravým tlačítkem na **LocalizingWpfInWf** a klikněte na tlačítko **uvolnit projekt**.  
  
     Označený název projektu **(není k dispozici)**.  
  
9. Klikněte pravým tlačítkem na **LocalizingWpfInWf**a klikněte na tlačítko **upravit LocalizingWpfInWf.csproj**.  
  
     Soubor projektu se otevře v editoru kódu.  
  
10. Zkopírujte následující řádek do první `PropertyGroup` v souboru projektu.  
  
    ```xml  
    <UICulture>en-US</UICulture>   
    ```  
  
11. Uložte soubor projektu a zavřete ho.  
  
12. V Průzkumníku řešení klikněte pravým tlačítkem na **LocalizingWpfInWf** a klikněte na tlačítko **znovu načíst projekt**.  
  
## <a name="assigning-resource-identifiers"></a>Přiřazení identifikátory prostředků  
 Lokalizovatelný obsah můžete namapovat k sestavení prostředků pomocí identifikátory prostředků. Když zadáte MsBuild.exe aplikace automaticky přiřadí identifikátory prostředků `updateuid` možnost.  
  
#### <a name="to-assign-resource-identifiers"></a>Přiřadit identifikátory prostředků  
  
1.  Z nabídky Start otevřete příkazový řádek sady Visual Studio.  
  
2.  Pomocí následujícího příkazu přiřaďte lokalizovatelný obsah identifikátory prostředků.  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  V Průzkumníku řešení klikněte dvakrát na **SimpleControl.xaml** a otevře se v editoru kódu. Zobrazí se `msbuild` příkaz přidala `Uid` atribut všechny elementy. To usnadňuje lokalizaci pomocí přidělování identifikátorů prostředků.  
  
     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  Stiskněte klávesu F6 sestavte řešení.  
  
## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Pomocí LocBaml k vytvoření satelitní sestavení  
 Lokalizovaný obsah uložený v jen prostředků *satelitní sestavení*. Pomocí nástroje příkazového řádku LocBaml.exe k vytvoření lokalizované sestavení pro vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.  
  
#### <a name="to-produce-a-satellite-assembly"></a>K vytvoření satelitní sestavení  
  
1.  Zkopírujte LocBaml.exe do složky obj\Debug vašeho projektu. Další informace najdete v tématu [lokalizaci aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).  
  
2.  V okně příkazového řádku použijte následující příkaz k extrakci řetězce prostředků do dočasného souboru.  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  Pomocí sady Visual Studio nebo jiném textovém editoru otevřete soubor temp.csv. Nahraďte řetězec `"Hello"` s jeho španělské překlad `"Hola"`.  
  
4.  Uložte soubor temp.csv.  
  
5.  Pomocí následujícího příkazu vygenerujte soubor lokalizovaný prostředek.  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     Soubor LocalizingWpfInWf.g.es ES.resources se vytvoří ve složce obj\Debug.  
  
6.  Použijte následující příkaz k vytvoření lokalizované satelitní sestavení.  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     Soubor LocalizingWpfInWf.resources.dll se vytvoří ve složce obj\Debug.  
  
7.  Zkopírujte soubor LocalizingWpfInWf.resources.dll do složky bin\Debug\es ES projektu. Nahraďte existující soubor.  
  
8.  Spusťte LocalizingWpfInWf.exe, který je umístěný ve složce bin\Debug vašeho projektu. Znovu sestavit aplikaci nebo satelitní sestavení budou přepsány.  
  
     Aplikace obsahuje lokalizované řetězce místo anglické řetězce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Lokalizace aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)  
 [Návod: Lokalizace Windows Forms](http://msdn.microsoft.com/library/9a96220d-a19b-4de0-9f48-01e5d82679e5)  
 [Návrhář WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
