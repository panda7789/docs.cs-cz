---
title: 'Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 3d4112d87dbd448c7e34d2b84d11b49f56e1dc44
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713342"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí návrháře
*Přístupový klíč* je znak podtržený text nabídky, položka nabídky nebo popisek ovládacích prvcích jako tlačítko. Umožňuje uživateli "tlačítko" stisknutím klávesy ALT v kombinaci s předdefinovanou přístupový klíč. Například, pokud tlačítko spustí postup tisk formuláře a proto jeho `Text` je nastavena na "Tisk," "Přidání znak ampersand (&) před písmeno" P "způsobí, že písmeno"P", chcete-li být podtržená v textu tlačítka v době běhu. Uživatele můžete spustit příkaz přidružený k tlačítku stisknutím kombinace kláves ALT + P. Nemůžete mít přístupový klíč pro ovládací prvek, který nemůže získat fokus.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-access-key-for-a-control"></a>Chcete-li vytvořit přístupový klíč pro ovládací prvek  
  
1.  V **vlastnosti** okno, nastaveno `Text` vlastnost na řetězec, který obsahuje znak ampersand (&) před písmenem, který bude přístupový klíč. Například nastavte na písmeno "P" jako přístupový klíč, zadejte **& Tisk** do mřížky.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Button>
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Nastavit Text, zobrazený ovládacím prvkem Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
