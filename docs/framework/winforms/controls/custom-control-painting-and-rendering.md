---
title: "Malování a vykreslování vlastního ovládacího prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 355a5842348aa4395d1841d0343080ddef634456
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-control-painting-and-rendering"></a>Malování a vykreslování vlastního ovládacího prvku
Vlastní vykreslování ovládacích prvků je jedním z mnoha složitá úloha, umožněno pomocí rozhraní .NET Framework. Při vytváření vlastního ovládacího prvku, máte mnoho možnosti týkající se grafické vzhledu ovládacího prvku. Vytváříte-li ovládací prvek, který dědí z `Control`, je nutné zadat kód, který umožňuje vaší řídit k vykreslení jeho grafické reprezentace. Pokud vytváříte uživatelský ovládací prvek dědění ze `UserControl`, nebo se dědí z jednoho z ovládacích prvků Windows Forms, můžete přepsat standardní grafické vyjádření a zadejte vlastní kód grafiky. Pokud chcete zadat vlastní vykreslení pro základní ovládací prvky systému `UserControl` vytváříte, možnosti omezenější, ale stále povolit širokou škálu grafické možnosti pro ovládací prvky a aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vykreslení ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 Ukazuje, jak program logiky, která zobrazuje ovládacího prvku.  
  
 [Ovládací prvky vykreslované uživatelem](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 Poskytuje přehled jednotlivými kroky při psaní a přepsání kód vykreslování ovládacího prvku.  
  
 [Základní ovládací prvky](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 Popisuje, jak implementovat vlastní vykreslení kód pro základních ovládacích prvků ve formulářích a uživatelské ovládací prvky.  
  
 [Postupy: Skrytí vlastního ovládacího prvku za běhu](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 Ukazuje, jak používat <xref:System.Windows.Forms.Control.Visible%2A> vlastnost skrýt a zobrazit ovládacího prvku.  
  
 [Postupy: Zajištění průhledného pozadí pro vlastní ovládací prvek](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 Ukazuje, jak používat <xref:System.Windows.Forms.Control.SetStyle%2A> metodu pro vytvoření barvu pozadí, který je plné krytí, transparentní nebo částečně transparentní.  
  
 [Vykreslování ovládacích prvků s vizuálními styly](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 Ukazuje, jak k vykreslení ovládacích prvků pomocí vizuální styly v operačních systémech, které je podporují.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Control>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.UserControl>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Popisuje tuto metodu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: Vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 Představuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkce grafiky sady Visual Studio perspektivy a poskytuje odkazy na další informace.  
  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 Popisuje typy vlastních ovládacích prvků, které můžete vytvářet.
