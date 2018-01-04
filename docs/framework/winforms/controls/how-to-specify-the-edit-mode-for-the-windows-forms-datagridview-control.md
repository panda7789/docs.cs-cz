---
title: "Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView"
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
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42773e29d7071c5bc5f3d5de3660c9891788b422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView
Ve výchozím nastavení, uživatelé mohou upravovat obsah aktuální <xref:System.Windows.Forms.DataGridView> textového pole buňky zadáním v ní nebo stisknete klávesu F2. To vloží buňky v režimu úprav Pokud jsou splněny všechny následující podmínky:  
  
-   Podkladové zdroje dat, podporuje úpravy.  
  
-   <xref:System.Windows.Forms.DataGridView> Řízení je povoleno.  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A> Hodnota vlastnosti není <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
-   `ReadOnly` Vlastnosti buněk, řádků, sloupce a řízení jsou nastaveny na `false`.  
  
 Uživatel v režimu úprav, můžete změnit hodnotu buňky a stiskněte klávesu ENTER k potvrzení změn nebo ESC vrátit zpátky na původní hodnotu buňky.  
  
 Můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> řídit tak, aby buňku vstupuje do režimu úprav, jakmile bude aktuální buňky. V takovém případě se neliší chování ENTER a ESC klíče, ale buňky zůstává v režimu úprav poté, co je hodnota potvrzené nebo vrátit zpět. Ovládací prvek můžete také nakonfigurovat tak, aby pouze v případě, že uživatelé budou psát v buňce nebo pouze když uživatelé stiskněte F2 buněk vstoupit do režimu úprav. Nakonec můžete zabránit v buňkách přepnutím do režimu úprav kromě při volání <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> metoda.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>Chcete-li změnit režimu úprav ovládacího prvku DataGridView  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> vlastnost na příslušné <xref:System.Windows.Forms.DataGridViewEditMode> výčtu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazuje na <xref:System> a <xref:System.Windows.Forms> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [Zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
