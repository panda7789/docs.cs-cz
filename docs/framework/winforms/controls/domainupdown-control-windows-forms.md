---
title: DomainUpDown – ovládací prvek
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: b538350a84e341d6b2759a7db28f8799f3777a86
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745837"
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown – ovládací prvek (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DomainUpDown> vypadá jako kombinace textového pole a dvojice tlačítek pro pohyb nahoru nebo dolů v seznamu. Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu možností. Uživatel může vybrat řetězec kliknutím na tlačítko nahoru a dolů pro pohyb v seznamu stisknutím kláves se šipkami nahoru a dolů nebo zadáním řetězce, který odpovídá položce v seznamu. Jedním z možných použití tohoto ovládacího prvku je výběr položek z abecedně seřazeného seznamu názvů. (Chcete-li seznam seřadit, nastavte vlastnost <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> na hodnotu `true`.) Funkce tohoto ovládacího prvku je velmi podobná poli seznamu nebo pole se seznamem, ale zabírá velmi málo místa.  
  
 Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. Vlastnost <xref:System.Windows.Forms.DomainUpDown.Items%2A> obsahuje seznam objektů, jejichž textové hodnoty jsou zobrazeny v ovládacím prvku. Pokud je <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> nastaveno na `false`, ovládací prvek automaticky dokončí text, který uživatel zadá a odpovídá hodnotě v seznamu. Pokud je <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> nastaveno na `true`, posun za poslední položkou přejde na první položku v seznamu a naopak. Klíčové metody ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Tento ovládací prvek zobrazí pouze textové řetězce. Pokud chcete ovládací prvek, který zobrazuje číselné hodnoty, použijte ovládací prvek <xref:System.Windows.Forms.NumericUpDown>. Další informace naleznete v tématu [ovládací prvek NumericUpDown](numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled ovládacího prvku DomainUpDown](domainupdown-control-overview-windows-forms.md)  
 Zavádí obecné koncepty ovládacího prvku <xref:System.Windows.Forms.DomainUpDown>, který umožňuje uživatelům procházet a vybírat ze seznamu textových řetězců.  
  
 [Postupy: Programové přidávání položek do ovládacích prvků Windows Forms DomainUpDown](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 Popisuje, jak zadat textové řetězce, které by měl ovládací prvek <xref:System.Windows.Forms.DomainUpDown> zobrazit.  
  
 [Postupy: Odebrání položek z ovládacích prvků Windows Forms DomainUpDown](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Popisuje, jak odstranit položky z ovládacího prvku <xref:System.Windows.Forms.DomainUpDown> v kódu.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Windows.Forms.DomainUpDown>  
 Popisuje tuto třídu a má odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Popisuje tuto třídu a má odkazy na všechny její členy..  
  
## <a name="related-sections"></a>Související oddíly  
 [Ovládací prvky, které můžete použít na model Windows Forms](controls-to-use-on-windows-forms.md)  
 Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.
