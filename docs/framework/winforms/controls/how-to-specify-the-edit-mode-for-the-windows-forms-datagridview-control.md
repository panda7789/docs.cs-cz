---
title: Určení režimu úprav pro ovládací prvek DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743761"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView
Ve výchozím nastavení mohou uživatelé upravovat obsah aktuální <xref:System.Windows.Forms.DataGridView> buňky textového pole, a to tak, že je zapíšete nebo stisknete F2. Tato akce převede buňku do režimu úprav, pokud jsou splněné všechny následující podmínky:  
  
- Podkladový zdroj dat podporuje úpravy.  
  
- Ovládací prvek <xref:System.Windows.Forms.DataGridView> je povolený.  
  
- Hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.EditMode%2A> není <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
- Vlastnosti `ReadOnly` buňky, řádku, sloupce a ovládacího prvku jsou nastaveny na `false`.  
  
 V režimu úprav může uživatel změnit hodnotu buňky a stisknutím klávesy ENTER Potvrdit změnu nebo klávesu ESC obnovit původní hodnotu buňky.  
  
 Můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> ovládací prvek tak, aby buňka vstoupila do režimu úprav, jakmile se stane aktuální buňkou. Chování kláves ENTER a ESC není v tomto případě změněno, ale buňka zůstane v režimu úprav poté, co je hodnota potvrzena nebo vrácena zpět. Můžete také nakonfigurovat ovládací prvek tak, aby buňky jako režim úprav byly zadány pouze v případě, že uživatel zadá tuto buňku, nebo pouze když uživatel stiskne klávesu F2. Nakonec můžete zabránit tomu, aby buňky vstoupily do režimu úprav s výjimkou případů, kdy zavoláte metodu <xref:System.Windows.Forms.DataGridView.BeginEdit%2A>.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>Změna režimu úprav ovládacího prvku DataGridView  
  
- Vlastnost <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> nastavte na příslušný výčet <xref:System.Windows.Forms.DataGridViewEditMode>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Odkazy na <xref:System> a <xref:System.Windows.Forms> sestavení.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
