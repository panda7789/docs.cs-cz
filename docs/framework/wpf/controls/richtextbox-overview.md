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
ms.openlocfilehash: 9aa0d33b3cb2c15ba9c1cb7e7d7be9a3125f66d3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162708"
---
# <a name="richtextbox-overview"></a>RichTextBox – přehled
<xref:System.Windows.Controls.RichTextBox> Řízení umožňuje zobrazit nebo upravit obsah toku včetně odstavce, obrázky, tabulky a dalších. Toto téma představuje <xref:System.Windows.Controls.TextBox> třídy a poskytuje příklady toho, jak ho použít v obou [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a C#.  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox nebo RichTextBox?  
 Obě <xref:System.Windows.Controls.RichTextBox> a <xref:System.Windows.Controls.TextBox> povolit uživatelům upravit text, ale dvou ovládacích prvků se používají v různých scénářích. A <xref:System.Windows.Controls.RichTextBox> je lepší volbou, když je to nutné pro uživatele k úpravě formátovaný text, obrázky, tabulky nebo jiné formátovaný obsah. Například úpravy dokumentu, článek nebo blogu, který vyžaduje formátování, obrázky, etc se nejlépe provádí pomocí <xref:System.Windows.Controls.RichTextBox>. A <xref:System.Windows.Controls.TextBox> vyžaduje míň systémových prostředků o <xref:System.Windows.Controls.RichTextBox> a je ideální v případě jenom prostý text musí být upraven (tj. využití ve formulářích). Zobrazit [TextBox – přehled](textbox-overview.md) Další informace o <xref:System.Windows.Controls.TextBox>. Následující tabulka shrnuje hlavní funkce <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox>.  
  
|Control|V reálném čase kontrolu pravopisu|Kontextová nabídka|Formátování příkazů, jako jsou <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (pev.cenu + B)|<xref:System.Windows.Documents.FlowDocument> obsah, jako jsou obrázky, odstavce, tabulky, atd.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Ano|Ano|Ne|Ne.|  
|<xref:System.Windows.Controls.RichTextBox>|Ano|Ano|Ano|Ano|  
  
 **Poznámka:** I když <xref:System.Windows.Controls.TextBox> nepodporuje formátování související příkazů, jako jsou <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (pev.cenu + B), mnoho základních příkazů podporují oba ovládací prvky, jako <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.  
  
 Funkce z výše uvedené tabulky se budeme věnovat jednotlivě podrobněji později.  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>Vytvoření prvku RichTextBox  
 Následující kód ukazuje, jak vytvořit <xref:System.Windows.Controls.RichTextBox> , že uživatel může upravovat formátovaného obsahu v.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 Konkrétně v upravit obsah <xref:System.Windows.Controls.RichTextBox> je plovoucího obsahu. Obsah toku může obsahovat mnoho typů prvků, včetně formátovaný text, obrázky, seznamy a tabulky. Zobrazit [přehled toku dokumentů](../advanced/flow-document-overview.md) pro podrobnější informace na dokumenty toku. Mohla obsahovat plovoucího obsahu <xref:System.Windows.Controls.RichTextBox> hostitele <xref:System.Windows.Documents.FlowDocument> objekt, který zase obsahuje upravitelný obsah. K předvedení plovoucího obsahu v <xref:System.Windows.Controls.RichTextBox>, následující kód ukazuje, jak vytvořit <xref:System.Windows.Controls.RichTextBox> odstavce a nějaký tučný text.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 Následující obrázek znázorňuje, jak tato ukázka vykreslí.  
  
 ![RichTextBox – s obsahem](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 Prvky, jako jsou <xref:System.Windows.Documents.Paragraph> a <xref:System.Windows.Documents.Bold> určit, jak obsahu uvnitř <xref:System.Windows.Controls.RichTextBox> se zobrazí. Jako uživatel upraví <xref:System.Windows.Controls.RichTextBox> obsahu, mohou změnit obsah tohoto toku. Další informace o funkcích plovoucího obsahu a jak pracovat s ním, najdete v článku [přehled toku dokumentů](../advanced/flow-document-overview.md).  
  
 **Poznámka:** Obsah uvnitř toku <xref:System.Windows.Controls.RichTextBox> nechová stejně jako plovoucího obsahu obsažené v jiných ovládacích prvků. Například neexistují žádné sloupce v <xref:System.Windows.Controls.RichTextBox> a proto žádná automatická změna velikosti chování. Navíc integrované funkce, jako je hledání, režim zobrazení, navigaci na stránce a přiblížení nejsou k dispozici v rámci <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>Kontrola pravopisu v reálném čase  
 Můžete povolit kontrolu pravopisu v reálném čase <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox>. Po zapnutí kontrolu pravopisu, zobrazí se červená čára pod všechna chybně napsaná slova (viz obrázek níže).  
  
 ![Textové pole s pravopisu&#45;kontrola](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Zobrazit [povolení kontroly pravopisu v ovládacím prvku úpravy textu](how-to-enable-spell-checking-in-a-text-editing-control.md) se dozvíte, jak povolit kontrolu pravopisu.  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>Kontextová nabídka  
 Ve výchozím nastavení obě <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> mít místní nabídky, která se zobrazí, když uživatel klepne pravým tlačítkem myši v ovládacím prvku. V místní nabídce umožňuje uživateli vyjmutí, kopírování nebo vkládání (viz obrázek níže).  
  
 ![Textové pole s místní nabídkou](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Můžete vytvořit vlastní vlastní místní nabídky, chcete-li přepsat výchozí hodnotu. Zobrazit [umístění vlastní místní nabídky v prvku RichTextBox](how-to-position-a-custom-context-menu-in-a-richtextbox.md) Další informace.  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>Příkazy pro úpravy  
 Úprava příkazů umožňuje uživatelům upravovat obsah uvnitř formátování <xref:System.Windows.Controls.RichTextBox>. Kromě základní příkazy, pro úpravy <xref:System.Windows.Controls.RichTextBox> obsahuje formátování příkazů, které <xref:System.Windows.Controls.TextBox> nepodporuje. Například při úpravách v <xref:System.Windows.Controls.RichTextBox>, uživatel může stisknutím pev.cenu + B přepněte formátování tučným písmem. Zobrazit <xref:System.Windows.Documents.EditingCommands> pro úplný seznam příkazů, které jsou k dispozici. Kromě používání klávesových zkratek, můžete integrovat příkazy až do další ovládací prvky jako tlačítka. Následující příklad ukazuje, jak vytvořit jednoduchý nástroj panel obsahující tlačítka, která uživatel může použít ke změně textu formátování.  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 Následující obrázek znázorňuje, jak tato ukázka zobrazí.  
  
 ![RichTextBox – s panelem nástrojů](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Rozpoznat, kdy se změní obsah  
 Obvykle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost má použít k detekci vždy, když text v <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox> místo změní <xref:System.Windows.UIElement.KeyDown> podle očekávání. Zobrazit [rozpoznat při Text ve textového pole došlo ke změně](how-to-detect-when-text-in-a-textbox-has-changed.md) příklad.  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>Uložení, načtení a tisk obsahu RichTextBox  
 Následující příklad ukazuje, jak uložit obsah <xref:System.Windows.Controls.RichTextBox> do souboru, načtení tohoto obsahu zpět do <xref:System.Windows.Controls.RichTextBox>a vytisknout obsah. Níže je kód pro příklad.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 Níže je kód za pro příklad.  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [– postupy](richtextbox-how-to-topics.md)
- [TextBox – přehled](textbox-overview.md)
