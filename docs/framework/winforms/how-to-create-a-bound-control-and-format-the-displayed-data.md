---
title: 'Postupy: Vytvoření připojeného ovládacího prvku a formátování zobrazených dat'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 8f4d3c4c738e31ab83d506dc7afb4e49b142765b
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508007"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Postupy: Vytvoření připojeného ovládacího prvku a formátování zobrazených dat
Pomocí Windows Forms – datová vazba, lze formátovat data zobrazená v ovládací prvek vázaný na data pomocí **formátování a rozšířené vazby** dialogové okno.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a>K vytvoření vazby ovládacího prvku a formátování zobrazených dat  
  
1.  Připojení ke zdroji dat.  
  
     Další informace najdete v tématu [připojení ke zdroji dat](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  Ve formuláři vyberte ovládací prvek a potom otevřete okno Vlastnosti.  
  
3.  Rozbalte **(DataBindings)** vlastnost a potom v **(rozšířené)** klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) zobrazíte **formátování a rozšířené vazby** dialogové okno, které obsahuje úplný seznam vlastností pro ovládací prvek.  
  
4.  Vyberte vlastnost, kterou chcete vytvořit vazbu a potom klikněte na **vazby** šipku.  
  
     Zobrazí se seznam dostupných datových zdrojů.  
  
5.  Rozbalení zdroje dat, kterou chcete svázat, dokud nenajdete jeden datový element, který chcete.  
  
     Pokud vytváříte vazbu na hodnotu sloupce v tabulce datové sady, rozbalte název datové sady a potom rozbalte název tabulky, chcete-li zobrazit názvy sloupců.  
  
6.  Klikněte na název elementu k vytvoření vazby.  
  
7.  V **typ** klikněte na formát, který chcete použít pro data zobrazí v ovládacím prvku.  
  
     V každém případě můžete zadat hodnotu, pokud obsahuje zdroj dat se zobrazí v ovládacím prvku <xref:System.DBNull>. V opačném případě možnosti mírně lišit v závislosti na zvoleném typu formátu. V následující tabulce jsou uvedeny typy formátů a možnosti.  
  
    |Typ formátu|Možnost formátování|  
    |-----------------|-----------------------|  
    |Žádné formátování|Žádné možnosti.|  
    |Číselné|Zadejte počet desetinných míst s použitím **desetinných míst** číselníku.|  
    |Měna|Zadejte počet desetinných míst s použitím **desetinných míst** číselníku.|  
    |Datum a čas|Vyberte datum a čas by měl být zobrazení tak, že vyberete jednu z položek v **typ** výběru.|  
    |vědecké|Zadejte počet desetinných míst s použitím **desetinných míst** číselníku.|  
    |Vlastní|Zadejte řetězec vlastního formátu pomocí.<br /><br /> Další informace najdete v tématu [Formatting Types](../../../docs/standard/base-types/formatting-types.md). **Poznámka:** vlastních formátovacích řetězců není zaručeno úspěšně odezvy komunikace mezi zdrojem dat a vázaného ovládacího prvku. Místo toho zpracovat <xref:System.Windows.Forms.Binding.Parse> nebo <xref:System.Windows.Forms.Binding.Format> události pro vazbu a použití vlastního formátování v kódu pro zpracování událostí.|  
  
8.  Klikněte na tlačítko **OK** zavřete **formátování a rozšířené vazby** dialogové okno a vraťte se do okna Vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [Ověřování uživatelského vstupu ve Windows Forms](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)
