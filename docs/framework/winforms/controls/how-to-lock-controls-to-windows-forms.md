---
title: 'Postupy: Uzamykání ovládacích prvků ve formulářích Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: f05da53f134f13bf5edbbe7ab8c5973f79bbca4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534742"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Postupy: Uzamykání ovládacích prvků ve formulářích Windows
Při návrhu uživatelské rozhraní (UI) aplikace systému Windows, je možné po jejich jsou umístěna správně, tak, aby není nechtěně přesunout nebo změnit jejich velikost, při nastavování jiných vlastností ovládacích prvků zamknout.  
  
 Kromě toho můžete zamykání a odemykání všechny ovládací prvky na formuláři najednou, což je užitečné pro formuláře s mnoha ovládací prvky, nebo můžete odemknout jednotlivých ovládacích prvků. Jakmile jste umístili všechny ovládací prvky. požadované místo na formuláři, uzamčení je na místě, aby se zabránilo chybné pohyb.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-lock-a-control"></a>K uzamčení ovládacího prvku  
  
1.  V **vlastnosti** okně klikněte na tlačítko **uzamčen** vlastnost a vyberte `true`. (Dvakrát klikněte na název přepne na nastavení vlastnosti).  
  
     Nebo klikněte pravým tlačítkem na ovládací prvek a zvolte **ovládací prvky zámku**.  
  
    > [!NOTE]
    >  Uzamykání ovládacích prvků sdělovat tažením nové velikosti nebo umístění na návrhovou plochu. Však můžete stále změnit velikost nebo umístění ovládacích prvků pomocí **vlastnosti** okno nebo v kódu.  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>Chcete-li zamknout všechny ovládací prvky ve formuláři  
  
1.  Z **formátu** nabídce zvolte **ovládací prvky zámku**.  
  
    > [!NOTE]
    >  Tento příkaz Zamkne velikost formuláře je také možné, protože formuláře je ovládací prvek.  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>Odemknout uzamčení všechny ovládací prvky ve formuláři  
  
1.  Z **formátu** nabídce zvolte **ovládací prvky zámku**.  
  
     Všechny dříve uzamčeném ovládací prvky na formuláři jsou nyní odemknout.  
  
### <a name="to-unlock-locked-controls-individually"></a>Odemknout uzamčení jednotlivě ovládací prvky  
  
1.  V **vlastnosti** okně klikněte na tlačítko **uzamčen** vlastnost a vyberte `false`. (Dvakrát klikněte na název přepne na nastavení vlastnosti).  
  
## <a name="see-also"></a>Viz také  
 [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)  
 [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Ovládací prvky Windows Forms podle funkce](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
