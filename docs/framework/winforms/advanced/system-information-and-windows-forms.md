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
ms.openlocfilehash: 2edc2e867259f8884467c3d5b0ae3d22ba391a77
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380107"
---
# <a name="system-information-and-windows-forms"></a>Systémové informace a Windows Forms
Někdy je potřeba shromáždit informace o počítači, který vaše aplikace běží na, abyste mohli dělat rozhodnutí v kódu. Například můžete mít funkci, která platí pouze při připojení k doméně konkrétního síťového; v takovém případě potřebujete způsob, jak určit doménu a zakázat funkce, pokud doména není k dispozici.  
  
 Můžete použít aplikace Windows Forms <xref:System.Windows.Forms.SystemInformation> třídu k určení řadu věcí na počítač v době běhu. Následující příklad ukazuje použití <xref:System.Windows.Forms.SystemInformation> třídy k načtení <xref:System.Windows.Forms.SystemInformation.UserName%2A> a <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
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
  
 Všichni členové <xref:System.Windows.Forms.SystemInformation> třídy jsou jen pro čtení; nelze změnit nastavení uživatele. Existuje více než 100 členy třídy, vrací informace o všechno, co z tento počet monitorů připojená k počítači (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) na mezery ikony v Průzkumníku Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> a <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Některé další užitečné členů <xref:System.Windows.Forms.SystemInformation> třídy zahrnují <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, a <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SystemInformation>
- [Správa výkonu v modelu Windows Forms](power-management-in-windows-forms.md)
