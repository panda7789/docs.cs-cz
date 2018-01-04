---
title: "Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms"
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
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81aa68a65d09b073b117f4d96dfc06e614d68aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms
*Přístupový klíč* je podrženého znaku v textu nabídky, položku nabídky nebo popisek ovládací prvek tlačítko. Pomocí přístupový klíč uživateli "Kliknutím na" tlačítko stisknutím klávesy ALT v kombinaci s předdefinované přístupový klíč. Například, pokud tlačítko spustí postup tisk formuláře a proto jeho `Text` vlastnost je nastavena na "Tisk" přidáte ampersand před písmenem "P" způsobí, že písmeno "P" podtržení v text tlačítka v době běhu. Uživatele můžete spustit příkaz přidružené tlačítko stisknutím ALT + P. Nemůže mít přístupový klíč pro ovládací prvek, který nemůže přijmout fokus.  
  
### <a name="to-create-an-access-key-for-a-control"></a>Chcete-li vytvořit přístupový klíč pro ovládací prvek  
  
1.  Nastavte `Text` vlastnost na řetězec, který obsahuje znak ampersand (&) před písmeno, které bude zástupce.  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  Zahrnout ampersand popisek bez vytvoření přístupový klíč, zahrnují dva ampersandy (& &). Znak ampersand se zobrazí v záhlaví a podtrhnou žádné znaky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Button>  
 [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
