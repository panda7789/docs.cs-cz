---
title: 'Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 7cb9278cd311d211ef95df238b930970ae472d05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012942"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView
Ve výchozím nastavení, uživatelé mohou upravovat obsah aktuální <xref:System.Windows.Forms.DataGridView> buňka s textem pole zadáním v ní nebo stisknutím klávesy F2. To umístí buňku v režimu úprav Pokud jsou splněny všechny následující podmínky:  
  
- Podkladový zdroj dat podporuje úpravy.  
  
- <xref:System.Windows.Forms.DataGridView> Je ovládací prvek povolený.  
  
- <xref:System.Windows.Forms.DataGridView.EditMode%2A> Hodnota vlastnosti není <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
- `ReadOnly` Vlastnosti buněk, řádků, sloupců a ovládacího prvku jsou nastaveny na `false`.  
  
 Uživatel v režimu úprav, můžete změnit hodnotu buňky a stisknutím ENTERU Potvrdit změnu nebo klávesou ESC Operaci vrátit na původní hodnotu buňky.  
  
 Můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> tak, aby buňky přejde do režimu úprav co nejdříve bude aktuální buňky. V tomto případě je beze změny chování klávesy ENTER a ESC, ale zůstane buňku v režimu úprav po hodnotu potvrzené nebo vrátit zpět. Ovládací prvek můžete také nakonfigurovat tak, aby pouze v případě, že uživatelé budou psát v buňce nebo pouze pokud uživatelé stisknutím klávesy F2 přejděte buňky vstoupit do režimu úprav. Nakonec můžete zabránit buňky přechod do režimu úprav, s výjimkou při volání <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> metody.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>Chcete-li změnit režim úprav ovládacího prvku DataGridView  
  
- Nastavte <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> vlastnosti na příslušné <xref:System.Windows.Forms.DataGridViewEditMode> výčtu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Odkazy <xref:System> a <xref:System.Windows.Forms> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
