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
# <a name="how-to-access-the-managed-html-document-object-model"></a><span data-ttu-id="63437-102">Postupy: Přístup k modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="63437-102">How to: Access the Managed HTML Document Object Model</span></span>
<span data-ttu-id="63437-103">Spravované HTML Document Object Model (DOM) se můžete dostat ze dvou typů aplikací:</span><span class="sxs-lookup"><span data-stu-id="63437-103">You can access the managed HTML Document Object Model (DOM) from two types of applications:</span></span>  
  
- <span data-ttu-id="63437-104">Aplikace Windows Forms (.exe), která hostované spravovanou <xref:System.Windows.Forms.WebBrowser> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="63437-104">A Windows Forms application (.exe) that hosted the managed <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="63437-105">Tyto dvě technologie se navzájem doplňují, se <xref:System.Windows.Forms.WebBrowser> ovládací prvek zobrazující stránku uživateli a modelu DOM jazyka HTML představující logické struktury dokumentu.</span><span class="sxs-lookup"><span data-stu-id="63437-105">These two technologies complement one another, with the <xref:System.Windows.Forms.WebBrowser> control displaying the page to the user and the HTML DOM representing the document's logical structure.</span></span>  
  
- <span data-ttu-id="63437-106">Windows Forms <xref:System.Windows.Forms.UserControl> hostované v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="63437-106">A Windows Forms <xref:System.Windows.Forms.UserControl> hosted within Internet Explorer.</span></span> <span data-ttu-id="63437-107">Můžete přístup k modelu DOM jazyka HTML představující stránku, na kterém vaše <xref:System.Windows.Forms.UserControl> hostována, aby bylo možné změnit strukturu dokumentu nebo otevřete modálních dialogových oken, mezi mnoho dalších možností.</span><span class="sxs-lookup"><span data-stu-id="63437-107">You can access the HTML DOM representing the page on which your <xref:System.Windows.Forms.UserControl> is hosted in order to change the document's structure or open modal dialog boxes, among many other possibilities.</span></span>  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a><span data-ttu-id="63437-108">Pro přístup k modelu DOM z aplikace Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63437-108">To access DOM from a Windows Forms application</span></span>  
  
1. <span data-ttu-id="63437-109">Hostitele <xref:System.Windows.Forms.WebBrowser> ovládací prvek v rámci vaší aplikace Windows Forms a monitorovat <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="63437-109">Host a <xref:System.Windows.Forms.WebBrowser> control within your Windows Forms application and monitor for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="63437-110">Podrobné informace o hostování ovládacích prvků a sledování událostí, naleznete v tématu [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="63437-110">For details on hosting controls and monitoring for events, see [Events](../../../standard/events/index.md).</span></span>  
  
2. <span data-ttu-id="63437-111">Načíst <xref:System.Windows.Forms.HtmlDocument> pro aktuální stránku díky přístupu <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnost <xref:System.Windows.Forms.WebBrowser> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="63437-111">Retrieve the <xref:System.Windows.Forms.HtmlDocument> for the current page by accessing the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a><span data-ttu-id="63437-112">Pro přístup k modelu DOM z UserControl hostované v aplikaci Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="63437-112">To access DOM from a UserControl hosted in Internet Explorer</span></span>  
  
1. <span data-ttu-id="63437-113">Vytvořte vlastní vlastní odvozenou třídu <xref:System.Windows.Forms.UserControl> třídy.</span><span class="sxs-lookup"><span data-stu-id="63437-113">Create your own custom derived class of the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="63437-114">Další informace najdete v tématu [jak: Vytváření složených ovládacích prvků](how-to-author-composite-controls.md).</span><span class="sxs-lookup"><span data-stu-id="63437-114">For more information, see [How to: Author Composite Controls](how-to-author-composite-controls.md).</span></span>  
  
2. <span data-ttu-id="63437-115">Umístěte následující kód uvnitř vaší obslužné rutiny události zatížení pro vaše <xref:System.Windows.Forms.UserControl>:</span><span class="sxs-lookup"><span data-stu-id="63437-115">Place the following code inside of your Load event handler for your <xref:System.Windows.Forms.UserControl>:</span></span>  
  
 [!code-csharp[AccessHTMLDOMControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="63437-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="63437-116">Robust Programming</span></span>  
  
1. <span data-ttu-id="63437-117">Při použití modelu DOM prostřednictvím <xref:System.Windows.Forms.WebBrowser> ovládacího prvku, byste měli vždy počkat, až <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> dojde k události, než se pokusíte o přístup k <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnost <xref:System.Windows.Forms.WebBrowser> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="63437-117">When using the DOM through the <xref:System.Windows.Forms.WebBrowser> control, you should always wait until the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event occurs before attempting to access the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="63437-118"><xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Událost se vyvolá po načtení celého dokumentu; Pokud používáte modelu DOM té, riskujete způsobující výjimku za běhu ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="63437-118">The <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event is raised after the entire document has loaded; if you use the DOM before then, you risk causing a run-time exception in your application.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="63437-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="63437-119">.NET Framework Security</span></span>  
  
1. <span data-ttu-id="63437-120">Vaše aplikace nebo <xref:System.Windows.Forms.UserControl> vyžaduje úplný vztah důvěryhodnosti pro přístup ke spravované HTML DOM</span><span class="sxs-lookup"><span data-stu-id="63437-120">Your application or <xref:System.Windows.Forms.UserControl> will require full trust in order to access the managed HTML DOM.</span></span> <span data-ttu-id="63437-121">Pokud nasazujete aplikace Windows Forms pomocí technologie ClickOnce, můžete požádat o zvýšení úrovně oprávnění nebo Trusted Application Deployment; úplný vztah důvěryhodnosti. Zobrazit [zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications) podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="63437-121">If you are deploying a Windows Forms application using ClickOnce, you can request full trust using either Permission Elevation or Trusted Application Deployment; see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63437-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63437-122">See also</span></span>

- [<span data-ttu-id="63437-123">Použití spravovaného modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="63437-123">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
