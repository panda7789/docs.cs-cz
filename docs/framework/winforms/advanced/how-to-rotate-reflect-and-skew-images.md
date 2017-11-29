---
title: "Postupy: Otáčení, převrácení a zkosení obrázků"
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
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eaa6286731d196dad387e1648644ca3e8103da03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-rotate-reflect-and-skew-images"></a>Postupy: Otáčení, převrácení a zkosení obrázků
Otočit, odrážel a zkreslit bitovou kopii zadáním cílového body pro rozích levém horním pravém horním a dolním původní bitové kopie. Tři cílové body určit afinní transformace, která se mapuje na rovnoběžník původní obdélníková bitové kopie.  
  
## <a name="example"></a>Příklad  
 Předpokládejme například, původní bitové kopie je obdélník se v levém horním rohu (0, 0), v pravém horním rohu (100, 0) a v levém dolním rohu (0, 50). Nyní předpokládejme, že ty namapujete tři odkazuje na cílový body následujícím způsobem.  
  
|Původní bodu|Cílového bodu|  
|--------------------|-----------------------|  
|Levý horní (0, 0)|(200, 20)|  
|Pravém (100, 0)|(110, 100)|  
|Dolním (0, 50)|(250, 30)|  
  
 Následující obrázek znázorňuje původní bitové kopie a bitovou kopii namapované na Kosoúhelník. Původní bitové kopie byly nesouměrně rozdělí, projeví, otáčet a přeložit. Osy x podél horního okraje původní bitové kopie je namapovaná na řádek, který spouští prostřednictvím (200, 20) a (110, 100). Osy y podél levého okraje původní bitové kopie je namapovaná na řádek, který spouští prostřednictvím (200, 20) a (250, 30).  
  
 ![Rozděluje](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")  
  
 Následující obrázek znázorňuje podobné transformace do bitové photographic.  
  
 ![Transformovat horolezec](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")  
  
 Následující obrázek znázorňuje podobně jako u metasoubory transformace.  
  
 ![Transformovat Metafile](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")  
  
 Následující příklad vytvoří bitové kopie na první obrázku je vidět.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nezapomeňte nahradit `Stripes.bmp` s cestou na obrázek, který je platný v systému.  
  
## <a name="see-also"></a>Viz také  
 [Práce s obrázky, rastrové obrázky, ikony a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
