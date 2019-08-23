---
title: TextBox – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 46600fd1a3023a80d49fae6f020279be6131916a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951490"
---
# <a name="textbox-overview"></a>TextBox – přehled
<xref:System.Windows.Controls.TextBox> Třída umožňuje zobrazit nebo upravit neformátovaný text. Běžné použití a <xref:System.Windows.Controls.TextBox> upravuje ve formuláři neformátovaný text. Například formulář žádající o jméno uživatele, telefonní číslo atd. by používal <xref:System.Windows.Controls.TextBox> ovládací prvky pro zadávání textu. Toto téma představuje <xref:System.Windows.Controls.TextBox> třídu a poskytuje příklady, jak ji použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] v a. C#  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>Textové pole nebo RichTextBox?  
 <xref:System.Windows.Controls.TextBox> A<xref:System.Windows.Controls.RichTextBox> umožňují uživatelům zadávat text, ale dva ovládací prvky se používají pro různé scénáře. Vyžaduje méně systémových prostředků <xref:System.Windows.Controls.RichTextBox> , takže je ideální, pokud je třeba upravit pouze prostý text (tj. využití ve formuláři). <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> Je lepší volbou, pokud je potřeba, aby uživatel mohl upravovat formátovaný text, obrázky, tabulky nebo jiný podporovaný obsah. Například úprava dokumentu, článku nebo blogu, který vyžaduje formátování, obrázky atd <xref:System.Windows.Controls.RichTextBox>., se nejlépe docílí pomocí. V následující tabulce najdete souhrn primárních funkcí <xref:System.Windows.Controls.TextBox> a. <xref:System.Windows.Controls.TextBox>  
  
|Control|Kontrola pravopisu v reálném čase|Kontextová nabídka|Formátování příkazů jako <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (centrum + B)|<xref:System.Windows.Documents.FlowDocument>obsah, jako jsou obrázky, odstavce, tabulky atd.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Ano|Ano|Ne|Ne.|  
|<xref:System.Windows.Controls.RichTextBox>|Ano|Ano|Ano (viz [Přehled RichTextBox](richtextbox-overview.md))|Ano (viz [Přehled RichTextBox](richtextbox-overview.md))|  
  
> [!NOTE]
> I <xref:System.Windows.Controls.TextBox> když nepodporuje formátování souvisejících příkazů pro úpravy jako <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (centrum + B), mnoho základních příkazů je podporováno v obou ovládacích prvcích, <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>jako je. Další informace naleznete v tématu <xref:System.Windows.Documents.EditingCommands>.  
  
 Funkce podporované nástrojem <xref:System.Windows.Controls.TextBox> jsou popsány v níže uvedených částech. Další informace o <xref:System.Windows.Controls.RichTextBox>naleznete v tématu [RichTextBox Overview](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Kontrola pravopisu v reálném čase  
 Můžete povolit kontrolu pravopisu v reálném čase v <xref:System.Windows.Controls.TextBox> nebo. <xref:System.Windows.Controls.RichTextBox> Když je kontrola pravopisu zapnutá, zobrazí se červená čára pod případnými nesprávně napsanými slovy (viz obrázek níže).  
  
 ![Textové pole s&#45;kontrolou pravopisu](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Informace o tom, jak povolit kontrolu pravopisu, najdete v tématu [Povolení kontroly pravopisu v ovládacím prvku pro úpravu textu](how-to-enable-spell-checking-in-a-text-editing-control.md) .  
  
### <a name="context-menu"></a>Kontextová nabídka  
 Ve výchozím nastavení má <xref:System.Windows.Controls.TextBox> obojí <xref:System.Windows.Controls.RichTextBox> i kontextovou nabídku, která se zobrazí, když uživatel klikne pravým tlačítkem myši uvnitř ovládacího prvku. Místní nabídka umožňuje uživateli vyjmutí, zkopírování nebo vložení (viz obrázek níže).  
  
 ![Textové pole s místní nabídkou](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Můžete vytvořit vlastní místní nabídku a přepsat tak výchozí chování. Další informace najdete v tématu [použití vlastní místní nabídky s](how-to-use-a-custom-context-menu-with-a-textbox.md) textovým polem.  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Vytváření textových polí  
 <xref:System.Windows.Controls.TextBox> Může být jeden řádek ve výšce nebo tvořený více řádky. Jeden řádek <xref:System.Windows.Controls.TextBox> je nejvhodnější pro vložení malých objemů prostého textu (tj. "Název", "telefonní číslo" atd. ve formuláři). Následující příklad ukazuje, jak vytvořit jeden řádek <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Můžete také vytvořit <xref:System.Windows.Controls.TextBox> , který umožňuje uživateli zadat více řádků textu. Například pokud váš formulář požádal o Biographical náčrta uživatele, budete chtít použít a <xref:System.Windows.Controls.TextBox> , který podporuje více řádků textu. Následující příklad ukazuje, jak použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k <xref:System.Windows.Controls.TextBox> definování ovládacího prvku, který se automaticky rozbalí, aby odpovídal více řádkům textu.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Nastavení atributu tak `Wrap` způsobí, že <xref:System.Windows.Controls.TextBox> při dosažení okraje ovládacího prvku se text zalomí na nový řádek a v případě potřeby automaticky rozšíří <xref:System.Windows.Controls.TextBox> ovládací prvek tak, aby zahrnoval místo pro nový řádek. <xref:System.Windows.Controls.TextBox.TextWrapping%2A>  
  
 Nastavením atributu tak `true` dojde k vložení nového řádku při stisknutí návratového klíče, <xref:System.Windows.Controls.TextBox> poté, co se znovu automaticky rozbalí, aby zahrnovalo místo pro nový řádek (v případě potřeby). <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>  
  
 Atribut přidá posuvník <xref:System.Windows.Controls.TextBox>do, aby bylo možné obsah ovládacího panelu <xref:System.Windows.Controls.TextBox> Procházet, pokud se <xref:System.Windows.Controls.TextBox> rozšíří nad rámec velikosti rámce nebo okna, které ho obklopuje. <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>  
  
 Další informace o různých úlohách spojených s použitím nástroje <xref:System.Windows.Controls.TextBox>najdete v tématu [Postupy: témata](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Rozpoznat změnu obsahu  
 Obvykle by <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se měla tato událost použít k detekci pokaždé, <xref:System.Windows.Controls.TextBox> když <xref:System.Windows.Controls.RichTextBox> se změní text, <xref:System.Windows.UIElement.KeyDown> a pak jako byste očekávali. Příklad naleznete v tématu [zjištění, kdy byl text v textovém poli změněn](how-to-detect-when-text-in-a-textbox-has-changed.md) .  
  
## <a name="see-also"></a>Viz také:

- [Témata s postupy](textbox-how-to-topics.md)
- [RichTextBox – přehled](richtextbox-overview.md)
