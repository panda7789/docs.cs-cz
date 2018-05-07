---
title: 'Postupy: Skrytí vlastního ovládacího prvku za běhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
ms.openlocfilehash: 51e804c7f01b55ed7504837042b6c32bf47d9405
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>Postupy: Skrytí vlastního ovládacího prvku za běhu
Existují situace, kdy můžete chtít vytvořit uživatelský ovládací prvek, který je v době běhu neviditelná. Ovládací prvek, který je hodiny výstrahy může být například neviditelná s výjimkou případů, kdy byl zvukově na upozornění. Toho dosahuje snadno nastavením <xref:System.Windows.Forms.Control.Visible%2A> vlastnost. Pokud <xref:System.Windows.Forms.Control.Visible%2A> vlastnost je `true`, vlastní ovládací prvek se zobrazí jako normální. Pokud `false`, bude skrytá vlastního ovládacího prvku. I když kód v vlastního ovládacího prvku může stále spustit při neviditelné, nebudete moci pracovat s ovládacím prvkem v uživatelském rozhraní. Pokud chcete vytvořit neviditelná ovládací prvek, který stále odpoví na uživatelský vstup (například kliknutí myší), měli byste vytvořit transparentní ovládacího prvku. Další informace najdete v tématu [poskytnutí vlastního ovládacího prvku průhledné pozadí](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>Chcete-li skrytí vlastního ovládacího prvku za běhu  
  
1.  Nastavte <xref:System.Windows.Forms.Control.Visible%2A> vlastnost `false`.  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Postupy: Zajištění průhledného pozadí pro vlastní ovládací prvek](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
