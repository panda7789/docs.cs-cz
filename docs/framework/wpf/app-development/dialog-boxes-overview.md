---
title: Přehled dialogových oken
description: Přečtěte si o různých dialogových oknech v prezentaci Windows Foundation (WPF), kterou můžete použít ke shromáždění a zobrazení informací.
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
ms.openlocfilehash: 822604dd694f2f6260496872fd7a1a8440a62535
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618139"
---
# <a name="dialog-boxes-overview"></a>Přehled dialogových oken
Samostatné aplikace mají obvykle hlavní okno, které zobrazuje hlavní data, přes které aplikace funguje, a zpřístupňuje funkce pro zpracování těchto dat prostřednictvím [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mechanismů, jako jsou panely nabídek, panely nástrojů a stavové řádky. Netriviální aplikace může také zobrazit další okna, aby bylo možné provést následující akce:  
  
- Zobrazí uživatelům konkrétní informace.  
  
- Shromažďování informací od uživatelů.  
  
- Zobrazují a shromažďují informace.  
  
 Tyto typy oken jsou známé jako dialogová *okna*a existují dva typy: modální a nemodální.  
  
 *Modální* dialogové okno se zobrazí v případě, že funkce potřebuje další data od uživatele, aby bylo možné pokračovat. Vzhledem k tomu, že funkce závisí na modálním dialogovém okně pro shromažďování dat, modální dialogové okno také brání uživateli v aktivaci jiných oken v aplikaci, když zůstane otevřený. Ve většině případů modální dialogové okno umožňuje uživateli signalizovat, že se dokončí pomocí modálního dialogového okna stisknutím tlačítka **OK** nebo **Storno** . Stisknutí tlačítka **OK** indikuje, že uživatel zadal data a přeje, aby funkce pokračovala v zpracování s těmito daty. Stisknutí tlačítka **Storno** indikuje, že uživatel chce zastavit funkci, aby se ukončila úplně. K otevření, uložení a tisku dat se zobrazují nejběžnější příklady modálních dialogových oken.  
  
 *Nemodální* dialogové okno na druhé straně nebrání uživateli v aktivaci jiných oken, když je otevřený. Pokud třeba uživatel chce najít výskyty konkrétního slova v dokumentu, hlavní okno často otevře dialogové okno s dotazem, kde se uživatel bude hledat. Vzhledem k tomu, že hledání slova nebrání uživateli v úpravách dokumentu, dialogové okno ale nemusí být modální. Nemodální dialogové okno má alespoň k dispozici tlačítko **Zavřít** pro zavření dialogového okna a může poskytnout další tlačítka pro spuštění určitých funkcí, jako je například tlačítko **Najít další** , které najde další slovo, které odpovídá kritériím hledání slov.  
  
 Windows Presentation Foundation (WPF) umožňuje vytvořit několik typů dialogových oken, včetně polí se zprávami, společných dialogových oken a vlastních dialogových oken. V tomto tématu jsou popsány jednotlivé a [dialogová okna ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) nabízí srovnávací příklady.  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a>Okna se zprávou  
 Okno se *zprávou* je dialogové okno, které se dá použít k zobrazení textových informací a k tomu, aby uživatelé mohli dělat rozhodnutí pomocí tlačítek. Následující obrázek ukazuje okno se zprávou, které zobrazuje textové informace, požádá o otázku a poskytne uživateli tři tlačítka k zodpovězení otázky.  
  
 ![Dialogové okno textový procesor s dotazem, zda chcete uložit změny do dokumentu před zavřením aplikace.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 Chcete-li vytvořit okno se zprávou, použijte <xref:System.Windows.MessageBox> třídu. <xref:System.Windows.MessageBox>umožňuje konfigurovat text, název, ikonu a tlačítka okna zprávy pomocí kódu podobného následujícímu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Chcete-li zobrazit okno se zprávou, zavolejte `static` <xref:System.Windows.MessageBox.Show%2A> metodu, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Pokud kód, který zobrazuje okno se zprávou potřebuje zjistit a zpracovat rozhodnutí uživatele (které tlačítko bylo stisknuto), může kód zkontrolovat výsledek pole zprávy, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Další informace o použití polí se zprávami naleznete v tématech <xref:System.Windows.MessageBox> , [Ukázka MessageBox](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)a [Ukázka dialogového okna](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox).  
  
 I když se <xref:System.Windows.MessageBox> může nabízet jednoduché uživatelské prostředí dialogového okna, výhoda použití <xref:System.Windows.MessageBox> je jediným typem okna, které mohou být zobrazeny aplikacemi, které běží v izolovaném prostoru zabezpečení s částečnou důvěryhodností (viz [zabezpečení](../security-wpf.md)), jako jsou například aplikace prohlížeče XAML (XBAP).  
  
 Většina dialogových oken zobrazuje a shromažďuje složitější data, než je výsledek okna se zprávou, včetně textu, výběru (zaškrtávací políčka), vzájemně se vylučujícího výběru (přepínačů) a výběru seznamu (seznamy, pole se seznamem, rozevírací seznamy). Pro tyto Windows Presentation Foundation (WPF) poskytuje několik běžných dialogových oken a umožňuje vytvářet vlastní dialogová okna, i když je použití buď omezené na aplikace spuštěné s úplným vztahem důvěryhodnosti.  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a>Společná dialogová okna  
 Systém Windows implementuje celou řadu opakovaně použitelných dialogových oken, která jsou společná pro všechny aplikace, včetně dialogových oken pro otevírání souborů, ukládání souborů a tisku. Vzhledem k tomu, že jsou tato dialogová okna implementovaná operačním systémem, můžou se sdílet mezi všemi aplikacemi, které běží na operačním systému, což pomáhá s konzistencí uživatelů. Když jsou uživatelé obeznámeni s používáním dialogového okna v jedné aplikaci, které poskytuje operační systém, nepotřebují se učit, jak používat toto dialogové okno v jiných aplikacích. Vzhledem k tomu, že jsou tato dialogová okna k dispozici pro všechny aplikace a protože umožňují zajistit konzistentní uživatelské prostředí, jsou označována jako *společná dialogová okna*.  
  
 Windows Presentation Foundation (WPF) zapouzdřuje otevřené dialogová okna soubor, uložit soubor a vytiskne společné a zpřístupňuje je jako spravované třídy, které můžete použít v samostatných aplikacích. V tomto tématu najdete stručný přehled jednotlivých.  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a>Dialogové okno otevřít soubor  
 Dialogové okno otevřít soubor zobrazené na následujícím obrázku je používáno funkcemi otevírání souborů k načtení názvu souboru, který chcete otevřít.  
  
 ![Otevřené dialogové okno zobrazující umístění pro načtení souboru.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 Dialogové okno společný otevřený soubor je implementováno jako <xref:Microsoft.Win32.OpenFileDialog> Třída a je umístěn v <xref:Microsoft.Win32> oboru názvů. Následující kód ukazuje, jak vytvořit, nakonfigurovat a zobrazit jeden a jak zpracovat výsledek.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Další informace o dialogovém okně otevřít soubor naleznete v tématu <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType> .  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog>dá se použít k bezpečnému načítání názvů souborů aplikací spuštěných s částečnou důvěryhodností (viz [zabezpečení](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a>dialogové okno Uložení souboru  
 Dialogové okno Uložit soubor zobrazené na následujícím obrázku je používáno funkcemi pro ukládání souborů k načtení názvu souboru, který chcete uložit.  
  
 ![Dialogové okno Uložit jako, kde se nachází umístění pro uložení souboru.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Dialogové okno běžný soubor pro uložení je implementováno jako <xref:Microsoft.Win32.SaveFileDialog> Třída a je umístěn v <xref:Microsoft.Win32> oboru názvů. Následující kód ukazuje, jak vytvořit, nakonfigurovat a zobrazit jeden a jak zpracovat výsledek.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Další informace o dialogovém okně Uložit soubor naleznete v tématu <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType> .  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a>Tisk – dialogové okno

Dialogové okno Tisk, které je znázorněno na následujícím obrázku, je používáno funkcemi tisku a umožňuje vybrat a nakonfigurovat tiskárnu, do které bude uživatel chtít tisknout data.  
  
![Snímek obrazovky, který zobrazuje dialogové okno Tisk.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
Dialogové okno běžný tisk je implementováno jako <xref:System.Windows.Controls.PrintDialog> Třída a je umístěn v <xref:System.Windows.Controls> oboru názvů. Následující kód ukazuje, jak vytvořit, nakonfigurovat a zobrazit jeden.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Další informace o dialogovém okně Tisk naleznete v tématu <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> . Podrobné informace o tisku v subsystému WPF najdete v tématu [Přehled tisku](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a>Vlastní dialogová okna

I když jsou běžná dialogová okna užitečná a měla by být použita, pokud je to možné, nepodporují požadavky dialogových oken specifických pro doménu. V těchto případech je potřeba vytvořit vlastní dialogová okna. Jak vidíte, zobrazí se dialogové okno se speciálním chováním. <xref:System.Windows.Window>implementuje tato chování a v důsledku toho můžete použít <xref:System.Windows.Window> k vytvoření vlastní modální a nemodální dialogová okna.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a>Vytvoření modálního vlastního dialogového okna

V tomto tématu se dozvíte <xref:System.Windows.Window> , jak použít k vytvoření typické implementace modálního dialogového okna, pomocí `Margins` dialogového okna jako příklad (viz [Ukázka dialogového okna](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)). `Margins`Dialogové okno je zobrazeno na následujícím obrázku.  
  
 ![Dialogové okno okraje s poli pro definování levého okraje, horního okraje, pravého okraje a dolního okraje.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Konfigurace modálního dialogového okna

Uživatelské rozhraní typického dialogového okna zahrnuje následující:  
  
- Různé ovládací prvky, které jsou požadovány pro shromáždění požadovaných dat.  
  
- Tlačítko **OK** , které uživatel klikne k zavření dialogového okna, vrátí se do funkce a pokračuje ve zpracování.  
  
- Tlačítko **Zrušit** , které uživatel klikne k zavření dialogového okna a zastavení funkce z dalšího zpracování.  
  
- Tlačítko **Zavřít** v záhlaví  
  
- Ikona.  
  
- Tlačítka **minimalizovat**, **maximalizovat**a **obnovit** .  
  
- **Systémová** nabídka pro minimalizaci, maximalizaci, obnovení a zavření dialogového okna.  
  
- Pozice nad a uprostřed okna, které otevřelo dialogové okno.  
  
- Možnost měnit velikost, pokud je to možné, aby se dialogové okno nezobrazovalo příliš malé a aby uživateli poskytoval užitečnou výchozí velikost. To vyžaduje, abyste nastavili výchozí a minimální rozměry.  
  
- Klávesa ESC jako klávesová zkratka, která způsobí stisknutí tlačítka **Storno** . To provedete nastavením <xref:System.Windows.Controls.Button.IsCancel%2A> Vlastnosti tlačítka **Storno** na `true` .  
  
- Klávesa ENTER (nebo RETURN) jako klávesová zkratka, která způsobí stisknutí tlačítka **OK** . Provedete to tak, že nastavíte <xref:System.Windows.Controls.Button.IsDefault%2A> vlastnost tlačítka **OK** `true` .  
  
Následující kód demonstruje tuto konfiguraci.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
Uživatelské prostředí pro dialogové okno se také rozšiřuje do řádku nabídek okna, které otevře dialogové okno. Když položka nabídky spustí funkci, která vyžaduje zásah uživatele prostřednictvím dialogového okna před pokračováním funkce, bude mít položka nabídky pro funkci tři tečky ve své hlavičce, jak je znázorněno zde.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Když položka nabídky spustí funkci, která zobrazí dialogové okno, které nevyžaduje zásah uživatele, jako je například dialogové okno o produktu, nepožaduje se tři tečky.  
  
#### <a name="opening-a-modal-dialog-box"></a>Otevření modálního dialogového okna

Dialogové okno se obvykle zobrazuje v důsledku toho, že uživatel vybere položku nabídky k provedení funkce specifické pro doménu, jako je například nastavení okrajů dokumentu ve wordovém procesoru. Zobrazení okna jako dialogového okna se podobá zobrazení normálního okna, přestože vyžaduje další konfiguraci specifickou pro dialogové okno. Celý proces vytvoření instance, konfigurace a otevření dialogového okna je zobrazen v následujícím kódu.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

V tomto příkladu kód předá do dialogového okna výchozí informace (aktuální okraje). Také nastaví <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> vlastnost s odkazem na okno, které zobrazuje dialogové okno. Obecně platí, že byste měli vždy nastavit vlastníka dialogového okna tak, aby poskytovala chování související se stavem okna, která jsou společná pro všechna dialogová okna (Další informace najdete v tématu [Přehled Windows WPF](wpf-windows-overview.md) ).

> [!NOTE]
> Aby bylo možné podporovat automatizaci uživatelského rozhraní (UI) pro dialogová okna (viz [Přehled automatizace uživatelského](../../ui-automation/ui-automation-overview.md)rozhraní), musíte zadat vlastníka.

Po nakonfigurování dialogového okna se zobrazí modální voláním <xref:System.Windows.Window.ShowDialog%2A> metody.  
  
#### <a name="validating-user-provided-data"></a>Ověřování dat poskytnutých uživatelem

Když se otevře dialogové okno a uživatel poskytne požadovaná data, zodpovídá za to, že zadaná data budou platná z následujících důvodů:  
  
- Z hlediska zabezpečení je nutné ověřit veškerý vstup.  
  
- V perspektivě specifické pro doménu zabraňuje ověřování dat zpracováním chybných dat pomocí kódu, což by mohlo potenciálně vyvolat výjimky.  
  
- V perspektivě uživatelského prostředí může dialogové okno uživatelům pomáhat zobrazit, která data zadaná jsou neplatná.  
  
- Z hlediska výkonu může ověřování dat v vícevrstvé aplikaci snížit počet přenosů mezi klientem a aplikačními vrstvami, zejména pokud se aplikace skládá z webových služeb nebo databází založených na serveru.  

Chcete-li ověřit vázaný ovládací prvek v subsystému WPF, je nutné definovat ověřovací pravidlo a přidružit ho k vazbě. Ověřovací pravidlo je vlastní třída, která je odvozena z <xref:System.Windows.Controls.ValidationRule> . Následující příklad ukazuje ověřovací pravidlo, `MarginValidationRule` které kontroluje, zda je hodnota vazby <xref:System.Double> a v rámci zadaného rozsahu.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

V tomto kódu je logika ověření ověřovacího pravidla implementována přepsáním <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody, která ověří data a vrátí vhodnou <xref:System.Windows.Controls.ValidationResult> .  

Chcete-li přidružit ověřovací pravidlo k ovládacímu prvku s vazbou, použijte následující kód.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Jakmile je pravidlo ověření přidružené, WPF ho automaticky použije při zadání dat do vázaného ovládacího prvku. Když ovládací prvek obsahuje neplatná data, WPF zobrazí červené ohraničení kolem neplatného ovládacího prvku, jak je znázorněno na následujícím obrázku.  
  
![Dialogové okno okraje s červeným ohraničením kolem neplatné hodnoty levého okraje](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF neomezuje uživatele na neplatný ovládací prvek, dokud nezadá platná data. Toto chování je dobré pro dialogové okno. uživatel by měl mít možnost volně procházet ovládací prvky v dialogovém okně bez ohledu na to, jestli jsou data platná. To však znamená, že uživatel může zadat neplatná data a stisknout tlačítko **OK** . Z tohoto důvodu musí váš kód také ověřit všechny ovládací prvky v dialogovém okně při stisknutí tlačítka **OK** pomocí zpracování <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Tento kód vytvoří výčet všech objektů závislosti v okně a, pokud jsou nějaké neplatné (vrátí se do něj <xref:System.Windows.Controls.Validation.GetHasError%2A> neplatný ovládací prvek, který vrátí fokus, `IsValid` Metoda vrátí `false` a okno se považuje za neplatné.  
  
Jakmile je dialogové okno platné, může být bezpečně ukončeno a vráceno. V rámci procesu vrácení musí být výsledek vrácen voláním funkce.  
  
#### <a name="setting-the-modal-dialog-result"></a>Nastavení výsledku modálního dialogového okna

Otevření dialogového okna pomocí <xref:System.Windows.Window.ShowDialog%2A> je zásadní jako volání metody: kód, který otevřel dialogové okno pomocí <xref:System.Windows.Window.ShowDialog%2A> čeká na <xref:System.Windows.Window.ShowDialog%2A> vrácení. Když se <xref:System.Windows.Window.ShowDialog%2A> vrátí, kód, který se nazývá, musí rozhodnout, jestli se má pokračovat ve zpracování nebo zastavení zpracování, na základě toho, jestli uživatel stiskne tlačítko **OK** nebo tlačítko **Storno** . Aby bylo toto rozhodnutí snazší, dialogové okno musí vrátit volbu uživatele jako <xref:System.Boolean> hodnotu, která je vrácena z <xref:System.Windows.Window.ShowDialog%2A> metody.  

Po kliknutí na tlačítko **OK** by se <xref:System.Windows.Window.ShowDialog%2A> měla vrátit `true` . Toho dosáhnete nastavením <xref:System.Windows.Window.DialogResult%2A> Vlastnosti dialogového okna při kliknutí na tlačítko **OK** .  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Všimněte si, že nastavení <xref:System.Windows.Window.DialogResult%2A> vlastnosti také způsobí, že se okno automaticky zavře, což řeší nutnost explicitního volání <xref:System.Windows.Window.Close%2A> .  
  
Při kliknutí na tlačítko **Storno** by se <xref:System.Windows.Window.ShowDialog%2A> měla vrátit `false` , což také vyžaduje nastavení <xref:System.Windows.Window.DialogResult%2A> Vlastnosti.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Je-li <xref:System.Windows.Controls.Button.IsCancel%2A> vlastnost tlačítka nastavena na hodnotu `true` a uživatel stiskne tlačítko **Storno** nebo klávesu ESC, <xref:System.Windows.Window.DialogResult%2A> je automaticky nastaven na hodnotu `false` . Následující značka má stejný účinek jako předchozí kód, aniž by bylo nutné <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost zpracovat.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Dialogové okno se automaticky vrátí `false` , když uživatel stiskne tlačítko **Zavřít** v záhlaví nebo klikne na položku nabídky **Zavřít** v nabídce **systém** .  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Zpracování dat vrácených z modálního dialogového okna  

Když <xref:System.Windows.Window.DialogResult%2A> je nastaveno v dialogovém okně, funkce, která ji otevřela, může mít výsledek dialogového okna kontrolou <xref:System.Windows.Window.DialogResult%2A> vlastnosti při <xref:System.Windows.Window.ShowDialog%2A> návratu.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

Pokud je výsledkem dialogu `true` , funkce použije tuto funkci jako hromádku k načtení a zpracování dat poskytnutých uživatelem.  
  
> [!NOTE]
> Po <xref:System.Windows.Window.ShowDialog%2A> vrácení nelze dialog znovu otevřít. Místo toho je třeba vytvořit novou instanci.

Pokud je výsledkem dialogu `false` , funkce by měla ukončit zpracování odpovídajícím způsobem.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a>Vytvoření vlastního dialogového okna s nemodálním seznamem

Nemodální dialogové okno, jako je například dialogové okno Najít zobrazené na následujícím obrázku, má stejný základní vzhled jako modální dialogové okno.  

![Snímek obrazovky, který zobrazuje dialogové okno Najít.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Chování se však mírně liší, jak je popsáno v následujících částech.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Otevření nemodálního dialogového okna

Nemodální dialogové okno je otevřeno voláním <xref:System.Windows.Window.Show%2A> metody.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

Na rozdíl od <xref:System.Windows.Window.ShowDialog%2A> , <xref:System.Windows.Window.Show%2A> vrátí okamžitě. V důsledku toho volající okno nemůže říct, že se zavře dialogové okno nemodální a proto neví, kdy se má v dialogovém okně Vyhledat výsledek nebo získat data z dialogového okna pro další zpracování. Místo toho musí dialogové okno vytvořit alternativní způsob, jak vrátit data do volajícího okna ke zpracování.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Zpracování dat vrácených z nemodálního dialogového okna  

V tomto příkladu `FindDialogBox` může vracet jeden nebo více výsledků hledání do hlavního okna, v závislosti na hledaném textu bez jakékoli konkrétní frekvence. Stejně jako modální dialogové okno může nemodální dialogové okno vracet výsledky pomocí vlastností. Okno, které vlastní dialogové okno, musí ale znát, kdy se tyto vlastnosti mají kontrolovat. Jedním ze způsobů, jak to povolit, je, aby se v dialogovém okně implementovala událost, která se vyvolá při každém nalezení textu. `FindDialogBox`implementuje `TextFoundEvent` pro tento účel, který první vyžaduje delegáta.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

Pomocí `TextFoundEventHandler` delegáta `FindDialogBox` implementuje `TextFoundEvent` .
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

V důsledku toho `Find` může událost vyvolat, když se najde výsledek hledání.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

V okně vlastníka pak musí být tato událost zaregistrována a zpracována.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Zavření dialogového okna s nemodálním seznamem

Vzhledem k tomu <xref:System.Windows.Window.DialogResult%2A> , že není nutné nastavit, může být nemodální dialogové okno Uzavřeno pomocí mechanismů systému, včetně následujících:  
  
- V záhlaví klikněte na tlačítko **Zavřít** .  
  
- Stiskněte kombinaci kláves ALT + F4.  
  
- Z nabídky **systém** zvolte možnost **Zavřít** .  
  
Další možností je, že váš kód může zavolat <xref:System.Windows.Window.Close%2A> při kliknutí na tlačítko **Zavřít** .  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Viz také:

- [Přehled překryvných objektů](../controls/popup-overview.md)
- [Ukázka dialogového okna](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
