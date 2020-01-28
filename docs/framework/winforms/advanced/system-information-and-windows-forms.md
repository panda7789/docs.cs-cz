---
title: Systémové informace
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
ms.openlocfilehash: a91e2fd8db0ef338ce30f89f11869f1b6698af3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732591"
---
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="bbe7c-102">Systémové informace a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbe7c-102">System Information and Windows Forms</span></span>
<span data-ttu-id="bbe7c-103">V některých případech je nutné shromáždit informace o počítači, na kterém je aplikace spuštěná, aby bylo možné ve svém kódu dělat rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="bbe7c-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="bbe7c-104">Můžete mít například funkci, která se dá použít jenom v případě, že je připojená k určité síťové doméně. v takovém případě budete potřebovat způsob, jak určit doménu a zakázat funkci, pokud doména není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="bbe7c-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="bbe7c-105">Aplikace model Windows Forms mohou použít třídu <xref:System.Windows.Forms.SystemInformation> k určení počtu položek pro počítač v době běhu.</span><span class="sxs-lookup"><span data-stu-id="bbe7c-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="bbe7c-106">Následující příklad ukazuje použití třídy <xref:System.Windows.Forms.SystemInformation> k načtení <xref:System.Windows.Forms.SystemInformation.UserName%2A> a <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span><span class="sxs-lookup"><span data-stu-id="bbe7c-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to "
+ Domain);
```  
  
 <span data-ttu-id="bbe7c-107">Všichni členové třídy <xref:System.Windows.Forms.SystemInformation> jsou jen pro čtení; nastavení uživatele nemůžete změnit.</span><span class="sxs-lookup"><span data-stu-id="bbe7c-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="bbe7c-108">Existuje více než 100 členů třídy, které vrací informace o všech monitorech připojených k počítači (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) k odstupu ikon v Průzkumníkovi Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> a <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span><span class="sxs-lookup"><span data-stu-id="bbe7c-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="bbe7c-109">Některé z užitečnějších členů třídy <xref:System.Windows.Forms.SystemInformation> zahrnují <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>a <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbe7c-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe7c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbe7c-110">See also</span></span>

- <xref:System.Windows.Forms.SystemInformation>
- [<span data-ttu-id="bbe7c-111">Správa výkonu v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbe7c-111">Power Management in Windows Forms</span></span>](power-management-in-windows-forms.md)
