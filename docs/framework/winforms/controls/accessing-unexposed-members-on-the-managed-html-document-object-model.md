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
ms.openlocfilehash: 8767ef0fb484d43ffad4888affebb9d6bb74cc3a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384637"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Přístup k nevystaveným členům v modelu spravovaného objektu dokumentu HTML
Spravované HTML Document Object Model (DOM) obsahuje třídu s názvem <xref:System.Windows.Forms.HtmlElement> , která zveřejňuje vlastnosti, metody a události, které mají společnou všechny prvky jazyka HTML. V některých případech však můžete potřebovat pro přístup ke členům, které použití spravovaného rozhraní nevystavuje přímo. Toto téma popisuje dva způsoby, jak přístup k nevystaveným členům, včetně [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] a VBScript funkce definované uvnitř na webové stránce.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Přístup k Nevystaveným členům prostřednictvím spravovaného rozhraní  
 <xref:System.Windows.Forms.HtmlDocument> a <xref:System.Windows.Forms.HtmlElement> poskytují čtyři metody, které umožňují přístup k nevystaveným členům. V následující tabulce jsou uvedeny typy a jejich odpovídající metody.  
  
|Typ členu|Metody|  
|-----------------|-----------------|  
|Vlastnosti (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Metody|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Události (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Události (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Události (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Při použití těchto metod se předpokládá, že máte element správného základního typu. Předpokládejme, že chcete naslouchat `Submit` události `FORM` elementu na HTML stránky tak, aby bylo možné provádět některé úkony předběžného zpracování na `FORM`od hodnoty předtím, než je uživatel odešle na server. V ideálním případě máte kontrolu nad HTML můžete nadefinovat `FORM` mít jedinečnou `ID` atribut.  
  
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
  
 Po načtení tuto stránku do <xref:System.Windows.Forms.WebBrowser> ovládacího prvku, lze použít <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> metodu pro načtení `FORM` za běhu pomocí `form1` jako argument.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Přístup k nespravovaná rozhraní  
 Můžete také přístup k nevystaveným členům v spravovaný model HTML DOM pomocí nespravovaná rozhraní modelu COM (Component Object) vystavené každou třídu modelu DOM. To se doporučuje, pokud je nutné provést několik volání proti nevystaveným členům, nebo pokud nevystaveným členům jiné nespravovaná rozhraní, které nejsou zabalené službou spravované HTML DOM  
  
 Následující tabulka uvádí všechny nespravovaná rozhraní, které jsou vystaveny prostřednictvím spravované HTML DOM Klikněte na každý odkaz pro jeho použití a příklad kódu.  
  
|Typ|Nespravovaná rozhraní|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 Nejjednodušší způsob, jak použít rozhraní modelu COM je přidat odkaz na nespravované knihovny HTML DOM (MSHTML.dll) z vašich aplikací, i když to není podporováno. Další informace najdete v tématu [934368 článku znalostní báze](https://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>Přístup k funkce skriptu  
 Stránku HTML můžete definovat jeden nebo více funkcí pomocí skriptovacího jazyka, jako [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] nebo VBScript. Tyto funkce jsou umístěny uvnitř `SCRIPT` stránky na stránce a lze je spustit na vyžádání nebo v reakci na události v modelu DOM.  
  
 Je možné volat jakékoli funkce skriptu definujete ve stránce HTML pomocí <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metody. Pokud metoda skript vrátí HTML element, můžete použít přetypování pro převod tento návratový výsledek <xref:System.Windows.Forms.HtmlElement>. Podrobnosti a příklady kódu naleznete v tématu <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Použití spravovaného modelu DOM (Document Object Model) HTML](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
