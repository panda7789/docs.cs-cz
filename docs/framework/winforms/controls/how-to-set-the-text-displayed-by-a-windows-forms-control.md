---
title: "Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 858d1d9b80af89be3e029ce59c521fa6e4d24c29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms
Ovládací prvky Windows Forms obvykle zobrazí text související s primární funkce ovládacího prvku. Například <xref:System.Windows.Forms.Button> obvykle zobrazí popisek indikující, jaká akce se provede při kliknutí na tlačítko. Pro všechny ovládací prvky, můžete nastavit nebo vrátí text s použitím <xref:System.Windows.Forms.Control.Text%2A> vlastnost. Písmo můžete změnit pomocí <xref:System.Windows.Forms.Control.Font%2A> vlastnost. Můžete také nastavit text pomocí návrháře.  Také najdete v části [postup: vytvoření přístup klíčů pro Windows Forms – ovládací prvky pomocí návrháře](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [postup: nastavení zobrazí Text s použitím ovládacího prvku Windows Forms návrháře](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [postupy: nastavení obrázku Zobrazí ve Windows Forms pomocí návrháře ovládacího prvku](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a>K nastavení textu zobrazovaného ovládacím prvkem prostřednictvím kódu programu  
  
1.  Nastavte <xref:System.Windows.Forms.Control.Text%2A> na řetězec.  
  
     Chcete-li vytvořit podtržené přístupový klíč, obsahuje znak ampersand (&) před písmeno, které bude přístupový klíč.  
  
2.  Nastavte <xref:System.Windows.Forms.Control.Font%2A> vlastností pro objekt typu <xref:System.Drawing.Font>.  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  Řídicí znak můžete zobrazit speciální znak v prvky uživatelského rozhraní, které by normálně jejich interpretace, například položky nabídky. Například následující řádek kódu nastaví položku nabídky textu k načtení "& teď pro něco úplně jiné":  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>  
 [Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
