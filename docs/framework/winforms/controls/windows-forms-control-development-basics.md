---
title: "Základní informace o vývoji ovládacích prvků Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca2bac983e25ab7453230a6718fe7eaa98e82275
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-control-development-basics"></a>Základní informace o vývoji ovládacích prvků Windows Forms
Ovládacího prvku Windows Forms je třída, která je odvozena přímo nebo nepřímo z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Následující seznam popisuje běžné scénáře pro vývoj Windows Forms – ovládací prvky:  
  
-   Kombinování stávající ovládací prvky pro vytvoření složeného ovládacího prvku.  
  
     Složené ovládací prvky pro zapouzdření uživatelské rozhraní, které lze znovu použít jako ovládací prvek. Příkladem složeného ovládacího prvku je ovládací prvek, který se skládá z textového pole a tlačítko pro obnovení. Visual Designer nabízí bohatou podporu pro vytváření složených prvků. K vytváření složených prvků, jsou odvozeny od <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. Základní třída <xref:System.Windows.Forms.UserControl> poskytuje směrování klávesnice pro podřízené prvky a umožňuje podřízené ovládací prvky pro práci jako skupina. Další informace najdete v tématu [vývoj složeného ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
-   Rozšíření existujícího ovládacího prvku a přizpůsobit nebo přidat do svých funkcí.  
  
     Tlačítko, jehož barvu nelze změnit a tlačítko, které má další vlastnost, která sleduje kolikrát bylo stisknuto jsou příklady rozšířených ovládacích prvků. Odvozování z něj a přepsání nebo přidáním vlastností, metod a událostí můžete přizpůsobit libovolný ovládací prvek Windows Forms.  
  
-   Vytvoření ovládacího prvku, který nemá kombinovat nebo rozšířit stávající ovládací prvky.  
  
     V tomto scénáři odvozeny od základní třídy vlastního ovládacího prvku <xref:System.Windows.Forms.Control>. Vám může přidat, stejně jako přepsat vlastnosti, metod a události základní třídy. Abyste mohli začít, najdete v části [postup: vývoj jednoduchého prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 Základní třída pro ovládací prvky Windows Forms, <xref:System.Windows.Forms.Control>, poskytuje vložení požadované pro visual zobrazení na straně klienta aplikace pro systém Windows. <xref:System.Windows.Forms.Control>poskytuje popisovač okna, zpracovává směrování zpráv a poskytuje události myši a klávesnice, jakož i mnoho dalších uživatel událostí rozhraní. Poskytuje pokročilé rozložení a má vlastnosti specifické pro visual zobrazení, jako například <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>a mnohé další. Kromě toho poskytuje zabezpečení, dělení na vlákna podporu a vzájemná funkční spolupráce s ovládacími prvky ActiveX. Protože mnoho infrastruktury od základní třídy, je poměrně snadné ho vyvíjet vlastní ovládací prvky Windows Forms.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vývoj ovládacího prvku jednoduché Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Vývoj ovládacího prvku složené Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Postupy: vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
