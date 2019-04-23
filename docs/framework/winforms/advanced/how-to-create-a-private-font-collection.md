---
title: 'Postupy: Vytvoření soukromé kolekce písem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
ms.openlocfilehash: f78d48c88b72388676f5e7ae963b98d8f1b4beac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210684"
---
# <a name="how-to-create-a-private-font-collection"></a>Postupy: Vytvoření soukromé kolekce písem
<xref:System.Drawing.Text.PrivateFontCollection> Třída dědí z <xref:System.Drawing.Text.FontCollection> abstraktní základní třída. Můžete použít <xref:System.Drawing.Text.PrivateFontCollection> objekt udržovat sadu písem speciálně pro danou aplikaci. Privátní písma kolekce může obsahovat nainstalované systémových písem, jakož i písma, které nebyly nainstalované v počítači. Chcete-li přidat soubor písma pro kolekci privátní písma, zavolejte <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> metodu <xref:System.Drawing.Text.PrivateFontCollection> objektu.  
  
 <xref:System.Drawing.Text.FontCollection.Families%2A> Vlastnost <xref:System.Drawing.Text.PrivateFontCollection> objekt obsahuje celou řadu <xref:System.Drawing.FontFamily> objekty.  
  
 Počet rodin písem v kolekci privátní písmo není nutně stejné jako číslo soubory písem, které byly přidány do kolekce. Například předpokládejme, že přidáte soubory ArialBd.tff Times.tff a TimesBd.tff do kolekce. Bude tři soubory, ale pouze dvě řady v kolekci protože Times.tff a TimesBd.tff patřit do stejné rodiny.  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá následující soubory tři písma <xref:System.Drawing.Text.PrivateFontCollection> objektu:  
  
-   C:\\*systemroot*\Fonts\Arial.tff (Arial, pravidelné)  
  
-   C:\\*systemroot*\Fonts\CourBI.tff (Kurýrní nové, tučná kurzíva)  
  
-   C:\\*systemroot*\Fonts\TimesBd.tff (časy New Roman, tučné písmo)  
  
 Kód načte pole <xref:System.Drawing.FontFamily> objekty z <xref:System.Drawing.Text.FontCollection.Families%2A> vlastnost <xref:System.Drawing.Text.PrivateFontCollection> objektu.  
  
 Pro každou <xref:System.Drawing.FontFamily> objekt v kolekci, kód volá <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metodou ke zjištění, zda jsou k dispozici různé styly (pravidelných, tučné, kurzíva, tučné písmo kurzíva, podtržení a přeškrtnutí). Argumenty předané <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metody jsou členy <xref:System.Drawing.FontStyle> výčtu.  
  
 Pokud je k dispozici, kombinaci dané rodině a styl <xref:System.Drawing.Font> objekt je vytvořen pomocí této rodiny a stylu. První argument předaný do <xref:System.Drawing.Font.%23ctor%2A> konstruktor je název rodiny písem (ne <xref:System.Drawing.FontFamily> jak se v případě jiných variace <xref:System.Drawing.Font.%23ctor%2A> konstruktoru). Po <xref:System.Drawing.Font> objekt je vytvořen, je předána <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> třídy zobrazovaný název řady spolu s názvem daného stylu.  
  
 Následující kód výstup je podobný výstup je znázorněno na následujícím obrázku:  
  
 ![Snímek obrazovky, který zobrazuje text v různých písma.](./media/how-to-create-a-private-font-collection/various-fonts-text-output.png)  
  
 Arial.tff (který byl přidán do kolekce privátní písem v následujícím příkladu kódu) je písmo pro Arial regulární style. Upozorňujeme však, že program výstup ukazuje několik dostupných stylů než standardní řady Arial písmo. Důvodem je, že [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete simulovat tučné, kurzíva a Tučná kurzíva styly ze standardního stylu. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Můžete také vytvářet vlnovkou a přeškrtnutí ze standardního stylu.  
  
 Obdobně [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete simulovat tučný styl kurzíva tučný styl nebo kurzívu. Výstup programu ukazuje, že tučný styl kurzíva k dispozici pro řadu časy Přestože TimesBd.tff (časy New Roman, bold) je jediná časy soubor v kolekci.  
  
 [!code-csharp[System.Drawing.FontsAndText#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Text.PrivateFontCollection>
- [Použití písem a textu](using-fonts-and-text.md)
