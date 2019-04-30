---
title: 'Postupy: Vrstvení objektů ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 8d0abbf0f71ac176d17261a0ae863938c575bdaf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941073"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Postupy: Vrstvení objektů ve Windows Forms
Při vytváření složitých uživatelského rozhraní nebo pracovat s více formulář dokumentu (MDI interface), budete často vrstvy ovládací prvky a podřízené formuláře, chcete-li vytvořit složitější uživatelská rozhraní (UI). Přesunout a mějte přehled o ovládací prvky a windows v rámci skupiny, manipulaci s jejich pořadí vykreslování. *Pořadí vykreslování* je vizuální rozvržení ovládací prvky ve formuláři podél osy z formuláře (hloubku). V horní části pořadí vykreslování okna se překrývá všech ostatních oken. Všechny ostatní okna překrývat okno v dolní části pořadí vykreslování.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-layer-controls-at-design-time"></a>K ovládacím prvkům vrstvy v době návrhu  
  
1. Vyberte ovládací prvek, který chcete vrstvy.  
  
2. Na **formátu** nabídky, přejděte k **pořadí**a potom klikněte na tlačítko **přenést dopředu** nebo **odeslat zpět**.  
  
### <a name="to-layer-controls-programmatically"></a>Ovládací prvky vrstvy prostřednictvím kódu programu  
  
- Použití <xref:System.Windows.Forms.Control.BringToFront%2A> a <xref:System.Windows.Forms.Control.SendToBack%2A> metody pro manipulaci s pořadí vykreslování ovládacích prvků.  
  
     Například pokud <xref:System.Windows.Forms.TextBox> ovládacího prvku, `txtFirstName`, je pod jiného ovládacího prvku a chcete mít v horní části, použijte následující kód:  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Podporuje formuláře Windows *používání kontejnerů ovládacích prvků*. Používání kontejnerů ovládacích prvků zahrnuje umístění celé řady kontrolních mechanismů v rámci nadřazeného ovládacího prvku, třeba počet <xref:System.Windows.Forms.RadioButton> ovládací prvky v rámci <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Potom můžete vrstvy ovládací prvky v rámci nadřazeného ovládacího prvku. Přesunutí skupinový rámeček přesune ovládací prvky, protože se nacházejí uvnitř.  
  
## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
