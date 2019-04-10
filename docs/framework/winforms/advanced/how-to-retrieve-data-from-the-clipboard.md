---
title: 'Postupy: Načtení dat ze schránky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: aca110339c94afd5442aed5a2481964b456154f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201608"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Postupy: Načtení dat ze schránky
<xref:System.Windows.Forms.Clipboard> Třída poskytuje metody, které vám umožní pracovat s funkcí schránky operačního systému Windows. Mnoho aplikací používá schránky jako dočasné úložiště pro data. Například textové procesory použít schránky během operací vyjmutí a vložení. Schránka je také užitečné pro přenos informací z jedné aplikace do jiného.  
  
 Některé aplikace ukládat data do schránky k navýšení tohoto počtu dalších aplikací, které mohou potenciálně používat data ve více formátech. Formát schránky není řetězec, který určuje formát. Aplikace, která používá formát identifikované můžete načíst přidružená data do schránky. <xref:System.Windows.Forms.DataFormats> Třída poskytující předdefinovaný formát názvy používat. Můžete také použít vlastní názvy ve formátu nebo použijte typ objektu jako jeho formát. Informace o přidávání dat do schránky, naleznete v tématu [jak: Přidání dat do schránky](how-to-add-data-to-the-clipboard.md).  
  
 Pokud chcete zjistit, zda schránky obsahuje data v určitém formátu, použijte jednu z `Contains` *formátu* metody nebo <xref:System.Windows.Forms.Clipboard.GetData%2A> metody. K načtení dat ze schránky, použijte jednu z `Get` *formátu* metody nebo <xref:System.Windows.Forms.Clipboard.GetData%2A> metody. Tyto metody jsou novinkou [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
 Pro přístup k datům ze schránky pomocí verzí starší než [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], použijte <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> metoda a volat metody vráceného <xref:System.Windows.Forms.IDataObject>. Pokud chcete zjistit, jestli konkrétní formát je k dispozici v vráceného objektu, například volání <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> metody.  
  
> [!NOTE]
>  Všechny aplikace pro systém Windows sdílení schránky. Obsah, proto se mohou změnit po přepnutí na jinou aplikaci.  
>   
>  <xref:System.Windows.Forms.Clipboard> Třídu jde použít jenom ve vláknech nastavit na jedno vlákno režim apartment (STA). Pokud chcete použít tuto třídu, ujistěte se, že vaše `Main` metoda je označena <xref:System.STAThreadAttribute> atribut.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>K načtení dat ze schránky v jedné, běžné formátu  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, nebo <xref:System.Windows.Forms.Clipboard.GetText%2A> metody. Volitelně můžete použít odpovídající `Contains` *formátu* metody, abyste mohli zjistit, jestli je k dispozici v určitém formátu data. Tyto metody jsou k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>K načtení dat ze schránky ve vlastním formátu  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.GetData%2A> metodu s názvem vlastního formátu. Tato metoda je k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Můžete také použít předdefinovaný formát názvů s <xref:System.Windows.Forms.Clipboard.SetData%2A> metody. Další informace naleznete v tématu <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>K načtení dat ze schránky ve více formátech  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> metody. Musíte použít tuto metodu pro načtení dat ze schránky na verze starší než [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Viz také:

- [Operace přetažení a podpora schránky](drag-and-drop-operations-and-clipboard-support.md)
- [Postupy: Přidání dat do schránky](how-to-add-data-to-the-clipboard.md)
