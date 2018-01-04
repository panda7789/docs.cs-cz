---
title: "RichTextBox – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e88afe5f9c35448b3234498af413500bee163abc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="richtextbox-overview"></a>RichTextBox – přehled
<xref:System.Windows.Controls.RichTextBox> Řízení umožňuje zobrazit nebo upravit obsah toku, včetně odstavců, obrázky, tabulky a další. Toto téma představuje <xref:System.Windows.Controls.TextBox> třídy a obsahuje příklady použití v obou [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)].  
  
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>Textové pole nebo RichTextBox?  
 Obě <xref:System.Windows.Controls.RichTextBox> a <xref:System.Windows.Controls.TextBox> umožňuje uživatelům upravovat text, ale dvou ovládacích prvků se používají v různých scénářích. A <xref:System.Windows.Controls.RichTextBox> je vhodnější, když je to nutné pro uživatele, který chcete upravit formátovaný text, obrázky, tabulky nebo další složitý obsah. Například úpravy dokumentu, článek nebo blogu, který vyžaduje formátování, Image, atd se nejlépe provádí pomocí <xref:System.Windows.Controls.RichTextBox>. A <xref:System.Windows.Controls.TextBox> vyžaduje méně systémových prostředků pak <xref:System.Windows.Controls.RichTextBox> a je ideální při jenom prostý text, musí být upravit (tj. využití ve formulářích). V tématu [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md) Další informace o <xref:System.Windows.Controls.TextBox>. Následující tabulka shrnuje hlavní funkce <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox>.  
  
|Ovládací prvek|Kontrola pravopisu v reálném čase|Kontextové nabídky|Formátování příkazy, jako je <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (pev.cenu + B)|<xref:System.Windows.Documents.FlowDocument>obsah, jako jsou bitové kopie, odstavců, tabulek atd.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Ano|Ano|Ne|Ne.|  
|<xref:System.Windows.Controls.RichTextBox>|Ano|Ano|Ano|Ano|  
  
 **Poznámka:** i když <xref:System.Windows.Controls.TextBox> nepodporuje formátování související příkazy, jako je <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (pev.cenu + B), mnoho základních příkazů podporuje obě ovládací prvky, jako <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.  
  
 Funkce z výše uvedené tabulce jsou podrobněji popsané později.  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>Vytváření RichTextBox  
 Následující kód ukazuje, jak vytvořit <xref:System.Windows.Controls.RichTextBox> smí uživatel upravovat bohaté obsah.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 Konkrétně v upravovat obsah <xref:System.Windows.Controls.RichTextBox> je obsah toku. Tok obsahu může obsahovat mnoho typů elementů včetně formátovaný text, obrázky, seznamy a tabulky. V tématu [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md) pro podrobných informací v dokumentech toku. Chcete-li obsahovat obsah toku, <xref:System.Windows.Controls.RichTextBox> hostitelů <xref:System.Windows.Documents.FlowDocument> objekt, který obsahuje upravovat obsah. K předvedení tok obsahu <xref:System.Windows.Controls.RichTextBox>, následující kód ukazuje, jak vytvořit <xref:System.Windows.Controls.RichTextBox> s odstavec a text uveden tučně.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 Následující obrázek znázorňuje, jak tato ukázka vykreslí.  
  
 ![RichTextBox s obsahem](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 Elementy <xref:System.Windows.Documents.Paragraph> a <xref:System.Windows.Documents.Bold> určit, jak obsahu uvnitř <xref:System.Windows.Controls.RichTextBox> se zobrazí. Jako uživatel upravuje <xref:System.Windows.Controls.RichTextBox> obsah, se změní, tento obsah toku. Další informace o funkcích tok obsahu a jak pracovat s ním najdete v tématu [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 **Poznámka:** toku obsahu uvnitř <xref:System.Windows.Controls.RichTextBox> není chovat úplně stejně jako obsah toku, které jsou obsažené v jiných ovládacích prvků. Například neexistují žádné sloupce v <xref:System.Windows.Controls.RichTextBox> a proto žádné Automatická změna velikosti chování. Navíc vestavěné funkce, jako je vyhledávání, zobrazování režimu, navigaci na stránce a přiblížení nejsou k dispozici v rámci <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>Kontrola pravopisu v reálném čase  
 Můžete povolit v reálném čase kontrolu pravopisu <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox>. Když je kontrola pravopisu zapnuté, red řádek se zobrazí pod všechny překlepu slova (viz následující obrázek).  
  
 ![Textové pole s pravopisu & č. 45; kontrola](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 V tématu [povolit kontrolu pravopisu v ovládacím prvku úpravy textu](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md) se dozvíte, jak povolit kontrola pravopisu.  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>Kontextové nabídky  
 Ve výchozím nastavení obě <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> mít z kontextové nabídky, která se zobrazí, když uživatel klikne pravým tlačítkem myši v ovládacím prvku. V místní nabídce umožňuje uživateli vyjmout, kopírovat nebo vložit (viz obrázek níže).  
  
 ![Textové pole s kontextovou nabídku](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Můžete vytvořit vlastní vlastní kontextovou nabídku přepsat výchozí nastavení. V tématu [umístit vlastní Kontextová nabídka v RichTextBox](../../../../docs/framework/wpf/controls/how-to-position-a-custom-context-menu-in-a-richtextbox.md) Další informace.  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>Úprava příkazů  
 Úprava příkazů umožňuje uživatelům upravovat obsah ve formátu <xref:System.Windows.Controls.RichTextBox>. Kromě toho basic úpravy příkazy, <xref:System.Windows.Controls.RichTextBox> obsahuje příkazy formátování, které <xref:System.Windows.Controls.TextBox> nepodporuje. Například při provádění úprav v <xref:System.Windows.Controls.RichTextBox>, uživatel může stiskněte pev.cenu + B k přepnutí formátování tučně. V tématu <xref:System.Windows.Documents.EditingCommands> úplný seznam příkazů, které jsou k dispozici. Kromě používání klávesových zkratek, můžete napojit příkazy až další ovládací prvky jako tlačítka. Následující příklad ukazuje, jak vytvořit jednoduchý nástroj panelu obsahující tlačítka, která uživatele můžete použít ke změně formátování textu.  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 Následující obrázek znázorňuje, jak tato ukázka zobrazuje.  
  
 ![RichTextBox s panelem nástrojů](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Rozpoznat, kdy se změní obsah  
 Obvykle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost se má použít k detekci vždy, když text v <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox> místo poté změní <xref:System.Windows.UIElement.KeyDown> podle očekávání. V tématu [zjistit při textu v textového pole došlo ke změně](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md) příklad.  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>Uložení, načtení a tisk obsahu RichTextBox  
 Následující příklad ukazuje, jak uložit obsah <xref:System.Windows.Controls.RichTextBox> do souboru, načíst tento obsah zpět do <xref:System.Windows.Controls.RichTextBox>a tisknout obsah. Níže je kód pro tento příklad.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 Níže je pro tento příklad kódu.  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Témata s postupy](../../../../docs/framework/wpf/controls/richtextbox-how-to-topics.md)  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)
