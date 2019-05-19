---
title: 'Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: a37f5d64e8ca10b26a8897d45b8757113ce900c9
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877600"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře
Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek mohl zobrazit více sloupců pro každý seznam položek v **podrobnosti** zobrazení. Sloupce, které slouží k zobrazení několik typů informací o každou položku seznamu. Seznam souborů může například zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru. Informace o naplnění sloupce po jejich vytvoření najdete v tématu [jak: Zobrazení podřízených položek ve sloupcích pomocí Windows Forms ovládací prvek ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-columns-in-the-designer"></a>Chcete-li přidat sloupce v Návrháři  
  
1. V **vlastnosti** okno, nastavte ovládacího prvku <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Details>.  
  
2.  V **vlastnosti** okna, klikněte na tlačítko **tlačítko se třemi tečkami** tlačítko (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) vedle položky <xref:System.Windows.Forms.ListView.Columns%2A> vlastnost .  
  
     **Editor kolekce ColumnHeader** se zobrazí.  
  
3. Použití **přidat** tlačítko pro přidání nové sloupce. Poté vyberte záhlaví sloupce a nastavit jeho text (titulek sloupec), zarovnání textu a šířku.  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
