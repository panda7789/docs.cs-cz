---
title: "PrintForm – součást (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 890d5a3a3f9c3a737a59e17fef0d4ac0407e9924
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="printform-component-visual-basic"></a>PrintForm – součást (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součásti pro [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] umožňuje vytisknout image Windows Form v době běhu. Své chování nahrazuje u `PrintForm` metoda v dřívějších verzích jazyka Visual Basic.  
  
 Ovládací prvky PowerPack jsou již zahrnuty v sadě Visual Studio, ale si můžete stáhnout z [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="printform-component-overview"></a>PrintForm – součást – přehled  
 Běžný scénář pro Windows Forms je vytvořit formulář, který je naformátován tak, aby připomínaly dokumentu formuláře nebo sestavy, a potom k tisku obrázek ve formátu. Přestože je možné použít <xref:System.Drawing.Printing.PrintDocument> součást k tomu, bude vyžadovat velké množství kódu. <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást umožňuje tisk obrázku formuláře k tiskárně, okno náhledu tisku nebo do souboru bez použití <xref:System.Drawing.Printing.PrintDocument> součásti.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást se nachází na **PowerPacks jazyka Visual Basic** kartě **sada nástrojů**. Když je přetáhli formulář se zobrazí na hlavním panelu součást oblasti malé pod dolní ohraničení tvaru. Pokud je součást vybraná, vlastnosti, které definují své chování může být nastavena v **vlastnosti** okno. Všechny tyto vlastnosti můžete také nastavit v kódu. Můžete také vytvořit instanci <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti v kódu bez přidání komponentu v době návrhu.  
  
 Při tisku formuláře je vytištěno vše v klientské oblasti formuláře. To zahrnuje všechny ovládací prvky a libovolný text nebo grafické vykresleny na formuláři pomocí jiných metod grafiky. Ve výchozím nastavení nejsou vytištěny záhlaví formuláře, posuvníky a ohraničení. Také ve výchozím nastavení <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součást vytiskne viditelné části formuláře. Například pokud uživatel změní velikost formuláře za běhu, pouze ovládací prvky a obrázky, které jsou aktuálně viditelné jsou vytisknout.  
  
 Tiskárny výchozí používané <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti je určen podle nastavení ovládacích panelů operačního systému.  
  
 Po inicializaci tisk standardní <xref:System.Drawing.Printing.PrintDocument> se zobrazí dialogové okno tisku. Toto dialogové okno umožňuje uživatelům tiskovou úlohu zrušit.  
  
### <a name="key-methods-properties-and-events"></a>Klíče metody, vlastnosti a události  
 Metodě klíče <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součást je <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metodu, která vytiskne obrázek formuláře tiskárny, okno náhledu tisku nebo souboru. Existují dvě verze <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metoda:  
  
-   Základní verze bez parametrů:`Print()`  
  
-   Přetížené verze s parametry, které určují tisk chování:`Print(printForm As Form, printFormOption As PrintOption)`  
  
     `PrintOption` Přetížené metody, určuje základní implementaci používá k vytištění formuláře, zda záhlaví formuláře, posuvníky a ohraničení vytisknou a jestli jsou vytisknout posouvatelného části formuláře.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> Vlastnost je klíčovou vlastnost <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti. Tato vlastnost určuje, zda je výstup odeslán na tiskárnu, zobrazí okno náhledu tisku nebo uložený jako soubor Encapsulated PostScript. Pokud <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> je nastavena na <xref:System.Drawing.Printing.PrintAction.PrintToFile>, <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> vlastnost určuje název a cesta k souboru.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> Vlastnost poskytuje přístup k základní <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> objekt, který umožňuje určit taková nastavení jako tiskárny, které mají být použity a počet kopií. Můžete taky zadat dotaz tiskárny funkce, například barvu nebo duplexní podpory. Tato vlastnost pravděpodobně není v **vlastnosti** okno; přístupná jenom z kódu.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> Vlastnost se používá k určení formátu tisknout při vyvolání <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součást prostřednictvím kódu programu. Pokud komponentu je přidán do formuláře v době návrhu, které tvoří je výchozí.  
  
 Klíče událostí <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti zahrnují následující:  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint>událost. Nastane při <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metoda je volána a před první stránka výtisků dokumentu.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint>událost. Vyskytne se po poslední tisknout.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings>událost. Nastane bezprostředně před každou tisknout.  
  
### <a name="remarks"></a>Poznámky  
 Pokud formulář obsahuje text nebo grafické vykresleny podle <xref:System.Drawing.Graphics> metody, použijte základní <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) metoda k jeho tisku. U některých operačních systémů nemusí vykreslení grafiky při přetížené <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metoda se používá.  
  
 Je-li ve tvaru, který je širší než šířka papíru v tiskárně, může být oříznutí pravé straně formuláře. Při návrhu formuláře pro tisk, ujistěte se, že formulář vešel na papír standardní velikosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, běžně se používají <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti.  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 [Postupy: tisk formuláře pomocí součásti PrintForm](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)  
 [Postupy: tisk klientské oblasti formuláře](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Postupy: tisk klientských i Neklientských oblastí formuláře](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Postupy: tisk posuvného formuláře](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
