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
ms.openlocfilehash: 824d42c40b07e8662395e7a1286b9a5a6112c415
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523077"
---
# <a name="how-to-create-a-private-font-collection"></a>Postupy: Vytvoření soukromé kolekce písem
<xref:System.Drawing.Text.PrivateFontCollection> Třída dědí z <xref:System.Drawing.Text.FontCollection> abstraktní základní třída. Můžete použít <xref:System.Drawing.Text.PrivateFontCollection> objekt udržovat sadu písem speciálně pro vaši aplikaci. Kolekce privátní písem může zahrnovat nainstalovaný systém písma, jakož i písma, které nebyly nainstalovány v počítači. Chcete-li přidat soubor písma na kolekci privátní písma, zavolejte <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> metodu <xref:System.Drawing.Text.PrivateFontCollection> objektu.  
  
 <xref:System.Drawing.Text.FontCollection.Families%2A> Vlastnost <xref:System.Drawing.Text.PrivateFontCollection> objekt obsahuje pole <xref:System.Drawing.FontFamily> objekty.  
  
 Počet rodiny písem v kolekci privátní písma není nutně stejný jako počet souborů písma, které jsou přidané do kolekce. Předpokládejme například, že se mají přidat soubory ArialBd.tff, Times.tff a TimesBd.tff do kolekce. Bude tři soubory, ale pouze dvě řady v kolekci protože Times.tff a TimesBd.tff patří do stejné rodiny.  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá následující soubory tři písma <xref:System.Drawing.Text.PrivateFontCollection> objektu:  
  
-   C:\\*systemroot*\Fonts\Arial.tff (Arial, regulární)  
  
-   C:\\*systemroot*\Fonts\CourBI.tff (Kurýrní nové, tučná kurzíva)  
  
-   C:\\*systemroot*\Fonts\TimesBd.tff (Times New Roman, tučně)  
  
 Kód načte pole <xref:System.Drawing.FontFamily> objekty z <xref:System.Drawing.Text.FontCollection.Families%2A> vlastnost <xref:System.Drawing.Text.PrivateFontCollection> objektu.  
  
 Pro každou <xref:System.Drawing.FontFamily> objekt v kolekci, volání kódu <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metodu pro určení, zda jsou k dispozici různé styly (obyčejný, tučné, kurzíva, tučná kurzíva, podtržení a přeškrtnutí). Argumenty předaný <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metoda jsou členy <xref:System.Drawing.FontStyle> výčtu.  
  
 Pokud je k dispozici, kombinaci danou rodinu nebo styl <xref:System.Drawing.Font> objekt se vytvoří pomocí této rodiny a stylu. První argument předaný <xref:System.Drawing.Font.%23ctor%2A> konstruktor je název rodiny písem (není <xref:System.Drawing.FontFamily> objektu stejně jako v případě pro jiné variace <xref:System.Drawing.Font.%23ctor%2A> konstruktor). Po <xref:System.Drawing.Font> vytvoření objektu, je předána <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> třída zobrazíte název rodiny společně s název stylu.  
  
 Výstup následující kód je podobná výstupní vidět na následujícím obrázku.  
  
 ![Text písem](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")  
  
 Arial.tff (která byla přidána do kolekce privátní písem v následujícím příkladu kódu) je v souboru Arial regulární styl písma. Upozorňujeme však, že program výstup ukazuje několik dostupných stylů než regular pro typu Arial. Je to způsobeno [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete simulovat tučné, kurzíva a Tučná kurzíva styly ze standardního stylu. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Můžete také vytvořit podtržení a přeškrtnutí ze standardního stylu.  
  
 Podobně [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete simulovat styl tučné kurzíva z tučné styl nebo styl kurzíva. Výstup programu ukazuje, že styl tučné kurzíva je k dispozici pro rodinu časy, i když je jedinou TimesBd.tff (Times New Roman, tučné) časy soubor v kolekci.  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 [Použití písem a textu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
