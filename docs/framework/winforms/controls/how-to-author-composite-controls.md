---
title: "Postupy: Vytváření složených ovládacích prvků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf68d4927daa79e160df42f94aff9cbcb611592
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-author-composite-controls"></a>Postupy: Vytváření složených ovládacích prvků
Složené ovládací prvky mohou být použity v mnoha způsoby. Můžete je v rámci projektu aplikace pracovní plochy Windows vytvářet a používat pouze ve formulářích v projektu. Nebo můžete vytvořit je v projektu knihovny ovládacích prvků Windows, kompilace projektu do sestavení a pomocí ovládacích prvků v jiném projektu. Můžete dokonce dědit z nich a použít dědičnost vizuálních prvků se přizpůsobit rychle pro zvláštní účely.  
  
> [!NOTE]
>  Pokud chcete vytvořit složeného ovládacího prvku na webové formuláře použít, najdete v článku [vývoj vlastních serverových ovládacích prvků ASP.NET](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-author-a-composite-control"></a>Pro vytvoření složeného ovládacího prvku  
  
1.  Otevřete nový **aplikace Windows** projekt s názvem `DemoControlHost`.  
  
2.  Na **projektu**nabídky, klikněte na tlačítko **přidat uživatelský ovládací prvek**.  
  
3.  V **přidat novou položku** dialogové okno, udělte třída název chcete složeného ovládacího prvku tak, aby měl souboru (vb nebo .cs soubor).  
  
4.  Klikněte **přidat** tlačítko pro vytvoření souboru třídy složeného ovládacího prvku.  
  
5.  Přidání ovládacích prvků z **sada nástrojů** na povrchu složeného ovládacího prvku.  
  
6.  V postupech událostí ke zpracování událostí vyvolaných složeného ovládacího prvku, nebo jeho základní ovládací prvky umístěte kód.  
  
7.  Zavřít návrháře složeného ovládacího prvku a uložte soubor po zobrazení výzvy.  
  
8.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Projekt musí být součástí pořadí u vlastních ovládacích prvků, než se objeví na **sada nástrojů**.  
  
9. Použití **DemoControlHost** kartě **sada nástrojů** přidání instancí ovládacího prvku na `Form1`.  
  
### <a name="to-author-a-control-class-library"></a>Pro vytvoření knihovny tříd ovládacího prvku  
  
1.  Otevřete nový **knihovny ovládacích prvků Windows** projektu.  
  
     Ve výchozím nastavení obsahuje projektu složeného ovládacího prvku.  
  
2.  Přidejte ovládacími prvky a kódem, jak je popsáno v předchozím postupu.  
  
3.  Vyberte ovládací prvek nechcete dědění třídy změnit, a nastavte **modifikátory** vlastnosti tohoto ovládacího prvku na **privátní**.  
  
4.  Vytvořte knihovnu DLL.  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Dědění z složeného ovládacího prvku v knihovnu tříd ovládacího prvku  
  
1.  Na **souboru** nabídky, přejděte na příkaz **přidat** a vyberte **nový projekt** přidat nový **aplikace pro systém Windows** projektu k řešení.  
  
2.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** složku pro nové projektu a zvolte **přidat odkaz na** otevřete **přidat odkaz na**dialogové okno.  
  
3.  Vyberte **projekty** kartě a dvakrát klikněte na projekt knihovny ovládacího prvku.  
  
4.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
5.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt knihovny ovládací prvek a vyberte **přidat novou položku** z místní nabídky.  
  
6.  Vyberte **zděděná uživatelský ovládací prvek** šablony z **přidat novou položku** dialogové okno.  
  
7.  V **výběr dědičnosti** dialogové okno pole, dvakrát klikněte na chcete použít dědění z ovládacího prvku.  
  
     Nový ovládací prvek se přidá do projektu.  
  
8.  Otevřete vizuálního návrháře pro nový ovládací prvek a přidat další základních ovládacích prvků.  
  
     Zobrazí se základní ovládací prvky, které byly zděděno z složeného ovládacího prvku v knihovně DLL a upravíte vlastnosti ovládacích prvků jejichž **modifikátory** vlastnost je **veřejné**. Nelze změnit vlastnosti ovládacího prvku jehož **modifikátory** vlastnost je **privátní**.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [Doporučení ohledně typu ovládacího prvku](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [Postupy: Vytváření ovládacích prvků pro Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
