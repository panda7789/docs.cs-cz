---
title: PrintForm – součást (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
ms.openlocfilehash: 879d31c5a572689d84af6b2e46f3d33e1a8841c8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777844"
---
# <a name="printform-component-visual-basic"></a>PrintForm – součást (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty v jazyce Visual Basic umožňuje tisk formuláře Windows obrázku za běhu. Své chování nahradí `PrintForm` metodu ve starších verzích jazyka Visual Basic.  
  
 Ovládací prvky PowerPack již nejsou zahrnuty v sadě Visual Studio, ale můžete stáhnout z [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="printform-component-overview"></a>Přehled komponenty PrintForm  
 Běžný scénář pro model Windows Forms, je vytvořit formulář, který je formátován tak, aby připomínaly formuláře dokument nebo zprávu, a potom k tisku obrázku ve formátu. Přestože lze použít <xref:System.Drawing.Printing.PrintDocument> součásti k tomu, bude vyžadovat velké množství kódu. <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty umožňuje tisk formuláře k tiskárně, okno náhledu tisku nebo soubor bitové kopie bez použití <xref:System.Drawing.Printing.PrintDocument> komponenty.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty se nachází na **sady Visual Basic PowerPack** karty **nástrojů**. Když je přetáhnout do formuláře se zobrazí v panelu komponent malé oblast pod spodní okraj pracovního formuláře. Pokud je součást vybraná, vlastnosti, které definují chování aplikace je možné nastavit v **vlastnosti** okna. Všechny tyto vlastnosti můžete také nastavit v kódu. Můžete také vytvořit instanci <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu v kódu bez přidání komponenty v době návrhu.  
  
 Při tisku formuláře je vytištěna všechno, co je v klientské oblasti formuláře. To zahrnuje všechny ovládací prvky a všechny textové nebo grafické vykreslené metody grafiky ve formuláři. Ve výchozím nastavení nejsou zobrazeny záhlaví okna formuláře, posuvníky a ohraničení. Také ve výchozím nastavení <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponenty vytiskne jenom viditelné části formuláře. Například pokud uživatel změní velikost formuláře v době běhu, pouze ovládací prvky a grafiku, které jsou aktuálně viditelné jsou zobrazeny.  
  
 Výchozí tiskárna používané <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponenta je určeno nastavení ovládacích panelů operačního systému.  
  
 Po inicializaci tisk standardní <xref:System.Drawing.Printing.PrintDocument> se zobrazí dialogové okno Tisk. Toto dialogové okno umožňuje uživatelům tiskovou úlohu zrušit.  
  
### <a name="key-methods-properties-and-events"></a>Klíčové metody, vlastnosti a události  
 Metodu klíče <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponenta je <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metodu, která vytiskne formuláře tiskárny, okno náhledu tisku nebo soubor bitové kopie. Existují dvě verze <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metody:  
  
-   Základní verze bez parametrů: `Print()`  
  
-   Přetížené verze s parametry, které určují chování tisku: `Print(printForm As Form, printFormOption As PrintOption)`  
  
     `PrintOption` Parametr přetížené metody určuje základní implementace používá k vytištění formuláře, určuje, zda jsou zobrazeny záhlaví formuláře, posuvníky a ohraničení a určuje, zda jsou zobrazeny posuvný části formuláře.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> Vlastnost je klíčovou vlastnost <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponenty. Tato vlastnost určuje, zda výstup je odeslán na tiskárnu, zobrazí v okně Náhled tisku nebo uložený jako soubor zapouzdřené PostScript. Pokud <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> je nastavena na <xref:System.Drawing.Printing.PrintAction.PrintToFile>, <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> vlastnost určuje název a cesta k souboru.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> Vlastnost poskytuje přístup k podkladové <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> objekt, který umožňuje určit tato nastavení jako tiskárny, kterou chcete použít a počet kopií k vytištění. Dotazovat můžete také možnosti tiskárny, například barvy nebo duplexní podpory. Tato vlastnost se nezobrazují v **vlastnosti** okno; je přístupný pouze z kódu.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> Vlastnost se používá k určení formuláře k vytištění při vyvolání <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponenty prostřednictvím kódu programu. Pokud součást je přidán do formuláře v době návrhu, výchozím nastavením je tento formulář.  
  
 Klíče událostí <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti zahrnují následující:  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> události. Nastane, když <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metoda je volána a před první stránka dokument vytiskne.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> události. Vyvolá se po vytištění poslední stránky.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> události. Nastane bezprostředně před každou tisknout.  
  
### <a name="remarks"></a>Poznámky  
 Pokud formulář obsahuje textové nebo grafické vykreslené <xref:System.Drawing.Graphics> metody, použijte základní <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) metoda ho vytisknout. U některých operačních systémů se nemusí vykreslit grafiky při přetížené <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metoda se používá.  
  
 Pokud je formuláře širší než šířka papíru v tiskárně, může být oříznou pravé části formuláře. Při návrhu formuláře pro tisk, ujistěte se, že formulář vejde na papír velikosti standard.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, běžně <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponenty.  
  
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
 [Postupy: Tisk formuláře pomocí komponenty PrintForm](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)  
 [Postupy: Tisk klientské oblasti formuláře](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Postupy: Tisk klientských i neklientských oblastí formuláře](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Postupy: Tisk posuvného formuláře](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
