---
title: "WebBrowser – zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3985fc9916b3e95e650502ef1f8dc301363b1f90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="webbrowser-security"></a><span data-ttu-id="dbf2b-102">WebBrowser – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="dbf2b-102">WebBrowser Security</span></span>
<span data-ttu-id="dbf2b-103"><xref:System.Windows.Forms.WebBrowser> Ovládací prvek je určen pro práci v pouze úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="dbf2b-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="dbf2b-104">Obsah HTML, který zobrazí v ovládacím prvku mohou pocházet z externích webových serverů a může obsahovat nespravovaného kódu ve formě skripty nebo ovládací prvky webového.</span><span class="sxs-lookup"><span data-stu-id="dbf2b-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="dbf2b-105">Pokud použijete <xref:System.Windows.Forms.WebBrowser> ovládací prvek v této situaci se ovládací prvek je již méně bezpečná, než by bylo Internet Explorer, ale spravovaný <xref:System.Windows.Forms.WebBrowser> řízení nezabrání takový nespravovaný kód spuštěný.</span><span class="sxs-lookup"><span data-stu-id="dbf2b-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="dbf2b-106">Další informace o zabezpečení problémy týkající se základní ActiveX `WebBrowser` řízení najdete v tématu [WebBrowser – ovládací prvek](http://go.microsoft.com/fwlink/?LinkId=198812).</span><span class="sxs-lookup"><span data-stu-id="dbf2b-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](http://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbf2b-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbf2b-107">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 [<span data-ttu-id="dbf2b-108">Přehled ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="dbf2b-108">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="dbf2b-109">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="dbf2b-109">WebBrowser Control</span></span>](http://go.microsoft.com/fwlink/?LinkId=198812)
