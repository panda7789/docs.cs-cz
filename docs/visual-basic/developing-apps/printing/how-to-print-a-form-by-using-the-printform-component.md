---
title: "Postupy: Tisk formuláře pomocí součásti PrintForm (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5edad4f04b98dcf0dfa328f111db5dcb423036e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a>Postupy: Tisk formuláře pomocí součásti PrintForm (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást umožňuje rychle tisk obrázku ve tvaru, který přesně tak, jak se zobrazí na obrazovce bez použití <xref:System.Drawing.Printing.PrintDocument> součásti. Následující postupy ukazují, jak tisk formuláře k tiskárně, okno náhledu tisku a do souboru Encapsulated PostScript.  
  
 Ovládací prvky PowerPack jsou již zahrnuty v sadě Visual Studio, ale si můžete stáhnout z [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-a-form-to-the-default-printer"></a>Tisk formuláře do výchozí tiskárny  
  
1.  V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do komponent.  
  
2.  V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro **tiskových**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a>K zobrazení formuláře v okně náhledu tisku  
  
1.  V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do komponent.  
  
2.  V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.  
  
3.  Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro **tiskových**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a>Tisk formuláře do souboru  
  
1.  V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do komponent.  
  
2.  V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToFile>.  
  
3.  Volitelně vyberte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> vlastnost a zadejte Úplná cesta a název cílového souboru.  
  
     Pokud tento krok přeskočíte, uživateli zobrazí výzva k zadání názvu souboru v době běhu.  
  
4.  Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro **tiskových**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [Postupy: tisk klientské oblasti formuláře](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Postupy: tisk klientských i Neklientských oblastí formuláře](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Postupy: tisk posuvného formuláře](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [PrintForm – součást](../../../visual-basic/developing-apps/printing/printform-component.md)
