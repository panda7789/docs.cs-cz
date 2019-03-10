---
title: DomainUpDown – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: 83d674e3fb7ff7e715b75c635b891cd4e9703a21
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704528"
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown – ovládací prvek (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> ovládací prvek vypadá jako kombinace textové pole a pár tlačítek pro procházení seznamu nahoru nebo dolů. Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu nabízených možností. Uživatel může vybrat řetězec klepáním na tlačítka procházení seznamu, stisknutím klávesy se šipkami nahoru a dolů nebo tak, že zadáte řetězec, který odpovídá položka v seznamu. Je možné použití pro tento ovládací prvek pro výběr položek ze seřazené podle abecedy seznam názvů. (Chcete-li seřadit seznam, nastavte <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> vlastnost `true`.) Funkce tohoto ovládacího prvku se velmi podobá seznamu nebo pole se seznamem, ale zabírá velmi málo místa.  
  
 Jsou klíčové vlastnosti ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Vlastnost obsahuje seznam objektů, jejichž hodnoty text se zobrazí v ovládacím prvku. Pokud <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> je nastavena na `false`, ovládací prvek automaticky dokončí text, že uživatel zadá a odpovídá hodnotě v seznamu. Pokud <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> je nastavena na `true`, posouvání za poslední položky se dostanete k první položku v seznamu a naopak. Jsou klíčové metody ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Tento ovládací prvek zobrazuje pouze textové řetězce. Pokud chcete ovládací prvek, který zobrazí číselných hodnot, použijte <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku. Další informace najdete v tématu [ovládací prvek NumericUpDown](numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled ovládacího prvku DomainUpDown](domainupdown-control-overview-windows-forms.md)  
 Představuje obecné koncepty <xref:System.Windows.Forms.DomainUpDown> ovládací prvek, který uživatelům umožňuje procházet a vyberte ze seznamu textového řetězce.  
  
 [Postupy: Programové přidání položek do ovládacích prvků Windows Forms DomainUpDown](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 Popisuje, jak určit textové řetězce <xref:System.Windows.Forms.DomainUpDown> ovládací prvek by měl zobrazit.  
  
 [Postupy: Odebrání položek z ovládacích prvků Windows Forms DomainUpDown](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Popisuje postup odstranění položek z <xref:System.Windows.Forms.DomainUpDown> ovládacího prvku v kódu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.DomainUpDown>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy...  
  
## <a name="related-sections"></a>Související oddíly  
 [Ovládací prvky používané ve formulářích Windows](controls-to-use-on-windows-forms.md)  
 Obsahuje úplný seznam všech ovládacích prvcích Windows Forms, s odkazy na informace o jejich použití.
