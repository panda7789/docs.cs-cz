---
title: TextBox – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 86b2cf8cb0c72186fd92bdad0af6bf5bd3fa9f3f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174429"
---
# <a name="textbox-overview"></a>TextBox – přehled
<xref:System.Windows.Controls.TextBox>Třída umožňuje zobrazit nebo upravit neformátovaný text. Běžné použití a <xref:System.Windows.Controls.TextBox> upravuje ve formuláři neformátovaný text. Například formulář žádající o jméno uživatele, telefonní číslo atd. by používal <xref:System.Windows.Controls.TextBox> ovládací prvky pro zadávání textu. V tomto tématu se seznámíte se <xref:System.Windows.Controls.TextBox> třídou a najdete v nich příklady, jak je používat v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jazycích i C#.  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>Textové pole nebo RichTextBox?  
 <xref:System.Windows.Controls.TextBox>A <xref:System.Windows.Controls.RichTextBox> umožňují uživatelům zadávat text, ale dva ovládací prvky se používají pro různé scénáře. <xref:System.Windows.Controls.TextBox>Vyžaduje méně systémových prostředků <xref:System.Windows.Controls.RichTextBox> , takže je ideální, pokud je třeba upravit pouze prostý text (tj. využití ve formuláři). <xref:System.Windows.Controls.RichTextBox>Je lepší volbou, pokud je potřeba, aby uživatel mohl upravovat formátovaný text, obrázky, tabulky nebo jiný podporovaný obsah. Například úprava dokumentu, článku nebo blogu, který vyžaduje formátování, obrázky atd., se nejlépe docílí pomocí <xref:System.Windows.Controls.RichTextBox> . V následující tabulce najdete souhrn primárních funkcí <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> .  
  
|Řízení|Kontrola pravopisu v reálném čase|Místní nabídka|Formátování příkazů jako <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (centrum + B)|<xref:System.Windows.Documents.FlowDocument>obsah, jako jsou obrázky, odstavce, tabulky atd.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Ano|Ano|Ne|Ne.|  
|<xref:System.Windows.Controls.RichTextBox>|Ano|Ano|Ano (viz [Přehled RichTextBox](richtextbox-overview.md))|Ano (viz [Přehled RichTextBox](richtextbox-overview.md))|  
  
> [!NOTE]
> I když nepodporuje <xref:System.Windows.Controls.TextBox> formátování souvisejících příkazů pro úpravy jako <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (centrum + B), mnoho základních příkazů je podporováno v obou ovládacích prvcích, jako je <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> . Další informace naleznete v tématu <xref:System.Windows.Documents.EditingCommands>.  
  
 Funkce podporované nástrojem <xref:System.Windows.Controls.TextBox> jsou popsány v níže uvedených částech. Další informace o <xref:System.Windows.Controls.RichTextBox> naleznete v tématu [RichTextBox Overview](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Kontrola pravopisu v reálném čase  
 Můžete povolit kontrolu pravopisu v reálném čase v <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox> . Když je kontrola pravopisu zapnutá, zobrazí se červená čára pod případnými nesprávně napsanými slovy (viz obrázek níže).  
  
 ![Textové pole s kontrolou pravopisu&#45;](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Informace o tom, jak povolit kontrolu pravopisu, najdete v tématu [Povolení kontroly pravopisu v ovládacím prvku pro úpravu textu](how-to-enable-spell-checking-in-a-text-editing-control.md) .  
  
### <a name="context-menu"></a>Místní nabídka  
 Ve výchozím nastavení <xref:System.Windows.Controls.TextBox> má obojí i <xref:System.Windows.Controls.RichTextBox> kontextovou nabídku, která se zobrazí, když uživatel klikne pravým tlačítkem myši uvnitř ovládacího prvku. Místní nabídka umožňuje uživateli vyjmutí, zkopírování nebo vložení (viz obrázek níže).  
  
 ![Textové pole s místní nabídkou](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Můžete vytvořit vlastní místní nabídku a přepsat tak výchozí chování. Další informace najdete v tématu [použití vlastní místní nabídky s](how-to-use-a-custom-context-menu-with-a-textbox.md) textovým polem.  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>Vytváření textových polí  
 <xref:System.Windows.Controls.TextBox>Může být jeden řádek ve výšce nebo tvořený více řádky. Jeden řádek <xref:System.Windows.Controls.TextBox> je nejvhodnější pro vkládání malých objemů prostého textu (tj. "název", "telefonní číslo" atd. ve formuláři). Následující příklad ukazuje, jak vytvořit jeden řádek <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Můžete také vytvořit <xref:System.Windows.Controls.TextBox> , který umožňuje uživateli zadat více řádků textu. Například pokud váš formulář požádal o Biographical náčrta uživatele, budete chtít použít a <xref:System.Windows.Controls.TextBox> , který podporuje více řádků textu. Následující příklad ukazuje, jak použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k definování <xref:System.Windows.Controls.TextBox> ovládacího prvku, který se automaticky rozbalí, aby odpovídal více řádkům textu.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Nastavení <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atributu tak `Wrap` způsobí, že při dosažení okraje ovládacího prvku se text zalomí na nový řádek a v <xref:System.Windows.Controls.TextBox> případě potřeby automaticky rozšíří <xref:System.Windows.Controls.TextBox> ovládací prvek tak, aby zahrnoval místo pro nový řádek.  
  
 Nastavením <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atributu tak `true` dojde k vložení nového řádku při STISKNUTí návratového klíče, poté, co se znovu automaticky rozbalí, <xref:System.Windows.Controls.TextBox> aby zahrnovalo místo pro nový řádek (v případě potřeby).  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>Atribut přidá posuvník do <xref:System.Windows.Controls.TextBox> , aby bylo možné obsah ovládacího panelu Procházet, <xref:System.Windows.Controls.TextBox> Pokud se <xref:System.Windows.Controls.TextBox> rozšíří nad rámec velikosti rámce nebo okna, které ho obklopuje.  
  
 Další informace o různých úlohách spojených s použitím nástroje najdete <xref:System.Windows.Controls.TextBox> v tématu [Postupy: témata](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>Rozpoznat změnu obsahu  
 Obvykle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> by se měla tato událost použít k detekci pokaždé, když se <xref:System.Windows.Controls.TextBox> změní text, a <xref:System.Windows.Controls.RichTextBox> pak jako byste <xref:System.Windows.UIElement.KeyDown> očekávali. Příklad naleznete v tématu [zjištění, kdy byl text v textovém poli změněn](how-to-detect-when-text-in-a-textbox-has-changed.md) .  
  
## <a name="see-also"></a>Viz také

- [– postupy](textbox-how-to-topics.md)
- [RichTextBox – přehled](richtextbox-overview.md)
