---
title: 'Postupy: Tisk klientských a neklientských oblastí formuláře (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- title bar [Visual Basic], printing
- printing
- borders [Visual Basic], printing
- entire form
- non-client area [Visual Basic], printing
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
ms.openlocfilehash: 566cf295462945a6bc90bc96f8907de34646bd00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584739"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a>Postupy: Tisk klientských a neklientských oblastí formuláře (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást umožňuje rychle tisk obrázku ve tvaru, který přesně tak, jak se zobrazí na obrazovce bez použití <xref:System.Drawing.Printing.PrintDocument> součásti. Následující postup ukazuje, jak tisk formuláře, včetně klientské oblasti a neklientská oblast. Neklientská oblast zahrnuje záhlaví, ohraničení a posuňte řádky.  
  
 Ovládací prvky PowerPack jsou již zahrnuty v sadě Visual Studio, ale si můžete stáhnout z [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a>Tisknout klientovi i neklientských oblastí formuláře  
  
1.  V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do komponent.  
  
2.  V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro tisku `Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  V některých operačních systémů, text nebo grafické vykresleny podle <xref:System.Drawing.Graphics> metody nestiskne správně. In this Case, použijte metodu kompatibilní tisk: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [Komponenta PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Postupy: Tisk posuvného formuláře](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
