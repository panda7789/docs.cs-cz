---
title: Použití vnořených grafických kontejnerů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
ms.openlocfilehash: ba6bba84100a0ddcc87894710a6d3099ab0ccff5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-nested-graphics-containers"></a>Použití vnořených grafických kontejnerů
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje kontejnery, které můžete použít k dočasnému nahradit nebo posílení součástí se stavem v <xref:System.Drawing.Graphics> objektu. Vytvořte kontejner voláním <xref:System.Drawing.Graphics.BeginContainer%2A> metodu <xref:System.Drawing.Graphics> objektu. Můžete volat <xref:System.Drawing.Graphics.BeginContainer%2A> opakovaně k vytvoření vnořené kontejnery. Každé volání <xref:System.Drawing.Graphics.BeginContainer%2A> musí být spárována s volání <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## <a name="transformations-in-nested-containers"></a>Transformace ve vnořených kontejnery  
 Následující příklad vytvoří <xref:System.Drawing.Graphics> objekt a kontejner, jež se <xref:System.Drawing.Graphics> objektu. Světové transformace <xref:System.Drawing.Graphics> objektu se překlad 100 jednotky ve směru osy x a 80 jednotky ve směru osy y. Světové transformace kontejneru je rotaci 30 stupňů. Kód provede volání `DrawRectangle(pen, -60, -30, 120, 60)` dvakrát. První volání <xref:System.Drawing.Graphics.DrawRectangle%2A> uvnitř kontejneru; volání je mezi volání <xref:System.Drawing.Graphics.BeginContainer%2A> a <xref:System.Drawing.Graphics.EndContainer%2A>. Druhé volání <xref:System.Drawing.Graphics.DrawRectangle%2A> po volání <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 V předchozí kód rámeček čerpají z uvnitř kontejneru převede první podle Světové transformace kontejneru (otočení) a poté podle Světové transformace <xref:System.Drawing.Graphics> objektu (překlad). Rámeček čerpají z mimo kontejner je transformovat pouze Světové transformace <xref:System.Drawing.Graphics> objektu (překlad). Následující obrázek znázorňuje dvou tvaru.  
  
 ![Vnořené kontejnery](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")  
  
## <a name="clipping-in-nested-containers"></a>Výstřižek ve vnořené kontejnery  
 Následující příklad ukazuje, jak vnořené kontejnery zpracování výstřižek oblasti. Kód vytvoří <xref:System.Drawing.Graphics> objekt a kontejner, jež se <xref:System.Drawing.Graphics> objektu. Výstřižek oblast <xref:System.Drawing.Graphics> objektu je obdélníku a oblast ořezu kontejneru elipsy. Kód vytvoří dvě volání <xref:System.Drawing.Graphics.DrawLine%2A> metoda. První volání <xref:System.Drawing.Graphics.DrawLine%2A> je uvnitř kontejneru a druhé volání <xref:System.Drawing.Graphics.DrawLine%2A> je mimo kontejner (po volání <xref:System.Drawing.Graphics.EndContainer%2A>). První řádek je oříznut podle průnik dvou výstřižek oblasti. Druhý řádek je oříznut pouze pomocí výstřižek obdélníkovou oblast <xref:System.Drawing.Graphics> objektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 Následující obrázek znázorňuje oříznutí dva řádky.  
  
 ![Vnořený kontejner](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")  
  
 Dva předchozí příklady ukazují, transformace a oblastí, výstřižek jsou kumulativní ve vnořené kontejnery. Pokud nastavíte Světové transformace kontejneru a <xref:System.Drawing.Graphics> objektu obě transformace uplatní na položky čerpají z uvnitř kontejneru. Transformace kontejneru bude použité první a transformace <xref:System.Drawing.Graphics> objektu se použije druhý. Pokud nastavíte oblasti výstřižek kontejneru a <xref:System.Drawing.Graphics> objektu položky čerpají z uvnitř kontejneru bude oříznut podle průnik dvou výstřižek oblasti.  
  
## <a name="quality-settings-in-nested-containers"></a>Nastavení kvality ve vnořené kontejnery  
 Nastavení kvality (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>a podobně) ve vnořené kontejnery nejsou kumulativní; místo toho nastavení kvality kontejneru dočasně nahradit nastavení kvality <xref:System.Drawing.Graphics> objektu. Když vytvoříte nový kontejner, nastavení kvality pro tento kontejner je nastaveno na výchozí hodnoty. Předpokládejme například, že máte <xref:System.Drawing.Graphics> objekt s režim vyhlazování <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Když vytvoříte kontejner, režim vyhlazování uvnitř kontejneru je výchozí režim vyhlazování. Můžete nastavit režim vyhlazování kontejneru a všechny položky čerpají z uvnitř kontejneru budou vykreslovat podle režim, který nastavíte. Položky, které jsou vykreslovány po zavolání <xref:System.Drawing.Graphics.EndContainer%2A> budou vykreslovat podle režim vyhlazování (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>), který byl na místě před volání <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>Několik vrstev vnořené kontejnery  
 Nejste omezený na jeden kontejner v <xref:System.Drawing.Graphics> objektu. Můžete vytvořit pořadí kontejnerů, každé vnořené v předchozím a můžete zadat Světové transformace, oblast ořezu a nastavení kvality každého z těchto vnořené kontejnery. Pokud z kontejneru nejvnitřnější kreslení metodu lze volat transformace se použijí v pořadí, počínaje nejvnitřnější kontejneru a konče nejkrajnější kontejneru. Položky čerpají z uvnitř kontejneru nejvnitřnější bude oříznut průsečíkem všech oblastech výstřižek.  
  
 Následující příklad vytvoří <xref:System.Drawing.Graphics> objektu a nastaví její Rady pro vykreslování textu <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kód vytvoří dvě kontejnery, jeden vnořených ve druhé. Rady pro vykreslování textu vnější kontejneru je nastaven na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, a Rady pro vykreslování textu vnitřní kontejneru je nastavena na <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kód nevykresluje tři řetězce: jedné z kontejneru vnitřní, jeden z vnějšího kontejneru a jedné z <xref:System.Drawing.Graphics> samotného objektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 Následující obrázek znázorňuje tři řetězce. Řetězce vykreslovat z kontejneru vnitřní a <xref:System.Drawing.Graphics> podle vyhlazení jsou vyhlazené objektu. Řetězec čerpají z kontejneru vnější není vyhlazené podle vyhlazení, protože <xref:System.Drawing.Graphics.TextRenderingHint%2A> je nastavena na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![Vnořené kontejnery](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics>  
 [Správa stavu grafického objektu](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)
