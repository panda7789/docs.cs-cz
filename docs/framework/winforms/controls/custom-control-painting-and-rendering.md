---
title: Malování a vykreslování vlastního ovládacího prvku
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: ec9002ffa4a7e2c82f59d52344764a01afe4c568
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722136"
---
# <a name="custom-control-painting-and-rendering"></a>Malování a vykreslování vlastního ovládacího prvku
Vlastní vykreslování ovládacích prvků je jednou z mnoha složité úkoly snadné rozhraním .NET Framework. Při vytváření vlastního ovládacího prvku, máte celou řadu možností týkající se vzhled grafického ovládacího prvku. Vytváříte-li ovládací prvek, který dědí z `Control`, je nutné zadat kód, který umožňuje ovládacího prvku k vykreslení jeho grafickou reprezentaci. Pokud vytváříte uživatelský ovládací prvek děděním z `UserControl`, nebo dědí z jednoho z ovládacích prvků Windows Forms, mohou přepsat standardní grafické vyjádření a poskytují grafického kódu. Pokud chcete poskytnout vlastní vykreslování pro základní ovládací prvky `UserControl` vytváříte, vaše možnosti omezenější, ale přesto umožňuje širokou škálu grafické možnosti pro ovládací prvky a aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vykreslení ovládacího prvku Windows Forms](rendering-a-windows-forms-control.md)  
 Ukazuje, jak aplikaci logiky, která se zobrazí ovládací prvek.  
  
 [Ovládací prvky vykreslované uživatelem](user-drawn-controls.md)  
 Poskytuje přehled o postup psaní a přepsáním kód pro vykreslování ovládacího prvku.  
  
 [Základní ovládací prvky](constituent-controls.md)  
 Popisuje, jak implementovat vlastní vykreslování kód pro základních ovládacích prvků ve formulářích a uživatelských ovládacích prvků.  
  
 [Postupy: Skrytí vlastního ovládacího prvku za běhu](how-to-make-your-control-invisible-at-run-time.md)  
 Ukazuje způsob použití <xref:System.Windows.Forms.Control.Visible%2A> vlastnost skrytí a zobrazení ovládacího prvku.  
  
 [Postupy: Zadejte svůj ovládací prvek průhledné pozadí](how-to-give-your-control-a-transparent-background.md)  
 Ukazuje způsob použití <xref:System.Windows.Forms.Control.SetStyle%2A> metodu pro vytvoření barvu pozadí, který je neprůhledný, průhledného nebo částečně.  
  
 [Vykreslování ovládacích prvků s vizuálními styly](rendering-controls-with-visual-styles.md)  
 Ukazuje, jak pro vykreslení ovládacích prvků pomocí vizuálních stylů v operačních systémech, které je podporují.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Control>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.UserControl>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Popisuje tuto metodu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: Vytváření grafických objektů pro kreslení](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 Zavádí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafické funkce z Visual Studio perspektivy a poskytuje odkazy na další informace.  
  
 [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)  
 Popisuje typy vlastních ovládacích prvků, které můžete vytvářet.
