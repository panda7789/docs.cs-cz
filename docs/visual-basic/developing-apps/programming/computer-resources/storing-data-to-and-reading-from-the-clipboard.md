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
ms.openlocfilehash: c8f15ac33ae92a13159c2a95435ba3d2391ace8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739203"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Ukládání dat do schránky a čtení ze schránky (Visual Basic)
Schránky slouží k ukládání dat, jako je například textu a obrázků. Protože schránky sdílí všech aktivních procesů, lze použít k přenosu dat mezi nimi. `My.Computer.Clipboard` Objekt umožňuje snadno přistupovat do schránky a číst z a do ní zapisovat.  
  
## <a name="reading-from-the-clipboard"></a>Čtení ze schránky  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metodu za účelem čtení textu do schránky. Následující kód načte text a zobrazí ho v okně se zprávou. Musí existovat text ze schránky. například správně spustit.  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **formulářových aplikací Windows > schránky**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> metodu pro načtení obrázku ze schránky. Tento příklad kontroluje, jestli je obrázek do schránky před načtením a ji přiřadíte `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **formulářových aplikací Windows > schránky**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Položky umístěné do schránky se zachová, i když je aplikace ukončena.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Určuje typ souboru je uložen do schránky  
 Data do schránky. může trvat několik různé podoby, jako je například text, zvukový soubor nebo obrázek. Aby bylo možné zjistit, jaký typ souboru je do schránky, můžete použít metody, jako <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, a <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metodu je možné použít, pokud máte vlastní formát, který chcete zkontrolovat.  
  
 Použití `ContainsImage` funkce určuje, jestli data obsažená ve schránce je obrázek. Následující kód zkontroluje, jestli se data bitovou kopii a odpovídajícím způsobem sestavy.  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a>Vymazat schránku  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metoda vymaže do schránky. Protože schránky je sdílet s jinými procesy, zrušením zaškrtnutí může mít vliv na těchto procesů.  
  
 Následující kód ukazuje způsob použití `Clear` metody.  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a>Zápis do schránky.  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> způsob zápisu textu do schránky. Následující kód zapíše řetězce "Toto je testovací řetězec" do schránky.  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 `SetText` Metoda přijímá parametr formátu, který obsahuje typ <xref:System.Windows.Forms.TextDataFormat>. Následující kód zapíše řetězce "Toto je testovací řetězec" do schránky jako text ve formátu RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> metody zapsat data do schránky. Tento příklad zapíše `DataObject` `dataChunk` do schránky ve vlastním formátu `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> metody zapsat zvuková data do schránky. Tento příklad vytvoří pole bajtů `musicReader`, načte soubor `cool.wav` do ní a zapíše jej do schránky.  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  Protože schránky je přístupný ostatním uživatelům, nepoužívejte ho pro ukládání citlivých informací, jako jsou hesla nebo důvěrná data.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Postupy: Čtení dat objektů ze souboru XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Postupy: Zápis dat objektů do souboru XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
