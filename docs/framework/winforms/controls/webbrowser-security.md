---
title: WebBrowser – zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 1e658c25ea19f966ac67402c6f3c7693c784d029
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214011"
---
# <a name="webbrowser-security"></a><span data-ttu-id="10423-102">WebBrowser – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="10423-102">WebBrowser Security</span></span>
<span data-ttu-id="10423-103"><xref:System.Windows.Forms.WebBrowser> Ovládací prvek je navržen pro práci v režimu pouze plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="10423-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="10423-104">HTML obsah zobrazený v ovládacím prvku mohou pocházet z externích webových serverů a může obsahovat nespravovaného kódu ve formě skriptů nebo webové ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="10423-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="10423-105">Pokud používáte <xref:System.Windows.Forms.WebBrowser> ovládací prvek v takovém případě ovládací prvek je již méně bezpečné než Internet Explorer by ale spravovanou <xref:System.Windows.Forms.WebBrowser> ovládací prvek nezabrání spuštění takových nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="10423-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="10423-106">Další informace o zabezpečení problémy týkající se základního ActiveX `WebBrowser` řídí, najdete v článku [ovládací prvek WebBrowser](https://go.microsoft.com/fwlink/?LinkId=198812).</span><span class="sxs-lookup"><span data-stu-id="10423-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10423-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10423-107">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="10423-108">WebBrowser – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="10423-108">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- [<span data-ttu-id="10423-109">WebBrowser – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="10423-109">WebBrowser Control</span></span>](https://go.microsoft.com/fwlink/?LinkId=198812)
