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
ms.openlocfilehash: a66edd0297b723b81c31675c9b0e6b6def9ed10a
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125860"
---
# <a name="using-nested-graphics-containers"></a>Použití vnořených grafických kontejnerů
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje kontejnery, které vám umožní dočasně nahradit nebo rozšířit části stavu v <xref:System.Drawing.Graphics> objektu. Vytvořte kontejner zavoláním <xref:System.Drawing.Graphics.BeginContainer%2A> metodu <xref:System.Drawing.Graphics> objektu. Můžete volat <xref:System.Drawing.Graphics.BeginContainer%2A> opakovaně k formulářů vnořeného kontejnery. Každé volání <xref:System.Drawing.Graphics.BeginContainer%2A> musí být párována s volání <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## <a name="transformations-in-nested-containers"></a>Transformace ve vnořené kontejnery  
 Následující příklad vytvoří <xref:System.Drawing.Graphics> objektů a kontejnerů, které <xref:System.Drawing.Graphics> objektu. Světové transformace <xref:System.Drawing.Graphics> objektu se překlad 100 jednotek ve směru osy x a 80 jednotek ve směru osy y. Světové transformace kontejneru je otočení kolem osy 30stupňů. Kód provádí volání `DrawRectangle(pen, -60, -30, 120, 60)` dvakrát. První volání <xref:System.Drawing.Graphics.DrawRectangle%2A> uvnitř kontejneru; to znamená, že volání spadá do rozsahu volání <xref:System.Drawing.Graphics.BeginContainer%2A> a <xref:System.Drawing.Graphics.EndContainer%2A>. Druhé volání <xref:System.Drawing.Graphics.DrawRectangle%2A> je po volání <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 V předchozím kódu obdélník načtené z uvnitř kontejneru se transformuje nejprve podle Světové transformace kontejneru (rotace) a pak podle Světové transformace <xref:System.Drawing.Graphics> objektu (překlad). Obdélník načtené z mimo kontejner je transformovat pouze Světové transformace <xref:System.Drawing.Graphics> objektu (překlad). Následující obrázek znázorňuje těmito dvěma obdélníky: 
  
 ![Obrázek, na kterém vnořené kontejnery.](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>Omezení ve vnořené kontejnery  
 Následující příklad ukazuje, jak vnořené kontejnery zpracování výstřižek oblastech. Kód vytvoří <xref:System.Drawing.Graphics> objektů a kontejnerů, které <xref:System.Drawing.Graphics> objektu. Výstřižek oblast <xref:System.Drawing.Graphics> obdélníku je objekt a oblast ořezu kontejneru je elipsu. Kód vytvoří dvě volání <xref:System.Drawing.Graphics.DrawLine%2A> metody. První volání <xref:System.Drawing.Graphics.DrawLine%2A> se nachází uvnitř kontejneru a druhé volání <xref:System.Drawing.Graphics.DrawLine%2A> je mimo kontejner (po volání <xref:System.Drawing.Graphics.EndContainer%2A>). První řádek je oříznutý ořezovou průnik dvou výstřižek oblastech. Druhý řádek je oříznut pouze podle oblasti Obdélníkový výstřižek <xref:System.Drawing.Graphics> objektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 Následující obrázek znázorňuje dvě zkrácený řádky:
  
 ![Obrázek, na kterém vnořený kontejner zkrácený řádky.](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 Jak dvě předchozí příklady ukazují, transformace a výstřižek oblasti jsou kumulativní ve vnořené kontejnery. Pokud nastavíte Světové transformace kontejneru a <xref:System.Drawing.Graphics> objektu, obě transformace uplatní na položky načtené z uvnitř kontejneru. Transformace kontejneru budou použité první a transformaci <xref:System.Drawing.Graphics> objektu se použije druhý. Pokud nastavíte oblastech oříznutí kontejneru a <xref:System.Drawing.Graphics> objektu položky načtené z uvnitř kontejneru bude oříznutý ořezovou průnik dvou výstřižek oblastech.  
  
## <a name="quality-settings-in-nested-containers"></a>Nastavení kvality ve vnořené kontejnery  
 Nastavení kvality (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>a podobně) ve vnořené kontejnery nejsou kumulativní; místo toho kvality nastavení kontejneru dočasně nahraďte nastavení kvality <xref:System.Drawing.Graphics> objektu. Když vytvoříte nový kontejner, kvalitu nastavení pro tento kontejner se nastaví na výchozí hodnoty. Předpokládejme například, že máte <xref:System.Drawing.Graphics> objekt s vyhlazování režim <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Při vytváření kontejneru režim vyhlazování uvnitř kontejneru je výchozí režim vyhlazování. Můžete libovolně nastavit režim vyhlazování kontejneru a všechny položky z vykreslí uvnitř kontejneru bude vykreslen podle režimu, který jste nastavili. Položky vykreslí po volání <xref:System.Drawing.Graphics.EndContainer%2A> bude vykreslen podle režim vyhlazování (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>), který byl na místě před voláním <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>Několik vrstev vnořené kontejnery  
 Nejste omezeni na jeden kontejner v <xref:System.Drawing.Graphics> objektu. Při vytváření pořadí kontejnerů, každá vnořená v předchozím a zadáte Světové transformace, oblast ořezu a nastavení kvalitu všech těchto vnořené kontejnery. Při volání kreslení metody z uvnitř vnitřní kontejneru, transformace se použijí v pořadí od nejvnitřnější kontejneru a konče nejkrajnější kontejneru. Položky načtené z uvnitř kontejneru nejvnitřnější bude oříznutý ořezovou průnik všech oblastech oříznutí.  
  
 Následující příklad vytvoří <xref:System.Drawing.Graphics> objekt a nastaví její pomocný parametr vykreslení textu na <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kód vytvoří dva kontejnery, jeden vnořený v rámci druhé. Pomocný parametr vykreslování textu vnější kontejneru je nastavena na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, a v pomocném parametru text vykreslování vnitřní kontejneru je nastavená na <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Nakreslí kód tři řetězce: jeden z vnitřní kontejner, jeden z vnějšího kontejneru a jeden z <xref:System.Drawing.Graphics> samotného objektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 Následující obrázek znázorňuje tři řetězce. Vykreslení z vnitřní kontejner a z řetězce <xref:System.Drawing.Graphics> objektu jsou vyhlazené podle vyhlazení. Řetězec z vnějšího kontejneru není vyhlazené podle vyhlazení vzhledem k tomu, <xref:System.Drawing.Graphics.TextRenderingHint%2A> je nastavena na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![Obrázek, na kterém řetězce z vnořené kontejnery.](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Drawing.Graphics>
- [Správa stavu grafického objektu](managing-the-state-of-a-graphics-object.md)
