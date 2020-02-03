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
# <a name="system-information-and-windows-forms"></a>Systémové informace a Windows Forms
V některých případech je nutné shromáždit informace o počítači, na kterém je aplikace spuštěná, aby bylo možné ve svém kódu dělat rozhodnutí. Můžete mít například funkci, která se dá použít jenom v případě, že je připojená k určité síťové doméně. v takovém případě budete potřebovat způsob, jak určit doménu a zakázat funkci, pokud doména není k dispozici.  
  
 Aplikace model Windows Forms mohou použít třídu <xref:System.Windows.Forms.SystemInformation> k určení počtu položek pro počítač v době běhu. Následující příklad ukazuje použití třídy <xref:System.Windows.Forms.SystemInformation> k načtení <xref:System.Windows.Forms.SystemInformation.UserName%2A> a <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
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
  
 Všichni členové třídy <xref:System.Windows.Forms.SystemInformation> jsou jen pro čtení; nastavení uživatele nemůžete změnit. Existuje více než 100 členů třídy, které vrací informace o všech monitorech připojených k počítači (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) k odstupu ikon v Průzkumníkovi Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> a <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Některé z užitečnějších členů třídy <xref:System.Windows.Forms.SystemInformation> zahrnují <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>a <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.SystemInformation>
- [Správa výkonu v modelu Windows Forms](power-management-in-windows-forms.md)
