---
title: "Přístup k nevystaveným členům v modelu spravovaného objektu dokumentu HTML"
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
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dda2581ceed854fa5121076f0c7b9df414bffe52
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="73fb4-102">Přístup k nevystaveným členům v modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="73fb4-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="73fb4-103">Spravované HTML modelu DOM (Document Object) obsahuje třídu s názvem <xref:System.Windows.Forms.HtmlElement> která zveřejňuje vlastnosti, metod a události, které mají společnou všechny elementy HTML.</span><span class="sxs-lookup"><span data-stu-id="73fb4-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="73fb4-104">V některých případech ale potřebujete pro přístup k členy, kteří použití spravovaného rozhraní nevystavuje přímo.</span><span class="sxs-lookup"><span data-stu-id="73fb4-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="73fb4-105">Toto téma popisuje dva způsoby pro přístup k nevystaveným členům, včetně [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] a VBScript funkcí definovaných v rámci webové stránky.</span><span class="sxs-lookup"><span data-stu-id="73fb4-105">This topic examines two ways for accessing unexposed members, including [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="73fb4-106">Přístup k Nevystaveným členům prostřednictvím spravovaného rozhraní</span><span class="sxs-lookup"><span data-stu-id="73fb4-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="73fb4-107"><xref:System.Windows.Forms.HtmlDocument>a <xref:System.Windows.Forms.HtmlElement> poskytují čtyři metody, které umožňují přístup k nevystaveným členům.</span><span class="sxs-lookup"><span data-stu-id="73fb4-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="73fb4-108">Následující tabulka uvádí typy a jejich odpovídající metody.</span><span class="sxs-lookup"><span data-stu-id="73fb4-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="73fb4-109">Typ členu</span><span class="sxs-lookup"><span data-stu-id="73fb4-109">Member Type</span></span>|<span data-ttu-id="73fb4-110">Metodu nebo metody</span><span class="sxs-lookup"><span data-stu-id="73fb4-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="73fb4-111">Vlastnosti (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="73fb4-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="73fb4-112">Metody</span><span class="sxs-lookup"><span data-stu-id="73fb4-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="73fb4-113">Události (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="73fb4-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="73fb4-114">Události (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="73fb4-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="73fb4-115">Události (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="73fb4-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="73fb4-116">Při použití těchto metod se předpokládá, že máte element správné základní typ.</span><span class="sxs-lookup"><span data-stu-id="73fb4-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="73fb4-117">Předpokládejme, že chcete pro naslouchání na `Submit` události `FORM` elementu na HTML stránky, aby mohli provést některé předběžné zpracování na `FORM`na hodnoty předtím, než je uživatel odešle na server.</span><span class="sxs-lookup"><span data-stu-id="73fb4-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="73fb4-118">V ideálním případě Pokud budete mít kontrolu nad HTML, můžete nadefinovat `FORM` tak, aby měl jedinečnou `ID` atribut.</span><span class="sxs-lookup"><span data-stu-id="73fb4-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
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
  
 <span data-ttu-id="73fb4-119">Po načtení této stránky do <xref:System.Windows.Forms.WebBrowser> ovládací prvek, můžete použít <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> metoda pro načtení `FORM` za běhu pomocí `form1` jako argument.</span><span class="sxs-lookup"><span data-stu-id="73fb4-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="73fb4-120">Přístup k nespravovaná rozhraní</span><span class="sxs-lookup"><span data-stu-id="73fb4-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="73fb4-121">Můžete také přístup k nevystaveným členům v spravovaný model HTML DOM pomocí rozhraní nespravované modelu COM (Component Object) vystavené každé třídy modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="73fb4-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="73fb4-122">Tato možnost se doporučuje Pokud máte několik volání proti nevystaveným členům, nebo pokud nevystaveným členům vrátit dalších nespravované rozhraní, které nejsou zabalené službou spravované HTML DOM</span><span class="sxs-lookup"><span data-stu-id="73fb4-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="73fb4-123">Následující tabulka uvádí všechna nespravované rozhraní vystavenou přes spravované HTML DOM</span><span class="sxs-lookup"><span data-stu-id="73fb4-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="73fb4-124">Klikněte na další informace o jeho využití a například kód každého odkazu.</span><span class="sxs-lookup"><span data-stu-id="73fb4-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="73fb4-125">Typ</span><span class="sxs-lookup"><span data-stu-id="73fb4-125">Type</span></span>|<span data-ttu-id="73fb4-126">Nespravovaná rozhraní</span><span class="sxs-lookup"><span data-stu-id="73fb4-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="73fb4-127">Nejjednodušší způsob, jak používat rozhraní COM je přidat odkaz na knihovnu nespravované modelu DOM jazyka HTML (MSHTML.dll) z vaší aplikace, i když to není podporován.</span><span class="sxs-lookup"><span data-stu-id="73fb4-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="73fb4-128">Další informace najdete v tématu [934368 článek znalostní báze Knowledge Base](http://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="73fb4-128">For more information, see [Knowledge Base Article 934368](http://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="73fb4-129">Přístup k funkce skriptu</span><span class="sxs-lookup"><span data-stu-id="73fb4-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="73fb4-130">Na stránce HTML můžete definovat jednu nebo více funkcí pomocí skriptovací jazyk [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] nebo VBScript.</span><span class="sxs-lookup"><span data-stu-id="73fb4-130">An HTML page can define one or more functions by using a scripting language such as [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] or VBScript.</span></span> <span data-ttu-id="73fb4-131">Tyto funkce jsou umístěny uvnitř `SCRIPT` stránky na stránce a dá se spouštět na vyžádání nebo v reakci na události na modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="73fb4-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="73fb4-132">Je možné volat jakékoli funkce skriptu definujete v stránky HTML pomocí <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="73fb4-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="73fb4-133">Pokud metoda skript vrátí HTML element, můžete použít přetypování převést tento návratový výsledek, který má <xref:System.Windows.Forms.HtmlElement>.</span><span class="sxs-lookup"><span data-stu-id="73fb4-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="73fb4-134">Příklad kódu a podrobnosti najdete v tématu <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span><span class="sxs-lookup"><span data-stu-id="73fb4-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fb4-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="73fb4-135">See Also</span></span>  
 [<span data-ttu-id="73fb4-136">Pomocí modelu objektu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="73fb4-136">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
