---
title: Bezpečnější tisk ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 2bf05461014c3511725cb28caf2de0eb4c2e1d5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621796"
---
# <a name="more-secure-printing-in-windows-forms"></a>Bezpečnější tisk ve Windows Forms
Aplikace Windows Forms často přinášejí tisk schopnosti. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Používá <xref:System.Drawing.Printing.PrintingPermission> třídy pro řízení přístupu k funkcím, tisk a přidružené <xref:System.Drawing.Printing.PrintingPermissionLevel> hodnota výčtu označující úroveň přístupu. Ve výchozím nastavení je ve výchozím nastavení do zóny místního intranetu a Internetu; povolené tisk úroveň přístupu je však omezeny v obou oblastech. Zda lze vytisknout vaší aplikace, vyžaduje zásah uživatele, nebo nelze tisk závisí na hodnotě oprávnění udělených aplikaci. Ve výchozím nastavení, obdrží zóny místního intranetu <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> přístup a zóny intranetu obdrží <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> přístup.  
  
 V následující tabulce jsou uvedeny funkce, která je dostupná na všech úrovních tisk oprávnění.  
  
|PrintingPermissionLevel|Popis|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Poskytuje úplný přístup ke všem nainstalovaných tiskáren.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Umožňuje tisk prostřednictvím kódu programu, použije se výchozí tiskárna a bezpečnější tisk přes omezující tisk dialogového okna. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Poskytuje pouze z více omezený dialogové okno Tisk. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Brání v přístupu k tiskárny. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečenější přístup k souborům a datům ve Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)
- [Dodatečné informace o zabezpečení ve Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)
- [Přehled zabezpečení ve Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)
- [Windows Forms – zabezpečení](../../../docs/framework/winforms/windows-forms-security.md)
