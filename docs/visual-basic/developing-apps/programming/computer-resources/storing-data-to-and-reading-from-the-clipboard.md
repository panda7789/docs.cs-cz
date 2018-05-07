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
ms.openlocfilehash: eb8ae25f260ed434c4aafcc064be8fb6bebaaac1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Ukládání dat do schránky a čtení ze schránky (Visual Basic)
Schránky slouží k ukládání dat, jako je například textu a obrázků. Protože schránky je sdílen všech aktivních procesů, může sloužit k přenosu dat mezi nimi. `My.Computer.Clipboard` Objekt umožňuje snadno přistupovat do schránky a čtení z a do něj zapisovat.  
  
## <a name="reading-from-the-clipboard"></a>Čtení ze schránky  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metodu za účelem čtení textu do schránky. Následující kód načte text a zobrazí v okně se zprávou. Musí být uložen do schránky například správné fungování text.  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu. V Sběrač fragmentů kódu je umístěn v **aplikacích Windows Forms > schránky**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> metodu pro načtení obrázku ze schránky. Tento příklad zkontroluje, pokud je bitovou kopii do schránky před jeho načítání a jeho k přiřazení `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu. V Sběrač fragmentů kódu je umístěn v **aplikacích Windows Forms > schránky**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Položky, které jsou umístěny do schránky zachová i po ukončení aplikace.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Určení typu souboru uložen do schránky  
 Data do schránky může trvat několik různých formulářů, například textu, zvukových souborů nebo bitovou kopii. Chcete-li zjistit, jaký typ souboru je do schránky, můžete použít metody, jako <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, a <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metodu lze použít, pokud máte vlastní formát, který chcete zkontrolovat.  
  
 Použití `ContainsImage` funkce k určení, zda data obsažená ve schránce je bitovou kopii. Následující kód zkontroluje, zda jsou data bitovou kopii a odpovídajícím způsobem sestavy.  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a>Vymazání schránky  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metoda vymaže do schránky. Protože schránky je sdílet s jinými procesy, vymazáním může mít vliv na těchto procesů.  
  
 Následující kód ukazuje způsob použití `Clear` metoda.  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a>Zápis do schránky.  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metodu pro zápis textu do schránky. Následující kód zapíše řetězec "Toto je test řetězec" do schránky.  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 `SetText` Metoda může přijmout parametr formátu, který obsahuje typ <xref:System.Windows.Forms.TextDataFormat>. Následující kód zapíše řetězec "Toto je test řetězec" do schránky jako text ve formátu RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> metoda zapsat data do schránky. Tento příklad zapíše `DataObject``dataChunk` do schránky ve vlastním formátu `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> metoda zapsat zvuk data do schránky. Tento příklad vytvoří bajtové pole `musicReader`, načte soubor `cool.wav` do ní a zapíše ho do schránky.  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  Protože schránky můžete mít přístup další uživatelé, nepoužívejte ho pro uložení citlivé informace, třeba hesla nebo důvěrné údaje.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>  
 [Postupy: Čtení dat objektů ze souboru XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [Postupy: Zápis dat objektů do souboru XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
