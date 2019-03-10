---
title: 'Postupy: Změna ohraničení Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: f188e14b304970840bfc35a592a445f68f9d7af7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713901"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Postupy: Změna ohraničení Windows Forms
Máte několik stylů ohraničení lze vybírat při určování vzhled a chování formulářů Windows. Pomocí změny <xref:System.Windows.Forms.Form.FormBorderStyle%2A> vlastnost, můžete řídit chování změny velikosti ve formuláři. Kromě toho nastavení <xref:System.Windows.Forms.Form.FormBorderStyle%2A> má vliv na způsob zobrazení záhlaví a co tlačítka se může zobrazit na to. Další informace naleznete v tématu <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Není k dispozici rozsáhlou podporu pro tuto úlohu v sadě Visual Studio.  
  
 Viz také [jak: Změna ohraničení Windows Forms pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Chcete-li nastavit styl ohraničení Windows Forms prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.Form.FormBorderStyle%2A> nastavte požadovaný styl. Následující příklad kódu nastaví styl ohraničení tvaru `DlgBx1` k <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     Viz také [jak: Vytváření dialogových oken během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).  
  
     Kromě toho pokud jste zvolili styl ohraničení pro formulář, který obsahuje volitelné **minimalizovat** a **Maximalizovat** tlačítka, můžete zadat, jestli má jeden nebo oba z těchto tlačítek funkční. Tato tlačítka jsou užitečné, pokud chcete přesně řídit činnost koncového uživatele. **Minimalizovat** a **Maximalizovat** tlačítka jsou ve výchozím nastavení povolené, a jejich funkce je zpracováván prostřednictvím **vlastnosti** okna.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
