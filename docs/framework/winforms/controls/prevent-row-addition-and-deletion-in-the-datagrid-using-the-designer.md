---
title: 'Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 20f9b85dc48ccd634468d0fed000120723f8ee5c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038193"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Někdy budete chtít uživatelům zabránit v zadávání nových řádků dat nebo při odstraňování stávajících řádků v <xref:System.Windows.Forms.DataGridView> ovládacím prvku. Nové řádky jsou zadány do speciálního řádku pro nové záznamy v dolní části ovládacího prvku. Když zaškrtnete přidávání řádků, řádek pro nové záznamy se nezobrazí. Ovládací prvek lze následně nastavit jen pro čtení zakázáním odstranění řádků a úprav buňky.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

## <a name="to-prevent-row-addition-and-deletion"></a>Prevence přidávání a odstraňování řádků

- V <xref:System.Windows.Forms.DataGridView> pravém horním rohu ovládacího prvku klikněte na glyf inteligentních značek ((./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")![glyf inteligentních značek]) a zrušte zaškrtnutí políčka **Povolit přidávání** a **povolování odstraňování** .

    > [!NOTE]
    >  Chcete-li nastavit, aby byl ovládací prvek úplně jen pro čtení, zrušte zaškrtnutí políčka **Povolit úpravy** .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Postupy: Vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
