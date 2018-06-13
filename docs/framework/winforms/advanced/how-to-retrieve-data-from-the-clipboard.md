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
ms.openlocfilehash: e06fb509bed32df0c18f2a03ae89765b3334b2c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524076"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Postupy: Načtení dat ze schránky
<xref:System.Windows.Forms.Clipboard> Třída poskytuje metody, které můžete použít k interakci s funkcí schránky operačního systému Windows. Mnoho aplikací používá schránky jako dočasné úložiště pro data. Například textové editory používat schránku během operace vyjímání a vkládání. Schránky je také užitečné pro přenos informací z jedné aplikace do jiné.  
  
 Některé aplikace ukládat data do schránky a zvýšit počet dalších aplikací, které mohou potenciálně používat data ve více formátech. Formát schránky je řetězec, který identifikuje formátu. Aplikace, která používá identifikovaných formát můžete načíst přidružená data do schránky. <xref:System.Windows.Forms.DataFormats> Třída poskytuje názvy ve formátu předdefinované pro vaše použití. Můžete také použít vlastní názvy ve formátu nebo použijte typ objektu jako formát. Informace o přidání dat do schránky najdete v tématu [postupy: přidání dat do schránky](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).  
  
 Pokud chcete zjistit, zda schránky obsahuje data v určitém formátu, použijte jednu z `Contains` *formátu* metody nebo <xref:System.Windows.Forms.Clipboard.GetData%2A> metoda. Pokud chcete načíst data ze schránky, použijte jednu z `Get` *formátu* metody nebo <xref:System.Windows.Forms.Clipboard.GetData%2A> metoda. Tyto metody jsou v nové [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
 Pro přístup k datům ze schránky pomocí verze starší než [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], použijte <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> metoda a volání metody vrácený <xref:System.Windows.Forms.IDataObject>. Pokud chcete zjistit, jestli konkrétní formát je k dispozici v vráceného objektu, například volání <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> metoda.  
  
> [!NOTE]
>  Všechny aplikace systému Windows sdílet systému schránky. Proto obsah se mohou změnit, když přejdete na jinou aplikaci.  
>   
>  <xref:System.Windows.Forms.Clipboard> Třídu lze použít pouze v vláken nastavit na jedno vlákno apartment (STA) režimu. Chcete-li použít tuto třídu, ověřte, zda vaše `Main` metoda je označena <xref:System.STAThreadAttribute> atribut.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>K načtení dat ze schránky v jednom, běžné formátu  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, nebo <xref:System.Windows.Forms.Clipboard.GetText%2A> metoda. Volitelně můžete pomocí odpovídající `Contains` *formát* metody nejprve k určení, zda jsou k dispozici v určitém formátu data. Tyto metody jsou k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>K načtení dat ze schránky ve vlastním formátu  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.GetData%2A> metodu s názvem vlastní formát. Tato metoda je k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Můžete také použít předdefinované formátu názvy s <xref:System.Windows.Forms.Clipboard.SetData%2A> metoda. Další informace naleznete v tématu <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>K načtení dat ze schránky ve více formátech  
  
1.  Použití <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> metoda. Tato metoda musí používat k načtení dat ze schránky na verze starší než [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Viz také  
 [Operace přetažení a podpora schránky](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [Postupy: Přidání dat do schránky](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
