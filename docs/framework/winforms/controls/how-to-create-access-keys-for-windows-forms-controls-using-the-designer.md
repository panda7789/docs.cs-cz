---
title: "Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53f9c46b282de795d6212f962f7296f76385aed2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře
*Přístupový klíč* je podrženého znaku v textu nabídky, položku nabídky nebo popisek ovládací prvek tlačítko. Umožňuje uživateli "tlačítko" stisknutím klávesy ALT v kombinaci s předdefinované přístupový klíč. Například, pokud tlačítko spustí postup tisk formuláře a proto jeho `Text` je nastavena na "Tisk" přidáte ampersand (&) před písmenem "P" způsobí písmenem "P" podtržení text tlačítka v době běhu. Uživatele můžete spustit příkaz přidružené tlačítko stisknutím ALT + P. Nemůže mít přístupový klíč pro ovládací prvek, který nemůže přijmout fokus.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-access-key-for-a-control"></a>Chcete-li vytvořit přístupový klíč pro ovládací prvek  
  
1.  V **vlastnosti** nastavte `Text` vlastnost na řetězec, který obsahuje znak ampersand (&) před písmeno, které bude přístupový klíč. Například pokud chcete nastavit písmenem "P" jako přístupový klíč, zadejte **& Tisk** v mřížce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Button>  
 [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
