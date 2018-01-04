---
title: "Postupy: Nastavení šířky a pera a zarovnání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e5858da25174c8bc1de18d534023b57b58253e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-pen-width-and-alignment"></a>Postupy: Nastavení šířky a pera a zarovnání
Při vytváření <xref:System.Drawing.Pen>, můžete zadat šířku pera jako jednoho z argumentů konstruktoru. Můžete také změnit šířku pera s <xref:System.Drawing.Pen.Width%2A> vlastnost <xref:System.Drawing.Pen> třídy.  
  
 Teoretické řádku má šířku 0. Při nakreslení čáry, která je 1 pixel široké, se na ose teoretické na pixelů. Pokud nakreslení čáry, která je více než jeden bod. široké, pixelů buď na střed v řádku teoretické nebo zobrazovat na jedné straně teoretické řádku. Můžete nastavit vlastnost zarovnání pera <xref:System.Drawing.Pen> k určení znázornění pixelů vykreslovány pomocí pera umístění relativně k teoretické řádky.  
  
 Hodnoty <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, a <xref:System.Drawing.Drawing2D.PenAlignment.Inset> která se zobrazují následující příklady kódu jsou členy <xref:System.Drawing.Drawing2D.PenAlignment> výčtu.  
  
 Následující příklad kódu nakreslí čáru dvakrát: jednou s černým pera šířky 1 a jednou pera zelená šířky 10.  
  
### <a name="to-vary-the-width-of-a-pen"></a>K odlišení šířku pera  
  
-   Nastavte hodnotu <xref:System.Drawing.Pen.Alignment%2A> vlastnost <xref:System.Drawing.Drawing2D.PenAlignment.Center> (výchozí) k určení pixelů vykreslené s zelenou pera, bude vycházet ze teoretické řádku. Následující obrázek znázorňuje výsledný řádek.  
  
     ![Pera](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")  
  
     Následující příklad kódu kreslení obdélníku dvakrát: jednou s černým pera šířky 1 a jednou pera zelená šířky 10.  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>Chcete-li změnit zarovnání pera  
  
-   Nastavte hodnotu <xref:System.Drawing.Pen.Alignment%2A> vlastnost <xref:System.Drawing.Drawing2D.PenAlignment.Center> k určení pixelů vykreslené s zelenou pera, bude vycházet ze hranice rámečku.  
  
     Následující obrázek znázorňuje výsledné rámeček.  
  
     ![Pera](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>Chcete-li vytvořit inset pera  
  
-   Změna zarovnání zelená pera změnou třetí příkaz v předchozím příkladu kódu:  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     Teď zobrazují pixelů na celý zelená řádku uvnitř obdélníku, jak je znázorněno na následujícím obrázku.  
  
     ![Pera](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")  
  
## <a name="see-also"></a>Viz také  
 [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
