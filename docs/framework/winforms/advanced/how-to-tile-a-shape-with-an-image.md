---
title: "Postupy: Dlaždicové vyplnění obrazce pomocí obrázku"
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
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8726322e9443042b76c28e7b4b22ebc51c871bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-tile-a-shape-with-an-image"></a>Postupy: Dlaždicové vyplnění obrazce pomocí obrázku
Stejně jako dlaždice mohou být umístěny vedle sebe tak, aby pokrývalo podlaží, obdélníková bitové kopie můžete umístěny vedle sebe výplně (dlaždice) obrazce. Na dlaždici vnitřek obrazce pomocí textury štětce. Když vytvoříte <xref:System.Drawing.TextureBrush> objektu jednoho z argumentů je předat do konstruktoru je <xref:System.Drawing.Image> objektu. Pokud používáte texture štětce k vyplnění vnitřku tvaru, tvar je vyplněn opakovaných kopie tuto bitovou kopii.  
  
 Vlastnost režim zalamování <xref:System.Drawing.TextureBrush> objektu určuje, jak je bitovou kopii orientované jako se opakuje v obdélníková mřížky. Zajistěte všechny dlaždice v mřížce mají stejné orientaci, nebo můžete použít bitovou kopii překlopit od pozice jeden mřížky na další. Překlopení může být vodorovně, vertical nebo obojí. Následující příklady ukazují dlaždice s různými typy překlopení.  
  
### <a name="to-tile-an-image"></a>Na dlaždici bitovou kopii  
  
-   Tento příklad používá následující obrázek 75 × 75 na dlaždici obdélníku 200 × 200.  
  
 ![Dlaždice 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")  
  
-   Následující obrázek znázorňuje, jak je rámeček rozložen formou dlaždic s bitovou kopii. Všimněte si, že všechny dlaždice mají stejné orientaci; není žádný překlopení.  
  
 ![Dlaždice 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>K převrácení bitovou kopii vodorovně při vedle sebe  
  
-   Tento příklad používá stejnou bitovou kopii 75 × 75 k vyplnění obdélníku 200 × 200. Režim zalamování nastavena na bitovou kopii Překlopit vodorovně. Následující obrázek znázorňuje, jak je rámeček rozložen formou dlaždic s bitovou kopii. Všimněte si, jak přesunout z jednoho dlaždice na další v daném řádku je obrázek vodorovně obráceně.  
  
 ![Dlaždice 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>K převrácení image ve svislém směru při vedle sebe  
  
-   Tento příklad používá stejnou bitovou kopii 75 × 75 k vyplnění obdélníku 200 × 200. Režim zalamování nastavena na bitovou kopii Překlopit svisle.  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>K převrácení bitovou kopii při dlaždice vodorovně a svisle  
  
-   Tento příklad používá stejnou bitovou kopii 75 × 75 na dlaždici obdélníku 200 × 200. Režim zalamování nastaven k převrácení bitovou kopii, vodorovně i svisle. Následující obrázek znázorňuje, jak je rámeček rozložen formou dlaždic imagí. Pamatujte, že jako přesunout z jednoho dlaždice na další v daném řádku, bitovou kopii je obráceno vodorovně a jak přesunout z jednoho dlaždice na další v daném sloupci bitovou kopii Svisle obráceně.  
  
 ![Dlaždice 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Viz také  
 [Použití štětce k vyplnění obrazců](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
