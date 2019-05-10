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
ms.openlocfilehash: 2c53dc315496d40b77e0bf0880c713ce3d3b4241
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614567"
---
# <a name="dialog-boxes-overview"></a>Přehled dialogových oken
Samostatné aplikace mají obvykle hlavní okno, že oba zobrazuje hlavní data nad tím, které aplikace funguje a zpřístupňuje funkci ke zpracování dat prostřednictvím [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mechanismy, jako je panel nabídek, panelů nástrojů a stavové řádky. Aplikace nejsou v netriviálních může také zobrazit další okna provést následující kroky:  
  
- Zobrazoval informace specifické pro uživatele.  
  
- Shromážděte informace od uživatelů.  
  
- Jak zobrazit a shromažďovat informace.  
  
 Tyto typy systému windows jsou označovány jako *dialogových oknech*, a existují dva typy: modální a nemodální.  
  
 A *modální* dialogové okno se zobrazí ve funkci, když funkce potřebovat další data od uživatele. abyste mohli pokračovat. Protože funkce závisí na poli modální dialogové okno pro shromažďování dat, modálních dialogových oken také zabraňuje uživateli aktivaci ostatních oken v aplikaci, zatímco zůstane otevřená. Ve většině případů modální dialogové okno umožňuje uživateli signalizuje, že po jejich dokončení se modální dialogové stisknutím kombinace kláves buď **OK** nebo **zrušit** tlačítko. Stisknutím klávesy **OK** tlačítko označující, že uživatel zadá data a chce, aby se funkce, který má pokračovat ve zpracování s daty. Stisknutím klávesy **zrušit** tlačítko označující, že uživatel chce funkce spuštění úplně zastavit. Otevření, uložení a tisku data jsou uvedeny nejčastěji používané příklady modálních dialogových oken.  
  
 A *nemodální* dialogovém okně na druhé straně nebrání uživatele aktivace ostatní okna, zatímco je otevřen. Například pokud chce uživatel vyhledat výskyty určité slovo v dokumentu, hlavní okno se často otevře dialogové okno pro požádat uživatele, na jaké slovo, které potřebují. Od hledání slovo nezabrání uživatele úpravy dokumentu, ale dialogové okno nemusí být modální. Nemodální dialogové okno obsahuje alespoň **zavřete** tlačítka zavřete dialogové okno a smíte uvést další tlačítka provádět konkrétní funkce, jako například **najít další** tlačítko Najít další aplikace word, který odpovídá kritériím hledání slovo hledání.  
  
 Windows Presentation Foundation (WPF) umožňuje vytvořit několik typů dialogových oknech, včetně okna se zprávou, společná dialogová okna a dialogová okna Vlastní. Toto téma popisuje a [dialogové okno pole ukázka](https://go.microsoft.com/fwlink/?LinkID=159984) obsahuje odpovídající příklady.  

<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>Okna se zprávou  
 A *okno se zprávou* je dialogové okno, které lze použít k zobrazení textové informace a umožňují uživatelům rozhodování využívat tlačítka. Následující obrázek znázorňuje okno se zprávou, která zobrazí textové informace, zeptá na otázku a poskytuje tři tlačítka odpověď na otázku uživatele.  
  
 ![Textový procesor dialogové okno s dotazem, zda chcete uložit změny v dokumentu, než aplikaci zavře.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 K vytvoření okna se zprávou, použijete <xref:System.Windows.MessageBox> třídy. <xref:System.Windows.MessageBox> Umožňuje konfigurovat pole text zprávy, název, ikonu a tlačítek pomocí kódu, jako je následující.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Chcete-li zobrazit okno se zprávou, zavolejte `static` <xref:System.Windows.MessageBox.Show%2A> způsob, jak je ukázáno v následujícím kódu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Pokud kód, který se zobrazí okno se zprávou potřebuje ke zjištění a zpracování rozhodnutí uživatele (stisknutí tlačítka, které), můžete kód kontrolovat výsledek zprávy pole, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Další informace o používání okna se zprávou, naleznete v tématu <xref:System.Windows.MessageBox>, [MessageBox ukázka](https://go.microsoft.com/fwlink/?LinkID=160023), a [dialogové okno pole ukázka](https://go.microsoft.com/fwlink/?LinkID=159984).  
  
 I když <xref:System.Windows.MessageBox> můžou nabízet a jednoduché dialogové okno pole činnost koncových uživatelů, výhodou použití <xref:System.Windows.MessageBox> , který je jediným typem okno, které lze zobrazit pomocí aplikace, které běží v rámci sandboxu zabezpečení částečné důvěryhodnosti (naleznete v tématu [zabezpečení](../security-wpf.md)), jako například [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 Většina dialogová okna zobrazení a shromažďování dat složitější než výsledek okno se zprávou, včetně textu, výběr (zaškrtávací políčka), vzájemně se vylučující výběru (přepínačů) a seznam výběru (pole se seznamem, pole se seznamem, rozevírací seznamy). Pro tyto Windows Presentation Foundation (WPF) poskytuje několik běžných dialogových oknech a vám umožní vytvořit vlastní dialogová okna, i když použití buď je omezené na aplikací spuštěných s úplným vztahem důvěryhodnosti.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Společná dialogová okna  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] implementuje širokou škálu opakovaně použitelné dialogová okna, které jsou společné pro všechny aplikace, včetně dialogová okna pro otevírání souborů, ukládání souborů a tisku. Protože tyto dialogová okna jsou implementovány v operačním systému, je možné sdílet mezi všechny aplikace, které běží na operačním systému, která pomáhá uživatelům konzistence; Když jsou uživatelé obeznámeni s použitím poskytované operačním systémem dialogového okna v jedné aplikaci, nepotřebují další informace o použití tohoto dialogového okna v jiných aplikacích. Protože jsou k dispozici pro všechny aplikace Tato dialogová okna a protože pomáhají poskytovat jednotné uživatelské prostředí, jsou označovány jako *společná dialogová okna*.  
  
 Windows Presentation Foundation (WPF) zapouzdřuje otevřít soubor, soubor uložit a společná dialogová okna tisku a zpřístupňuje je jako spravovaných tříd pro použití v samostatné aplikace. Toto téma nabízí stručný přehled každé.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Dialogové okno otevřít soubor  
 Dialogovém okně Otevřít soubor je znázorněno na následujícím obrázku používá soubor otevírání funkce načíst název souboru k otevření.  
  
 ![Otevřené dialogové okno zobrazuje umístění pro načtení souboru.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 Běžné dialogové okno otevřít soubor je implementovaný jako <xref:Microsoft.Win32.OpenFileDialog> třídy a je umístěn v <xref:Microsoft.Win32> oboru názvů. Následující kód ukazuje, jak vytvářet, konfigurovat a zobrazit jednu a tom, jak zpracovat výsledek.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Další informace o dialogovém okně Otevřít soubor najdete v tématu <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> je možné bezpečně načíst názvy souborů aplikací spuštěných s částečnou důvěryhodností (viz [zabezpečení](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Soubor dialogové okno Uložit  
 Uložení souboru dialogovém okně je znázorněno na následujícím obrázku používá funkci pro uložení souboru načíst název soubor, který chcete uložit.  
  
 ![Uložit jako dialogové okno zobrazuje umístění pro uložení souboru.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Běžné uložit soubor dialogovému oknu je implementovaný jako <xref:Microsoft.Win32.SaveFileDialog> třídy a je umístěn v <xref:Microsoft.Win32> oboru názvů. Následující kód ukazuje, jak vytvářet, konfigurovat a zobrazit jednu a tom, jak zpracovat výsledek.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Další informace o uložení souboru dialogové okno, najdete v článku <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Dialogové okno Tisk  
 Do dialogového okna Tisk pole, je znázorněno na následujícím obrázku, používá funkce tisku vyberte a nakonfigurujte tiskárny, uživatele chcete vytisknout data.  
  
 ![Snímek obrazovky ukazující dialogové okno Tisk.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
 Běžné dialogového okna Tisk pole je implementovaný jako <xref:System.Windows.Controls.PrintDialog> třídy a je umístěn v <xref:System.Windows.Controls> oboru názvů. Následující kód ukazuje, jak vytvářet, konfigurovat a zobrazit jednu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Další informace o dialogovém okně tisku, naleznete v tématu <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Pro podrobnou diskuzi o tisk ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], naleznete v tématu [přehled tisku](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Vlastní dialogová okna  
 Společná dialogová okna jsou užitečné a by měl použít, pokud je to možné, že nepodporují požadavky dialogová okna specifického pro doménu. V těchto případech je potřeba vytvořit vlastní dialogová okna. Jak uvidíme, je dialogové okno s zvláštní chování. <xref:System.Windows.Window> implementuje tyto chování a v důsledku toho použijete <xref:System.Windows.Window> k vytvoření vlastní modální a nemodální dialogová okna.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Vytvoření modálního dialogového okna vlastní  
 Toto téma ukazuje, jak používat <xref:System.Windows.Window> pro vytvoření pole implementace typické modální dialogové okno, pomocí `Margins` dialogové okno s ukázkovým (naleznete v tématu [dialogové okno pole ukázka](https://go.microsoft.com/fwlink/?LinkID=159984)). `Margins` Dialogové okno se zobrazí na následujícím obrázku.  
  
 ![Dialogové okno okraje s pole k definování levý okraj, horní okraj, pravý okraj a dolní okraj.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Konfigurace modální dialogové okno  
 Uživatelské rozhraní pro typické dialogové okno obsahuje následující:  
  
- Různé ovládací prvky, které jsou nutné shromáždit požadovaná data.  
  
- Zobrazení **OK** tlačítko, že uživatelé klikněte na tlačítko pro dialogové okno zavřete, vraťte se na funkci a pokračovat ve zpracování.  
  
- Zobrazení **zrušit** tlačítko, které uživatelé kliknou na dialogové okno zavřít a zastavit funkce z další zpracování.  
  
- Zobrazení **Zavřít** tlačítko v záhlaví programu.  
  
- Zobrazuje ikonu.  
  
- Zobrazuje **minimalizovat**, **Maximalizovat**, a **obnovení** tlačítka.  
  
- Zobrazení **systému** chcete minimalizovat, maximalizovat, obnovení a zavřete dialogové okno, v nabídce.  
  
- Otevřete výše a v centru okna, které se otevřelo dialogové okno.  
  
- Dialogová okna by měl být umožňující změnu velikosti, kde je to možné, zabránit dialogových oken příliš malé a uživateli poskytnout užitečné výchozí velikost, je potřeba nastavit výchozí a minimální dimenzí v uvedeném pořadí.  
  
- Stisknutím klávesy ESC by měl být nakonfigurovaný jako klávesové zkratky, které způsobí, že **zrušit** tlačítka se aktivovala. Toho dosáhnete pomocí nastavení <xref:System.Windows.Controls.Button.IsCancel%2A> vlastnost **zrušit** tlačítko `true`.  
  
- Stisknutím klávesy ENTER (nebo RETURN) by měl být nakonfigurovaný jako klávesové zkratky, které způsobí, že **OK** tlačítka se aktivovala. Toho dosáhnete pomocí nastavení <xref:System.Windows.Controls.Button.IsDefault%2A> vlastnost **OK** tlačítko `true`.  
  
 Následující kód ukazuje tuto konfiguraci.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 Uživatelské prostředí pro dialogové okno se také rozšiřuje na řádku nabídek, které se otevře dialogové okno. Při spuštění funkce, která vyžaduje interakci uživatele prostřednictvím dialogového okna před pokračováním funkci položku nabídky položky nabídky pro funkci bude mít tři tečky v záhlaví, jak je znázorněno zde.  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 Při spuštění funkce, která se zobrazí dialogové okno, které nevyžaduje zásah uživatele, jako je například dialogové okno informací o aplikaci položky nabídky se třemi tečkami nevyžaduje.  
  
#### <a name="opening-a-modal-dialog-box"></a>Otevírání modální dialogové okno  
 Dialogové okno se obvykle zobrazí v důsledku výběru položky nabídky, kterou uživatel k provedení doménově specifické funkce, jako je nastavení okrajů dokumentu v textovém editoru. Zobrazuje jako dialogové okno je podobný zobrazující normálního okna, i když se vyžaduje další dialogové okno konfigurace specifické pro pole. Celý proces vytvoření instance, konfigurace a otevřete dialogové okno se zobrazí v následujícím kódu.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 Tady je kód předávání informací výchozí (aktuální okraje) dialogové okno. Také se nastaví <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> vlastnost s odkazem na okně, které se zobrazuje dialogové okno. Obecně byste měli nastavit vlastníka pro dialogové okno k poskytování okno stavu chování, které jsou společné pro všechny dialogová okna (viz [přehled WPF Windows](wpf-windows-overview.md) Další informace).  
  
> [!NOTE]
>  Musíte zadat vlastníka pro podporu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] automatizace pro dialogová okna (viz [Přehled automatizace uživatelského rozhraní](../../ui-automation/ui-automation-overview.md)).  
  
 Po dokončení konfigurace dialogové okno se modálně zobrazí při volání <xref:System.Windows.Window.ShowDialog%2A> metody.  
  
#### <a name="validating-user-provided-data"></a>Ověřování dat uživatelem zadaný  
 Když se otevře dialogové okno a uživatel zadá požadovaná data, dialogové okno zodpovídá za to, že zadaná data nejsou platná z následujících důvodů:  
  
- Z hlediska zabezpečení by měl být ověřen veškerý vstup.  
  
- Z hlediska specifického pro doménu ověření dat. zabraňuje chybná data zpracovává kód, který může potenciálně vyvolat výjimky.  
  
- Z pohledu uživatelské prostředí dialogové okno můžete uživatelům pomoci tím, že zobrazuje data, která jste zadali, není platný.  
  
- Z hlediska výkonu ověřování dat v vícevrstvou aplikaci můžete snížit počet výměn mezi klientem a aplikačních vrstev, zejména pokud se aplikace skládají z webové služby nebo databáze na serveru.  
  
 K ověření vázaného ovládacího prvku v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], budete muset definovat ověřovací pravidlo a přidružte jej k vazbě. Ověřovací pravidlo představuje vlastní třídu, která je odvozena z <xref:System.Windows.Controls.ValidationRule>. Následující příklad ukazuje ověřovací pravidlo `MarginValidationRule`, která zkontroluje, vázaná hodnota <xref:System.Double> a je v rámci zadaného rozsahu.  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 V tomto kódu je implementovat logiku ověření ověřovací pravidlo tak, že přepíšete <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu, která ověří data a vrátí odpovídající <xref:System.Windows.Controls.ValidationResult>.  
  
 Ověřovací pravidlo přidružit vázaného ovládacího prvku, použijte následující kód.  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 Po přidružení, ověřovací pravidlo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automaticky použije se při zadávání dat do vázaného ovládacího prvku. Když ovládací prvek obsahuje neplatná data [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] červené ohraničení kolem neplatný ovládací prvek se zobrazí, jak je znázorněno na následujícím obrázku.  
  
 ![Dialogové okno okraje červené ohraničení kolem hodnoty Neplatný levý okraj.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] neomezuje uživatele na neplatný ovládací prvek, dokud zadali platná data. Toto je správné chování pro dialogové okno; Uživatel by měl být schopní vyznat volně ovládacích prvků v dialogovém okně, jestli data jsou platná. To ale znamená může uživatel zadat neplatná data a stiskněte klávesu **OK** tlačítko. Z tohoto důvodu je váš kód také potřeba ověřit všechny ovládací prvky v dialogovém okně když **OK** stisknutí tlačítka pomocí manipulace <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 Tento kód vytvoří výčet všech objektů závislost na okno a jestli je některý neplatný (vrácené <xref:System.Windows.Controls.Validation.GetHasError%2A>, neplatný ovládací prvek získá fokus, `IsValid` vrátí metoda `false`, a v okně je považován za neplatný.  
  
 Jakmile dialogového okna je platný, může bezpečně zavřít a vrátit. Jako součást procesu vratky musí vrátit výsledek volání funkce.  
  
#### <a name="setting-the-modal-dialog-result"></a>Nastavení výsledku modální dialogové okno  
 Otevření dialogového okna pole pomocí <xref:System.Windows.Window.ShowDialog%2A> je v podstatě jako volání metody: kód, který otevře dialogové okno pole pomocí <xref:System.Windows.Window.ShowDialog%2A> počká <xref:System.Windows.Window.ShowDialog%2A> vrátí. Když <xref:System.Windows.Window.ShowDialog%2A> vrátí, kód, který volá musí rozhodnout, jestli chcete pokračovat ve zpracování nebo zastaví zpracovávání, podle toho, jestli uživatel stiskl **OK** tlačítko nebo **zrušit** tlačítko. Pro usnadnění tohoto rozhodnutí, musí vracet výběru uživatele jako dialogové okno <xref:System.Boolean> hodnotu, která je vrácena z <xref:System.Windows.Window.ShowDialog%2A> metody.  
  
 Když **OK** po kliknutí na tlačítko, <xref:System.Windows.Window.ShowDialog%2A> by měla vrátit `true`. Toho dosáhnete pomocí nastavení <xref:System.Windows.Window.DialogResult%2A> pole vlastnost dialogového okna, kdy **OK** po kliknutí na tlačítko.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 Poznámka: Toto nastavení <xref:System.Windows.Window.DialogResult%2A> vlastnost zároveň způsobí, že okno zavřete automaticky, ve kterém nebude potřeba explicitně volat <xref:System.Windows.Window.Close%2A>.  
  
 Když **zrušit** po kliknutí na tlačítko, <xref:System.Windows.Window.ShowDialog%2A> by měla vrátit `false`, což také vyžaduje, aby nastavení <xref:System.Windows.Window.DialogResult%2A> vlastnost.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 Když tlačítka <xref:System.Windows.Controls.Button.IsCancel%2A> je nastavena na `true` a uživatel stiskne buď **zrušit** tlačítko nebo klávesy ESC <xref:System.Windows.Window.DialogResult%2A> se automaticky nastaví na `false`. Následující kód má stejný účinek jako předchozí kód, aniž by bylo nutné zpracovat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 Dialogové okno se automaticky vrátí `false` když uživatel stiskne klávesu **Zavřít** tlačítko v záhlaví nebo zvolí **Zavřít** položku nabídky z **systému** nabídky.  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Zpracování dat vrácených z modální dialogové okno  
 Když <xref:System.Windows.Window.DialogResult%2A> nastavená funkce, která se otevře dialogové okno, můžete získat výsledku dialogového okna zkontrolováním <xref:System.Windows.Window.DialogResult%2A> vlastnost při <xref:System.Windows.Window.ShowDialog%2A> vrátí.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 Pokud je výsledek dialogu `true`, funkce, která používá jako hromádka načíst a zpracovat data zadaná uživatelem.  
  
> [!NOTE]
>  Po <xref:System.Windows.Window.ShowDialog%2A> vrátila, nelze znovu otevřít dialogové okno. Místo toho budete muset vytvořit novou instanci.  
  
 Pokud je výsledek dialogu `false`, funkce by měla končit zpracování odpovídajícím způsobem.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Vytvoření nemodálního dialogového okna vlastní  
 Nemodálního dialogového okna, například dialogového okna Najít, které je znázorněno na následujícím obrázku má stejné základní vzhled jako modální dialogové.  
  
 ![Snímek obrazovky ukazující dialogové okno hledání.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  
  
 Chování je však poněkud lišit, a jak je popsáno v následujících částech.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Otevřete dialogové okno nemodální  
 Nemodální dialogové okno se otevře pomocí volání <xref:System.Windows.Window.Show%2A> metody.  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 Na rozdíl od <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> vrátí hodnotu okamžitě. V důsledku toho okna volání nelze zjistit, když nemodální dialogové okno se zavře a proto neví, kdy se mají vyhledávat výsledku dialogového okna nebo získání dat z dialogového okna pro další zpracování. Místo toho dialogové okno je potřeba vytvořit alternativní způsob vrátit data do okna pro zpracování volání.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Zpracování Data vrácená z nemodálního dialogového okna  
 V tomto příkladu `FindDialogBox` může vrátit výsledky do hlavního okna, v závislosti na text vyhledávaná bez všechny konkrétní frekvence hledání jeden nebo více. Stejně jako modální dialogové okno, může vrátit nemodální dialogové okno výsledků za použití vlastností. V okně, který vlastní dialogových oken však musí vědět, kdy se má zjišťovat tyto vlastnosti. Jedním ze způsobů, aby to bylo se pro dialogové okno pro implementaci událost, která je vyvolána pokaždé, když se text nachází. `FindDialogBox` implementuje `TextFoundEvent` pro tento účel, který první vyžaduje delegáta.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 Použití `TextFoundEventHandler` delegovat, `FindDialogBox` implementuje `TextFoundEvent`.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 V důsledku toho `Find` může vyvolat událost, když se nenajde výsledek hledání.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind2)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind3)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind3)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind4)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind4)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind5)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind5)]  
  
 Okno vlastníka pak musí zaregistrovat ve službě a zpracování této události.  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>Zavření nemodální dialogové okno  
 Protože <xref:System.Windows.Window.DialogResult%2A> nemusí být nastaven, nemodální dialogové okno můžete zavřít pomocí systému poskytují mechanismy, které patří:  
  
- Kliknutím **Zavřít** tlačítko v záhlaví programu.  
  
- Stisknutím klávesy ALT + F4.  
  
- Výběr **Zavřít** z **systému** nabídky.  
  
 Alternativně může váš kód volat <xref:System.Windows.Window.Close%2A> při **Zavřít** po kliknutí na tlačítko.  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled prvku Popup](../controls/popup-overview.md)
- [Dialogové okno pole vzorku](https://go.microsoft.com/fwlink/?LinkID=159984)
- [Ukázka ovládacího prvku ColorPicker vlastní](https://go.microsoft.com/fwlink/?LinkID=159977)
