---
title: Ukládání dat do schránky a čtení ze schránky (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 19d0fcafb76c40a00939de59968dfaf2e6bd683c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921300"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Ukládání dat do schránky a čtení ze schránky (Visual Basic)
Schránky slouží k ukládání dat, jako je například textu a obrázků. Protože schránky sdílí všech aktivních procesů, lze použít k přenosu dat mezi nimi. `My.Computer.Clipboard` Objekt umožňuje snadno přistupovat do schránky a číst z a do ní zapisovat.  
  
## <a name="reading-from-the-clipboard"></a>Čtení ze schránky  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metodu za účelem čtení textu do schránky. Následující kód načte text a zobrazí ho v okně se zprávou. Musí existovat text ze schránky. například správně spustit.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **formulářových aplikací Windows > schránky**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> metodu pro načtení obrázku ze schránky. Tento příklad kontroluje, jestli je obrázek do schránky před načtením a ji přiřadíte `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **formulářových aplikací Windows > schránky**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Položky umístěné do schránky se zachová, i když je aplikace ukončena.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Určuje typ souboru je uložen do schránky  
 Data do schránky. může trvat několik různé podoby, jako je například text, zvukový soubor nebo obrázek. Aby bylo možné zjistit, jaký typ souboru je do schránky, můžete použít metody, jako <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, a <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metodu je možné použít, pokud máte vlastní formát, který chcete zkontrolovat.  
  
 Použití `ContainsImage` funkce určuje, jestli data obsažená ve schránce je obrázek. Následující kód zkontroluje, jestli se data bitovou kopii a odpovídajícím způsobem sestavy.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Vymazat schránku  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metoda vymaže do schránky. Protože schránky je sdílet s jinými procesy, zrušením zaškrtnutí může mít vliv na těchto procesů.  
  
 Následující kód ukazuje způsob použití `Clear` metody.  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Zápis do schránky.  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> způsob zápisu textu do schránky. Následující kód zapíše řetězce "Toto je testovací řetězec" do schránky.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 `SetText` Metoda přijímá parametr formátu, který obsahuje typ <xref:System.Windows.Forms.TextDataFormat>. Následující kód zapíše řetězce "Toto je testovací řetězec" do schránky jako text ve formátu RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> metody zapsat data do schránky. Tento příklad zapíše `DataObject` `dataChunk` do schránky ve vlastním formátu `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> metody zapsat zvuková data do schránky. Tento příklad vytvoří pole bajtů `musicReader`, načte soubor `cool.wav` do ní a zapíše jej do schránky.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
>  Protože schránky je přístupný ostatním uživatelům, nepoužívejte ho pro ukládání citlivých informací, jako jsou hesla nebo důvěrná data.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Postupy: Čtení dat objektů ze souboru XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Postupy: Zápis dat objektů do souboru XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
