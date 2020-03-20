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
ms.openlocfilehash: c98d6a45d151d4b683a21e48eaeb5f4a19eaadb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187458"
---
# <a name="dialog-boxes-overview"></a>Přehled dialogových oken
Samostatné aplikace mají obvykle hlavní okno, které zobrazuje hlavní data, přes které aplikace pracuje, a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zpřístupňuje funkce pro zpracování dat prostřednictvím mechanismů, jako jsou panely nabídek, panely nástrojů a stavové panely. Netriviální aplikace může také zobrazit další okna provést následující:  
  
- Zobrazit uživatelům konkrétní informace.  
  
- Shromažďujte informace od uživatelů.  
  
- Zobrazují i shromažďují informace.  
  
 Tyto typy oken jsou označovány jako *dialogová okna*a existují dva typy: modální a nemodální.  
  
 *Modální* dialogové okno je zobrazeno funkcí, když funkce potřebuje další data od uživatele, aby pokračovala. Vzhledem k tomu, že funkce závisí na modálním dialogovém okně pro shromažďování dat, modální dialogové okno také zabraňuje uživateli v aktivaci jiných oken v aplikaci, zatímco zůstane otevřená. Ve většině případů modální dialogové okno umožňuje uživateli signalizovat po dokončení modálního dialogového okna stisknutím tlačítka **OK** nebo **Storno.** Stisknutí tlačítka **OK** znamená, že uživatel zadal data a chce, aby funkce pokračovala ve zpracování s těmito daty. Stisknutí tlačítka **Storno** znamená, že uživatel chce funkci úplně zastavit. Nejběžnější příklady modálních dialogových oken se zobrazují pro otevírání, ukládání a tisk dat.  
  
 *Nemodální* dialogové okno na druhé straně nebrání uživateli v aktivaci jiných oken, když je otevřen. Pokud například uživatel chce v dokumentu najít výskyty určitého slova, hlavní okno často otevře dialogové okno, ve které se uživatele zeptá, jaké slovo hledá. Vzhledem k tomu, že hledání slova nebrání uživateli v úpravách dokumentu, nemusí být dialogové okno modální. Nemodální dialogové okno poskytuje alespoň tlačítko **Zavřít** pro zavření dialogového okna a může poskytnout další tlačítka pro spuštění určitých funkcí, jako je například tlačítko **Najít další,** aby bylo možné najít další slovo, které odpovídá kritériím hledání hledání slov.  
  
 Windows Presentation Foundation (WPF) umožňuje vytvořit několik typů dialogových oken, včetně oken se zprávami, běžných dialogových oken a vlastních dialogových oken. Toto téma popisuje každý a [ukázka dialogového okna](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) obsahuje odpovídající příklady.  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a>Okna se zprávami  
 *Okno se zprávou* je dialogové okno, které lze použít k zobrazení textových informací a k tomu, aby se uživatelé mohli rozhodovat pomocí tlačítek. Na následujícím obrázku je zobrazeno okno se zprávou, které zobrazuje textové informace, položí otázku a poskytne uživateli tři tlačítka pro zodpovězení otázky.  
  
 ![Dialogové okno textový procesor s dotazem, zda chcete uložit změny do dokumentu před ukončením aplikace.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 Chcete-li vytvořit okno se <xref:System.Windows.MessageBox> zprávou, použijte třídu. <xref:System.Windows.MessageBox>umožňuje nakonfigurovat text, název, ikonu a tlačítka pole se zprávou pomocí následujícího kódu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Chcete-li zobrazit okno se `static` <xref:System.Windows.MessageBox.Show%2A> zprávou, volání metody, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Když kód, který zobrazuje okno se zprávou potřebuje zjistit a zpracovat rozhodnutí uživatele (které tlačítko bylo stisknuto), kód můžete zkontrolovat výsledek okna se zprávou, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Další informace o používání oken <xref:System.Windows.MessageBox>zpráv naleznete v [tématu Ukázka messageboxu](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)a [Ukázka dialogového okna](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox).  
  
 Ačkoli <xref:System.Windows.MessageBox> může nabídnout jednoduché dialogové okno uživatelské <xref:System.Windows.MessageBox> prostředí, výhodou použití je, že je jediný typ okna, které mohou být zobrazeny aplikacemi, které běží v rámci zabezpečení částečné důvěryhodnosti izolovaného prostoru (viz [zabezpečení](../security-wpf.md)), jako jsou aplikace prohlížeče XAML (XBAPs).  
  
 Většina dialogových oken zobrazuje a shromažďuje složitější data než výsledek okna se zprávou, včetně textu, výběru (zaškrtávacích políček), vzájemně se vylučujícího výběru (přepínací tlačítka) a výběru seznamu (seznamy, pole se seznamem, rozevírací seznamy). Pro tyto Windows Presentation Foundation (WPF) poskytuje několik běžných dialogových oken a umožňuje vytvořit vlastní dialogová okna, i když použití buď je omezena na aplikace s plnou důvěryhodností.  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a>Běžná dialogová okna  
 Systém Windows implementuje řadu opakovaně použitelných dialogových oken, která jsou společná pro všechny aplikace, včetně dialogových oken pro otevírání souborů, ukládání souborů a tisk. Vzhledem k tomu, že tato dialogová okna jsou implementována operačním systémem, mohou být sdílena mezi všemi aplikacemi spuštěnými v operačním systému, což pomáhá uživateli konzistenci prostředí; Pokud jsou uživatelé obeznámeni s použitím dialogového okna za předpokladu operačního systému v jedné aplikaci, nemusí se naučit, jak toto dialogové okno používat v jiných aplikacích. Vzhledem k tomu, že tato dialogová okna jsou k dispozici pro všechny aplikace a protože pomáhají poskytovat konzistentní uživatelské prostředí, jsou označována jako *běžná dialogová okna*.  
  
 Windows Presentation Foundation (WPF) zapouzdřuje otevřený soubor, uložit soubor a vytisknout běžná dialogová okna a zpřístupňuje je jako spravované třídy pro použití v samostatných aplikacích. Toto téma obsahuje stručný přehled každého z nich.  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a>Dialogové okno Otevřít soubor  
 Dialogové okno Otevřít soubor zobrazené na následujícím obrázku slouží funkcí mj.  
  
 ![Dialogové okno Otevřít zobrazující umístění pro načtení souboru.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 Společné dialogové okno otevřít soubor <xref:Microsoft.Win32.OpenFileDialog> je implementováno <xref:Microsoft.Win32> jako třída a je umístěno v oboru názvů. Následující kód ukazuje, jak vytvořit, nakonfigurovat a zobrazit jeden a jak zpracovat výsledek.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Další informace o dialogovém okně <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>Otevřít soubor naleznete v tématu .  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog>lze bezpečně načíst názvy souborů aplikacemi spuštěnými s částečnou důvěryhodností (viz [Zabezpečení](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a>dialogové okno Uložení souboru  
 Dialogové okno Uložit soubor zobrazené na následujícím obrázku slouží funkcí ukládání souborů k načtení názvu souboru, který chcete uložit.  
  
 ![Dialogové okno Uložit jako zobrazující umístění pro uložení souboru.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Společné dialogové okno uložit soubor <xref:Microsoft.Win32.SaveFileDialog> je implementováno jako <xref:Microsoft.Win32> třída a je umístěno v oboru názvů. Následující kód ukazuje, jak vytvořit, nakonfigurovat a zobrazit jeden a jak zpracovat výsledek.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Další informace o dialogovém okně <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>Uložit soubor naleznete v tématu .  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a>Tisk – dialogové okno

Tiskové dialogové okno zobrazené na následujícím obrázku se používá při tisku funkce pro výběr a konfiguraci tiskárny, kterou by uživatel chtěl vytisknout data.  
  
![Snímek obrazovky s tiskovým dialogovým oknem](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
Společné tiskové dialogové okno je <xref:System.Windows.Controls.PrintDialog> implementováno jako <xref:System.Windows.Controls> třída a je umístěno v oboru názvů. Následující kód ukazuje, jak vytvořit, nakonfigurovat a zobrazit jeden.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Další informace o tiskovém dialogovém okně naleznete v tématu <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Podrobnou diskusi o tisku v wpf, naleznete [v tématu Tisk Přehled](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a>Vlastní dialogová okna

Zatímco běžná dialogová okna jsou užitečná a měla by být použita, pokud je to možné, nepodporují požadavky dialogových oken specifických pro doménu. V těchto případech je třeba vytvořit vlastní dialogová okna. Jak uvidíme, dialogové okno je okno se zvláštním chováním. <xref:System.Windows.Window>implementuje tato chování a v <xref:System.Windows.Window> důsledku toho můžete použít k vytvoření vlastních modálních a nemodálních dialogových oken.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a>Vytvoření modálního vlastního dialogového okna

Toto téma ukazuje, jak použít <xref:System.Windows.Window> k vytvoření typické `Margins` implementace modálního dialogového okna pomocí dialogového okna jako příkladu (viz [Ukázka dialogového okna).](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) Dialogové `Margins` okno je zobrazeno na následujícím obrázku.  
  
 ![Dialogové okno Okraje s poli pro definování levého okraje, horního okraje, pravého okraje a dolního okraje.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Konfigurace modálního dialogového okna

Uživatelské rozhraní pro typické dialogové okno obsahuje následující:  
  
- Různé ovládací prvky, které jsou nutné ke shromažďování požadovaných dat.  
  
- Tlačítko **OK,** na které uživatelé klepnou, zavředialogové okno, vrátí se k funkci a bude pokračovat ve zpracování.  
  
- Tlačítko **Storno,** na které uživatelé klepnou, zavřete dialogové okno a zastavíte další zpracování funkce.  
  
- Tlačítko **Zavřít** v záhlaví.  
  
- Ikona.  
  
- **Tlačítka Minimalizovat**, **Maximalizovat**a **Obnovit.**  
  
- Nabídka **Systém** pro minimalizaci, maximalizaci, obnovení a zavření dialogového okna.  
  
- Pozice nad a uprostřed okna, které otevřelo dialogové okno.  
  
- Možnost změnit velikost, pokud je to možné, aby se zabránilo tomu, že dialogové okno bude příliš malé, a poskytnout uživateli užitečnou výchozí velikost. To vyžaduje, abyste nastavili výchozí i minimální rozměry.  
  
- Klávesa ESC jako klávesová zkratka, která způsobí stisknutí tlačítka **Storno.** To provést nastavením <xref:System.Windows.Controls.Button.IsCancel%2A> vlastnosti tlačítka `true` **Storno** na .  
  
- Klávesa ENTER (nebo RETURN) jako klávesová zkratka, která způsobí stisknutí tlačítka **OK.** To provést nastavením <xref:System.Windows.Controls.Button.IsDefault%2A> vlastnosti tlačítka `true` **OK** .  
  
Následující kód ukazuje tuto konfiguraci.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
Uživatelské prostředí pro dialogové okno se také rozšiřuje do řádku nabídek okna, které dialogové okno otevře. Pokud položka nabídky spustí funkci, která vyžaduje interakci uživatele prostřednictvím dialogového okna, než může funkce pokračovat, bude mít položka nabídky pro funkci v záhlaví tři tečky, jak je znázorněno zde.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Pokud položka nabídky spustí funkci, která zobrazuje dialogové okno, které nevyžaduje interakci uživatele, například dialogové okno O aplikaci, není tři tečky vyžadovány.  
  
#### <a name="opening-a-modal-dialog-box"></a>Otevření modálního dialogového okna

Dialogové okno se obvykle zobrazí v důsledku toho, že uživatel vybere položku nabídky, aby provedl funkci specifickou pro doménu, například nastavení okrajů dokumentu v textovém editoru. Zobrazení okna jako dialogového okna je podobné zobrazení normálního okna, i když vyžaduje další konfiguraci specifickou pro dialogové okno. Celý proces vytváření instancí, konfigurace a otevírání dialogového okna je zobrazen v následujícím kódu.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

Zde kód předá výchozí informace (aktuální okraje) do dialogového okna. Nastaví také <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> vlastnost s odkazem na okno, které zobrazuje dialogové okno. Obecně byste měli vždy nastavit vlastníka pro dialogové okno poskytovat chování související se stavem okna, které jsou společné pro všechna dialogová okna (další informace naleznete v tématu [Přehled systému WPF Windows).](wpf-windows-overview.md)

> [!NOTE]
> Je nutné poskytnout vlastníka pro podporu automatizace uživatelského rozhraní (UI) pro dialogová okna (viz [Přehled automatizace uživatelského rozhraní).](../../ui-automation/ui-automation-overview.md)

Po konfiguraci dialogového okna se zobrazí modálně voláním <xref:System.Windows.Window.ShowDialog%2A> metody.  
  
#### <a name="validating-user-provided-data"></a>Ověření dat poskytnutých uživateli

Při otevření dialogového okna a uživatel i poskytuje požadovaná data, dialogové okno je zodpovědný za zajištění, že zadaný data je platný z následujících důvodů:  
  
- Z hlediska zabezpečení by měl y ověřovat všechny vstupy.  
  
- Z hlediska specifické pro doménu ověřování dat zabraňuje zpracování chybných dat kódem, což by mohlo potenciálně vyvolat výjimky.  
  
- Z hlediska uživatelského prostředí může dialogové okno pomoci uživatelům tím, že jim ukáže, která data zadali, je neplatná.  
  
- Z hlediska výkonu může ověření dat ve vícevrstvé aplikaci snížit počet zpátečních cest mezi klientem a aplikačními vrstvami, zejména pokud se aplikace skládá z webových služeb nebo databází založených na serveru.  

Chcete-li ověřit vázaný ovládací prvek v WPF, musíte definovat ověřovací pravidlo a přidružit jej k vazbě. Ověřovací pravidlo je vlastní třída, <xref:System.Windows.Controls.ValidationRule>která je odvozena od . Následující příklad ukazuje ověřovací `MarginValidationRule`pravidlo , které kontroluje, <xref:System.Double> zda vázaná hodnota je a je v zadaném rozsahu.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

V tomto kódu je ověřovací logika ověřovacího pravidla <xref:System.Windows.Controls.ValidationRule.Validate%2A> implementována přepsáním metody, která ověří data a vrátí příslušnou <xref:System.Windows.Controls.ValidationResult>.  

Chcete-li přidružit ověřovací pravidlo k vázanému ovládacímu prvku, použijte následující značky.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Jakmile je ověřovací pravidlo přidruženo, WPF jej automaticky použije při zadání dat do vázaného ovládacího prvku. Pokud ovládací prvek obsahuje neplatná data, WPF zobrazí červené ohraničení kolem neplatného ovládacího prvku, jak je znázorněno na následujícím obrázku.  
  
![Dialogové okno Okraje s červeným ohraničením kolem neplatné hodnoty levého okraje.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF neomezuje uživatele na neplatný ovládací prvek, dokud nezadali platná data. To je dobré chování pro dialogové okno; Uživatel by měl mít možnost volně procházet ovládací prvky v dialogovém okně bez ohledu na to, zda jsou data platná. To však znamená, že uživatel může zadat neplatná data a stisknout tlačítko **OK.** Z tohoto důvodu váš kód také potřebuje ověřit všechny **OK** ovládací prvky v <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dialogovém okně při stisknutí tlačítka OK zpracováním události.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Tento kód vytvoří výčet všech objektů závislostí v okně a pokud <xref:System.Windows.Controls.Validation.GetHasError%2A>jsou některé neplatné (jak je vráceno , neplatný ovládací prvek získá fokus, `IsValid` metoda vrátí `false`a okno je považováno za neplatné.  
  
Jakmile je dialogové okno platné, může se bezpečně zavřít a vrátit. Jako součást procesu vrácení je třeba vrátit výsledek volající funkce.  
  
#### <a name="setting-the-modal-dialog-result"></a>Nastavení výsledku modálního dialogu

Otevření dialogového <xref:System.Windows.Window.ShowDialog%2A> okna pomocí je zásadně jako volání metody: <xref:System.Windows.Window.ShowDialog%2A> kód, <xref:System.Windows.Window.ShowDialog%2A> který otevřel dialogové okno pomocí čeká, až se vrátí. Když <xref:System.Windows.Window.ShowDialog%2A> vrátí, kód, který volal, se musí rozhodnout, zda pokračovat ve zpracování nebo zastavit zpracování, na základě toho, zda uživatel stiskl tlačítko **OK** nebo **tlačítko Storno.** Pro usnadnění tohoto rozhodnutí dialogové okno musí vrátit volbu <xref:System.Boolean> uživatele jako hodnotu, která je vrácena <xref:System.Windows.Window.ShowDialog%2A> z metody.  

Po **OK** klepnutí na tlačítko <xref:System.Windows.Window.ShowDialog%2A> OK `true`by se měl vrátit . Toho je dosaženo <xref:System.Windows.Window.DialogResult%2A> nastavením vlastnosti dialogového okna po klepnutí na tlačítko **OK.**  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Všimněte si, že nastavení vlastnosti <xref:System.Windows.Window.DialogResult%2A> také způsobí, že okno <xref:System.Windows.Window.Close%2A>zavřít automaticky, což zmírňuje potřebu explicitně volat .  
  
Po klepnutí na tlačítko <xref:System.Windows.Window.ShowDialog%2A> **Storno** by se <xref:System.Windows.Window.DialogResult%2A> měl vrátit `false`, což také vyžaduje nastavení vlastnosti.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Pokud je vlastnost <xref:System.Windows.Controls.Button.IsCancel%2A> tlačítka nastavena na `true` a uživatel stiskne tlačítko **Storno** nebo klávesu ESC, <xref:System.Windows.Window.DialogResult%2A> je automaticky nastavenna na `false`. Následující značky má stejný účinek jako předchozí kód, bez <xref:System.Windows.Controls.Primitives.ButtonBase.Click> nutnosti zpracování události.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Dialogové okno se `false` automaticky vrátí, když uživatel stiskne tlačítko **Zavřít** v záhlaví nebo z nabídky **Systém** vybere položku nabídky **Zavřít.**  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Zpracování dat vrácených z modálního dialogového okna  

Je-li <xref:System.Windows.Window.DialogResult%2A> nastavena dialogové okno, funkce, která otevřela může získat <xref:System.Windows.Window.DialogResult%2A> výsledek <xref:System.Windows.Window.ShowDialog%2A> dialogového okna kontrolou vlastnost při vrácení.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

Pokud je `true`výsledkem dialogového okna , funkce ji používá jako podnět k načtení a zpracování dat poskytnutých uživatelem.  
  
> [!NOTE]
> Po <xref:System.Windows.Window.ShowDialog%2A> vrácení dialogového okna nelze znovu otevřít. Místo toho je třeba vytvořit novou instanci.

Pokud je `false`výsledek dialogového okna , funkce by měla odpovídajícím způsobem ukončit zpracování.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a>Vytvoření nemodlavého vlastního dialogového okna

Nemodální dialogové okno, například dialogové okno Najít zobrazené na následujícím obrázku, má stejný základní vzhled jako modální dialogové okno.  

![Snímek obrazovky s dialogovým oknem Najít](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Chování je však mírně odlišné, jak je popsáno v následujících částech.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Otevření nemodálního dialogového okna

Nemodální dialogové okno se <xref:System.Windows.Window.Show%2A> otevře voláním metody.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

Na <xref:System.Windows.Window.ShowDialog%2A> <xref:System.Windows.Window.Show%2A> rozdíl od , vrátí okamžitě. V důsledku toho volající okno nelze zjistit, kdy je nemodální dialogové okno uzavřeno, a proto neví, kdy zkontrolovat výsledek dialogového okna nebo získat data z dialogového okna pro další zpracování. Místo toho dialogové okno musí vytvořit alternativní způsob, jak vrátit data do volacího okna pro zpracování.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Zpracování dat vrácených z nemodlavého dialogového okna  

V tomto příkladu `FindDialogBox` může vrátit jeden nebo více výsledků hledání do hlavního okna, v závislosti na hledaném textu bez jakékoli konkrétní frekvence. Stejně jako u modálního dialogového okna může nemodální dialogové okno vrátit výsledky pomocí vlastností. Okno, které je vlastní dialogové okno však musí vědět, kdy zkontrolovat tyto vlastnosti. Jedním ze způsobů, jak to povolit, je pro dialogové okno implementovat událost, která je vyvolána vždy, když je nalezen text. `FindDialogBox``TextFoundEvent` pro tento účel, což nejprve vyžaduje delegáta.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

Pomocí `TextFoundEventHandler` delegáta `FindDialogBox` implementuje `TextFoundEvent`.
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

V důsledku `Find` toho může vyvolat událost při nalezení výsledku hledání.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

Okno vlastníka se pak musí zaregistrovat a zpracovat tuto událost.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Zavření nemodlavého dialogového okna

Vzhledem k tomu, <xref:System.Windows.Window.DialogResult%2A> že není nutné nastavit, modenální dialog lze zavřít pomocí systému poskytují mechanismy, včetně následujících:  
  
- Klikněte na tlačítko **Zavřít** v záhlaví.  
  
- Stisknutím kláves ALT+F4.  
  
- Z nabídky **Systém** zvolte **Zavřít.**  
  
Případně může váš kód <xref:System.Windows.Window.Close%2A> volat po klepnutí na tlačítko **Zavřít.**  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Viz také

- [Přehled překryvných objektů](../controls/popup-overview.md)
- [Ukázka dialogového okna](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
