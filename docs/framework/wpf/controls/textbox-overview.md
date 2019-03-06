---
title: TextBox – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 5ddd6600493cd127f8024f23594c628476cac19e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361067"
---
# <a name="textbox-overview"></a>TextBox – přehled
<xref:System.Windows.Controls.TextBox> Třída umožňuje zobrazení nebo úpravě neformátovaného textu. Běžně se používají <xref:System.Windows.Controls.TextBox> upravuje neformátovaného textu ve formuláři. Například byste použili atd formuláře s žádostí o uživatelské jméno, telefonní číslo, <xref:System.Windows.Controls.TextBox> ovládací prvky pro zadávání textu. Toto téma představuje <xref:System.Windows.Controls.TextBox> třídy a poskytuje příklady toho, jak ho použít v obou [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a C#.  
  
 
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox nebo RichTextBox?  
 Obě <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> umožňují uživatelům se vstupním textem, ale pro různé scénáře se používají dva ovládací prvky. A <xref:System.Windows.Controls.TextBox> vyžaduje míň systémových prostředků o <xref:System.Windows.Controls.RichTextBox> tak, aby byl ideální, pokud musí upravit pouze prostý text (tj. využívání ve formě). A <xref:System.Windows.Controls.RichTextBox> je lepší volbou, když je nutné pro uživatele k úpravě formátovaný text, obrázky, tabulky nebo jiné podporované obsahu. Například úpravy dokumentu, článek nebo blogu, který vyžaduje formátování, obrázky, etc se nejlépe provádí pomocí <xref:System.Windows.Controls.RichTextBox>. Následující tabulka shrnuje primární funkce <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBox>.  
  
|Control|V reálném čase kontrolu pravopisu|Kontextová nabídka|Formátování příkazů, jako jsou <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (pev.cenu + B)|<xref:System.Windows.Documents.FlowDocument> obsah, jako jsou obrázky, odstavce, tabulky, atd.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Ano|Ano|Ne|Ne.|  
|<xref:System.Windows.Controls.RichTextBox>|Ano|Ano|Ano (viz [RichTextBox – přehled](richtextbox-overview.md))|Ano (viz [RichTextBox – přehled](richtextbox-overview.md))|  
  
> [!NOTE]
>  I když <xref:System.Windows.Controls.TextBox> nemá nepodporuje formátování související úpravy příkazy jako <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (pev.cenu + B), mnoho základních příkazů podporují oba ovládací prvky, jako <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>. Další informace naleznete v tématu <xref:System.Windows.Documents.EditingCommands>.  
  
 Nepodporované funkce <xref:System.Windows.Controls.TextBox> jsou popsané v následujících částech. Další informace o <xref:System.Windows.Controls.RichTextBox>, naleznete v tématu [RichTextBox – přehled](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>V reálném čase kontrolu pravopisu  
 Můžete povolit v reálném čase kontrolu pravopisu v <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox>. Po zapnutí kontrolu pravopisu, zobrazí se červená čára pod všechna chybně napsaná slova (viz obrázek níže).  
  
 ![Textové pole s pravopisu&#45;kontrola](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Zobrazit [povolení kontroly pravopisu v ovládacím prvku úpravy textu](how-to-enable-spell-checking-in-a-text-editing-control.md) se dozvíte, jak povolit kontrolu pravopisu.  
  
### <a name="context-menu"></a>Kontextová nabídka  
 Ve výchozím nastavení obě <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> mít místní nabídky, která se zobrazí, když uživatel klepne pravým tlačítkem myši v ovládacím prvku. V místní nabídce umožňuje uživateli vyjmutí, kopírování nebo vkládání (viz obrázek níže).  
  
 ![Textové pole s místní nabídkou](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Můžete vytvořit vlastní vlastní místní nabídky potlačit výchozí chování. Zobrazit [použití vlastní místní nabídky u objektu TextBox](how-to-use-a-custom-context-menu-with-a-textbox.md) Další informace.  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Vytváření textových polí  
 A <xref:System.Windows.Controls.TextBox> může být jeden řádek na výšku nebo zahrnovat více řádků. Jeden řádek <xref:System.Windows.Controls.TextBox> je nejvhodnější pro vložení malé množství prostý text (tj.) "Name", "Telefonní číslo" atd. ve formě). Následující příklad ukazuje, jak vytvořit jeden řádek <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Můžete také vytvořit <xref:System.Windows.Controls.TextBox> , který umožňuje uživateli zadat více řádků textu. Například pokud se zobrazí dotaz formuláře pro osobních sketch uživatele, by chcete použít <xref:System.Windows.Controls.TextBox> , která podporuje více řádků textu. Následující příklad ukazuje, jak používat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k definování <xref:System.Windows.Controls.TextBox> ovládací prvek, který automaticky přizpůsobí více řádků textu.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Nastavení <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atribut `Wrap` způsobí, že text, který má zabalit do nového řádku na okraj <xref:System.Windows.Controls.TextBox> ovládací prvek je dosaženo, automatické rozbalování <xref:System.Windows.Controls.TextBox> ovládacího prvku v případě potřeby zadejte místo pro nový řádek.  
  
 Nastavení <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atribut `true` způsobí, že nový řádek má být vložen při stisknutí klávesy RETURN, znovu automaticky rozšiřuje <xref:System.Windows.Controls.TextBox> zahrnout místa pro nový řádek, v případě potřeby.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Přidá posuvník pro atribut <xref:System.Windows.Controls.TextBox>tak, aby obsah <xref:System.Windows.Controls.TextBox> posunout Pokud <xref:System.Windows.Controls.TextBox> rozbalí nad rámec velikost rámu nebo okna, který ji obklopuje.  
  
 Další informace o různých úloh spojených s použitím <xref:System.Windows.Controls.TextBox>, naleznete v tématu [postupy: témata](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Rozpoznat, kdy se změní obsah  
 Obvykle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost má použít k detekci vždy, když text v <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox> změní, nikoli <xref:System.Windows.UIElement.KeyDown> podle očekávání. Zobrazit [rozpoznat při Text ve textového pole došlo ke změně](how-to-detect-when-text-in-a-textbox-has-changed.md) příklad.  
  
## <a name="see-also"></a>Viz také:
- [Témata s postupy](textbox-how-to-topics.md)
- [RichTextBox – přehled](richtextbox-overview.md)
