---
title: DomainUpDown – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 86703a96d4845414d043161e0efa67bfde9278db
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745856"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DomainUpDown> je v podstatě kombinací textového pole a dvojice tlačítek pro pohyb nahoru nebo dolů v seznamu. Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu možností. Uživatel může vybrat řetězec kliknutím na tlačítko nahoru a dolů pro pohyb v seznamu stisknutím kláves se šipkami nahoru a dolů nebo zadáním řetězce, který odpovídá položce v seznamu. Jedním z možných použití tohoto ovládacího prvku je výběr položek z abecedně seřazeného seznamu názvů.  
  
> [!NOTE]
> Chcete-li seznam seřadit, nastavte vlastnost <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> na hodnotu `true`.  
  
 Funkce tohoto ovládacího prvku je velmi podobná poli seznamu nebo pole se seznamem, ale zabírá velmi málo místa.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. Vlastnost <xref:System.Windows.Forms.DomainUpDown.Items%2A> obsahuje seznam objektů, jejichž textové hodnoty jsou zobrazeny v ovládacím prvku. Pokud je <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> nastaveno na `false`, ovládací prvek automaticky dokončí text, který uživatel zadá a odpovídá hodnotě v seznamu. Pokud je <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> nastaveno na `true`, posun za poslední položkou přejde na první položku v seznamu a naopak. Klíčové metody ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Tento ovládací prvek zobrazí pouze textové řetězce. Pokud chcete ovládací prvek, který zobrazuje číselné hodnoty, použijte ovládací prvek <xref:System.Windows.Forms.NumericUpDown>. Další informace naleznete v tématu [Přehled ovládacího prvku NumericUpDown](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DomainUpDown>
- [Ovládací prvek DomainUpDown](domainupdown-control-windows-forms.md)
