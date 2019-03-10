---
title: 'Postupy: Přidání dat do schránky.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 1f04203cd5c006f778d09ddc3fef3cfa1be4666e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717121"
---
# <a name="how-to-add-data-to-the-clipboard"></a>Postupy: Přidání dat do schránky.
<xref:System.Windows.Forms.Clipboard> Třída poskytuje metody, které vám umožní pracovat s funkcí schránky operačního systému Windows. Mnoho aplikací používá schránky jako dočasné úložiště pro data. Například textové procesory použít schránky během operací vyjmutí a vložení. Schránka je také užitečné pro přenos dat z jedné aplikace do jiné.  
  
 Když přidáte data do schránky, můžete určit formát dat tak, aby další aplikace dokáže rozpoznat data, pokud používají tento formát. Můžete také přidat data do schránky v několika různých formátech. zvyšte počet jiných aplikací, které mohou potenciálně používat data.  
  
 Formát schránky není řetězec, který určuje formát tak, aby aplikace, která se použije tento formát můžete načíst související data. <xref:System.Windows.Forms.DataFormats> Třída poskytující předdefinovaný formát názvy používat. Můžete také použít vlastní názvy ve formátu nebo použít objekt typu jako jeho formát.  
  
 Chcete-li přidat data do schránky. v jeden nebo více formátů, použijte <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metody. Libovolný objekt můžete předat této metodě, ale můžete přidat data v různých formátech, musíte nejprve přidat data do samostatný objekt navrženy pro práci s více formátů. Obvykle přidáte data <xref:System.Windows.Forms.DataObject>, ale můžete použít libovolný typ, který implementuje <xref:System.Windows.Forms.IDataObject> rozhraní.  
  
 V [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], můžete přidat data přímo do schránky s použitím nové metody, které jsou navržené tak, aby základní úlohy schránky jednodušší. Tyto metody používejte při práci s daty ve formátu jeden, běžné například podle textu.  
  
> [!NOTE]
>  Všechny aplikace pro systém Windows sdílení schránky. Obsah, proto se mohou změnit po přepnutí na jinou aplikaci.  
>   
>  <xref:System.Windows.Forms.Clipboard> Třídu jde použít jenom ve vláknech nastavit na jedno vlákno režim apartment (STA). Pokud chcete použít tuto třídu, ujistěte se, že vaše `Main` metoda je označena <xref:System.STAThreadAttribute> atribut.  
>   
>  Objekt musí být serializovatelný, které budou umístěny do schránky. Chcete-li typ serializovatelný, označte ji pomocí <xref:System.SerializableAttribute> atribut. Pokud předáte metodě schránky není serializovatelný objekt, metoda selže bez vyvolání výjimky. Další informace o serializaci naleznete v tématu <xref:System.Runtime.Serialization>.  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Jak přidat data do schránky. v jedné, běžné formátu  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, nebo <xref:System.Windows.Forms.Clipboard.SetText%2A> metody. Tyto metody jsou k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Chcete-li přidat data do schránky ve vlastním formátu  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.SetData%2A> metodu s názvem vlastního formátu. Tato metoda je k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Můžete také použít předdefinovaný formát názvů s <xref:System.Windows.Forms.Clipboard.SetData%2A> metody. Další informace naleznete v tématu <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Chcete-li přidat data do schránky ve více formátech  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metoda a předejte jí <xref:System.Windows.Forms.DataObject> , který obsahuje vaše data. Musíte použít tuto metodu můžete přidat do schránky ve verzích starších než [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Viz také:
- [Operace přetažení a podpora schránky](drag-and-drop-operations-and-clipboard-support.md)
- [Postupy: Načtení dat ze schránky](how-to-retrieve-data-from-the-clipboard.md)
