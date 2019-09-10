---
title: RichTextBox – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: bfed42bcf3693ef744b3ed2b54ebe070931513a9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855732"
---
# <a name="richtextbox-overview"></a>RichTextBox – přehled

<xref:System.Windows.Controls.RichTextBox> Ovládací prvek umožňuje zobrazit nebo upravit obsah toku včetně odstavců, obrázků, tabulek a dalších. Toto téma představuje <xref:System.Windows.Controls.TextBox> třídu a poskytuje příklady, jak ji použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] v a. C#

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a>Textové pole nebo RichTextBox?

<xref:System.Windows.Controls.RichTextBox> A<xref:System.Windows.Controls.TextBox> umožňují uživatelům upravovat text, ale dva ovládací prvky se používají v různých scénářích. <xref:System.Windows.Controls.RichTextBox> Je lepší volbou, pokud je potřeba, aby uživatel mohl upravovat formátovaný text, obrázky, tabulky nebo jiné bohaté obsahy. Například úprava dokumentu, článku nebo blogu, který vyžaduje formátování, obrázky atd <xref:System.Windows.Controls.RichTextBox>., se nejlépe docílí pomocí. Vyžaduje méně systémových prostředků <xref:System.Windows.Controls.RichTextBox> a je ideální, pokud je třeba upravit pouze prostý text (tj. využití ve formulářích). <xref:System.Windows.Controls.TextBox> Další informace o <xref:System.Windows.Controls.TextBox>najdete v tématu [Přehled textového pole](textbox-overview.md) . V následující tabulce jsou shrnuty hlavní funkce <xref:System.Windows.Controls.TextBox> a. <xref:System.Windows.Controls.RichTextBox>

|Control|Kontrola pravopisu v reálném čase|Kontextová nabídka|Formátování příkazů jako <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (centrum + B)|<xref:System.Windows.Documents.FlowDocument>obsah, jako jsou obrázky, odstavce, tabulky atd.|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|Ano|Ano|Ne|Ne.|
|<xref:System.Windows.Controls.RichTextBox>|Ano|Ano|Ano|Ano|

> [!NOTE]
> I <xref:System.Windows.Controls.TextBox> když nepodporuje formátování související příkazy jako <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (centrum + B), mnoho základních příkazů je podporováno v obou ovládacích prvcích, jako <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>je například.

Funkce z výše uvedené tabulky jsou podrobněji popsány později.

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a>Vytvoření RichTextBox

Následující kód ukazuje <xref:System.Windows.Controls.RichTextBox> , jak vytvořit, aby uživatel mohl upravovat bohatou úpravu obsahu v.

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

Konkrétně upravený obsah v <xref:System.Windows.Controls.RichTextBox> nástroji je obsahem toku. Obsah toku může obsahovat mnoho typů prvků, včetně formátovaného textu, obrázků, seznamů a tabulek. Podrobné informace o dokumentech Flow najdete v tématu [Přehled flowového dokumentu](../advanced/flow-document-overview.md) . Aby mohl obsah toku obsahovat, <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Documents.FlowDocument> hostitelé objekt, který zase obsahuje upravitelný obsah. Chcete-li předvést obsah <xref:System.Windows.Controls.RichTextBox>toku v, následující kód ukazuje, jak <xref:System.Windows.Controls.RichTextBox> vytvořit s odstavcem a nějakým tučným textem.

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

Následující obrázek ukazuje, jak se tato ukázka vykresluje.

![RichTextBox s obsahem](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")

Prvky jako <xref:System.Windows.Documents.Paragraph> a <xref:System.Windows.Documents.Bold> určují, <xref:System.Windows.Controls.RichTextBox> jak se obsah uvnitř zobrazí. Při úpravách <xref:System.Windows.Controls.RichTextBox> obsahu uživatel změní tento tok obsahu. Další informace o funkcích obsahu toku a o tom, jak s ním pracovat, najdete v tématu [Přehled dokumentů Flow](../advanced/flow-document-overview.md).

> [!NOTE]
> Obsah toku uvnitř a <xref:System.Windows.Controls.RichTextBox> se chová stejně jako obsah toku obsažený v jiných ovládacích prvcích. Například neexistují žádné sloupce v typu <xref:System.Windows.Controls.RichTextBox> , a proto žádné chování při automatické změně velikosti. V nástroji nejsou k dispozici <xref:System.Windows.Controls.RichTextBox>také integrované funkce, jako je hledání, režim zobrazení, navigace na stránce a přiblížení.

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a>Kontrola pravopisu v reálném čase

Kontrolu pravopisu v reálném čase můžete povolit v <xref:System.Windows.Controls.TextBox> nebo. <xref:System.Windows.Controls.RichTextBox> Když je kontrola pravopisu zapnutá, zobrazí se červená čára pod případnými nesprávně napsanými slovy (viz obrázek níže).

![Textové pole s&#45;kontrolou pravopisu](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")

Informace o tom, jak povolit kontrolu pravopisu, najdete v tématu [Povolení kontroly pravopisu v ovládacím prvku pro úpravu textu](how-to-enable-spell-checking-in-a-text-editing-control.md) .

<a name="context_menu"></a>

## <a name="context-menu"></a>Kontextová nabídka

Ve výchozím nastavení má <xref:System.Windows.Controls.TextBox> obojí <xref:System.Windows.Controls.RichTextBox> i kontextovou nabídku, která se zobrazí, když uživatel klikne pravým tlačítkem myši uvnitř ovládacího prvku. Místní nabídka umožňuje uživateli vyjmutí, kopírování nebo vložení (viz obrázek níže).

![Textové pole s místní nabídkou](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")

Můžete vytvořit vlastní místní nabídku a přepsat tak výchozí. Další informace najdete v tématu věnovaném [umístění vlastní kontextové nabídky ve RichTextBox](how-to-position-a-custom-context-menu-in-a-richtextbox.md) .

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a>Příkazy pro úpravy

Příkazy pro úpravy umožňují uživatelům formátovat Upravitelný obsah v <xref:System.Windows.Controls.RichTextBox>rámci. Kromě základních příkazů <xref:System.Windows.Controls.RichTextBox> pro úpravy zahrnuje příkazy formátování, <xref:System.Windows.Controls.TextBox> které nepodporují. Například při úpravách v <xref:System.Windows.Controls.RichTextBox>nástroji může uživatel stisknutím centra + B přepnout formátování textu tučně. Úplný <xref:System.Windows.Documents.EditingCommands> seznam dostupných příkazů najdete v tématu. Kromě používání klávesových zkratek můžete příkazy připojit až k ostatním ovládacím prvkům, jako jsou tlačítka. Následující příklad ukazuje, jak vytvořit jednoduchý panel nástrojů obsahující tlačítka, která může uživatel použít ke změně formátování textu.

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

Následující obrázek ukazuje, jak se tato ukázka zobrazuje.

![RichTextBox s panelem nástrojů](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a>Rozpoznat změnu obsahu

Obvykle by <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se měla tato událost použít k detekci pokaždé, <xref:System.Windows.Controls.TextBox> když <xref:System.Windows.Controls.RichTextBox> se změní text <xref:System.Windows.UIElement.KeyDown> v nebo, a pak i tak, jak byste mohli očekávat. Příklad naleznete v tématu [zjištění, kdy byl text v textovém poli změněn](how-to-detect-when-text-in-a-textbox-has-changed.md) .

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a>Uložení, načtení a tisk obsahu RichTextBox

Následující příklad ukazuje, jak uložit obsah <xref:System.Windows.Controls.RichTextBox> souboru do souboru, načíst tento obsah zpět <xref:System.Windows.Controls.RichTextBox>do a vytisknout obsah. Níže je uveden kód pro příklad.

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

Níže je kód na pozadí pro příklad.

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a>Viz také:

- [Témata s postupy](richtextbox-how-to-topics.md)
- [TextBox – přehled](textbox-overview.md)
