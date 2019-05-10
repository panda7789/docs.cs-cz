---
title: Základní informace o vývoji ovládacích prvků Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: 8d9dedc016a8fda654fecb2ee09c7206b3ddea82
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584772"
---
# <a name="windows-forms-control-development-basics"></a>Základní informace o vývoji ovládacích prvků Windows Forms
Je třída, která je odvozena přímo nebo nepřímo z ovládacího prvku Windows Forms <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Následující seznam popisuje běžné scénáře pro vývoj ovládacích prvků Windows Forms:  
  
- Kombinování existující ovládací prvky pro vytvoření složeného ovládacího prvku.  
  
     Složené ovládací prvky zapouzdřují uživatelské rozhraní, které lze znovu použít jako ovládací prvek. Příklad složený ovládací prvek je ovládací prvek, který se skládá z textového pole a tlačítko pro obnovení. Vizuální návrhářské nástroje nabízí bohatou podporu pro vytváření složených ovládacích prvků. Pro vytvoření složeného ovládacího prvku, jsou odvozeny z <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. Základní třída <xref:System.Windows.Forms.UserControl> zajišťuje směrování klávesnice pro podřízené ovládací prvky a umožňuje podřízené ovládací prvky pro práci s jako skupinu. Další informace najdete v tématu [vývoj složeného ovládacího prvku Windows Forms](developing-a-composite-windows-forms-control.md).  
  
- Rozšíření existujícího ovládacího prvku jej přizpůsobit nebo přidat její funkčnosti.  
  
     Tlačítko, jejichž barva se nedá změnit a tlačítko, které obsahuje další vlastnost, který sleduje, kolikrát se kliklo jsou příkladem rozšířené ovládací prvky. Můžete přizpůsobit libovolný ovládací prvek Windows Forms odvozený z něj a přepsání nebo přidáním vlastnosti, metody a události.  
  
- Vytvoření ovládacího prvku, který kombinovat nebo rozšířit existující ovládací prvky.  
  
     V tomto scénáři odvozen od základní třídy ovládacího prvku <xref:System.Windows.Forms.Control>. Můžete lze přidat také přepsat vlastnosti, metody a události základní třídy. Abyste mohli začít, najdete v článku [jak: Vývoj ovládacího prvku jednoduchého Windows Forms](how-to-develop-a-simple-windows-forms-control.md).  
  
 Základní třída pro ovládací prvky Windows Forms, <xref:System.Windows.Forms.Control>, poskytuje zajistí funkčnost systému vyžadované pro zobrazení vizuálu v aplikacích založených na Windows na straně klienta. <xref:System.Windows.Forms.Control> obsahuje popisovač okna, zpracovává směrování zpráv a události myši a klávesnice, stejně jako mnoho dalších uživatelské rozhraní události. Poskytuje pokročilé rozložení a má vlastnosti specifické pro zobrazení vizuálu, například <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>a mnoha dalších. Kromě toho poskytuje zabezpečení, práce s vlákny podpory a vzájemná funkční spolupráce s ovládacími prvky ActiveX. Protože tolik infrastruktury poskytuje základní třídy, je poměrně snadné pro vývoj vlastních ovládacích prvků Windows Forms.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vývoj ovládacího prvku jednoduchého Windows Forms](how-to-develop-a-simple-windows-forms-control.md)
- [Vývoj složeného ovládacího prvku Windows Forms](developing-a-composite-windows-forms-control.md)
- [Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
