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
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="74cdb-102">Přístup k nevystaveným členům v modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="74cdb-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="74cdb-103">Managed HTML model DOM (Document Object Model) (DOM) obsahuje třídu s názvem <xref:System.Windows.Forms.HtmlElement> , která zveřejňuje vlastnosti, metody a události, které mají společné prvky HTML.</span><span class="sxs-lookup"><span data-stu-id="74cdb-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="74cdb-104">Někdy ale budete potřebovat přístup ke členům, který spravované rozhraní nezveřejňuje přímo.</span><span class="sxs-lookup"><span data-stu-id="74cdb-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="74cdb-105">Toto téma prověřuje dva způsoby přístupu k nevystaveným členům, včetně funkcí jazyka JScript a VBScript definovaných v rámci webové stránky.</span><span class="sxs-lookup"><span data-stu-id="74cdb-105">This topic examines two ways for accessing unexposed members, including JScript and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="74cdb-106">Přístup k nevystaveným členům prostřednictvím spravovaných rozhraní</span><span class="sxs-lookup"><span data-stu-id="74cdb-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="74cdb-107"><xref:System.Windows.Forms.HtmlDocument>a <xref:System.Windows.Forms.HtmlElement> poskytují čtyři metody, které umožňují přístup k nevystaveným členům.</span><span class="sxs-lookup"><span data-stu-id="74cdb-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="74cdb-108">V následující tabulce jsou uvedeny typy a jejich odpovídající metody.</span><span class="sxs-lookup"><span data-stu-id="74cdb-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="74cdb-109">Typ členu</span><span class="sxs-lookup"><span data-stu-id="74cdb-109">Member Type</span></span>|<span data-ttu-id="74cdb-110">Metoda (y)</span><span class="sxs-lookup"><span data-stu-id="74cdb-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="74cdb-111">Vlastnosti (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="74cdb-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="74cdb-112">Metody</span><span class="sxs-lookup"><span data-stu-id="74cdb-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="74cdb-113">Události (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="74cdb-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="74cdb-114">Události (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="74cdb-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="74cdb-115">Události (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="74cdb-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="74cdb-116">Při použití těchto metod se předpokládá, že máte prvek správného základního typu.</span><span class="sxs-lookup"><span data-stu-id="74cdb-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="74cdb-117">Předpokládejme, že chcete naslouchat `Submit` události `FORM` elementu na stránce HTML, aby bylo možné provést některé `FORM`předběžné zpracování hodnot na hodnotách, než je uživatel odešle na server.</span><span class="sxs-lookup"><span data-stu-id="74cdb-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="74cdb-118">V ideálním případě, pokud máte kontrolu nad kódem HTML, byste definovali `FORM` , aby měl jedinečný `ID` atribut.</span><span class="sxs-lookup"><span data-stu-id="74cdb-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
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
  
 <span data-ttu-id="74cdb-119">Po <xref:System.Windows.Forms.WebBrowser> načtení této stránky do ovládacího prvku lze <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> použít metodu pro načtení `FORM` za běhu pomocí `form1` jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="74cdb-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="74cdb-120">Přístup k nespravovaným rozhraním</span><span class="sxs-lookup"><span data-stu-id="74cdb-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="74cdb-121">Můžete také přistupovat k nevystaveným členům ve spravovaném modelu HTML DOM pomocí nespravovaných rozhraní modelu COM (Component Object Model) vystavených každou třídou modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="74cdb-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="74cdb-122">To se doporučuje v případě, že je nutné provést několik volání proti nevystaveným členům nebo pokud nevystavené členy vrátí jiná nespravovaná rozhraní, která nejsou zabalena spravovaným modelem HTML DOM.</span><span class="sxs-lookup"><span data-stu-id="74cdb-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="74cdb-123">V následující tabulce jsou uvedena všechna nespravovaná rozhraní, která jsou vystavena prostřednictvím spravovaného modelu HTML DOM.</span><span class="sxs-lookup"><span data-stu-id="74cdb-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="74cdb-124">Kliknutím na každý odkaz zobrazíte vysvětlení jeho použití, například kód.</span><span class="sxs-lookup"><span data-stu-id="74cdb-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="74cdb-125">type</span><span class="sxs-lookup"><span data-stu-id="74cdb-125">Type</span></span>|<span data-ttu-id="74cdb-126">Nespravované rozhraní</span><span class="sxs-lookup"><span data-stu-id="74cdb-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="74cdb-127">Nejjednodušší způsob, jak používat rozhraní COM, je přidat odkaz na nespravovanou HTML knihovnu HTML (MSHTML. dll) z vaší aplikace, i když to není podporováno.</span><span class="sxs-lookup"><span data-stu-id="74cdb-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="74cdb-128">Další informace najdete v [článku 934368 znalostní báze](https://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="74cdb-128">For more information, see [Knowledge Base Article 934368](https://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="74cdb-129">Přístup k funkcím skriptu</span><span class="sxs-lookup"><span data-stu-id="74cdb-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="74cdb-130">Stránka HTML může definovat jednu nebo více funkcí pomocí skriptovacího jazyka, jako je například JScript nebo VBScript.</span><span class="sxs-lookup"><span data-stu-id="74cdb-130">An HTML page can define one or more functions by using a scripting language such as JScript or VBScript.</span></span> <span data-ttu-id="74cdb-131">Tyto funkce jsou umístěny uvnitř `SCRIPT` stránky na stránce a lze je spustit na vyžádání nebo v reakci na událost v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="74cdb-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="74cdb-132">Můžete zavolat libovolné funkce skriptu, které definujete na stránce HTML pomocí <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="74cdb-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="74cdb-133">Pokud metoda skriptu vrátí prvek jazyka HTML, lze použít přetypování k převedení výsledku vrátí na <xref:System.Windows.Forms.HtmlElement>.</span><span class="sxs-lookup"><span data-stu-id="74cdb-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="74cdb-134">Podrobnosti a příklady kódu naleznete v tématu <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span><span class="sxs-lookup"><span data-stu-id="74cdb-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74cdb-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74cdb-135">See also</span></span>

- [<span data-ttu-id="74cdb-136">Použití spravovaného modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="74cdb-136">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
