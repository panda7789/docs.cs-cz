---
title: 'Postupy: Tisk posuvného formuláře (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
ms.openlocfilehash: d43c2e0e564f6f0c37831cd3105a16c4bc4aaea0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a>Postupy: Tisk posuvného formuláře (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást umožňuje rychle tisk obrázku ve tvaru, bez použití <xref:System.Drawing.Printing.PrintDocument> součásti. Ve výchozím nastavení je aktuálně viditelné části formuláře vytištěno; Pokud uživatel má ke změně velikosti formuláře za běhu, bitovou kopii nestiskne tak, jak má. Následující postup ukazuje, jak tisk posuvného formuláře, v oblasti úplnou klienta i v případě, že velikost formuláře byla změněna.  
  
 Ovládací prvky PowerPack jsou již zahrnuty v sadě Visual Studio, ale si můžete stáhnout z [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a>Tisk posuvného formuláře v oblasti úplnou klienta  
  
1.  V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást budou přidány do komponent.  
  
2.  V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro **tiskových**`Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  V některých operačních systémů, text nebo grafické vykresleny podle <xref:System.Drawing.Graphics> metody nestiskne správně. V takovém případě nebudete moct tisknout se `Scrollable` parametr.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [Komponenta PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Postupy: Tisk klientské oblasti formuláře](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Postupy: Tisk klientských i neklientských oblastí formuláře](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
