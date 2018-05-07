---
title: 'Postupy: Přidání dat do schránky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 6002acfadfd0e688ef432baacbdabffb83890cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-data-to-the-clipboard"></a>Postupy: Přidání dat do schránky
<xref:System.Windows.Forms.Clipboard> Třída poskytuje metody, které můžete použít k interakci s funkcí schránky operačního systému Windows. Mnoho aplikací používá schránky jako dočasné úložiště pro data. Například textové editory používat schránku během operace vyjímání a vkládání. Schránka je také užitečné pro přenos dat z jedné aplikace do jiné.  
  
 Při přidání dat do schránky, můžete určit formát dat tak, aby ostatní aplikace poznáte data, pokud používají tohoto formátu. Můžete také přidat data do schránky v několika různých formátech zvyšte počet dalších aplikací, které mohou potenciálně používat data.  
  
 Formát schránky je řetězec, který identifikuje formát tak, aby aplikace, která použije tento formát můžete načíst přidružená data. <xref:System.Windows.Forms.DataFormats> Třída poskytuje názvy ve formátu předdefinované pro vaše použití. Můžete také použít vlastní názvy ve formátu nebo použít typ objektu jako formát.  
  
 Chcete-li přidat data do schránky. v jedné nebo více formátů, použijte <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metoda. Jakýkoli objekt můžete předat této metodě, ale chcete-li přidat data ve více formátech, je nejprve nutno přidat data na samostatný objekt navrženy pro práci s více formátů. Obvykle budete přidávat data <xref:System.Windows.Forms.DataObject>, ale můžete použít libovolný typ, který implementuje <xref:System.Windows.Forms.IDataObject> rozhraní.  
  
 V [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], data přímo do schránky můžete přidat pomocí nové metody navržený tak, aby základní úlohy schránky jednodušší. Pomocí těchto metod při práci s daty ve formátu jeden, běžné například textu.  
  
> [!NOTE]
>  Všechny aplikace systému Windows sdílet do schránky. Proto obsah se mohou změnit, když přejdete na jinou aplikaci.  
>   
>  <xref:System.Windows.Forms.Clipboard> Třídu lze použít pouze v vláken nastavit na jedno vlákno apartment (STA) režimu. Chcete-li použít tuto třídu, ověřte, zda vaše `Main` metoda je označena <xref:System.STAThreadAttribute> atribut.  
>   
>  Objekt musí být serializovatelný pro něj k uvedení do schránky. Chcete-li typu serializable, označte ji s <xref:System.SerializableAttribute> atribut. Pokud předáte objekt neserializovatelných metoda schránky, metoda selže bez způsobení výjimky. Další informace o serializaci najdete v tématu <xref:System.Runtime.Serialization>.  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Chcete-li přidat data do schránky. v jedné, běžné formátu  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, nebo <xref:System.Windows.Forms.Clipboard.SetText%2A> metoda. Tyto metody jsou k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Chcete-li přidat data do schránky ve vlastním formátu  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.SetData%2A> metodu s názvem vlastní formát. Tato metoda je k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Můžete také použít předdefinované formátu názvy s <xref:System.Windows.Forms.Clipboard.SetData%2A> metoda. Další informace naleznete v tématu <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Chcete-li přidat data do schránky ve více formátech  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metoda a předejte jí <xref:System.Windows.Forms.DataObject> která obsahuje vaše data. Tato metoda nutné použít k přidání dat do schránky ve verzích starších než [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Viz také  
 [Operace přetažení a podpora schránky](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [Postupy: Načtení dat ze schránky](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
