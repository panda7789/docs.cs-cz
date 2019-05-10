---
title: 'Postupy: Nastavení šířky a pera a zarovnání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: 1f1ea6e8ef0b94aa46a4bf8177d59e59297d6e3f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605825"
---
# <a name="how-to-set-pen-width-and-alignment"></a>Postupy: Nastavení šířky a pera a zarovnání
Když vytvoříte <xref:System.Drawing.Pen>, můžete zadat šířku pera jako jeden z argumentů konstruktoru. Můžete také změnit šířku pera s <xref:System.Drawing.Pen.Width%2A> vlastnost <xref:System.Drawing.Pen> třídy.  
  
 Teoretické řádek má šířku 0. Když nakreslíte čáru, která je 1 pixelu široké, se na řádku teoretické na pixely. Pokud nakreslení čáry, která je více než jeden pixel široké pixely se buď na řádku teoretické nebo zobrazovat na jedné straně teoretické řádku. Můžete nastavit vlastnost zarovnání pera <xref:System.Drawing.Pen> k určení, jak bude umístěna pixelů vykresleno pomocí pera vzhledem k teoretické řádky.  
  
 Hodnoty <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, a <xref:System.Drawing.Drawing2D.PenAlignment.Inset> , která se zobrazují následující příklady kódu jsou členy <xref:System.Drawing.Drawing2D.PenAlignment> výčtu.  
  
 Následující příklad kódu nakreslí čáru dvakrát: jednou perem černé šířky 1 a posléze s zelené pera šířky 10.  
  
### <a name="to-vary-the-width-of-a-pen"></a>Postup obměny šířku pera  
  
- Nastavte hodnotu <xref:System.Drawing.Pen.Alignment%2A> vlastnost <xref:System.Drawing.Drawing2D.PenAlignment.Center> (výchozí) k určení, že bude pixelů vykreslit zelený perem teoretické řádku na střed. Následující obrázek znázorňuje výsledný řádek.  
  
     ![Černá čára dynamického zajišťování s zelené zvýraznění.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-line.gif)  
  
     Následující příklad kódu kreslení obdélníku dvakrát: jednou perem černé šířky 1 a posléze s zelené pera šířky 10.  
  
     [!code-csharp[System.Drawing.UsingAPen#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>Chcete-li změnit zarovnání pera  
  
- Nastavte hodnotu <xref:System.Drawing.Pen.Alignment%2A> vlastnost <xref:System.Drawing.Drawing2D.PenAlignment.Center> k určení, že bude pixelů vykreslit zelený perem na hranici obdélník na střed.  
  
     Výsledný obdélníku na následujícím obrázku:
  
     ![Obdélník vykresleno pomocí černého dynamického zajišťování řádky s zelené zvýraznění.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-rectangle.gif)  
  
     [!code-csharp[System.Drawing.UsingAPen#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>Vytvoření inset pera  
  
- Změna zarovnání zelené pera tak, že upravíte třetí příkaz v předchozím příkladu kódu následujícím způsobem:  
  
     [!code-csharp[System.Drawing.UsingAPen#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     Pixelů na šířku zelenou čáru zobrazují na vnitřní obdélníku, jak je znázorněno na následujícím obrázku:
  
     ![Obdélník vykresleno pomocí černého řádky široký zelenou čárou uvnitř.](./media/how-to-set-pen-width-and-alignment/green-pixels-inside-rectangle.gif)  
  
## <a name="see-also"></a>Viz také:

- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
