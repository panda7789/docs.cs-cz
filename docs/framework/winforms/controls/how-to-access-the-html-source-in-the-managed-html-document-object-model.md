---
title: 'Postupy: Přístup ke zdroji HTML ve spravovaném objektu modelu dokumentu HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: 49a50bdf5ea0f24d712458c739b7829ee73d157a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>Postupy: Přístup ke zdroji HTML ve spravovaném objektu modelu dokumentu HTML
<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> a <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnosti <xref:System.Windows.Forms.WebBrowser> řízení vrátit HTML aktuálního dokumentu, který existoval, když se napřed zobrazí. Nicméně pokud změníte stránce pomocí volání metod a vlastností, jako třeba <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> a <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, tyto změny se neprojeví při volání <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> a <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>. Pokud chcete získat nejaktuálnější zdrojový kód HTML pro modelu DOM, musí volat <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> vlastnost v elementu HTML.  
  
 Následující postup ukazuje, jak načíst zdroji dynamické a zobrazit ji v samostatné místní nabídky.  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>Načítání zdroji dynamické s vlastností OuterHtml  
  
1.  Vytvořte novou aplikaci Windows Forms. Spustit s jedním <xref:System.Windows.Forms.Form>a pojmenujte ji `Form1`.  
  
2.  Hostitel <xref:System.Windows.Forms.WebBrowser> řízení v aplikaci Windows Forms a pojmenujte ji `WebBrowser1`. Další informace najdete v tématu [postupy: přidání schopností webového prohlížeče do formulářové aplikace Windows](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).  
  
3.  Vytvořte druhý <xref:System.Windows.Forms.Form> ve vaší aplikaci s názvem `CodeForm`.  
  
4.  Přidat <xref:System.Windows.Forms.RichTextBox> řídit k `CodeForm` a nastavit jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost `Fill`.  
  
5.  Vytvoření veřejné vlastnosti na `CodeForm` názvem `Code`.  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  Přidat <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1` k vaší <xref:System.Windows.Forms.Form>a sledování <xref:System.Windows.Forms.Control.Click> událostí. Informace o sledování událostí najdete v tématu [události](../../../../docs/standard/events/index.md).  
  
7.  Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Vždy otestovat hodnotu <xref:System.Windows.Forms.WebBrowser.Document%2A> před pokusem o jeho načtení. Pokud není aktuální stránku dokončení načítání, <xref:System.Windows.Forms.WebBrowser.Document%2A> nebo jeden nebo více jeho podřízených objektů nemusí být inicializován.  
  
## <a name="see-also"></a>Viz také  
 [Použití spravovaného modelu DOM (Document Object Model) HTML](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)  
 [Přehled ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
