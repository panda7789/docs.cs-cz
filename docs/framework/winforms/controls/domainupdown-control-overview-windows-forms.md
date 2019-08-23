---
title: DomainUpDown – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965304"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown – přehled ovládacího prvku (Windows Forms)
Model Windows Forms <xref:System.Windows.Forms.DomainUpDown> ovládací prvek je v podstatě kombinací textového pole a dvojice tlačítek pro pohyb nahoru nebo dolů v seznamu. Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu možností. Uživatel může vybrat řetězec kliknutím na tlačítko nahoru a dolů pro pohyb v seznamu stisknutím kláves se šipkami nahoru a dolů nebo zadáním řetězce, který odpovídá položce v seznamu. Jedním z možných použití tohoto ovládacího prvku je výběr položek z abecedně seřazeného seznamu názvů.  
  
> [!NOTE]
> Chcete-li seznam seřadit, nastavte <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> vlastnost na `true`hodnotu.  
  
 Funkce tohoto ovládacího prvku je velmi podobná poli seznamu nebo pole se seznamem, ale zabírá velmi málo místa.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Vlastnost obsahuje seznam objektů, jejichž textové hodnoty jsou zobrazeny v ovládacím prvku. Pokud <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> je nastaveno na `false`, ovládací prvek automaticky dokončí text, který uživatel zadá a odpovídá hodnotě v seznamu. Pokud <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> je nastaveno na `true`, posun za poslední položkou přejde na první položku v seznamu a naopak. Klíčové metody ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a. <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>  
  
 Tento ovládací prvek zobrazí pouze textové řetězce. Pokud chcete ovládací prvek, který zobrazuje číselné hodnoty, použijte <xref:System.Windows.Forms.NumericUpDown> ovládací prvek. Další informace naleznete v tématu [Přehled ovládacího prvku NumericUpDown](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DomainUpDown>
- [Ovládací prvek DomainUpDown](domainupdown-control-windows-forms.md)
