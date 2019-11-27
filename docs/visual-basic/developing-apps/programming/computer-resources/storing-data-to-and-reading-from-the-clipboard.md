---
title: Ukládání dat do schránky a čtení z ní
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 243fb237f3f9ba53f8b29079df08531c102c78dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349736"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Ukládání dat do schránky a jejich čtení (Visual Basic)

Schránku lze použít k ukládání dat, jako je například text a obrázky. Vzhledem k tomu, že schránka sdílí všechny aktivní procesy, lze ji použít k přenosu dat mezi nimi. Objekt `My.Computer.Clipboard` umožňuje snadný přístup ke schránce a čtení z ní a zápis do ní.  
  
## <a name="reading-from-the-clipboard"></a>Čtení ze schránky  

 K přečtení textu ve schránce použijte metodu <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A>. Následující kód přečte text a zobrazí jej v okně se zprávou. Ve schránce musí být uložený text, aby mohl být příklad správně spuštěn.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > schránka**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Pomocí metody <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> načtěte obrázek ze schránky. Tento příklad zkontroluje, zda je před načtením do schránky obrázek, a přiřadí ho k `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > schránka**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Položky umístěné ve schránce zůstanou i po vypnutí aplikace.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Určení typu souboru uloženého ve schránce  

 Data ve schránce mohou mít řadu různých forem, jako je například text, zvukový soubor nebo obrázek. Aby bylo možné určit, jakým způsobem je soubor ve schránce, můžete použít metody, jako <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>a <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. Metodu <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> lze použít, pokud máte vlastní formát, který chcete kontrolovat.  
  
 Pomocí funkce `ContainsImage` určíte, zda jsou data obsažená ve schránce obrázkem. Následující kód zkontroluje, zda se jedná o odpovídající obrázek a sestavy.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Vymazávání schránky  

 Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> vymaže schránku. Vzhledem k tomu, že schránka sdílí jiné procesy, její zrušení může mít vliv na tyto procesy.  
  
 Následující kód ukazuje, jak použít metodu `Clear`.  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Zápis do schránky  

 Použijte metodu <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> k zápisu textu do schránky. Následující kód zapíše řetězec "Toto je testovací řetězec" do schránky.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 Metoda `SetText` může přijmout parametr formátu, který obsahuje typ <xref:System.Windows.Forms.TextDataFormat>. Následující kód zapíše řetězec "Toto je testovací řetězec" do schránky jako text RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 K zápisu dat do schránky použijte metodu <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A>. Tento příklad zapíše `DataObject` `dataChunk` do schránky v `specialFormat`vlastního formátu.  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 Pomocí metody <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> zapište zvuková data do schránky. Tento příklad vytvoří `musicReader`bajtové pole, přečte soubor `cool.wav` a pak ho zapíše do schránky.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> Vzhledem k tomu, že je možné k schránce získat jiní uživatelé, nepoužívejte ji k ukládání citlivých informací, jako jsou hesla nebo důvěrná data.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Postupy: Čtení dat objektů ze souboru XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Postupy: Zápis dat objektů do souboru XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
