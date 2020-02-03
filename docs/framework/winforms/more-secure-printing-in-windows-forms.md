---
title: Bezpečnější tisk
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 6285b76d01660bfa761ea606421f264bdc0c0af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734889"
---
# <a name="more-secure-printing-in-windows-forms"></a>Bezpečnější tisk ve Windows Forms
Mezi aplikace model Windows Forms často patří možnosti tisku. .NET Framework používá <xref:System.Drawing.Printing.PrintingPermission> třídu pro řízení přístupu k funkcím tisku a související hodnotu výčtu <xref:System.Drawing.Printing.PrintingPermissionLevel> k označení úrovně přístupu. Ve výchozím nastavení je tisk povolený ve výchozím nastavení v zóně Místní intranet a Internet. úroveň přístupu je však omezená v obou zónách. Bez ohledu na to, jestli vaše aplikace může tisknout, vyžaduje zásah uživatele nebo nemůže tisknout, závisí na hodnotě oprávnění udělené aplikaci. Ve výchozím nastavení obdrží zóna místního intranetu přístup <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> a intranetová zóna obdrží přístup <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.  
  
 V následující tabulce jsou uvedeny funkce, které jsou k dispozici na každé úrovni oprávnění k tisku.  
  
|PrintingPermissionLevel|Popis|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Poskytuje úplný přístup ke všem nainstalovaným tiskárnám.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Povolí programové tisk na výchozí tiskárně a bezpečnější tisk pomocí dialogového okna omezujícího tisku. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Poskytuje tisk pouze z dialogového okna s více omezeními. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Znemožní přístup k tiskárnám. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> je podmnožinou <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Viz také

- [Zabezpečenější přístup k souborům a datům ve Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Dodatečné informace o zabezpečení ve Windows Forms](additional-security-considerations-in-windows-forms.md)
- [Přehled zabezpečení ve Windows Forms](security-in-windows-forms-overview.md)
- [Windows Forms – zabezpečení](windows-forms-security.md)
