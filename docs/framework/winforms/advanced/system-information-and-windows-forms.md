---
title: "Systémové informace a Windows Forms"
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
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6657556ffb49c19e6ffc3ef5462de341a93112b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="ceebc-102">Systémové informace a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ceebc-102">System Information and Windows Forms</span></span>
<span data-ttu-id="ceebc-103">Někdy je nutné shromažďovat informace o počítači, který vaše aplikace běží na tak, aby rozhodnutí v kódu.</span><span class="sxs-lookup"><span data-stu-id="ceebc-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="ceebc-104">Například můžete mít funkce, které platí pouze při připojení k doméně konkrétní síť; v takovém případě musíte způsob, jak určit domény a zakázat funkce, pokud doména není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ceebc-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="ceebc-105">Můžete použít formulářových aplikací Windows <xref:System.Windows.Forms.SystemInformation> třídu k určení existuje řada věcí o počítač za běhu.</span><span class="sxs-lookup"><span data-stu-id="ceebc-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="ceebc-106">Následující příklad ukazuje, jak pomocí <xref:System.Windows.Forms.SystemInformation> třída načíst <xref:System.Windows.Forms.SystemInformation.UserName%2A> a <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span><span class="sxs-lookup"><span data-stu-id="ceebc-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to " _  
+ Domain)  
```  
  
 <span data-ttu-id="ceebc-107">Všichni členové <xref:System.Windows.Forms.SystemInformation> třídy jsou jen pro čtení, nelze změnit nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="ceebc-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="ceebc-108">Existuje více než 100 členy třídy, vrácení informace všechno, co z tento počet monitorů k počítači připojené (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) k mezery ikony v Průzkumníku Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> a <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span><span class="sxs-lookup"><span data-stu-id="ceebc-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="ceebc-109">Některé další užitečné členů <xref:System.Windows.Forms.SystemInformation> třída zahrnovat <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, a <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span><span class="sxs-lookup"><span data-stu-id="ceebc-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceebc-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ceebc-110">See Also</span></span>  
 <xref:System.Windows.Forms.SystemInformation>  
 [<span data-ttu-id="ceebc-111">Řízení spotřeby v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ceebc-111">Power Management in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)
