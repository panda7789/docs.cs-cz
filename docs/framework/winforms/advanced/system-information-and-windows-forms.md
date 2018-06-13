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
ms.openlocfilehash: 727bcc53750081ae2d957527332ed3199c7d8e8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524112"
---
# <a name="system-information-and-windows-forms"></a>Systémové informace a Windows Forms
Někdy je nutné shromažďovat informace o počítači, který vaše aplikace běží na tak, aby rozhodnutí v kódu. Například můžete mít funkce, které platí pouze při připojení k doméně konkrétní síť; v takovém případě musíte způsob, jak určit domény a zakázat funkce, pokud doména není k dispozici.  
  
 Můžete použít formulářových aplikací Windows <xref:System.Windows.Forms.SystemInformation> třídu k určení existuje řada věcí o počítač za běhu. Následující příklad ukazuje, jak pomocí <xref:System.Windows.Forms.SystemInformation> třída načíst <xref:System.Windows.Forms.SystemInformation.UserName%2A> a <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
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
  
 Všichni členové <xref:System.Windows.Forms.SystemInformation> třídy jsou jen pro čtení, nelze změnit nastavení uživatele. Existuje více než 100 členy třídy, vrácení informace všechno, co z tento počet monitorů k počítači připojené (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) k mezery ikony v Průzkumníku Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> a <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Některé další užitečné členů <xref:System.Windows.Forms.SystemInformation> třída zahrnovat <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, a <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.SystemInformation>  
 [Správa výkonu v modelu Windows Forms](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)
