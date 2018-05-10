---
title: Přístup k nevystaveným členům v modelu spravovaného objektu dokumentu HTML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: d2fbccfb3ecd7716420ca951e86f728798d25258
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Přístup k nevystaveným členům v modelu spravovaného objektu dokumentu HTML
Spravované HTML modelu DOM (Document Object) obsahuje třídu s názvem <xref:System.Windows.Forms.HtmlElement> která zveřejňuje vlastnosti, metod a události, které mají společnou všechny elementy HTML. V některých případech ale potřebujete pro přístup k členy, kteří použití spravovaného rozhraní nevystavuje přímo. Toto téma popisuje dva způsoby pro přístup k nevystaveným členům, včetně [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] a VBScript funkcí definovaných v rámci webové stránky.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Přístup k Nevystaveným členům prostřednictvím spravovaného rozhraní  
 <xref:System.Windows.Forms.HtmlDocument> a <xref:System.Windows.Forms.HtmlElement> poskytují čtyři metody, které umožňují přístup k nevystaveným členům. Následující tabulka uvádí typy a jejich odpovídající metody.  
  
|Typ členu|Metodu nebo metody|  
|-----------------|-----------------|  
|Vlastnosti (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Metody|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Události (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Události (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Události (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Při použití těchto metod se předpokládá, že máte element správné základní typ. Předpokládejme, že chcete pro naslouchání na `Submit` události `FORM` elementu na HTML stránky, aby mohli provést některé předběžné zpracování na `FORM`na hodnoty předtím, než je uživatel odešle na server. V ideálním případě Pokud budete mít kontrolu nad HTML, můžete nadefinovat `FORM` tak, aby měl jedinečnou `ID` atribut.  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 Po načtení této stránky do <xref:System.Windows.Forms.WebBrowser> ovládací prvek, můžete použít <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> metoda pro načtení `FORM` za běhu pomocí `form1` jako argument.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Přístup k nespravovaná rozhraní  
 Můžete také přístup k nevystaveným členům v spravovaný model HTML DOM pomocí rozhraní nespravované modelu COM (Component Object) vystavené každé třídy modelu DOM. Tato možnost se doporučuje Pokud máte několik volání proti nevystaveným členům, nebo pokud nevystaveným členům vrátit dalších nespravované rozhraní, které nejsou zabalené službou spravované HTML DOM  
  
 Následující tabulka uvádí všechna nespravované rozhraní vystavenou přes spravované HTML DOM Klikněte na další informace o jeho využití a například kód každého odkazu.  
  
|Typ|Nespravovaná rozhraní|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 Nejjednodušší způsob, jak používat rozhraní COM je přidat odkaz na knihovnu nespravované modelu DOM jazyka HTML (MSHTML.dll) z vaší aplikace, i když to není podporován. Další informace najdete v tématu [934368 článek znalostní báze Knowledge Base](http://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>Přístup k funkce skriptu  
 Na stránce HTML můžete definovat jednu nebo více funkcí pomocí skriptovací jazyk [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] nebo VBScript. Tyto funkce jsou umístěny uvnitř `SCRIPT` stránky na stránce a dá se spouštět na vyžádání nebo v reakci na události na modelu DOM.  
  
 Je možné volat jakékoli funkce skriptu definujete v stránky HTML pomocí <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metoda. Pokud metoda skript vrátí HTML element, můžete použít přetypování převést tento návratový výsledek, který má <xref:System.Windows.Forms.HtmlElement>. Příklad kódu a podrobnosti najdete v tématu <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Použití spravovaného modelu DOM (Document Object Model) HTML](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
