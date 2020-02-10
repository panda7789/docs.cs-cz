---
title: WebBrowser – zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: b25cabca050d06dbfe97c563eb56622d1f21be54
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095252"
---
# <a name="webbrowser-security"></a><span data-ttu-id="ab406-102">WebBrowser – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ab406-102">WebBrowser Security</span></span>
<span data-ttu-id="ab406-103"><xref:System.Windows.Forms.WebBrowser> ovládací prvek je navržený tak, aby fungoval pouze v plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ab406-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="ab406-104">Obsah HTML zobrazený v ovládacím prvku může pocházet z externích webových serverů a může obsahovat nespravovaný kód ve formě skriptů nebo webových ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ab406-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="ab406-105">Použijete-li ovládací prvek <xref:System.Windows.Forms.WebBrowser> v této situaci, není ovládací prvek méně zabezpečený než aplikace Internet Explorer, ale spravovaný <xref:System.Windows.Forms.WebBrowser> ovládací prvek nebrání v běhu tohoto nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ab406-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="ab406-106">Další informace o problémech se zabezpečením souvisejícím s podkladovým ovládacím prvkem ActiveX `WebBrowser` najdete v tématu [ovládací prvek WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ab406-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab406-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab406-107">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="ab406-108">Přehled ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="ab406-108">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- <span data-ttu-id="ab406-109">[Ovládací prvek WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ab406-109">[WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span></span>
