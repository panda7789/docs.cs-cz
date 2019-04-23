---
title: Metody výběru ovládacího prvku Windows Forms Button
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: f2881646a05d257044c6461f822a4c35a225f8c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223287"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Metody výběru ovládacího prvku Windows Forms Button
Tlačítka Windows Forms je vybrat následujícími způsoby:  
  
-   Pomocí myši klikněte na tlačítko.  
  
-   Vyvolání tlačítka <xref:System.Windows.Forms.Control.Click> událost v kódu.  
  
-   Přesunutí výběru na tlačítko stisknutím klávesy TAB a pak klikněte na tlačítko stisknutím klávesy MEZERNÍK nebo ENTER.  
  
-   Stisknutím klávesy (ALT + podtržené písmeno) pro tlačítko. Další informace o přístupových klíčů najdete v tématu [jak: Vytváření přístupových klíčů pro ovládací prvky Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
-   Pokud je tlačítko "přijímat" tlačítko formuláře, stisknutím klávesy ENTER vybere tlačítko, i v případě, že jiný ovládací prvek má fokus – s výjimkou, pokud tento jiný ovládací prvek je jiné tlačítko, víceřádkové textové pole nebo vlastního ovládacího prvku, který zachycuje klávesu enter.  
  
-   Pokud je tlačítko "Storno" tlačítko formuláře, stiskněte klávesu ESC vybere tlačítko, i v případě, že jiný ovládací prvek má fokus.  
  
-   Volání <xref:System.Windows.Forms.Button.PerformClick%2A> metoda klikněte na tlačítko prostřednictvím kódu programu.  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku Button](button-control-overview-windows-forms.md)
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Ovládací prvek Button](button-control-windows-forms.md)
