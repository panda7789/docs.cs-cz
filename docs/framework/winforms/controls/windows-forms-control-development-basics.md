---
title: Základy pro vývoj ovládacích prvků
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: fab0a76e2f9fdb7e2f89e9d6a10dd9c522a6d8e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739918"
---
# <a name="windows-forms-control-development-basics"></a>Základní informace o vývoji ovládacích prvků Windows Forms
Model Windows Forms ovládací prvek je třída, která je odvozena přímo nebo nepřímo z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Následující seznam popisuje běžné scénáře pro vývoj model Windows Formsch ovládacích prvků:  
  
- Kombinování existujících ovládacích prvků a vytváření složeného ovládacího prvku  
  
     Složené ovládací prvky zapouzdřují uživatelské rozhraní, které lze znovu použít jako ovládací prvek. Příkladem složeného ovládacího prvku je ovládací prvek, který se skládá z textového pole a tlačítka obnovit. Vizuální návrháři nabízí bohatou podporu pro vytváření složených ovládacích prvků. Chcete-li vytvořit složený ovládací prvek, odvodit z <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. Základní třída <xref:System.Windows.Forms.UserControl> poskytuje směrování klávesnice pro podřízené ovládací prvky a umožňuje podřízeným ovládacím prvkům pracovat jako skupina. Další informace naleznete v tématu [Vývoj složeného ovládacího prvku model Windows Forms](developing-a-composite-windows-forms-control.md).  
  
- Rozšíření existujícího ovládacího prvku tak, aby ho bylo možné přizpůsobit nebo přidat k jeho funkcím.  
  
     Tlačítko, jehož barvu nelze změnit, a tlačítko, které má další vlastnost, která sleduje, kolikrát bylo kliknuto, jsou příklady rozšířených ovládacích prvků. Můžete přizpůsobit libovolný model Windows Forms ovládací prvek odvozením z něj a přepsáním nebo přidáním vlastností, metod a událostí.  
  
- Vytváření ovládacího prvku, který nespojuje ani nerozšiřuje stávající ovládací prvky.  
  
     V tomto scénáři odvodit ovládací prvek ze základní třídy <xref:System.Windows.Forms.Control>. Můžete přidat i vlastnosti přepisu, metody a události základní třídy. Chcete-li začít, přečtěte si téma [Postupy: Vývoj jednoduchého ovládacího prvku model Windows Forms](how-to-develop-a-simple-windows-forms-control.md).  
  
 Základní třída pro ovládací prvky model Windows Forms, <xref:System.Windows.Forms.Control>, poskytuje instalace, která je nutná pro vizuální zobrazení v aplikacích pro systém Windows na straně klienta. <xref:System.Windows.Forms.Control> poskytuje popisovač okna, zpracovává směrování zpráv a poskytuje události myši a klávesnice a také mnoho dalších událostí uživatelského rozhraní. Poskytuje pokročilé rozložení a obsahuje vlastnosti, které jsou specifické pro vizuální zobrazení, například <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>a mnoho dalších. Navíc poskytuje zabezpečení, podporu vláken a interoperabilitu s ovládacími prvky ActiveX. Vzhledem k tomu, že velká část infrastruktury je poskytována základní třídou, je poměrně snadné vyvíjet vlastní ovládací prvky model Windows Forms.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms](how-to-develop-a-simple-windows-forms-control.md)
- [Vývoj složeného ovládacího prvku Windows Forms](developing-a-composite-windows-forms-control.md)
- [Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
