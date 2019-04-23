---
title: Systémové informace a Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: eeb469dbf4553634aa50d0a9ea17e9b2464defb4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228897"
---
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="a45ef-102">Systémové informace a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a45ef-102">System Information and Windows Forms</span></span>
<span data-ttu-id="a45ef-103">Někdy je potřeba shromáždit informace o počítači, který vaše aplikace běží na, abyste mohli dělat rozhodnutí v kódu.</span><span class="sxs-lookup"><span data-stu-id="a45ef-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="a45ef-104">Například můžete mít funkci, která platí pouze při připojení k doméně konkrétního síťového; v takovém případě potřebujete způsob, jak určit doménu a zakázat funkce, pokud doména není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a45ef-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="a45ef-105">Můžete použít aplikace Windows Forms <xref:System.Windows.Forms.SystemInformation> třídu k určení řadu věcí na počítač v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a45ef-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="a45ef-106">Následující příklad ukazuje použití <xref:System.Windows.Forms.SystemInformation> třídy k načtení <xref:System.Windows.Forms.SystemInformation.UserName%2A> a <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span><span class="sxs-lookup"><span data-stu-id="a45ef-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
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
  
 <span data-ttu-id="a45ef-107">Všichni členové <xref:System.Windows.Forms.SystemInformation> třídy jsou jen pro čtení; nelze změnit nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="a45ef-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="a45ef-108">Existuje více než 100 členy třídy, vrací informace o všechno, co z tento počet monitorů připojená k počítači (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) na mezery ikony v Průzkumníku Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> a <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span><span class="sxs-lookup"><span data-stu-id="a45ef-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="a45ef-109">Některé další užitečné členů <xref:System.Windows.Forms.SystemInformation> třídy zahrnují <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, a <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span><span class="sxs-lookup"><span data-stu-id="a45ef-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a45ef-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a45ef-110">See also</span></span>

- <xref:System.Windows.Forms.SystemInformation>
- [<span data-ttu-id="a45ef-111">Správa výkonu v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a45ef-111">Power Management in Windows Forms</span></span>](power-management-in-windows-forms.md)
