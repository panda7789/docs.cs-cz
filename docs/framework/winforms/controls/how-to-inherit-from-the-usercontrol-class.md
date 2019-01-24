---
title: 'Postupy: Dědit ze třídy UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 4c3f3d6775f3fdf511e59b360d6c356e2d4fabee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532094"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Postupy: Dědit ze třídy UserControl
Kombinování funkcí jeden nebo více ovládacích prvků Windows Forms s vlastní kód, můžete vytvořit *uživatelský ovládací prvek*. Uživatelské ovládací prvky zkombinovat vývoj rychlé ovládacích prvků, funkce a všestrannost vlastní vlastnosti a metody ovládacího prvku standardní formulářů Windows. Když začnete vytvoření uživatelského ovládacího prvku, zobrazí se viditelné designer, na kterém můžete umístit standardní ovládací prvky Windows Forms. Tyto ovládací prvky zachovat všechny své vlastní funkce, jakož i vzhled a chování (vzhled a chování) standardní ovládací prvky. Jakmile tyto ovládací prvky jsou integrované do uživatelského ovládacího prvku, ale už nejsou k dispozici prostřednictvím kódu. Uživatelský ovládací prvek provede vlastní vykreslovací a také zpracovává všechny základní funkce související s ovládacími prvky.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-user-control"></a>Chcete-li vytvořit uživatelský ovládací prvek  
  
1.  Vytvořte nový **Knihovna ovládacích prvků Windows** projektu.  
  
     Nový projekt je vytvořen s prázdný uživatelský ovládací prvek.  
  
2.  Přetáhněte ovládací prvky z **Windows Forms** karty **nástrojů** do návrháře.  
  
3.  Tyto ovládací prvky by měl umístěn a navržená tak, jak mají zobrazit v ovládacím prvku konečného uživatele. Pokud chcete umožňují vývojářům pro přístup k základní ovládací prvky, musí deklarovat jako public nebo selektivně vystavení vlastností základních ovládacího prvku. Podrobnosti najdete v tématu [jak: Vystavení vlastností základních ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).  
  
4.  Implementujte všechny vlastní metody nebo vlastnosti, které bude obsahovat váš ovládací prvek.  
  
5.  Stisknutím klávesy F5 sestavte projekt a spusťte váš ovládací prvek **UserControl – kontejner testů**. Další informace najdete v tématu [jak: Testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
## <a name="see-also"></a>Viz také:
- [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
- [Postupy: Dědit ze třídy Control](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)
- [Postupy: Dědění z existujících Windows Forms ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)
- [Postupy: Autor ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)
- [Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Postupy: Testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
