---
title: 'Postupy: Tisk formuláře pomocí součásti PrintForm (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
ms.openlocfilehash: 723524c7c9876d353624ad47d504ea2528a31cfe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422724"
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a>Postupy: Tisk formuláře pomocí součásti PrintForm (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty umožňuje rychlý tisk obrázek formuláře přesně tak, jak se zobrazí na obrazovce bez použití <xref:System.Drawing.Printing.PrintDocument> komponenty. Následující postupy ukazují, jak tisk formuláře tiskárny, okno náhledu tisku a soubor zapouzdřené PostScript.  
  
 Ovládací prvky PowerPack již nejsou zahrnuty v sadě Visual Studio, ale můžete stáhnout z [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-a-form-to-the-default-printer"></a>Tisk formuláře, použije se výchozí tiskárna  
  
1.  V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do panelu komponent.  
  
2.  V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny událostí pro **tisk**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a>K zobrazení formuláře v okně Náhled tisku  
  
1.  V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do panelu komponent.  
  
2.  V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.  
  
3.  Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny událostí pro **tisk**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a>Tisk formuláře do souboru  
  
1.  V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do panelu komponent.  
  
2.  V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToFile>.  
  
3.  Volitelně můžete vybrat <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> vlastnost a zadejte úplnou cestu a název souboru název cílového souboru.  
  
     Pokud tento krok přeskočíte, uživateli zobrazí výzva k zadání názvu souboru v době běhu.  
  
4.  Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny událostí pro **tisk**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [Postupy: Tisk klientské oblasti formuláře](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Postupy: Tisk klientských i neklientských oblastí formuláře](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Postupy: Tisk posuvného formuláře](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [Komponenta PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
