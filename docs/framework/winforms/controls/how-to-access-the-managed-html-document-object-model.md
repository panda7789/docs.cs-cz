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
# <a name="how-to-access-the-managed-html-document-object-model"></a><span data-ttu-id="f7014-102">Postupy: Přístup k modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="f7014-102">How to: Access the Managed HTML Document Object Model</span></span>
<span data-ttu-id="f7014-103">Je dostupný spravované HTML modelu DOM (Document Object) na dva typy aplikací:</span><span class="sxs-lookup"><span data-stu-id="f7014-103">You can access the managed HTML Document Object Model (DOM) from two types of applications:</span></span>  
  
-   <span data-ttu-id="f7014-104">Aplikace Windows Forms (.exe), který hostil spravovaný <xref:System.Windows.Forms.WebBrowser> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f7014-104">A Windows Forms application (.exe) that hosted the managed <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="f7014-105">Tyto dvě technologie doplňují jiné, s <xref:System.Windows.Forms.WebBrowser> řízení zobrazení stránky uživateli a modelu DOM jazyka HTML představující logické struktury dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f7014-105">These two technologies complement one another, with the <xref:System.Windows.Forms.WebBrowser> control displaying the page to the user and the HTML DOM representing the document's logical structure.</span></span>  
  
-   <span data-ttu-id="f7014-106">Windows Forms <xref:System.Windows.Forms.UserControl> hostovaným v rámci aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f7014-106">A Windows Forms <xref:System.Windows.Forms.UserControl> hosted within Internet Explorer.</span></span> <span data-ttu-id="f7014-107">Můžete získat přístup k modelu DOM jazyka HTML představující stránku, na které vaši <xref:System.Windows.Forms.UserControl> je hostována, aby bylo možné změnit strukturu dokumentu nebo otevřete modálních dialogových oken, mezi mnoha dalších možností.</span><span class="sxs-lookup"><span data-stu-id="f7014-107">You can access the HTML DOM representing the page on which your <xref:System.Windows.Forms.UserControl> is hosted in order to change the document's structure or open modal dialog boxes, among many other possibilities.</span></span>  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a><span data-ttu-id="f7014-108">Pro přístup k modelu DOM z aplikace Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7014-108">To access DOM from a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="f7014-109">Hostitele <xref:System.Windows.Forms.WebBrowser> v aplikaci Windows Forms řídit a monitorovat <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="f7014-109">Host a <xref:System.Windows.Forms.WebBrowser> control within your Windows Forms application and monitor for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="f7014-110">Podrobnosti o hostování ovládacích prvků a sledování událostí najdete v tématu [události](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="f7014-110">For details on hosting controls and monitoring for events, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
2.  <span data-ttu-id="f7014-111">Načtení <xref:System.Windows.Forms.HtmlDocument> pro aktuální stránku přímým přístupem <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnost <xref:System.Windows.Forms.WebBrowser> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f7014-111">Retrieve the <xref:System.Windows.Forms.HtmlDocument> for the current page by accessing the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a><span data-ttu-id="f7014-112">Pro přístup k modelu DOM z UserControl hostované v aplikaci Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="f7014-112">To access DOM from a UserControl hosted in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="f7014-113">Vytvoření vlastní vlastní třídy odvozené z <xref:System.Windows.Forms.UserControl> třídy.</span><span class="sxs-lookup"><span data-stu-id="f7014-113">Create your own custom derived class of the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="f7014-114">Další informace najdete v tématu [postupy: vytváření složených ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f7014-114">For more information, see [How to: Author Composite Controls](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).</span></span>  
  
2.  <span data-ttu-id="f7014-115">Vložte následující kód uvnitř vaší obslužné rutiny události zatížení pro vaše <xref:System.Windows.Forms.UserControl>:</span><span class="sxs-lookup"><span data-stu-id="f7014-115">Place the following code inside of your Load event handler for your <xref:System.Windows.Forms.UserControl>:</span></span>  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f7014-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f7014-116">Robust Programming</span></span>  
  
1.  <span data-ttu-id="f7014-117">Při použití modelu DOM prostřednictvím <xref:System.Windows.Forms.WebBrowser> řízení, byste měli vždy počkat, dokud <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> události dojde před pokusem o přístup <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnost <xref:System.Windows.Forms.WebBrowser> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f7014-117">When using the DOM through the <xref:System.Windows.Forms.WebBrowser> control, you should always wait until the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event occurs before attempting to access the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="f7014-118"><xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Událost se vyvolá po celý dokument načetl; Pokud chcete použít modelu DOM předtím, riskujete způsobí spuštění výjimka ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f7014-118">The <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event is raised after the entire document has loaded; if you use the DOM before then, you risk causing a run-time exception in your application.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f7014-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f7014-119">.NET Framework Security</span></span>  
  
1.  <span data-ttu-id="f7014-120">Aplikace nebo <xref:System.Windows.Forms.UserControl> bude vyžadovat úplný vztah důvěryhodnosti, aby měli přístup na spravované HTML DOM</span><span class="sxs-lookup"><span data-stu-id="f7014-120">Your application or <xref:System.Windows.Forms.UserControl> will require full trust in order to access the managed HTML DOM.</span></span> <span data-ttu-id="f7014-121">Pokud nasazujete aplikaci Windows Forms pomocí [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], můžete požádat o úplný vztah důvěryhodnosti pomocí zvýšení úrovně oprávnění nebo nasazení důvěryhodných aplikací, zjistit [zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications) podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="f7014-121">If you are deploying a Windows Forms application using [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], you can request full trust using either Permission Elevation or Trusted Application Deployment; see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7014-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7014-122">See Also</span></span>  
 [<span data-ttu-id="f7014-123">Použití spravovaného modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="f7014-123">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
