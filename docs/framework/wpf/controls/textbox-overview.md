---
title: "TextBox – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1116093ddcd95c99deac8a1e1b14fef3b0a458f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="textbox-overview"></a>TextBox – přehled
<xref:System.Windows.Controls.TextBox> Vám umožňuje zobrazit nebo upravit neformátovaný text. Běžně se používají <xref:System.Windows.Controls.TextBox> upravuje neformátovaný text ve formuláři. Například formulář žádostí o uživatelské jméno, telefonní číslo atd využije <xref:System.Windows.Controls.TextBox> ovládací prvky pro zadávání textu. Toto téma představuje <xref:System.Windows.Controls.TextBox> třídy a obsahuje příklady použití v obou [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)].  
  
 
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>Textové pole nebo RichTextBox?  
 Obě <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> povolit uživatelům zadejte text, ale používají se dvou ovládacích prvků pro různé scénáře. A <xref:System.Windows.Controls.TextBox> vyžaduje méně systémových prostředků pak <xref:System.Windows.Controls.RichTextBox> tak, aby byl ideální, když je potřeba upravit pouze ve formátu prostého textu (tj. využití ve formuláři). A <xref:System.Windows.Controls.RichTextBox> je lepší volbou, pokud je nutné, aby uživatelům upravit formátovaný text, obrázky, tabulky nebo jiné podporované obsahu. Například úpravy dokumentu, článek nebo blogu, který vyžaduje formátování, Image, atd se nejlépe provádí pomocí <xref:System.Windows.Controls.RichTextBox>. Následující tabulka shrnuje primární funkce <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBox>.  
  
|Ovládací prvek|Kontrola pravopisu v reálném čase|Kontextové nabídky|Formátování příkazy, jako je <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (pev.cenu + B)|<xref:System.Windows.Documents.FlowDocument>obsah, jako jsou bitové kopie, odstavců, tabulek atd.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Ano|Ano|Ne|Ne.|  
|<xref:System.Windows.Controls.RichTextBox>|Ano|Ano|Ano (viz [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md))|Ano (viz [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md))|  
  
> [!NOTE]
>  I když <xref:System.Windows.Controls.TextBox> nemá nepodporuje formátování související úpravy příkazy jako <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (pev.cenu + B), mnoho základních příkazů podporuje obě ovládací prvky, jako <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>. Další informace naleznete v tématu <xref:System.Windows.Documents.EditingCommands>.  
  
 Nepodporované funkce <xref:System.Windows.Controls.TextBox> jsou popsané v následujících částech. Další informace o <xref:System.Windows.Controls.RichTextBox>, najdete v části [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Kontrola pravopisu v reálném čase  
 Můžete povolit v reálném čase kontrola pravopisu v <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox>. Když je kontrola pravopisu zapnuté, red řádek se zobrazí pod všechny překlepu slova (viz následující obrázek).  
  
 ![Textové pole s pravopisu & č. 45; kontrola](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 V tématu [povolit kontrolu pravopisu v ovládacím prvku úpravy textu](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md) se dozvíte, jak povolit kontrola pravopisu.  
  
### <a name="context-menu"></a>Kontextové nabídky  
 Ve výchozím nastavení obě <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> mít z kontextové nabídky, která se zobrazí, když uživatel klikne pravým tlačítkem myši v ovládacím prvku. V místní nabídce umožňuje uživateli vyjmout, kopírovat nebo vložit (viz následující obrázek).  
  
 ![Textové pole s kontextovou nabídku](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Můžete vytvořit vlastní vlastní kontextovou nabídku přepsat výchozí chování. V tématu [pomocí textové pole z kontextové nabídky vlastní](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md) Další informace.  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Vytváření textová pole  
 A <xref:System.Windows.Controls.TextBox> může být jeden řádek na výšku nebo tvoří více řádků. Jeden řádek <xref:System.Windows.Controls.TextBox> je nejvhodnější pro vložení malé množství ve formátu prostého textu (tj.) "Název", "Telefonní číslo", atd. ve formuláři). Následující příklad ukazuje, jak vytvořit jeden řádek <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Můžete také vytvořit <xref:System.Windows.Controls.TextBox> umožňuje uživateli zadat více řádků textu. Například pokud se zobrazí dotaz svého formuláře pro osobních nákresu uživatele, by chcete použít <xref:System.Windows.Controls.TextBox> , která podporuje více řádků textu. Následující příklad ukazuje, jak používat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k definování <xref:System.Windows.Controls.TextBox> ovládací prvek, který automaticky přizpůsobí více řádků textu.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Nastavení <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atribut `Wrap` způsobí, že text jej do nového řádku při okraji <xref:System.Windows.Controls.TextBox> ovládací prvek je dosaženo, automaticky se zvětšující <xref:System.Windows.Controls.TextBox> řízení v případě potřeby zadejte místo pro nový řádek.  
  
 Nastavení <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atribut `true` způsobí, že má být vložen při stisknutí klávesy NÁVRATOVÝ, znovu automaticky rozšiřování nový řádek <xref:System.Windows.Controls.TextBox> zahrnout prostor pro nový řádek, v případě potřeby.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Přidá posuvníku do atribut <xref:System.Windows.Controls.TextBox>tak, aby obsah <xref:System.Windows.Controls.TextBox> posunout prostřednictvím Pokud <xref:System.Windows.Controls.TextBox> rozšíří překračuje velikost rámce nebo v okně, která obklopuje ho.  
  
 Další informace o různé úlohy související s používáním <xref:System.Windows.Controls.TextBox>, najdete v části [postupy](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Rozpoznat, kdy se změní obsah  
 Obvykle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost se má použít k detekci vždy, když text v <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox> změní, místo pak <xref:System.Windows.UIElement.KeyDown> podle očekávání. V tématu [zjistit při textu v textového pole došlo ke změně](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md) příklad.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: témata](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
