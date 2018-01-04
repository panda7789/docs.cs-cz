---
title: "Postupy: Přístup k modelu spravovaného objektu dokumentu HTML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83ee8c5e0cd578a0eb821a35a27c5ff0072e5533
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-the-managed-html-document-object-model"></a>Postupy: Přístup k modelu spravovaného objektu dokumentu HTML
Je dostupný spravované HTML modelu DOM (Document Object) na dva typy aplikací:  
  
-   Aplikace Windows Forms (.exe), který hostil spravovaný <xref:System.Windows.Forms.WebBrowser> ovládacího prvku. Tyto dvě technologie doplňují jiné, s <xref:System.Windows.Forms.WebBrowser> řízení zobrazení stránky uživateli a modelu DOM jazyka HTML představující logické struktury dokumentu.  
  
-   Windows Forms <xref:System.Windows.Forms.UserControl> hostovaným v rámci aplikace Internet Explorer. Můžete získat přístup k modelu DOM jazyka HTML představující stránku, na které vaši <xref:System.Windows.Forms.UserControl> je hostována, aby bylo možné změnit strukturu dokumentu nebo otevřete modálních dialogových oken, mezi mnoha dalších možností.  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>Pro přístup k modelu DOM z aplikace Windows Forms  
  
1.  Hostitele <xref:System.Windows.Forms.WebBrowser> v aplikaci Windows Forms řídit a monitorovat <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí. Podrobnosti o hostování ovládacích prvků a sledování událostí najdete v tématu [události](../../../../docs/standard/events/index.md).  
  
2.  Načtení <xref:System.Windows.Forms.HtmlDocument> pro aktuální stránku přímým přístupem <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnost <xref:System.Windows.Forms.WebBrowser> ovládacího prvku.  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>Pro přístup k modelu DOM z UserControl hostované v aplikaci Internet Explorer  
  
1.  Vytvoření vlastní vlastní třídy odvozené z <xref:System.Windows.Forms.UserControl> třídy. Další informace najdete v tématu [postupy: vytváření složených ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).  
  
2.  Vložte následující kód uvnitř vaší obslužné rutiny události zatížení pro vaše <xref:System.Windows.Forms.UserControl>:  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
1.  Při použití modelu DOM prostřednictvím <xref:System.Windows.Forms.WebBrowser> řízení, byste měli vždy počkat, dokud <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> události dojde před pokusem o přístup <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnost <xref:System.Windows.Forms.WebBrowser> ovládacího prvku. <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Událost se vyvolá po celý dokument načetl; Pokud chcete použít modelu DOM předtím, riskujete způsobí spuštění výjimka ve vaší aplikaci.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
  
1.  Aplikace nebo <xref:System.Windows.Forms.UserControl> bude vyžadovat úplný vztah důvěryhodnosti, aby měli přístup na spravované HTML DOM Pokud nasazujete aplikaci Windows Forms pomocí [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], můžete požádat o úplný vztah důvěryhodnosti pomocí zvýšení úrovně oprávnění nebo nasazení důvěryhodných aplikací, zjistit [zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications) podrobnosti.  
  
## <a name="see-also"></a>Viz také  
 [Použití spravovaného modelu DOM (Document Object Model) HTML](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
