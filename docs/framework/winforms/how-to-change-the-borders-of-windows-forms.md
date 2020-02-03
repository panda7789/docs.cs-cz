---
title: Změnit ohraničení formuláře
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 2c8eb25b44c7406e4312f432f2d69524346f94d6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739562"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Postupy: Změna ohraničení Windows Forms
Máte několik stylů ohraničení, ze kterých si můžete vybrat, když určíte vzhled a chování model Windows Forms. Změnou vlastnosti <xref:System.Windows.Forms.Form.FormBorderStyle%2A> můžete řídit chování formuláře při změně velikosti. Kromě toho nastavení <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ovlivňuje způsob zobrazení záhlaví a také to, jaká tlačítka se na něm mohou zobrazovat. Další informace naleznete v tématu <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.  
  
 Viz také [Postupy: Změna ohraničení model Windows Forms pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Nastavení stylu ohraničení model Windows Forms programově  
  
- Vlastnost <xref:System.Windows.Forms.Form.FormBorderStyle%2A> nastavte na styl, který chcete. Následující příklad kódu nastaví styl ohraničení formuláře `DlgBx1` na <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
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
  
     Viz také [Postupy: vytváření dialogových oken v době návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).  
  
     Pokud jste navíc vybrali styl ohraničení formuláře, který poskytuje Volitelná tlačítka **minimalizovat** a **maximalizovat** , můžete určit, zda chcete, aby obě tato tlačítka byla funkční. Tato tlačítka jsou užitečná, když chcete přesně řídit činnost koncového uživatele. Tlačítka **minimalizovat** a **maximalizovat** jsou ve výchozím nastavení povolena a jejich funkce jsou zpracovávány prostřednictvím okna **vlastnosti** .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
