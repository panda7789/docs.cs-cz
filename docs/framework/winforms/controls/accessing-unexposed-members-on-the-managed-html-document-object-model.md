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
ms.openlocfilehash: 525ef52ecbbc61fba787fa8286c56c638d837faf
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988393"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Přístup k nevystaveným členům v modelu spravovaného objektu dokumentu HTML
Managed HTML model DOM (Document Object Model) (DOM) obsahuje třídu s názvem <xref:System.Windows.Forms.HtmlElement> , která zveřejňuje vlastnosti, metody a události, které mají společné prvky HTML. Někdy ale budete potřebovat přístup ke členům, který spravované rozhraní nezveřejňuje přímo. Toto téma prověřuje dva způsoby přístupu k nevystaveným členům, včetně funkcí jazyka JScript a VBScript definovaných v rámci webové stránky.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Přístup k nevystaveným členům prostřednictvím spravovaných rozhraní  
 <xref:System.Windows.Forms.HtmlDocument>a <xref:System.Windows.Forms.HtmlElement> poskytují čtyři metody, které umožňují přístup k nevystaveným členům. V následující tabulce jsou uvedeny typy a jejich odpovídající metody.  
  
|Typ členu|Metoda (y)|  
|-----------------|-----------------|  
|Vlastnosti (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Metody|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Události (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Události (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Události (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Při použití těchto metod se předpokládá, že máte prvek správného základního typu. Předpokládejme, že chcete naslouchat `Submit` události `FORM` elementu na stránce HTML, aby bylo možné provést některé `FORM`předběžné zpracování hodnot na hodnotách, než je uživatel odešle na server. V ideálním případě, pokud máte kontrolu nad kódem HTML, byste definovali `FORM` , aby měl jedinečný `ID` atribut.  
  
```html  
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
  
 Po <xref:System.Windows.Forms.WebBrowser> načtení této stránky do ovládacího prvku lze <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> použít metodu pro načtení `FORM` za běhu pomocí `form1` jako argumentu.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Přístup k nespravovaným rozhraním  
 Můžete také přistupovat k nevystaveným členům ve spravovaném modelu HTML DOM pomocí nespravovaných rozhraní modelu COM (Component Object Model) vystavených každou třídou modelu DOM. To se doporučuje v případě, že je nutné provést několik volání proti nevystaveným členům nebo pokud nevystavené členy vrátí jiná nespravovaná rozhraní, která nejsou zabalena spravovaným modelem HTML DOM.  
  
 V následující tabulce jsou uvedena všechna nespravovaná rozhraní, která jsou vystavena prostřednictvím spravovaného modelu HTML DOM. Kliknutím na každý odkaz zobrazíte vysvětlení jeho použití, například kód.  
  
|type|Nespravované rozhraní|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 Nejjednodušší způsob, jak používat rozhraní COM, je přidat odkaz na nespravovanou HTML knihovnu HTML (MSHTML. dll) z vaší aplikace, i když to není podporováno. Další informace najdete v [článku 934368 znalostní báze](https://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>Přístup k funkcím skriptu  
 Stránka HTML může definovat jednu nebo více funkcí pomocí skriptovacího jazyka, jako je například JScript nebo VBScript. Tyto funkce jsou umístěny uvnitř `SCRIPT` stránky na stránce a lze je spustit na vyžádání nebo v reakci na událost v modelu DOM.  
  
 Můžete zavolat libovolné funkce skriptu, které definujete na stránce HTML pomocí <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metody. Pokud metoda skriptu vrátí prvek jazyka HTML, lze použít přetypování k převedení výsledku vrátí na <xref:System.Windows.Forms.HtmlElement>. Podrobnosti a příklady kódu naleznete v tématu <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Použití spravovaného modelu DOM (Document Object Model) HTML](using-the-managed-html-document-object-model.md)
