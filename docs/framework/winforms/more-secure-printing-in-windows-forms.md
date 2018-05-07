---
title: Bezpečnější tisk ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 976079f39e13186014b77e85c092c37be11238b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="more-secure-printing-in-windows-forms"></a>Bezpečnější tisk ve Windows Forms
Aplikace Windows Forms často zahrnují dalo tisku. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Používá <xref:System.Drawing.Printing.PrintingPermission> třída pro řízení přístupu k funkcím tisku a přidružené <xref:System.Drawing.Printing.PrintingPermissionLevel> hodnota výčtu udávajících úroveň přístupu. Ve výchozím nastavení je tisk povolené ve výchozím nastavení v zóny místního intranetu a Internetu; úroveň přístupu, je však omezená z obou zóny. Jestli vaše aplikace může tisknout, vyžaduje interakci s uživatelem, nebo nelze tiskových závisí na hodnotě oprávnění udělená aplikaci. Ve výchozím nastavení, obdrží zóny místního intranetu <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> přístup a zóny intranetu obdrží <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> přístup.  
  
 Následující tabulka uvádí funkce, která je k dispozici v jednotlivých tisk úroveň oprávnění.  
  
|PrintingPermissionLevel|Popis|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Poskytuje úplný přístup k všech nainstalovaných tiskáren.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Umožňuje tisk prostřednictvím kódu programu do výchozí tiskárny a bezpečnější tisk prostřednictvím omezující Tisk dialogové okno. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Poskytuje tisk jenom z dalších omezený dialogového okna. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Brání přístupu k tiskárny. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečenější přístup k souborům a datům ve Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Dodatečné informace o zabezpečení ve Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Přehled zabezpečení ve Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Windows Forms – zabezpečení](../../../docs/framework/winforms/windows-forms-security.md)
