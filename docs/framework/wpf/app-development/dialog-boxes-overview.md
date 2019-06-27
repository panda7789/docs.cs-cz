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
ms.openlocfilehash: 8008feb91a72353a74a647cf79bcecbf7023f962
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410561"
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
### <a name="save-file-dialog-box"></a>dialogové okno Uložení souboru  
 Uložení souboru dialogovém okně je znázorněno na následujícím obrázku používá funkci pro uložení souboru načíst název soubor, který chcete uložit.  
  
 ![Uložit jako dialogové okno zobrazuje umístění pro uložení souboru.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Běžné uložit soubor dialogovému oknu je implementovaný jako <xref:Microsoft.Win32.SaveFileDialog> třídy a je umístěn v <xref:Microsoft.Win32> oboru názvů. Následující kód ukazuje, jak vytvářet, konfigurovat a zobrazit jednu a tom, jak zpracovat výsledek.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Další informace o uložení souboru dialogové okno, najdete v článku <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Tisk – dialogové okno

Do dialogového okna Tisk pole, je znázorněno na následujícím obrázku, používá funkce tisku vyberte a nakonfigurujte tiskárny, uživatele chcete vytisknout data.  
  
![Snímek obrazovky ukazující dialogové okno Tisk.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
Běžné dialogového okna Tisk pole je implementovaný jako <xref:System.Windows.Controls.PrintDialog> třídy a je umístěn v <xref:System.Windows.Controls> oboru názvů. Následující kód ukazuje, jak vytvářet, konfigurovat a zobrazit jednu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Další informace o dialogovém okně tisku, naleznete v tématu <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Podrobnou diskuzi o tisk v subsystému WPF naleznete v tématu [přehled tisku](../advanced/printing-overview.md).  
  
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
  
- **OK** tlačítko, že uživatelé klikněte na tlačítko pro dialogové okno zavřete, vraťte se na funkci a pokračovat ve zpracování.  
  
- A **zrušit** tlačítko, které uživatelé kliknou na dialogové okno zavřít a zastavit funkce z další zpracování.  
  
- A **Zavřít** tlačítko v záhlaví programu.  
  
- Ikona.  
  
- **Minimalizovat**, **Maximalizovat**, a **obnovení** tlačítka.  
  
- A **systému** chcete minimalizovat, maximalizovat, obnovení a zavřete dialogové okno, v nabídce.  
  
- Na pozici výše a to ve střední části okna, které se otevřelo dialogové okno.  
  
- Možnost změnit velikost, kde je to možné, zabránit dialogových oken příliš malé a uživateli poskytnout užitečné výchozí velikost. Tomu je potřeba nastavit výchozí a minimální dimenze.  
  
- Klávesu ESC, jako klávesovou zkratku, která způsobí, že **zrušit** tlačítka se aktivovala. To provedete tak, že nastavíte <xref:System.Windows.Controls.Button.IsCancel%2A> vlastnost **zrušit** tlačítko `true`.  
  
- Klávesu ENTER (nebo RETURN) jako klávesové zkratky, které způsobí, že **OK** tlačítka se aktivovala. To provedete tak, že nastavíte <xref:System.Windows.Controls.Button.IsDefault%2A> vlastnost **OK** tlačítko `true`.  
  
Následující kód ukazuje tuto konfiguraci.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
Uživatelské prostředí pro dialogové okno se také rozšiřuje na řádku nabídek, které se otevře dialogové okno. Při spuštění funkce, která vyžaduje interakci uživatele prostřednictvím dialogového okna před pokračováním funkci položku nabídky položky nabídky pro funkci bude mít tři tečky v záhlaví, jak je znázorněno zde.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Při spuštění funkce, která se zobrazí dialogové okno, které nevyžaduje zásah uživatele, jako je například dialogové okno informací o aplikaci položky nabídky se třemi tečkami nevyžaduje.  
  
#### <a name="opening-a-modal-dialog-box"></a>Otevírání modální dialogové okno

Dialogové okno se obvykle zobrazí v důsledku výběru položky nabídky, kterou uživatel k provedení doménově specifické funkce, jako je nastavení okrajů dokumentu v textovém editoru. Zobrazuje jako dialogové okno je podobný zobrazující normálního okna, i když se vyžaduje další dialogové okno konfigurace specifické pro pole. Celý proces vytvoření instance, konfigurace a otevřete dialogové okno se zobrazí v následujícím kódu.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

Tady kód předá informace výchozí (aktuální okraje) do dialogového okna. Také nastaví <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> vlastnost s odkazem na okně, které se zobrazuje dialogové okno. Obecně byste měli nastavit vlastníka pro dialogové okno k poskytování okno stavu chování, které jsou společné pro všechny dialogová okna (viz [přehled WPF Windows](wpf-windows-overview.md) Další informace).

> [!NOTE]
> Musíte zadat vlastníka pro podporu automatizace uživatelského rozhraní (UI) pro dialogová okna (viz [Přehled automatizace uživatelského rozhraní](../../ui-automation/ui-automation-overview.md)).

Po dokončení konfigurace dialogové okno se modálně zobrazí při volání <xref:System.Windows.Window.ShowDialog%2A> metody.  
  
#### <a name="validating-user-provided-data"></a>Ověřování dat uživatelem zadaný

Když se otevře dialogové okno a uživatel zadá požadovaná data, dialogové okno zodpovídá za to, že zadaná data nejsou platná z následujících důvodů:  
  
- Z hlediska zabezpečení by měl být ověřen veškerý vstup.  
  
- Z hlediska specifického pro doménu ověření dat. zabraňuje chybná data zpracovává kód, který může potenciálně vyvolat výjimky.  
  
- Z pohledu uživatelské prostředí dialogové okno můžete uživatelům pomoci tím, že zobrazuje data, která jste zadali, není platný.  
  
- Z hlediska výkonu ověřování dat v vícevrstvou aplikaci můžete snížit počet výměn mezi klientem a aplikačních vrstev, zejména pokud se aplikace skládají z webové služby nebo databáze na serveru.  

K ověření vázaného ovládacího prvku v objektu WPF, musíte definovat ověřovací pravidlo a přidružte jej k vazbě. Ověřovací pravidlo představuje vlastní třídu, která je odvozena z <xref:System.Windows.Controls.ValidationRule>. Následující příklad ukazuje ověřovací pravidlo `MarginValidationRule`, která zkontroluje, vázaná hodnota <xref:System.Double> a je v rámci zadaného rozsahu.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

V tomto kódu je implementovat logiku ověření ověřovací pravidlo tak, že přepíšete <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu, která ověří data a vrátí odpovídající <xref:System.Windows.Controls.ValidationResult>.  

Ověřovací pravidlo přidružit vázaného ovládacího prvku, použijte následující kód.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Po přidružení ověřovací pravidlo WPF ji automaticky použít při zadávání dat do vázaného ovládacího prvku. Ovládací prvek obsahuje neplatná data, WPF zobrazí červené ohraničení kolem neplatný ovládací prvek, jak je znázorněno na následujícím obrázku.  
  
![Dialogové okno okraje červené ohraničení kolem hodnoty Neplatný levý okraj.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF neomezuje uživatele na neplatný ovládací prvek, dokud zadali platná data. Toto je správné chování pro dialogové okno; Uživatel by měl být schopní vyznat volně ovládacích prvků v dialogovém okně, jestli data jsou platná. To ale znamená může uživatel zadat neplatná data a stiskněte klávesu **OK** tlačítko. Z tohoto důvodu je váš kód také potřeba ověřit všechny ovládací prvky v dialogovém okně když **OK** stisknutí tlačítka pomocí manipulace <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Tento kód vytvoří výčet všech objektů závislost na okno a jestli je některý neplatný (vrácené <xref:System.Windows.Controls.Validation.GetHasError%2A>, neplatný ovládací prvek získá fokus, `IsValid` vrátí metoda `false`, a v okně je považován za neplatný.  
  
Jakmile dialogového okna je platný, může bezpečně zavřít a vrátit. Jako součást procesu vratky musí vrátit výsledek volání funkce.  
  
#### <a name="setting-the-modal-dialog-result"></a>Nastavení výsledku modální dialogové okno

Otevření dialogového okna pole pomocí <xref:System.Windows.Window.ShowDialog%2A> je v podstatě jako volání metody: kód, který otevře dialogové okno pole pomocí <xref:System.Windows.Window.ShowDialog%2A> počká <xref:System.Windows.Window.ShowDialog%2A> vrátí. Když <xref:System.Windows.Window.ShowDialog%2A> vrátí, kód, který volá musí rozhodnout, jestli chcete pokračovat ve zpracování nebo zastaví zpracovávání, podle toho, jestli uživatel stiskl **OK** tlačítko nebo **zrušit** tlačítko. Pro usnadnění tohoto rozhodnutí, musí vracet výběru uživatele jako dialogové okno <xref:System.Boolean> hodnotu, která je vrácena z <xref:System.Windows.Window.ShowDialog%2A> metody.  

Když **OK** po kliknutí na tlačítko, <xref:System.Windows.Window.ShowDialog%2A> by měla vrátit `true`. Toho dosáhnete pomocí nastavení <xref:System.Windows.Window.DialogResult%2A> pole vlastnost dialogového okna, kdy **OK** po kliknutí na tlačítko.  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Poznámka: Toto nastavení <xref:System.Windows.Window.DialogResult%2A> vlastnost zároveň způsobí, že okno zavřete automaticky, ve kterém nebude potřeba explicitně volat <xref:System.Windows.Window.Close%2A>.  
  
Když **zrušit** po kliknutí na tlačítko, <xref:System.Windows.Window.ShowDialog%2A> by měla vrátit `false`, což také vyžaduje, aby nastavení <xref:System.Windows.Window.DialogResult%2A> vlastnost.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Když tlačítka <xref:System.Windows.Controls.Button.IsCancel%2A> je nastavena na `true` a uživatel stiskne buď **zrušit** tlačítko nebo klávesy ESC <xref:System.Windows.Window.DialogResult%2A> se automaticky nastaví na `false`. Následující kód má stejný účinek jako předchozí kód, aniž by bylo nutné zpracovat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Dialogové okno se automaticky vrátí `false` když uživatel stiskne klávesu **Zavřít** tlačítko v záhlaví nebo zvolí **Zavřít** položku nabídky z **systému** nabídky.  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Zpracování dat vrácených z modální dialogové okno  

Když <xref:System.Windows.Window.DialogResult%2A> nastavená funkce, která se otevře dialogové okno, můžete získat výsledku dialogového okna zkontrolováním <xref:System.Windows.Window.DialogResult%2A> vlastnost při <xref:System.Windows.Window.ShowDialog%2A> vrátí.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

Pokud je výsledek dialogu `true`, funkce, která používá jako hromádka načíst a zpracovat data zadaná uživatelem.  
  
> [!NOTE]
> Po <xref:System.Windows.Window.ShowDialog%2A> vrátila, nelze znovu otevřít dialogové okno. Místo toho budete muset vytvořit novou instanci.

Pokud je výsledek dialogu `false`, funkce by měla končit zpracování odpovídajícím způsobem.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Vytvoření nemodálního dialogového okna vlastní

Nemodálního dialogového okna, například dialogového okna Najít, které je znázorněno na následujícím obrázku má stejné základní vzhled jako modální dialogové.  

![Snímek obrazovky ukazující dialogové okno hledání.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Chování je však poněkud lišit, a jak je popsáno v následujících částech.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Otevřete dialogové okno nemodální

Nemodální dialogové okno se otevře pomocí volání <xref:System.Windows.Window.Show%2A> metody.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  
 
[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

Na rozdíl od <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> vrátí hodnotu okamžitě. V důsledku toho okna volání nelze zjistit, když nemodální dialogové okno se zavře a proto neví, kdy se mají vyhledávat výsledku dialogového okna nebo získání dat z dialogového okna pro další zpracování. Místo toho dialogové okno je potřeba vytvořit alternativní způsob vrátit data do okna pro zpracování volání.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Zpracování data vrácená z nemodálního dialogového okna  

V tomto příkladu `FindDialogBox` může vrátit výsledky do hlavního okna, v závislosti na text vyhledávaná bez všechny konkrétní frekvence hledání jeden nebo více. Stejně jako modální dialogové okno, může vrátit nemodální dialogové okno výsledků za použití vlastností. V okně, který vlastní dialogových oken však musí vědět, kdy se má zjišťovat tyto vlastnosti. Jedním ze způsobů, aby to bylo se pro dialogové okno pro implementaci událost, která je vyvolána pokaždé, když se text nachází. `FindDialogBox` implementuje `TextFoundEvent` pro tento účel, který první vyžaduje delegáta.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

Použití `TextFoundEventHandler` delegovat, `FindDialogBox` implementuje `TextFoundEvent`.
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

V důsledku toho `Find` může vyvolat událost, když se nenajde výsledek hledání.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

Okno vlastníka pak musí zaregistrovat ve službě a zpracování této události.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Zavření nemodální dialogové okno

Protože <xref:System.Windows.Window.DialogResult%2A> nemusí být nastaven, nemodální dialogové okno můžete zavřít pomocí systému poskytují mechanismy, které patří:  
  
- Kliknutím **Zavřít** tlačítko v záhlaví programu.  
  
- Stisknutím klávesy ALT + F4.  
  
- Výběr **Zavřít** z **systému** nabídky.  
  
Alternativně může váš kód volat <xref:System.Windows.Window.Close%2A> při **Zavřít** po kliknutí na tlačítko.  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Viz také:

- [Přehled prvku Popup](../controls/popup-overview.md)
- [Dialogové okno pole vzorku](https://go.microsoft.com/fwlink/?LinkID=159984)
