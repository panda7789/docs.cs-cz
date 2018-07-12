---
title: Přehled dialogových oken
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
ms.openlocfilehash: 110e42fea8d5586e471ae36ead46bed304cf9f48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549153"
---
# <a name="dialog-boxes-overview"></a>Přehled dialogových oken
Samostatné aplikace obvykle mají hlavní okno, jak zobrazuje hlavní data, přes které aplikace funguje a zpřístupňuje funkci pro zpracování dat prostřednictvím [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mechanismy jako řádky nabídek, panely nástrojů a stavové řádky. Netriviální aplikace může také zobrazit další okna udělat následující:  
  
-   Má uživatelům zobrazit konkrétní informace.  
  
-   Shromážděte informace od uživatelů.  
  
-   Jak zobrazit a shromažďovat informace.  
  
 Tyto typy systému windows se označují jako *dialogová okna*, a existují dva typy: modální a nemodální.  
  
 A *modální* dialogové okno se zobrazí funkcí, když funkce potřebuje další data od uživatele. Chcete-li pokračovat. Protože funkce závisí na modálních dialogových oken pro shromažďování dat, modálních dialogových oken také zabraňuje uživateli v aktivace jiné systému windows v aplikaci, zatímco zůstane otevřený. Ve většině případů modální dialogové okno umožňuje uživateli signalizován dokončily s modálních dialogových oken stisknutím buď **OK** nebo **zrušit** tlačítko. Kliknutím **OK** tlačítko označuje, že uživatel zadá data a chce, aby se funkce, kterou chcete pokračovat ve zpracování s daty. Stisknutím **zrušit** tlačítko označující, že uživatel chce funkce spuštění úplně zastavit. Otevření, uložení a tisku data se zobrazují nejběžnější příklady modální dialogová okna.  
  
 A *nemodální* dialogové okno, na druhé straně nezabrání uživatele aktivace jiné systému windows je otevřen. Například pokud chce uživatel vyhledat určité slovo v dokumentu, hlavní okno bude často otevřete dialogové okno požádat uživatele, jaké aplikace word, které potřebují. Od hledání slovo není uživateli zabránit v úpravy dokumentu, ale není musí být modální dialogové okno. Dialogové okno nemodální alespoň poskytuje **zavřete** tlačítko zavřete dialogové okno a může poskytnout další tlačítka provést specifické funkce, jako například **najít další** tlačítko Najít další aplikace word, odpovídá kritériím hledání slovo hledání.  
  
 Windows Presentation Foundation (WPF) můžete vytvořit několik typů dialogových oken, včetně okna zpráv, společná dialogová okna a vlastní dialogová okna. Toto téma popisuje a [dialogové okno pole ukázka](http://go.microsoft.com/fwlink/?LinkID=159984) obsahuje odpovídající příklady.  
  
 
  
<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>Okna zpráv  
 A *okno se zprávou* je dialogu, který lze použít k zobrazení textové informace a aby uživatelé mohli rozhodováním o tlačítka. Následující obrázek znázorňuje okno se zprávou, která zobrazí textové informace, požádá otázku a poskytuje tři tlačítka odpověď na otázku uživatele.  
  
 ![Dialogové okno textový editor](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure1.png "DialogBoxesOverviewFigure1")  
  
 Chcete-li vytvořit okno se zprávou, je použít <xref:System.Windows.MessageBox> třídy. <xref:System.Windows.MessageBox> Umožňuje konfigurovat pole text zprávy, název, ikona a tlačítka, pomocí kódu podobně jako tento.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Chcete-li zobrazit okno se zprávou, zavolejte `static` <xref:System.Windows.MessageBox.Show%2A> metoda, jak je ukázáno v následujícím kódu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Když se kód, který se zobrazí okno se zprávou potřebuje ke zjištění a zpracování rozhodnutí uživatele (které tlačítko bylo stisknuto tlačítko), můžete kód prohlédnout pole výsledek zprávy, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Další informace o používání oken zpráv najdete v tématu <xref:System.Windows.MessageBox>, [MessageBox ukázka](http://go.microsoft.com/fwlink/?LinkID=160023), a [dialogové okno pole ukázka](http://go.microsoft.com/fwlink/?LinkID=159984).  
  
 I když <xref:System.Windows.MessageBox> může nabízet jednoduché dialogové okno pole činnost koncového uživatele, výhodou použití <xref:System.Windows.MessageBox> je, který je jediným typem okno, které lze zobrazit aplikace, které jsou spuštěny v izolovaném prostoru zabezpečení částečné důvěryhodnosti (viz [zabezpečení](../../../../docs/framework/wpf/security-wpf.md)), jako například [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 Většina dialogová okna zobrazení a shromažďování dat složitější než výsledek okno se zprávou, včetně textu, výběr (zaškrtávací políčka), vzájemně se vylučuje výběr (přepínače) a seznamu výběru (seznamy, pole se seznamem, rozevírací seznamy). Pro tyto Windows Presentation Foundation (WPF) poskytuje několik běžných dialogových oken a vám umožní vytvořit vlastní dialogových oken, i když použití buď je omezeno na aplikace spuštěné s úplným vztahem důvěryhodnosti.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Společná dialogová okna  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] implementuje celou řadu opakovaně použitelné dialogových oken, které jsou společné pro všechny aplikace, včetně dialogová okna pro otevírání souborů, ukládání souborů a tisku. Vzhledem k tomu, že tyto dialogy jsou implementované v operačním systému, mohou být sdílená mezi všechny aplikace spuštěné na operačním systému, která pomáhá uživatelské prostředí konzistence; Když uživatelé obeznámeni s používáním poskytované operačním systémem dialogového okna v jedné aplikaci, nemusí se dozvíte, jak používat toto okno zobrazené v ostatních aplikacích. Protože tyto dialogy jsou k dispozici pro všechny aplikace, a protože pomáhají zajistit konzistentní prostředí, se označují jako *společná dialogová okna*.  
  
 Windows Presentation Foundation (WPF) zapouzdří otevření souboru, uložit soubor a tisk společná dialogová okna a zpřístupňuje je jako spravované třídy pro použití v samostatné aplikace. Toto téma obsahuje stručný přehled jednotlivých.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Dialogové okno otevření souboru  
 Dialogové okno otevření souboru, vidět na následujícím obrázku se používá pomocí funkce otevírání souboru pro získání názvu souboru k otevření.  
  
 ![Otevřete dialogové okno](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure2.png "DialogBoxesOverviewFigure2")  
  
 Běžné dialogové okno otevření souboru je implementovaný jako <xref:Microsoft.Win32.OpenFileDialog> třídy a nachází se v <xref:Microsoft.Win32> oboru názvů. Následující kód ukazuje, jak vytvářet, konfigurovat a zobrazit jednu a jak zpracovat výsledek.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Další informace o dialogové okno otevření souboru, najdete v části <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> aplikace s částečnou důvěryhodností lze bezpečně načíst názvy souborů (viz [zabezpečení](../../../../docs/framework/wpf/security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Soubor dialogové okno uložení  
 Uložení souboru dialogové okno, znázorňuje následující obrázek, souborem uložení funkce slouží k načtení název souboru pro uložení.  
  
 ![Dialogové okno Uložit jako](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure3.png "DialogBoxesOverviewFigure3")  
  
 Nejběžnější uložit dialogové okno souborů je implementovaný jako <xref:Microsoft.Win32.SaveFileDialog> třídy a nachází se v <xref:Microsoft.Win32> oboru názvů. Následující kód ukazuje, jak vytvářet, konfigurovat a zobrazit jednu a jak zpracovat výsledek.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Další informace o uložení souboru dialogové okno, najdete v části <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Tisk – dialogové okno  
 Tiskové dialogové vidět na následujícím obrázku se používá podle funkce tisku a vyberte a nakonfigurujte tiskárny, uživatele chcete vytisknout data.  
  
 ![Dialogové okno tisku](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure4.png "DialogBoxesOverviewFigure4")  
  
 Běžné tiskové dialogové okno je implementovaný jako <xref:System.Windows.Controls.PrintDialog> třídy a nachází se v <xref:System.Windows.Controls> oboru názvů. Následující kód ukazuje, jak vytvářet, konfigurovat a zobrazit jednu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Další informace v dialogovém okně tisku najdete v tématu <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Pro podrobnou diskuzi o tisk v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], najdete v části [přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Vlastní dialogová okna  
 Společná dialogová okna jsou užitečné i a by měl použít, pokud je to možné, které nepodporují požadavky specifické pro doménu dialogových oken. V takových případech musíte vytvořit vlastní dialogová okna. Ukážeme, je dialogové okno s zvláštní chování. <xref:System.Windows.Window> implementuje tyto chování a v důsledku toho používáte <xref:System.Windows.Window> vytvořit vlastní modální a nemodální dialogová okna.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Vytváření modálních dialogových vlastní pole  
 Toto téma ukazuje, jak používat <xref:System.Windows.Window> pro vytvoření implementace pole typické modální dialogové okno, pomocí `Margins` dialogové okno jako příklad (najdete v části [dialogové okno pole ukázka](http://go.microsoft.com/fwlink/?LinkID=159984)). `Margins` Dialogové okno je znázorněno na následujícím obrázku.  
  
 ![Dialogové okno okraje](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure5.png "DialogBoxesOverviewFigure5")  
  
#### <a name="configuring-a-modal-dialog-box"></a>Konfigurace modální dialogové okno  
 Uživatelské rozhraní pro typické dialogové okno zahrnuje následující:  
  
-   Různé ovládacích prvků, které jsou potřeba shromáždit k požadovaným datům.  
  
-   Zobrazuje **OK** tlačítko uživatele klikněte na tlačítko Zavřít dialogové okno, vraťte se na funkce a pokračovat ve zpracování.  
  
-   Zobrazení **zrušit** tlačítko, které uživatelé kliknou na dialogové okno zavřít a zastavit funkce z další zpracování.  
  
-   Zobrazení **Zavřít** tlačítko v záhlaví.  
  
-   Zobrazuje ikonu.  
  
-   Zobrazuje **minimalizaci**, **Maximalizovat**, a **obnovení** tlačítka.  
  
-   Zobrazení **systému** chcete minimalizovat, maximalizovat, obnovit a zavřít dialogové okno, v nabídce.  
  
-   Otevírání výše a ve středu okno otevřít dialogové okno.  
  
-   Dialogová okna by měl být umožňující změnu velikosti, kde je to možné, tak, aby dialogovém okně nebylo příliš malá a uživateli poskytnout užitečné výchozí velikost, musíte nastavit výchozí a minimální dimenzí v uvedeném pořadí.  
  
-   Stisknutím klávesy ESC by měl být nakonfigurovaný jako klávesové zkratky, které způsobí, že **zrušit** stisknout tlačítko. Toho dosáhnete pomocí nastavení <xref:System.Windows.Controls.Button.IsCancel%2A> vlastnost **zrušit** tlačítko pro `true`.  
  
-   Stisknutím klávesy ENTER (nebo RETURN) by měl být nakonfigurovaný jako klávesové zkratky, které způsobí, že **OK** stisknout tlačítko. Toho dosáhnete pomocí nastavení <xref:System.Windows.Controls.Button.IsDefault%2A> vlastnost **OK** tlačítko `true`.  
  
 Následující kód ukazuje, tato konfigurace.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 Činnost koncového uživatele pro dialogové okno taky ji rozšiřuje na panelu nabídek okna, které se otevře dialogové okno. Funkci, která vyžaduje interakci uživatele pomocí dialogového okna, před pokračováním funkce spuštění položku nabídky položku nabídky pro funkci bude mít tři tečky v hlavičce, jak je vidět tady.  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 Když položku nabídky spustí funkci, která se zobrazí dialogové okno, které nevyžaduje zásah uživatele, například dialogové okno informací o aplikaci se třemi tečkami nevyžaduje.  
  
#### <a name="opening-a-modal-dialog-box"></a>Otevírání modální dialogové okno  
 Dialogové okno se zobrazí obvykle v důsledku výběru položky nabídky uživatelem provádět funkce specifické pro doménu, například nastavení okrajů dokumentu v textovém editoru. Zobrazuje jako dialogové okno je podobná zobrazující okno normální, ale vyžaduje další dialogové okno konfigurace specifické pro pole. Celý proces vytváření instancí, konfigurace a otevřete dialogové okno se zobrazí v následujícím kódu.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 Zde je kód předání informací výchozí (aktuální okraje) dialogové okno. Také se nastaví <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> vlastnost s odkazem na okně, které se zobrazuje dialogové okno. Obecně platí, musí být vždy nastavená vlastníka pro dialogové okno zajistit stavu související chování okno, které jsou společné pro všechny dialogových oken (viz [WPF ve Windows – přehled](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md) Další informace).  
  
> [!NOTE]
>  Je nutné zadat vlastníka pro podporu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] automatizace pro dialogová okna (viz [Přehled automatizace uživatelského rozhraní](../../../../docs/framework/ui-automation/ui-automation-overview.md)).  
  
 Po dokončení konfigurace dialogové okno se modálně zobrazí při volání <xref:System.Windows.Window.ShowDialog%2A> metoda.  
  
#### <a name="validating-user-provided-data"></a>Ověřování dat zadaný uživatelem  
 Když se otevře dialogové okno a uživatel nezadá požadovaná data, dialogové okno se zajistí, že zadaná data jsou platná z následujících důvodů:  
  
-   Z hlediska zabezpečení by měl být ověřen veškerý vstup.  
  
-   Z hlediska specifické pro doménu ověření dat zpracovávaných kód, který může potenciálně generování výjimek nebude chybná data.  
  
-   Z hlediska uživatelské prostředí, dialogové okno můžete pomáhají uživatelům tím, že zobrazuje, která data vstupu je neplatný.  
  
-   Z hlediska výkonu ověření dat ve vícevrstvé aplikace můžete snížit počet přenosů mezi klientem a aplikačními vrstvami, zejména v případě, že aplikace se skládá z webových služeb nebo na serveru databáze.  
  
 K ověření připojeného ovládacího prvku v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], je nutné definovat ověřovací pravidlo a přidružte ji k vazby. Pravidla ověřování je vlastní třídu, která je odvozena z <xref:System.Windows.Controls.ValidationRule>. Následující příklad ukazuje ověřovací pravidlo `MarginValidationRule`, které kontroly, které je vázaná hodnota <xref:System.Double> a je v zadaném rozsahu.  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 V tomto kódu logiku ověření pravidla ověřování implementované přepsání <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu, která ověří data a vrátí odpovídající <xref:System.Windows.Controls.ValidationResult>.  
  
 Chcete-li přidružit ověřovacího pravidla připojeného ovládacího prvku, použijte následující kód.  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 Jakmile ověřovací pravidlo souvisí, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automaticky použije je při zadávání dat do připojeného ovládacího prvku. Pokud ovládací prvek obsahuje neplatná data [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zobrazí červené ohraničení kolem neplatný ovládací prvek, jak je znázorněno na následujícím obrázku.  
  
 ![Neplatný levým okrajem](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure7.png "DialogBoxesOverviewFigure7")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] neomezuje uživatele na neplatný ovládací prvek, dokud zadali platná data. Toto je dobré chování pro dialogové okno; Uživatel by mohli volně přejděte ovládacích prvků v dialogovém okně, zda data jsou platná. To znamená však může uživatel zadat neplatná data a stiskněte klávesu **OK** tlačítko. Z tohoto důvodu kódu také je nutné ověřit všechny ovládací prvky v dialogu když **OK** stisknutí tlačítka ve zpracování <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 Tento kód zobrazí všechny objekty závislost na okno a, pokud jsou některé neplatné (jak ho vrátila <xref:System.Windows.Controls.Validation.GetHasError%2A>, neplatný ovládací prvek získá fokus, `IsValid` metoda vrátí `false`, a okna považovány za neplatné.  
  
 Jakmile dialogové okno je platné, může bezpečně zavřít a vrátit. Jako součást procesu vratky musí vrátit výsledek volání funkce.  
  
#### <a name="setting-the-modal-dialog-result"></a>Výsledek modální dialogové okno nastavení  
 Otevřete dialogové okno pole pomocí <xref:System.Windows.Window.ShowDialog%2A> je zásadně jako volání metody: kód, který otevřít dialogové okno pole pomocí <xref:System.Windows.Window.ShowDialog%2A> čeká, až <xref:System.Windows.Window.ShowDialog%2A> vrátí. Když <xref:System.Windows.Window.ShowDialog%2A> vrátí, kód, který vyžaduje volán rozhodnout, jestli chcete pokračovat ve zpracování nebo zastavit zpracování, podle toho, zda uživatel stisknutí **OK** tlačítko nebo **zrušit** tlačítko. Pro usnadnění tohoto rozhodnutí, musí vrátit volby uživatele jako dialogové okno <xref:System.Boolean> hodnotu, která je vrácena z <xref:System.Windows.Window.ShowDialog%2A> metoda.  
  
 Když **OK** po kliknutí na tlačítko <xref:System.Windows.Window.ShowDialog%2A> by měla vrátit `true`. Toho dosáhnete pomocí nastavení <xref:System.Windows.Window.DialogResult%2A> vlastnost dialogového okna zadejte, kdy **OK** po kliknutí na tlačítko.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 Poznámka: Toto nastavení <xref:System.Windows.Window.DialogResult%2A> vlastnost také způsobí, že okno zavřete automaticky, ve kterém není nutné explicitně volání <xref:System.Windows.Window.Close%2A>.  
  
 Když **zrušit** po kliknutí na tlačítko <xref:System.Windows.Window.ShowDialog%2A> by měla vrátit `false`, což také vyžaduje nastavení <xref:System.Windows.Window.DialogResult%2A> vlastnost.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 Když na tlačítko <xref:System.Windows.Controls.Button.IsCancel%2A> je nastavena na `true` a uživatel stiskne buď **zrušit** tlačítko nebo klávesy ESC <xref:System.Windows.Window.DialogResult%2A> se automaticky nastaví na `false`. Následující kód je výsledek stejný jako předchozí kód, aniž by bylo nutné zpracování <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 Dialogové okno automaticky vrátí `false` při stisknutí **Zavřít** tlačítko v záhlaví nebo zvolí **Zavřít** položky nabídky z **systému** nabídky.  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Zpracování dat vrácených modální dialogové okno  
 Když <xref:System.Windows.Window.DialogResult%2A> nastavena funkce, která ho otevřít dialogové okno, můžete získat výsledek dialogu pole zkontrolováním <xref:System.Windows.Window.DialogResult%2A> vlastnost při <xref:System.Windows.Window.ShowDialog%2A> vrátí.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 Pokud je výsledek dialogu `true`, funkce, používá jako cue k načtení a zpracování dat zadané uživatelem.  
  
> [!NOTE]
>  Po <xref:System.Windows.Window.ShowDialog%2A> vrátilo nelze znovu otevřít dialogové okno. Místo toho musíte vytvořit novou instanci.  
  
 Pokud je výsledek dialogu `false`, funkce, měli byste ukončit zpracování správně.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Vytvoření nemodálního dialogové okno Vlastní  
 Nemodální dialogového okna, například dialogové okno Najít vidět na následujícím obrázku má stejné základní vzhled jako modálních dialogových oken.  
  
 ![Dialogové okno vyhledávání](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure6.PNG "DialogBoxesOverviewFigure6")  
  
 Chování je však mírně liší, jak je popsáno v následujících částech.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Otevření dialogového okna bez režimu  
 Otevření dialogového okna bez režimu voláním <xref:System.Windows.Window.Show%2A> metoda.  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 Na rozdíl od <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> vrátí okamžitě. Okno volání v důsledku toho nelze zjistit, když nemodálního dialogu se zavře a proto nebude vědět, kdy se mají kontrolovat výsledku dialogové okno pole nebo získat data z dialogového okna pro další zpracování. Místo toho musí dialogové okno vytvořit alternativní způsob vrátit data do okna volání pro zpracování.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Zpracování Data vrácená z nemodálního dialogové okno  
 V tomto příkladu `FindDialogBox` může vrátit jednu nebo více Najít výsledky do hlavního okna, v závislosti na text se hledají bez žádné konkrétní frekvence. Jak se modální dialogové okno, může vrátit nemodální dialogové okno výsledků pomocí vlastnosti. Okně, které vlastní dialogové okno však musí vědět, kdy mají být vyhledávána tyto vlastnosti. Je možné povolit pro dialogové okno pro implementaci událost, která se vyvolá, vždy, když je nalezen text. `FindDialogBox` implementuje `TextFoundEvent` pro tento účel, který první vyžaduje delegáta.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 Pomocí `TextFoundEventHandler` delegovat, `FindDialogBox` implementuje `TextFoundEvent`.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 V důsledku toho `Find` může vyvolat událost, když se najde výsledku hledání.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind2)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind3)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind3)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind4)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind4)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind5)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind5)]  
  
 Nadřazené okno pak musí zaregistrovat a zpracování této události.  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>Zavření dialogového okna bez režimu  
 Protože <xref:System.Windows.Window.DialogResult%2A> nemusí být nastavené, nemodálního okna je možné uzavřít pomocí systému poskytují mechanismy, včetně následujících:  
  
-   Kliknutím **Zavřít** tlačítko v záhlaví.  
  
-   Stisknutím ALT + F4.  
  
-   Výběr **Zavřít** z **systému** nabídky.  
  
 Alternativně můžete volat kódu <xref:System.Windows.Window.Close%2A> při **Zavřít** po kliknutí na tlačítko.  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled prvku Popup](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Dialogové okno pole ukázka](http://go.microsoft.com/fwlink/?LinkID=159984)  
 [Ukázka ColorPicker vlastního ovládacího prvku](http://go.microsoft.com/fwlink/?LinkID=159977)
