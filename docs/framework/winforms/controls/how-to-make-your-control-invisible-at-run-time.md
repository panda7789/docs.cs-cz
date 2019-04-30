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
ms.openlocfilehash: e9af529541a40a951d6defea180dbbef04c8f3be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913702"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>Postupy: Skrytí vlastního ovládacího prvku za běhu
Existují situace, kdy můžete chtít vytvořit uživatelský ovládací prvek není viditelný v době běhu. Například může být ovládací prvek, který je budíku neviditelné s výjimkou případů, kdy byl zvukově alarm. Snadno toho dosahuje tím, že nastavíte <xref:System.Windows.Forms.Control.Visible%2A> vlastnost. Pokud <xref:System.Windows.Forms.Control.Visible%2A> vlastnost `true`, ovládací prvek se zobrazí jako obvykle. Pokud `false`, bude skrytý ovládací prvek. I když kód v ovládacím prvku přesto mohou být spuštěny při neviditelné, nebudete moci pracovat s ovládacím prvkem prostřednictvím uživatelského rozhraní. Pokud chcete vytvořit skrytý ovládací prvek, který se stále reaguje na uživatelský vstup (například kliknutí myší), měli byste vytvořit transparentní ovládacího prvku. Další informace najdete v tématu [poskytuje ovládací prvek průhledné pozadí](how-to-give-your-control-a-transparent-background.md).  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>Chcete-li skrytí vlastního ovládacího prvku za běhu  
  
1. Nastavte <xref:System.Windows.Forms.Control.Visible%2A> vlastnost `false`.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.Visible%2A>
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
- [Postupy: Zadejte svůj ovládací prvek průhledné pozadí](how-to-give-your-control-a-transparent-background.md)
