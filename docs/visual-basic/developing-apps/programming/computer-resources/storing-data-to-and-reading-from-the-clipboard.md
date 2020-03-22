---
title: Ukládání dat do schránky a čtení ze schránky
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349736"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Ukládání dat do schránky a čtení ze schránky (Visual Basic)

Schránku lze použít k ukládání dat, například textu a obrázků. Vzhledem k tomu, že schránka je sdílena všemi aktivními procesy, lze ji použít k přenosu dat mezi nimi. Objekt `My.Computer.Clipboard` umožňuje snadný přístup ke schránce a čtení a zápis do ní.  
  
## <a name="reading-from-the-clipboard"></a>Čtení ze schránky  

 Pomocí <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metody můžete číst text ve schránce. Následující kód přečte text a zobrazí jej v poli se zprávou. Aby byl příklad správně spuštěn, musí být ve schránce uložen text.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu IntelliSense. Ve výběru fragmentu kódu je umístěn ve **schránce aplikací > Windows Forms**. Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Pomocí <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> této metody načtěte obraz ze schránky. V tomto příkladu se zobrazí, zda je ve schránce obrázek `PictureBox1`před načtením a přiřazením k aplikaci .  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu IntelliSense. Ve výběru fragmentu kódu je umístěn ve **schránce aplikací > Windows Forms**. Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Položky umístěné ve schránce budou zachovány i po ukončení aplikace.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Určení typu souboru uloženého ve schránce  

 Data ve schránce mohou mít řadu různých forem, například text, zvukový soubor nebo obrázek. Chcete-li zjistit, jaký druh souboru je ve schránce, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>můžete <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>použít metody, jako <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>je například , <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, a . Metodu <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> lze použít, pokud máte vlastní formát, který chcete zkontrolovat.  
  
 Pomocí `ContainsImage` funkce určete, zda jsou data obsažená ve schránce obrazem. Následující kód zkontroluje, zda data je obrázek a sestavy odpovídajícím způsobem.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Vymazání schránky  

 Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> vymaže schránku. Vzhledem k tomu, že schránka je sdílena jinými procesy, vymazání může mít vliv na tyto procesy.  
  
 Následující kód ukazuje, jak `Clear` používat metodu.  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Zápis do schránky  

 Pomocí <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metody zapisovat text do schránky. Následující kód zapíše řetězec "Toto je testovací řetězec" do schránky.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 Metoda `SetText` může přijmout parametr formátu, který <xref:System.Windows.Forms.TextDataFormat>obsahuje typ . Následující kód zapíše řetězec "Toto je testovací řetězec" do schránky jako text RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 Pomocí <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> této metody zapisujete data do schránky. Tento příklad `DataObject` `dataChunk` zapisuje do `specialFormat`schránky ve vlastním formátu .  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 Pomocí <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> této metody zapisujte zvuková data do schránky. Tento příklad vytvoří bajtové `musicReader`pole `cool.wav` , přečte do něj soubor a zapíše jej do schránky.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> Vzhledem k tomu, že ke schránce mají přístup jiní uživatelé, nepoužívejte ji k ukládání citlivých informací, jako jsou hesla nebo důvěrná data.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Postup: Čtení dat objektů ze souboru XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Postup: Zápis dat objektu do souboru XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
