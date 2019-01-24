---
title: 'Postupy: Vytváření složených ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: f2dc0ca7c2514ad444904b707a2cea9d57849660
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549795"
---
# <a name="how-to-author-composite-controls"></a>Postupy: Vytváření složených ovládacích prvků
Složené ovládací prvky mohou být použity v mnoha způsoby. Můžete vytvářet je v rámci projektu aplikace klasické pracovní plochy Windows a používat pouze u formulářů v projektu. Nebo můžete vytvářet v projektu knihovny ovládací prvků Windows, zkompilujte projekt do sestavení a pomocí ovládacích prvků v jiných projektech. Dokonce je možné zdědit z nich a můžete si je přizpůsobit rychle pro zvláštní účely vizuální dědění.  
  
> [!NOTE]
>  Pokud chcete vytvořit složeného ovládacího prvku k použití na webové formuláře, naleznete v tématu [vývoj vlastních serverových ovládacích prvků ASP.NET](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-composite-control"></a>Pro vytvoření složeného ovládacího prvku  
  
1.  Otevřete novou **aplikace Windows** projekt s názvem `DemoControlHost`.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat uživatelský ovládací prvek**.  
  
3.  V **přidat novou položku** dialogové okno, poskytují třídy soubor (.vb nebo .cs) název, který chcete mít složeného ovládacího prvku.  
  
4.  Vyberte **přidat** tlačítko pro vytvoření souboru třídy složeného ovládacího prvku.  
  
5.  Přidání ovládacích prvků **nástrojů** na povrchu složeného ovládacího prvku.  
  
6.  Umístěte kód procedury událostí ke zpracování událostí vyvolaných pomocí složeného ovládacího prvku nebo jeho základní ovládací prvky.  
  
7.  Zavřít Návrhář složeného ovládacího prvku a uložte soubor po zobrazení výzvy.  
  
8.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Projekt musí být sestaveny v pořadí pro vlastní ovládací prvky se zobrazí v **nástrojů**.  
  
9. Použití **DemoControlHost** karty **nástrojů** přidat instance ovládacího prvku na `Form1`.  
  
### <a name="to-author-a-control-class-library"></a>Chcete-li vytvořit knihovnu tříd ovládacího prvku  
  
1.  Otevřete novou **Knihovna ovládacích prvků Windows** projektu.  
  
     Ve výchozím nastavení projekt obsahuje složeného ovládacího prvku.  
  
2.  Přidání ovládacích prvků a kód, jak je popsáno v předchozím postupu.  
  
3.  Zvolte ovládací prvek nechcete, aby dědění třídy změnit a nastavit **modifikátory** vlastnosti tohoto ovládacího prvku na **privátní**.  
  
4.  Sestavení knihovny DLL.  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Chcete-li dědit ze složeného ovládacího prvku v knihovně tříd ovládacího prvku  
  
1.  Na **souboru** nabídky, přejděte k **přidat** a vyberte **nový projekt** přidáte nový **aplikace Windows** projektu do řešení.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** složku pro nový projekt a zvolte **přidat odkaz** otevřít **přidat odkaz**dialogové okno.  
  
3.  Vyberte **projekty** kartě a dvakrát klikněte na váš projekt knihovny ovládacích prvků.  
  
4.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
5.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na váš projekt knihovny ovládacích prvků a vyberte **přidat novou položku** z místní nabídky.  
  
6.  Vyberte **zděděné uživatelský ovládací prvek** šablonu z **přidat novou položku** dialogové okno.  
  
7.  V **výběr dědičnosti** dialogové okno pole, poklepejte na ovládací prvek se má Zdědit z.  
  
     Nový ovládací prvek se přidá do vašeho projektu.  
  
8.  Otevřete vizuálního návrháře pro nový ovládací prvek a přidat další základní ovládací prvky.  
  
     Můžete zjistit základní ovládací prvky, které byly zděděny ze složeného ovládacího prvku v knihovně DLL, ale můžete změnit vlastnosti ovládacích prvků jehož **modifikátory** vlastnost **veřejné**. Nelze změnit vlastnosti ovládacího prvku jehož **modifikátory** vlastnost **privátní**.  
  
## <a name="see-also"></a>Viz také:
- [Návod: Vytvoření složeného ovládacího prvku s jazykem Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [Doporučení ohledně typu ovládacího prvku](../../../../docs/framework/winforms/controls/control-type-recommendations.md)
- [Postupy: Autor ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)
- [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
