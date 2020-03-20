---
title: TextBox – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 9fbae5ac4de4c78a1086bcbd9bfc9e01eb597fb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186646"
---
# <a name="textbox-overview"></a>TextBox – přehled
Třída <xref:System.Windows.Controls.TextBox> umožňuje zobrazit nebo upravit neformátovaný text. Běžné použití a <xref:System.Windows.Controls.TextBox> je úprava neformátovaného textu ve formuláři. Například formulář s žádostí o jméno uživatele, telefonní <xref:System.Windows.Controls.TextBox> číslo atd. Toto téma <xref:System.Windows.Controls.TextBox> představuje třídu a poskytuje příklady, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jak ji používat v obou a C#.  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>Textové pole nebo pole RichTextBox?  
 Oba <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> a umožňují uživatelům zadávat text, ale dva ovládací prvky se používají pro různé scénáře. A <xref:System.Windows.Controls.TextBox> vyžaduje méně systémových prostředků, <xref:System.Windows.Controls.RichTextBox> pak je ideální, když je třeba upravit pouze prostý text (tj. použití ve formě). A <xref:System.Windows.Controls.RichTextBox> je lepší volbou, pokud je nutné, aby uživatel upravoval formátovaný text, obrázky, tabulky nebo jiný podporovaný obsah. Například úprava dokumentu, článku nebo blogu, který vyžaduje formátování, obrázků atd., je nejlépe provedena pomocí <xref:System.Windows.Controls.RichTextBox>. Níže uvedená tabulka shrnuje primární funkce <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBox>.  
  
|Řízení|Kontrola pravopisu v reálném čase|Místní nabídka|Příkazy pro formátování <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> jako (Ctr+B)|<xref:System.Windows.Documents.FlowDocument>obsah, jako jsou obrázky, odstavce, tabulky atd.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Ano|Ano|Ne|Ne.|  
|<xref:System.Windows.Controls.RichTextBox>|Ano|Ano|Ano (viz [Přehled richtextboxu)](richtextbox-overview.md)|Ano (viz [Přehled richtextboxu)](richtextbox-overview.md)|  
  
> [!NOTE]
> Přestože <xref:System.Windows.Controls.TextBox> nepodporuje formátování související úpravy <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> příkazy jako (Ctr + B), mnoho základních <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>příkazů jsou podporovány oba ovládací prvky, jako je například . Další informace naleznete v tématu <xref:System.Windows.Documents.EditingCommands>.  
  
 Funkce podporované <xref:System.Windows.Controls.TextBox> jsou uvedeny v následujících částech. Další informace <xref:System.Windows.Controls.RichTextBox>naleznete v tématu [Přehled richtextboxu](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Kontrola pravopisu v reálném čase  
 V a <xref:System.Windows.Controls.TextBox> nebo . <xref:System.Windows.Controls.RichTextBox> Když je kontrola pravopisu zapnutá, zobrazí se pod všemi chybně napsanými slovy červená čára (viz obrázek níže).  
  
 ![Textové okno s kontrolou&#45;pravopisu](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Informace [o povolení kontroly pravopisu v ovládacím prvku pro úpravy textu](how-to-enable-spell-checking-in-a-text-editing-control.md) najdete v tématu Povolení kontroly pravopisu v ovládacím prvku pro úpravy textu.  
  
### <a name="context-menu"></a>Místní nabídka  
 Ve výchozím <xref:System.Windows.Controls.TextBox> nastavení <xref:System.Windows.Controls.RichTextBox> oba a mají místní nabídku, která se zobrazí, když uživatel klepne pravým tlačítkem myši uvnitř ovládacího prvku. Místní nabídka umožňuje uživateli vyjmout, zkopírovat nebo vložit (viz obrázek níže).  
  
 ![Textové pole s místní nabídkou](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Můžete vytvořit vlastní kontextovou nabídku a přepsat tak výchozí chování. Další informace najdete [v tématu Použití vlastní kontextové nabídky s textovým polem.](how-to-use-a-custom-context-menu-with-a-textbox.md)  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>Vytváření textových polí  
 A <xref:System.Windows.Controls.TextBox> může být jedna čára na výšku nebo může obsahovat více řádků. Jeden řádek <xref:System.Windows.Controls.TextBox> je nejvhodnější pro vložení malého množství prostého textu (tj. "Jméno", "Telefonní číslo" atd. ve formuláři). Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.TextBox>jeden řádek .  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Můžete také vytvořit, <xref:System.Windows.Controls.TextBox> který umožňuje uživateli zadat více řádků textu. Pokud například formulář požádá o biografii uživatele, budete chtít použít <xref:System.Windows.Controls.TextBox> a, která podporuje více řádků textu. Následující příklad ukazuje, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jak použít <xref:System.Windows.Controls.TextBox> k definování ovládacího prvku, který se automaticky rozbalí tak, aby vyhovoval více řádkům textu.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Nastavení <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atributu `Wrap` způsobí, že text obtékat <xref:System.Windows.Controls.TextBox> na nový řádek při <xref:System.Windows.Controls.TextBox> dosažení okraje ovládacího prvku, automaticky rozbalí ovládací prvek zahrnout prostor pro nový řádek, v případě potřeby.  
  
 Nastavení <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atributu `true` způsobí, že nový řádek, který má být vložen při <xref:System.Windows.Controls.TextBox> stisknutí klávesy RETURN, opět automaticky rozbalí o prostor pro nový řádek, v případě potřeby.  
  
 Atribut <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> přidá posuvník <xref:System.Windows.Controls.TextBox>do aplikace , <xref:System.Windows.Controls.TextBox> takže obsah tohoto prvku <xref:System.Windows.Controls.TextBox> lze posouvat, pokud se rozšíří za velikost rámečku nebo okna, které jej obepínají.  
  
 Další informace o různých úkolech <xref:System.Windows.Controls.TextBox>spojených s používáním aplikace naleznete v [tématu Témata](textbox-how-to-topics.md)s postupy .  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>Zjistit, kdy se obsah změní  
 Obvykle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost by měla být použita <xref:System.Windows.Controls.TextBox> k <xref:System.Windows.Controls.RichTextBox> detekci <xref:System.Windows.UIElement.KeyDown> vždy, když text v nebo změny, spíše než, jak byste mohli očekávat. Viz [Zjistit, kdy se změnil text v textovém poli.](how-to-detect-when-text-in-a-textbox-has-changed.md)  
  
## <a name="see-also"></a>Viz také

- [Témata s postupy](textbox-how-to-topics.md)
- [RichTextBox – přehled](richtextbox-overview.md)
