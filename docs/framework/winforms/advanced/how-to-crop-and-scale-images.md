---
title: "Postupy: Oříznutí a změna měřítka obrázků"
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
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8fb5d527cd1047197f370c4a9a9b1f8f33461653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-crop-and-scale-images"></a>Postupy: Oříznutí a změna měřítka obrázků
<xref:System.Drawing.Graphics> Třída poskytuje několik <xref:System.Drawing.Graphics.DrawImage%2A> metody, některé z nich musí mít zdrojové a cílové parametry obdélníku, které můžete použít k oříznutí a škálování bitové kopie.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru disku Apple.gif. Kód nakreslí obrázek celý apple v původní velikost. Kód pak zavolá <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu k vykreslení část apple bitové kopie v cílovém obdélníku, která je větší než původní bitové kopie apple.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Metoda určuje, jaká část apple kreslení prohlížením rámeček zdroj, který je určený třetí, čtvrté, páté a šesté argumenty. V takovém případě apple oříznuty na 75 procent svou šířku a výšku 75 procent.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Metoda určuje, kde k vykreslení oříznutý apple a jak velký aby oříznutý apple pohledem na cílovém obdélníku, který je určeného druhý argument. V takovém případě cílového rámeček je 30 procent širší a 30 procent vyšší než původní bitové kopie.  
  
 Následující obrázek znázorňuje původní apple a škálovat, oříznout apple.  
  
 ![Oříznutí a změna velikosti](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nezapomeňte nahradit `Apple.gif` s název souboru obrázku a cestu, která jsou platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Práce s obrázky, rastrové obrázky, ikony a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
