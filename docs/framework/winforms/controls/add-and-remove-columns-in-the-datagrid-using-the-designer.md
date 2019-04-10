---
title: 'Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 80ede9b7bc5bf667e03dc0a745fbc0b5f6c2663a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343282"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek musí obsahovat sloupce, pokud chcete zobrazit data. Pokud budete chtít ručně naplnění ovládacího prvku, je nutné přidat sloupce sami. Případně lze vazbu ovládacího prvku ke zdroji dat, která vytvoří a naplní sloupce automaticky. Pokud zdroj dat obsahuje více sloupců, než které chcete zobrazit, můžete odebrat nežádoucí sloupce.  
  
 Následující postup vyžaduje **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-a-column-using-the-designer"></a>Chcete-li přidat sloupec pomocí návrháře  
  
1. Klikněte na inteligentní označit piktogram (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> ovládací prvek a potom vyberte **přidat sloupec**.  
  
2. V **přidat sloupec** dialogového okna zvolte **sloupec datové vazby** možnost a vyberte sloupec ze zdroje dat nebo zvolte **nepřipojeného sloupce** možnost a definovat sloupec pomocí do příslušných polí.  
  
3. Klikněte na tlačítko **přidat** tlačítko Přidat sloupec by ji zobrazit v návrháři, pokud existující sloupce již nevyplní oblasti ovládacího prvku zobrazení.  
  
    > [!NOTE]
    >  Můžete upravit vlastnosti sloupce v **upravit sloupce** dialogové okno, které se dá dostat z ovládacího prvku inteligentních značek.  
  
### <a name="to-remove-a-column-using-the-designer"></a>Chcete-li odebrat sloupce pomocí návrháře  
  
1. Zvolte **upravit sloupce** z ovládacího prvku inteligentních značek.  
  
2. Vyberte sloupec **vybrané sloupce** seznamu.  
  
3. Klikněte na tlačítko **odebrat** tlačítko pro odstranění sloupce by ji zmizí z návrháře.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Postupy: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
