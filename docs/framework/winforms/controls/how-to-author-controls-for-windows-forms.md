---
title: 'Postupy: Autor ovládacích prvků Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
ms.openlocfilehash: a6ea57dda8f034684e8590ce4c3b6d37ab01230e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579521"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Postupy: Autor ovládacích prvků Windows Forms
Ovládací prvek představuje grafické propojení mezi uživateli a program. Ovládací prvek můžete zadat nebo zpracování dat, přijímají vstup uživatele, reagovat na události nebo provádět spoustu dalších funkcí, které se připojují uživatele a aplikace. Vzhledem k tomu, že ovládací prvek je v podstatě komponent pomocí grafického rozhraní, může sloužit všechny funkce, které nemá komponenty, a poskytnout interakce s uživatelem. Vytvoření ovládacích prvků pro obsluhu zvláštní účely a vytváření ovládacích prvků je jenom další úlohou programování. Následující kroky se na základě těchto skutečností představují Přehled ovládacího prvku proces tvorby. Další informace o odkazech na jednotlivé kroky.  
  
> [!NOTE]
>  Pokud chcete vytvořit vlastní ovládací prvek pro použití na webové formuláře, naleznete v tématu [vyvíjet vlastní serverové ovládací prvky ASP.NET](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-control"></a>Chcete-li vytvořit ovládací prvek  
  
1.  Zjistěte, co chcete ovládací prvek k provedení, nebo jaké části bude přehrávat ve vaší aplikaci. Faktory vzít v úvahu, jsou:  
  
    -   Jaký druh grafického rozhraní je potřeba?  
  
    -   Jaké konkrétní uživatelské interakce zpracuje tento ovládací prvek?  
  
    -   Poskytuje všechny existující ovládací prvky funkce, které potřebujete?  
  
    -   Dosáhnete toho, funkce, které jsou kombinací několika ovládacích prvků Windows Forms potřebujete?  
  
2.  Pokud potřebujete objektový model pro ovládací prvek, určíte, jak bude distribuované v rámci modelu objektu funkce a rozdělení funkcí mezi ovládacím prvkem a podobjektů. Objektový model může být užitečné, pokud plánujete komplexní ovládací prvek nebo chtít začlenit několika funkcí.  
  
3.  Určit typ ovládacího prvku (například uživatelský ovládací prvek, vlastní ovládací prvek, zděděný ovládací prvek Windows Forms) budete potřebovat. Podrobnosti najdete v tématu [doporučení ohledně typu ovládacího prvku](../../../../docs/framework/winforms/controls/control-type-recommendations.md) a [typy Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
4.  Express funkce jako vlastnosti, metody a události ovládacího prvku a jeho podřízeným objektům nebo podpůrné struktury a přiřaďte úrovně přístupu odpovídající (například veřejné, chráněné a tak dále).  
  
5.  Pokud potřebujete vlastní vykreslování ovládacího prvku, přidejte kód pro něj. Podrobnosti najdete v tématu [vlastní ovládací prvek Malování a vykreslování](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
6.  Pokud váš ovládací prvek dědí z <xref:System.Windows.Forms.UserControl>, můžete otestovat jeho chování za běhu sestavení projektu ovládacího prvku a jeho spuštěním **kontejner testu UserControl**. Další informace najdete v tématu [jak: Testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
7.  Můžete také testování a ladění ovládacího prvku vytvořením nového projektu, jako je například aplikace Windows a že ho umístíte do kontejneru. Tento proces je znázorněn v rámci [názorný postup: Vytvoření složeného ovládacího prvku s jazykem Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8.  Při přidávání jednotlivých funkcí, přidání funkcí do projektu testu vykonávat nové funkce.  
  
9. Zopakujte rafinace návrhu.  
  
10. Zabalení a nasazení ovládacího prvku. Podrobnosti najdete v tématu [nasazování aplikací, služeb a komponent](https://msdn.microsoft.com/library/wtzawcsz).  
  
## <a name="see-also"></a>Viz také:
- [Návod: Vytvoření složeného ovládacího prvku s jazykem Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Postupy: Dědit ze třídy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)
- [Postupy: Dědit ze třídy Control](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)
- [Postupy: Dědění z existujících Windows Forms ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)
- [Postupy: Testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
