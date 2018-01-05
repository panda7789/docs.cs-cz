---
title: "Bezpečnější tisk ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f36ee150e4dcca74141b644a55451abd4a4fd21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="2a57d-102">Bezpečnější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a57d-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="2a57d-103">Aplikace Windows Forms často zahrnují dalo tisku.</span><span class="sxs-lookup"><span data-stu-id="2a57d-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="2a57d-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Používá <xref:System.Drawing.Printing.PrintingPermission> třída pro řízení přístupu k funkcím tisku a přidružené <xref:System.Drawing.Printing.PrintingPermissionLevel> hodnota výčtu udávajících úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="2a57d-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="2a57d-105">Ve výchozím nastavení je tisk povolené ve výchozím nastavení v zóny místního intranetu a Internetu; úroveň přístupu, je však omezená z obou zóny.</span><span class="sxs-lookup"><span data-stu-id="2a57d-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="2a57d-106">Jestli vaše aplikace může tisknout, vyžaduje interakci s uživatelem, nebo nelze tiskových závisí na hodnotě oprávnění udělená aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2a57d-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="2a57d-107">Ve výchozím nastavení, obdrží zóny místního intranetu <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> přístup a zóny intranetu obdrží <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> přístup.</span><span class="sxs-lookup"><span data-stu-id="2a57d-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="2a57d-108">Následující tabulka uvádí funkce, která je k dispozici v jednotlivých tisk úroveň oprávnění.</span><span class="sxs-lookup"><span data-stu-id="2a57d-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="2a57d-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="2a57d-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="2a57d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2a57d-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="2a57d-111">Poskytuje úplný přístup k všech nainstalovaných tiskáren.</span><span class="sxs-lookup"><span data-stu-id="2a57d-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="2a57d-112">Umožňuje tisk prostřednictvím kódu programu do výchozí tiskárny a bezpečnější tisk prostřednictvím omezující Tisk dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2a57d-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="2a57d-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span><span class="sxs-lookup"><span data-stu-id="2a57d-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="2a57d-114">Poskytuje tisk jenom z dalších omezený dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="2a57d-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="2a57d-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span><span class="sxs-lookup"><span data-stu-id="2a57d-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="2a57d-116">Brání přístupu k tiskárny.</span><span class="sxs-lookup"><span data-stu-id="2a57d-116">Prevents access to printers.</span></span> <span data-ttu-id="2a57d-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span><span class="sxs-lookup"><span data-stu-id="2a57d-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a57d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a57d-118">See Also</span></span>  
 [<span data-ttu-id="2a57d-119">Zabezpečenější přístup k souborům a datům ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a57d-119">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [<span data-ttu-id="2a57d-120">Dodatečné informace o zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a57d-120">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [<span data-ttu-id="2a57d-121">Přehled zabezpečení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a57d-121">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [<span data-ttu-id="2a57d-122">Windows Forms – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2a57d-122">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)
