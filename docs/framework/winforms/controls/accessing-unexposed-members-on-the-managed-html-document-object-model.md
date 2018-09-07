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
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086800"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="2b9dd-102">Přístup k nevystaveným členům v modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="2b9dd-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="2b9dd-103">Spravované HTML Document Object Model (DOM) obsahuje třídu s názvem <xref:System.Windows.Forms.HtmlElement> , která zveřejňuje vlastnosti, metody a události, které mají společnou všechny prvky jazyka HTML.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="2b9dd-104">V některých případech však můžete potřebovat pro přístup ke členům, které použití spravovaného rozhraní nevystavuje přímo.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="2b9dd-105">Toto téma popisuje dva způsoby, jak přístup k nevystaveným členům, včetně [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] a VBScript funkce definované uvnitř na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-105">This topic examines two ways for accessing unexposed members, including [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="2b9dd-106">Přístup k Nevystaveným členům prostřednictvím spravovaného rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b9dd-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="2b9dd-107"><xref:System.Windows.Forms.HtmlDocument> a <xref:System.Windows.Forms.HtmlElement> poskytují čtyři metody, které umožňují přístup k nevystaveným členům.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="2b9dd-108">V následující tabulce jsou uvedeny typy a jejich odpovídající metody.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="2b9dd-109">Typ členu</span><span class="sxs-lookup"><span data-stu-id="2b9dd-109">Member Type</span></span>|<span data-ttu-id="2b9dd-110">Metody</span><span class="sxs-lookup"><span data-stu-id="2b9dd-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2b9dd-111">Vlastnosti (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="2b9dd-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="2b9dd-112">Metody</span><span class="sxs-lookup"><span data-stu-id="2b9dd-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="2b9dd-113">Události (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="2b9dd-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="2b9dd-114">Události (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="2b9dd-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="2b9dd-115">Události (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="2b9dd-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="2b9dd-116">Při použití těchto metod se předpokládá, že máte element správného základního typu.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="2b9dd-117">Předpokládejme, že chcete naslouchat `Submit` události `FORM` elementu na HTML stránky tak, aby bylo možné provádět některé úkony předběžného zpracování na `FORM`od hodnoty předtím, než je uživatel odešle na server.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="2b9dd-118">V ideálním případě máte kontrolu nad HTML můžete nadefinovat `FORM` mít jedinečnou `ID` atribut.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
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
  
 <span data-ttu-id="2b9dd-119">Po načtení tuto stránku do <xref:System.Windows.Forms.WebBrowser> ovládacího prvku, lze použít <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> metodu pro načtení `FORM` za běhu pomocí `form1` jako argument.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="2b9dd-120">Přístup k nespravovaná rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b9dd-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="2b9dd-121">Můžete také přístup k nevystaveným členům v spravovaný model HTML DOM pomocí nespravovaná rozhraní modelu COM (Component Object) vystavené každou třídu modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="2b9dd-122">To se doporučuje, pokud je nutné provést několik volání proti nevystaveným členům, nebo pokud nevystaveným členům jiné nespravovaná rozhraní, které nejsou zabalené službou spravované HTML DOM</span><span class="sxs-lookup"><span data-stu-id="2b9dd-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="2b9dd-123">Následující tabulka uvádí všechny nespravovaná rozhraní, které jsou vystaveny prostřednictvím spravované HTML DOM</span><span class="sxs-lookup"><span data-stu-id="2b9dd-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="2b9dd-124">Klikněte na každý odkaz pro jeho použití a příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="2b9dd-125">Typ</span><span class="sxs-lookup"><span data-stu-id="2b9dd-125">Type</span></span>|<span data-ttu-id="2b9dd-126">Nespravovaná rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b9dd-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="2b9dd-127">Nejjednodušší způsob, jak použít rozhraní modelu COM je přidat odkaz na nespravované knihovny HTML DOM (MSHTML.dll) z vašich aplikací, i když to není podporováno.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="2b9dd-128">Další informace najdete v tématu [934368 článku znalostní báze](https://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="2b9dd-128">For more information, see [Knowledge Base Article 934368](https://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="2b9dd-129">Přístup k funkce skriptu</span><span class="sxs-lookup"><span data-stu-id="2b9dd-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="2b9dd-130">Stránku HTML můžete definovat jeden nebo více funkcí pomocí skriptovacího jazyka, jako [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] nebo VBScript.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-130">An HTML page can define one or more functions by using a scripting language such as [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] or VBScript.</span></span> <span data-ttu-id="2b9dd-131">Tyto funkce jsou umístěny uvnitř `SCRIPT` stránky na stránce a lze je spustit na vyžádání nebo v reakci na události v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="2b9dd-132">Je možné volat jakékoli funkce skriptu definujete ve stránce HTML pomocí <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="2b9dd-133">Pokud metoda skript vrátí HTML element, můžete použít přetypování pro převod tento návratový výsledek <xref:System.Windows.Forms.HtmlElement>.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="2b9dd-134">Podrobnosti a příklady kódu naleznete v tématu <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span><span class="sxs-lookup"><span data-stu-id="2b9dd-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b9dd-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b9dd-135">See Also</span></span>  
 [<span data-ttu-id="2b9dd-136">Použití spravovaného modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="2b9dd-136">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
