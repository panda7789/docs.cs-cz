---
title: "Postupy: Vytváření ovládacích prvků pro Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 125e3f1c32c5186cce0b28aa3f8d1eff1ef95a09
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-author-controls-for-windows-forms"></a>Postupy: Vytváření ovládacích prvků pro Windows Forms
Ovládací prvek představuje grafické propojení mezi uživatelem a programu. Ovládací prvek můžete poskytnout nebo zpracování dat, přijímají vstup uživatele, reakce na události nebo proveďte libovolný počet dalších funkcí, které připojit aplikaci a uživatele. Protože ovládací prvek je v podstatě komponenta s grafickým rozhraním, může posloužit všechny funkce, která neobsahuje komponentu, a jejich interakci s uživatelem. Vytvoření ovládacích prvků k obsluze konkrétní účely a vytváření ovládacích prvků je jenom další programovacích úloh. Následující kroky si uvědomit, představují Přehled ovládacího prvku procesu vytváření. Odkazy poskytují další informace o jednotlivých kroků.  
  
> [!NOTE]
>  Pokud chcete vytvořit vlastní ovládací prvek použít na webových formulářů, najdete v článku [vývoj vlastních serverových ovládacích prvků ASP.NET](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-author-a-control"></a>K vytváření ovládacího prvku  
  
1.  Zjistěte, co chcete ovládacího prvku k provedení, nebo co je součástí přehraje ve vaší aplikaci. Faktory vzít v úvahu jsou:  
  
    -   Jaký druh grafické rozhraní potřebujete?  
  
    -   Jaké konkrétní interakcí zpracuje tento ovládací prvek?  
  
    -   Poskytuje všechny stávající ovládací prvky funkce, které potřebujete?  
  
    -   Můžete získat funkce, které potřebujete kombinací několik ovládací prvky Windows Forms?  
  
2.  Pokud potřebujete objektový model pro vlastní ovládací prvek, zjistěte, jak funkce bude distribuované v rámci objektový model a zdola nahoru funkcí mezi ovládacího prvku a podobjektů. Model objektu může být užitečné, pokud jsou plánování komplexní ovládací prvek nebo chtějí začlenit několik funkce.  
  
3.  Určuje typ ovládacího prvku (například uživatelský ovládací prvek, vlastní ovládací prvek, zděděné ovládacího prvku Windows Forms) potřebujete. Podrobnosti najdete v tématu [doporučení ohledně typu ovládacího prvku](../../../../docs/framework/winforms/controls/control-type-recommendations.md) a [typy vlastní prvky](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
4.  Express funkce jako vlastnosti, metod a události ovládacího prvku a jeho podřízeným objektům nebo jiné struktury a přiřaďte odpovídající přístup úrovně (například veřejné, chráněné a tak dále).  
  
5.  Pokud potřebujete vlastní Malování pro ovládací prvek, přidáte kód pro ni. Podrobnosti najdete v tématu [vlastní ovládací prvek Malování a vykreslování](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
6.  Pokud vlastní ovládací prvek dědí z <xref:System.Windows.Forms.UserControl>, můžete otestovat své chování runtime sestavení projektu ovládací prvek a jeho spuštěním **UserControl Test kontejneru**. Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
7.  Můžete také testování a ladění vlastního ovládacího prvku vytvořením nového projektu, například aplikace pro systém Windows a jeho umístění do kontejneru. Tento proces je znázorněn v rámci [návod: Vytvoření složeného ovládacího prvku pomocí Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8.  Při přidávání jednotlivých funkcí, přidejte do projektu testovací vykonávat funkci nové funkce.  
  
9. Opakujte upřesnění návrhu.  
  
10. Zabalení a nasazení vlastního ovládacího prvku. Podrobnosti najdete v tématu [nasazení aplikací, služeb a komponent](https://msdn.microsoft.com/library/wtzawcsz).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Postupy: Dědění ze třídy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Postupy: Dědění ze třídy Control](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Postupy: Dědění ze stávajících ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Postupy: Otestování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
