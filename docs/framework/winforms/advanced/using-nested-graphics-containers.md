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
ms.openlocfilehash: 460ebb37ee62691a1e282f756840121fd378ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182466"
---
# <a name="using-nested-graphics-containers"></a>Použití vnořených grafických kontejnerů
GDI+ poskytuje kontejnery, které můžete použít k dočasnému <xref:System.Drawing.Graphics> nahrazení nebo rozšíření části stavu v objektu. Kontejner vytvoříte voláním <xref:System.Drawing.Graphics.BeginContainer%2A> metody <xref:System.Drawing.Graphics> objektu. Můžete volat <xref:System.Drawing.Graphics.BeginContainer%2A> opakovaně tvořit vnořené kontejnery. Každé volání <xref:System.Drawing.Graphics.BeginContainer%2A> do písmene a) musí být spárováno s voláním . <xref:System.Drawing.Graphics.EndContainer%2A>  
  
## <a name="transformations-in-nested-containers"></a>Transformace ve vnořených kontejnerech  
 Následující příklad vytvoří <xref:System.Drawing.Graphics> objekt a kontejner <xref:System.Drawing.Graphics> v rámci tohoto objektu. Světovou transformací objektu <xref:System.Drawing.Graphics> je překlad 100 jednotek ve směru x a 80 jednotek ve směru y. Světová transformace kontejneru je rotace o 30 stupňů. Kód provede volání `DrawRectangle(pen, -60, -30, 120, 60)` dvakrát. První volání <xref:System.Drawing.Graphics.DrawRectangle%2A> je uvnitř kontejneru; to znamená, že volání je <xref:System.Drawing.Graphics.BeginContainer%2A> mezi <xref:System.Drawing.Graphics.EndContainer%2A>volání a . Druhé volání <xref:System.Drawing.Graphics.DrawRectangle%2A> je po volání <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 V předchozím kódu obdélník nakreslené z uvnitř kontejneru je transformována nejprve transformace světa kontejneru <xref:System.Drawing.Graphics> (otočení) a pak transformace světa objektu (překlad). Obdélník nakreslený mimo kontejner je transformován pouze <xref:System.Drawing.Graphics> světovou transformací objektu (překladu). Následující obrázek znázorňuje dva obdélníky:
  
 ![Obrázek, který znázorňuje vnořené kontejnery.](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>Oříznutí ve vnořených kontejnerech  
 Následující příklad ukazuje, jak vnořené kontejnery zpracovávají oblasti oříznutí. Kód vytvoří <xref:System.Drawing.Graphics> objekt a kontejner <xref:System.Drawing.Graphics> v rámci tohoto objektu. Ořezová oblast <xref:System.Drawing.Graphics> objektu je obdélník a oblast oříznutí kontejneru je elipsa. Kód provede dvě volání <xref:System.Drawing.Graphics.DrawLine%2A> metody. První volání <xref:System.Drawing.Graphics.DrawLine%2A> je uvnitř kontejneru a druhé <xref:System.Drawing.Graphics.DrawLine%2A> volání je mimo kontejner <xref:System.Drawing.Graphics.EndContainer%2A>(po volání). První řádek je oříznut průsečíkem dvou ořezových oblastí. Druhý řádek je oříznut pouze obdélníkovou ořezovou <xref:System.Drawing.Graphics> oblastí objektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 Následující obrázek znázorňuje dva oříznuté řádky:
  
 ![Obrázek znázorněný kontejner s oříznutými čarami.](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 Jak ukazují dva předchozí příklady, transformace a oblasti oříznutí jsou kumulativní v vnořených kontejnerech. Pokud nastavíte transformace světa kontejneru <xref:System.Drawing.Graphics> a objektu, obě transformace se budou vztahovat na položky čerpané z uvnitř kontejneru. Transformace kontejneru bude použita jako první a <xref:System.Drawing.Graphics> transformace objektu bude použita jako druhý. Pokud nastavíte ořezové oblasti <xref:System.Drawing.Graphics> kontejneru a objektu, položky nakreslené zevnitř kontejneru budou oříznuty průsečíkem dvou ořezových oblastí.  
  
## <a name="quality-settings-in-nested-containers"></a>Nastavení kvality ve vnořených kontejnerech  
 Nastavení kvality<xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.TextRenderingHint%2A>( , , a podobně) ve vnořených kontejnerech nejsou kumulativní; místo toho nastavení kvality kontejneru dočasně nahradit <xref:System.Drawing.Graphics> nastavení kvality objektu. Při vytváření nového kontejneru jsou nastavení kvality pro tento kontejner nastavena na výchozí hodnoty. Předpokládejme například, <xref:System.Drawing.Graphics> že máte objekt s <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>režimem vyhlazení . Když vytvoříte kontejner, režim vyhlazení uvnitř kontejneru je výchozí režim vyhlazení. Můžete nastavit režim vyhlazení kontejneru a všechny položky čerpané z kontejneru budou vykresleny podle nastaveného režimu. Položky nakreslené <xref:System.Drawing.Graphics.EndContainer%2A> po volání budou vykresleny<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>podle režimu vyhlazení ( <xref:System.Drawing.Graphics.BeginContainer%2A>), který byl na místě před voláním .  
  
## <a name="several-layers-of-nested-containers"></a>Několik vrstev vnořených kontejnerů  
 Nejste omezeni na jeden <xref:System.Drawing.Graphics> kontejner v objektu. Můžete vytvořit posloupnost kontejnerů, každý vnořený v předchozím a můžete určit transformaci světa, oblast oříznutí a nastavení kvality každého z těchto vnořených kontejnerů. Pokud voláte metodu výkresu z vnitřku nejvnitřnějšího kontejneru, transformace budou použity v pořadí, počínaje nejvnitřnějším kontejnerem a končícím nejkrajnějším kontejnerem. Položky nakreslené z vnitřku nejvnitřnějšího kontejneru budou oříznuty průsečíkem všech ořezových oblastí.  
  
 Následující příklad vytvoří <xref:System.Drawing.Graphics> objekt a nastaví <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>jeho nápovědu pro vykreslování textu na . Kód vytvoří dva kontejnery, jeden vnořený v rámci druhého. Nápověda k vykreslování textu vnějšího kontejneru je nastavena na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>a nápověda k vykreslení textu vnitřního kontejneru je nastavena na <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kód nakreslí tři řetězce: jeden z vnitřního kontejneru, jeden <xref:System.Drawing.Graphics> z vnějšího kontejneru a jeden z samotného objektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 Následující obrázek znázorňuje tři řetězce. Řetězce nakreslené z vnitřního <xref:System.Drawing.Graphics> kontejneru a z objektu jsou vyhlazeny vyhlazením. Řetězec nakreslený z vnějšího kontejneru není vyhlazen <xref:System.Drawing.Graphics.TextRenderingHint%2A> vyhlazením, protože vlastnost je nastavena na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![Obrázek, který znázorňuje řetězce nakreslené z vnořených kontejnerů.](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Drawing.Graphics>
- [Správa stavu grafického objektu](managing-the-state-of-a-graphics-object.md)
