---
title: Přístup k rámcům v modelu spravovaného objektu dokumentu HTML
ms.date: 03/30/2017
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
ms.openlocfilehash: b48a93cef2ea8fd2d39f58d8f458c4b287a10154
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207505"
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a>Přístup k rámcům v modelu spravovaného objektu dokumentu HTML
Některé dokumentů HTML se skládají z *rámce*, nebo okna, která může pojmout své vlastní dokumenty odlišné HTML. Pomocí rámce usnadňuje vytvoření stránky HTML, ve kterých zůstat statický, jako je například navigační panel některé části stránky, zatímco jiné rámce neustále mění svůj obsah.  
  
 Autoři HTML můžete vytvořit rámce v jednom ze dvou způsobů:  
  
-   Pomocí `FRAMESET` a `FRAME` značky, které pak vytvoří pevné windows.  
  
 -nebo-  
  
-   Pomocí `IFRAME` značku, která vytvoří plovoucího okna, které můžete změnit jejich umístění v době běhu.  
  
1.  Protože snímky obsahují dokumenty ve formátu HTML, jsou reprezentovány jako prvků okna a rámce elementy v objektu modelu dokumentu (DOM).  
  
2.  Při přístupu `FRAME` nebo `IFRAME` značky pomocí kolekce rámce <xref:System.Windows.Forms.HtmlWindow>, jsou načítání prvku okno odpovídající rámečku. Reprezentuje všechny dynamických vlastností rámečku, například jeho aktuální adresu URL, dokumentů a velikost.  
  
3.  Při přístupu `FRAME` nebo `IFRAME` značky pomocí <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> vlastnost <xref:System.Windows.Forms.HtmlWindow>, <xref:System.Windows.Forms.HtmlElement.Children%2A> kolekce nebo metody, jako <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> nebo <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, jsou načítání rámce elementu. To představuje statické vlastnosti rámečku, včetně adresa URL zadaná v původní soubor HTML.  
  
## <a name="frames-and-security"></a>Rámce a zabezpečení  
 Přístup k rámce ztěžuje fakt, že spravovaný model HTML DOM implementuje bezpečnostní opatření známé jako *mezi rámci skriptování zabezpečení*. Pokud dokument obsahuje `FRAMESET` s dvěma nebo více `FRAME`s v různých doménách, tyto `FRAME`nemůžou komunikovat s sebou. Jinými slovy `FRAME` , zobrazí obsah webového serveru nelze přistupovat k informacím v `FRAME` , který hostuje server třetí strany, jako http://www.adatum.com/. Je implementována tato zabezpečení na úrovni <xref:System.Windows.Forms.HtmlWindow> třídy. Můžete získat obecné informace o `FRAME` hostování jiný web, jako je například jeho adresa URL, ale bude mít přístup k jeho <xref:System.Windows.Forms.HtmlWindow.Document%2A> nebo změna velikosti či umístění jeho hostování `FRAME` nebo `IFRAME`.  
  
 Toto pravidlo platí také pro windows, které můžete otevřít pomocí <xref:System.Windows.Forms.HtmlWindow.Open%2A> a <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> metody. Pokud je okno otevření v jiné doméně ze stránky hostované v <xref:System.Windows.Forms.WebBrowser> řízení, nebudete moct přesouvat toto okno a zkontrolujte jeho obsah. Tyto vynutí se omezení taky Pokud použijete <xref:System.Windows.Forms.WebBrowser> ovládací prvek zobrazí web, který se liší od webu použít k nasazení aplikace na základě formulářů Windows. Pokud používáte [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] použít technologii nasazení k instalaci aplikace z webu A a <xref:System.Windows.Forms.WebBrowser> zobrazíte webový server B, nebude možné k datům přístup k webu pro B.  
  
 Další informace o skriptování najdete v tématu [o skriptování mezi rámci a zabezpečení](http://msdn.microsoft.com/library/ms533028.aspx).  
  
## <a name="see-also"></a>Viz také  
 [Element rámce &#124; objekt s rámečkem](http://msdn.microsoft.com/library/ms535250.aspx)  
 [Použití spravovaného modelu DOM (Document Object Model) HTML](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
