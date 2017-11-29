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
ms.openlocfilehash: babf3d235f4cca61ad6d0e5fdc4e6b6146c7d060
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="custom-control-painting-and-rendering"></a>Malování a vykreslování vlastního ovládacího prvku
Vlastní vykreslování ovládacích prvků je jedním z mnoha složitá úloha, umožněno pomocí rozhraní .NET Framework. Při vytváření vlastního ovládacího prvku, máte mnoho možnosti týkající se grafické vzhledu ovládacího prvku. Vytváříte-li ovládací prvek, který dědí z `Control`, je nutné zadat kód, který umožňuje vaší řídit k vykreslení jeho grafické reprezentace. Pokud vytváříte uživatelský ovládací prvek dědění ze `UserControl`, nebo se dědí z jednoho z ovládacích prvků Windows Forms, můžete přepsat standardní grafické vyjádření a zadejte vlastní kód grafiky. Pokud chcete zadat vlastní vykreslení pro základní ovládací prvky systému `UserControl` vytváříte, možnosti omezenější, ale stále povolit širokou škálu grafické možnosti pro ovládací prvky a aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vykreslování ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 Ukazuje, jak program logiky, která zobrazuje ovládacího prvku.  
  
 [Ovládací prvky vykreslované uživatelem](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 Poskytuje přehled jednotlivými kroky při psaní a přepsání kód vykreslování ovládacího prvku.  
  
 [Základní ovládací prvky](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 Popisuje, jak implementovat vlastní vykreslení kód pro základních ovládacích prvků ve formulářích a uživatelské ovládací prvky.  
  
 [Postupy: skrytí vlastního ovládacího prvku za běhu](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 Ukazuje, jak používat <xref:System.Windows.Forms.Control.Visible%2A> vlastnost skrýt a zobrazit ovládacího prvku.  
  
 [Postupy: poskytnout vlastní ovládací prvek průhledné pozadí](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 Ukazuje, jak používat <xref:System.Windows.Forms.Control.SetStyle%2A> metodu pro vytvoření barvu pozadí, který je plné krytí, transparentní nebo částečně transparentní.  
  
 [Vykreslení ovládacích prvků s vizuálními styly](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 Ukazuje, jak k vykreslení ovládacích prvků pomocí vizuální styly v operačních systémech, které je podporují.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Control>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.UserControl>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Popisuje tuto metodu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 Představuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkce grafiky sady Visual Studio perspektivy a poskytuje odkazy na další informace.  
  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 Popisuje typy vlastních ovládacích prvků, které můžete vytvářet.
