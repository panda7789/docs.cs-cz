---
title: DomainUpDown – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: bfe3e7239f77c6f1a0d9bb46a96c704653b43364
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102853"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> ovládací prvek je v podstatě kombinací textové pole a pár tlačítek pro procházení seznamu nahoru nebo dolů. Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu nabízených možností. Uživatel může vybrat řetězec klepáním na tlačítka procházení seznamu, stisknutím klávesy se šipkami nahoru a dolů nebo tak, že zadáte řetězec, který odpovídá položka v seznamu. Je možné použití pro tento ovládací prvek pro výběr položek ze seřazené podle abecedy seznam názvů.  
  
> [!NOTE]
>  Chcete-li seřadit seznam, nastavte <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> vlastnost `true`.  
  
 Funkce tohoto ovládacího prvku se velmi podobá seznamu nebo pole se seznamem, ale zabírá velmi málo místa.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Jsou klíčové vlastnosti ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Vlastnost obsahuje seznam objektů, jejichž hodnoty text se zobrazí v ovládacím prvku. Pokud <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> je nastavena na `false`, ovládací prvek automaticky dokončí text, že uživatel zadá a odpovídá hodnotě v seznamu. Pokud <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> je nastavena na `true`, posouvání za poslední položky se dostanete k první položku v seznamu a naopak. Jsou klíčové metody ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Tento ovládací prvek zobrazuje pouze textové řetězce. Pokud chcete ovládací prvek, který zobrazí číselných hodnot, použijte <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku. Další informace najdete v tématu [Přehled ovládacího prvku NumericUpDown](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DomainUpDown>
- [Ovládací prvek DomainUpDown](domainupdown-control-windows-forms.md)
