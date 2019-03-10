---
title: 'Postupy: Přístup ke zdroji HTML v objektovém modelu spravovaného dokumentu HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: b9122e2c5bebdde2e04507973ccfeb924d0ad23e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723644"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>Postupy: Přístup ke zdroji HTML v objektovém modelu spravovaného dokumentu HTML
<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> a <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnosti <xref:System.Windows.Forms.WebBrowser> ovládací prvek vrátí kód HTML aktuálního dokumentu jako existovala při prvním zobrazení. Ale při úpravě stránky pomocí volání metody a vlastnosti, například <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> a <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, tyto změny se nezobrazí při volání <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> a <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>. Chcete-li získat nejnovější zdrojový kód HTML pro modelu DOM, musíte volat <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> vlastnosti elementu HTML.  
  
 Následující postup ukazuje, jak načíst dynamické zdroje a zobrazí v samostatném nabídku.  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>Načítání dynamické zdroje pomocí vlastnosti vnější HTML  
  
1.  Vytvoření nové aplikace Windows Forms. Začněte s jedním <xref:System.Windows.Forms.Form>a jeho volání `Form1`.  
  
2.  Hostitel <xref:System.Windows.Forms.WebBrowser> ovládací prvek v aplikaci Windows Forms a pojmenujte ho `WebBrowser1`. Další informace najdete v tématu [jak: Přidání schopností webového prohlížeče do formulářové aplikaci Windows](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).  
  
3.  Vytvořte druhý <xref:System.Windows.Forms.Form> ve vaší aplikaci s názvem `CodeForm`.  
  
4.  Přidat <xref:System.Windows.Forms.RichTextBox> mít pod kontrolou `CodeForm` a nastavte jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost `Fill`.  
  
5.  Vytvoření veřejné vlastnosti na `CodeForm` volá `Code`.  
  
     [!code-csharp[DisplayWebBrowserCode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  Přidat <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1` k vaší <xref:System.Windows.Forms.Form>a monitorovat <xref:System.Windows.Forms.Control.Click> událostí. Podrobnosti o sledování událostí najdete v tématu [události](../../../standard/events/index.md).  
  
7.  Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.  
  
     [!code-csharp[DisplayWebBrowserCode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Vždy testování hodnot <xref:System.Windows.Forms.WebBrowser.Document%2A> před pokusem o jeho načtení. Pokud není aktuální stránky dokončeno načítání, <xref:System.Windows.Forms.WebBrowser.Document%2A> nebo jeden nebo více jeho podřízených objektů nemusí být inicializovány.  
  
## <a name="see-also"></a>Viz také:
- [Použití spravovaného modelu DOM (Document Object Model) HTML](using-the-managed-html-document-object-model.md)
- [Přehled ovládacího prvku WebBrowser](webbrowser-control-overview.md)
