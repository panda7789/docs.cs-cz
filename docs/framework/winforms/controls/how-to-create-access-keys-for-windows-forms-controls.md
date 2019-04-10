---
title: 'Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: e6c829553163359301bad2cd896fc43562ee8069
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334455"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms
*Přístupový klíč* je znak podtržený text nabídky, položka nabídky nebo popisek ovládacích prvcích jako tlačítko. Přístupový klíč uživatel může "klikněte" tlačítko stisknutím klávesy ALT v kombinaci s předdefinovanou přístupový klíč. Například, pokud tlačítko spustí postup tisk formuláře a proto jeho `Text` je nastavena na "Print","Přidání ampersand před písmeno"P"způsobí, že písmeno"P", chcete-li být podtržený text tlačítka v době běhu. Uživatele můžete spustit příkaz přidružený k tlačítku stisknutím kombinace kláves ALT + P. Nemůžete mít přístupový klíč pro ovládací prvek, který nemůže získat fokus.  
  
### <a name="to-create-an-access-key-for-a-control"></a>Chcete-li vytvořit přístupový klíč pro ovládací prvek  
  
1. Nastavte `Text` vlastnost na řetězec, který obsahuje znak ampersand (&) před písmenem, který bude klávesovou zkratku.  
  
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
    >  Vložit znak ampersand titulek bez vytvoření přístupového klíče, zahrnují dva ampersandy (& &). Znak ampersand se zobrazí v záhlaví a žádné znaky jsou podtrženy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Button>
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
