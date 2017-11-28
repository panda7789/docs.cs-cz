---
title: "Postupy: Dědění ze třídy UserControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fbeb2712742ae4c500ccd14a19c397d5d411c73a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Postupy: Dědění ze třídy UserControl
Chcete-li funkci jeden nebo více ovládacích prvků Windows Forms kombinovat s vlastní kód, můžete vytvořit *uživatelský ovládací prvek*. Uživatelské ovládací prvky kombinovat vývoj rychlé ovládacího prvku, funkce a všestrannost vlastní vlastnosti a metody ovládací prvek standardní Windows Forms. Když začnete vytvoření uživatelského ovládacího prvku, máte k ruce viditelné designer, na který můžete umístit standardní ovládací prvky Windows Forms. Tyto ovládací prvky zachovat všechny jejich vyplývajících funkce, jakož i vzhled a chování (vzhled a chování) standardní ovládací prvky. Jakmile tyto ovládací prvky jsou součástí uživatelského ovládacího prvku, ale jsou již k dispozici prostřednictvím kódu. Uživatelský ovládací prvek nepodporuje svůj vlastní Malování a také zpracovává všechny základní funkce související s ovládacími prvky.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-user-control"></a>Vytvoření uživatelského ovládacího prvku  
  
1.  Vytvořte novou **knihovny ovládacích prvků Windows** projektu.  
  
     Nový projekt se vytvoří s prázdnou uživatelského ovládacího prvku.  
  
2.  Přetáhněte ovládací prvky z **Windows Forms** kartě **sada nástrojů** do vašeho návrháře.  
  
3.  Tyto ovládací prvky by měl být umístěný a navržená tak, jak chcete, aby se objevily v ovládacím prvku konečného uživatele. Pokud chcete povolit uživatelům přístup k základní ovládací prvky, musí deklarovat jako veřejný nebo selektivně vystavení vlastností základních ovládacího prvku. Podrobnosti najdete v tématu [postupy: vystavení vlastností prvku prvky](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).  
  
4.  Implementujte jakékoliv vlastní metody nebo vlastnosti, které bude obsahovat vlastní ovládací prvek.  
  
5.  Stiskněte klávesu F5, aby se projekt sestavil a spuštění vlastního ovládacího prvku v **UserControl – kontejner testů**. Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
## <a name="see-also"></a>Viz také  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Postupy: dědění ze třídy Control](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Postupy: dědění ze stávajícího systému Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Postupy: vytváření ovládacích prvků pro Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
