---
title: 'Postupy: Přístup k modelu spravovaného objektu dokumentu HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
ms.openlocfilehash: 2a195dc6583d5a0a72bd08b66f8933f4002e879a
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487277"
---
# <a name="how-to-access-the-managed-html-document-object-model"></a>Postupy: Přístup k modelu spravovaného objektu dokumentu HTML
Spravované HTML Document Object Model (DOM) se můžete dostat ze dvou typů aplikací:  
  
- Aplikace Windows Forms (.exe), která hostované spravovanou <xref:System.Windows.Forms.WebBrowser> ovládacího prvku. Tyto dvě technologie se navzájem doplňují, se <xref:System.Windows.Forms.WebBrowser> ovládací prvek zobrazující stránku uživateli a modelu DOM jazyka HTML představující logické struktury dokumentu.  
  
- Windows Forms <xref:System.Windows.Forms.UserControl> hostované v aplikaci Internet Explorer. Můžete přístup k modelu DOM jazyka HTML představující stránku, na kterém vaše <xref:System.Windows.Forms.UserControl> hostována, aby bylo možné změnit strukturu dokumentu nebo otevřete modálních dialogových oken, mezi mnoho dalších možností.  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>Pro přístup k modelu DOM z aplikace Windows Forms  
  
1. Hostitele <xref:System.Windows.Forms.WebBrowser> ovládací prvek v rámci vaší aplikace Windows Forms a monitorovat <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí. Podrobné informace o hostování ovládacích prvků a sledování událostí, naleznete v tématu [události](../../../standard/events/index.md).  
  
2. Načíst <xref:System.Windows.Forms.HtmlDocument> pro aktuální stránku díky přístupu <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnost <xref:System.Windows.Forms.WebBrowser> ovládacího prvku.  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>Pro přístup k modelu DOM z UserControl hostované v aplikaci Internet Explorer  
  
1. Vytvořte vlastní vlastní odvozenou třídu <xref:System.Windows.Forms.UserControl> třídy. Další informace najdete v tématu [jak: Vytváření složených ovládacích prvků](how-to-author-composite-controls.md).  
  
2. Umístěte následující kód uvnitř vaší obslužné rutiny události zatížení pro vaše <xref:System.Windows.Forms.UserControl>:  
  
 [!code-csharp[AccessHTMLDOMControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
1. Při použití modelu DOM prostřednictvím <xref:System.Windows.Forms.WebBrowser> ovládacího prvku, byste měli vždy počkat, až <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> dojde k události, než se pokusíte o přístup k <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnost <xref:System.Windows.Forms.WebBrowser> ovládacího prvku. <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Událost se vyvolá po načtení celého dokumentu; Pokud používáte modelu DOM té, riskujete způsobující výjimku za běhu ve vaší aplikaci.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
  
1. Vaše aplikace nebo <xref:System.Windows.Forms.UserControl> vyžaduje úplný vztah důvěryhodnosti pro přístup ke spravované HTML DOM Pokud nasazujete aplikace Windows Forms pomocí technologie ClickOnce, můžete požádat o zvýšení úrovně oprávnění nebo Trusted Application Deployment; úplný vztah důvěryhodnosti. Zobrazit [zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications) podrobnosti.  
  
## <a name="see-also"></a>Viz také:

- [Použití spravovaného modelu DOM (Document Object Model) HTML](using-the-managed-html-document-object-model.md)
