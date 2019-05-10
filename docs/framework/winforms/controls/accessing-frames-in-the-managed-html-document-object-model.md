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
ms.openlocfilehash: 9a02a912c170bfc4d997f1d8a0fe4f4d5bedb147
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665812"
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a>Přístup k rámcům v modelu spravovaného objektu dokumentu HTML
Některé dokumenty HTML se skládají z celkového počtu *snímků*, nebo windows, které může obsahovat vlastní odlišné dokumentů HTML. Pomocí snímků usnadňuje vytvoření stránky HTML, ve kterých zůstat statický, jako je například navigační panel, jeden nebo více kusů stránky, zatímco jiné rámce neustále měnit jejich obsah.  
  
 Autoři HTML můžete vytvořit snímky v jednom ze dvou způsobů:  
  
- Použití `FRAMESET` a `FRAME` značky, které vytvářejí oprava systému windows.  
  
 -nebo-  
  
- Použití `IFRAME` značky, který vytvoří okno s plovoucí desetinnou čárkou, které lze přesunout za běhu.  
  
1. Protože snímky obsahují dokumentů HTML, jsou reprezentovány v modelu Document Object Model (DOM) jako prvků a elementů rámce.  
  
2. Při přístupu `FRAME` nebo `IFRAME` značky pomocí shromažďování snímků <xref:System.Windows.Forms.HtmlWindow>, načítají okno prvek odpovídající rámce. Reprezentuje všechny rámce dynamických vlastností, jako je například aktuální adresy URL, dokumentů a velikost.  
  
3. Při přístupu `FRAME` nebo `IFRAME` značky pomocí <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> vlastnost <xref:System.Windows.Forms.HtmlWindow>, <xref:System.Windows.Forms.HtmlElement.Children%2A> kolekce nebo metod, jako <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> nebo <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, načítají elementu rámce. Reprezentuje statické vlastnosti rámce, včetně adresy URL zadané v původním souboru HTML.  
  
## <a name="frames-and-security"></a>Rámce a zabezpečení  
 Přístup k snímků je složité fakt, že spravovaný model HTML DOM implementuje bezpečnostní opatření, označované jako *mezi rámci skriptovací zabezpečení*. Pokud dokument obsahuje `FRAMESET` s dvěma nebo více `FRAME`s v různých doménách, tyto `FRAME`s nemůžou komunikovat mezi sebou. Jinými slovy `FRAME` , zobrazí obsah z webu nelze přístup k informacím o `FRAME` , který je hostitelem lokality třetích stran, jako `http://www.adatum.com/`. Se implementuje toto zabezpečení na úrovni <xref:System.Windows.Forms.HtmlWindow> třídy. Obecné informace můžete získat informace o `FRAME` hostování jiný web, jako je například její adresu URL, ale nelze získat přístup k jeho <xref:System.Windows.Forms.HtmlWindow.Document%2A> nebo změna velikosti či umístění jeho hostování `FRAME` nebo `IFRAME`.  
  
 Toto pravidlo platí také pro windows, které můžete otevřít pomocí <xref:System.Windows.Forms.HtmlWindow.Open%2A> a <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> metody. Pokud je okno otevření v jiné doméně než stránky hostované v <xref:System.Windows.Forms.WebBrowser> ovládacího prvku, nebudete moci přesunout okno nebo zkontrolovat jeho obsah. Tato omezení se vynucují také, pokud použijete <xref:System.Windows.Forms.WebBrowser> ovládací prvek pro zobrazení webové stránky, která se liší od webu použít k nasazení aplikace založené na formulářích Windows. Pokud používáte [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] technologie nasazení k instalaci aplikace z webu a použít <xref:System.Windows.Forms.WebBrowser> k zobrazení webu B, nebudete mít k datům přístup k webu B.  
  
## <a name="see-also"></a>Viz také:

- [\<rámec > – element](https://developer.mozilla.org/docs/Web/HTML/Element/frame)
- [Použití spravovaného modelu DOM (Document Object Model) HTML](using-the-managed-html-document-object-model.md)
