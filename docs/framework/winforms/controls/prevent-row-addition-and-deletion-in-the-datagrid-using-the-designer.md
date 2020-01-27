---
title: Zabránit přidávání a odstraňování řádků v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: cc9aff0f15d1bd6de5c469ee7069a99f3360837a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728705"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Někdy budete chtít uživatelům zabránit v zadávání nových řádků dat nebo odstranění existujících řádků v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Nové řádky jsou zadány do speciálního řádku pro nové záznamy v dolní části ovládacího prvku. Když zaškrtnete přidávání řádků, řádek pro nové záznamy se nezobrazí. Ovládací prvek lze následně nastavit jen pro čtení zakázáním odstranění řádků a úprav buňky.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-prevent-row-addition-and-deletion"></a>Prevence přidávání a odstraňování řádků

- V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a zrušte zaškrtnutí políčka **Povolit přidávání** a **povolování odstraňování** .

    > [!NOTE]
    > Chcete-li nastavit, aby byl ovládací prvek úplně jen pro čtení, zrušte zaškrtnutí políčka **Povolit úpravy** .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Postupy: vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
