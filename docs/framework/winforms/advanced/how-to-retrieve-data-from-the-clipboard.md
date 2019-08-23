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
ms.openlocfilehash: 88c2f2d872ae32b2cb3f0df13ce4816400695385
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963787"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Postupy: Načtení dat ze schránky
<xref:System.Windows.Forms.Clipboard> Třída poskytuje metody, které můžete použít k interakci s funkcí schránky operačního systému Windows. Mnoho aplikací používá schránku jako dočasné úložiště pro data. Například procesory aplikace Word používají schránku během operací vyjmutí a vložení. Schránka je užitečná také pro přenos informací z jedné aplikace do jiné.  
  
 Některé aplikace ukládají data ve schránce ve více formátech, aby se zvýšil počet dalších aplikací, které můžou data potenciálně používat. Formát schránky je řetězec, který určuje formát. Aplikace, která používá identifikovaný formát, může načíst přidružená data ve schránce. <xref:System.Windows.Forms.DataFormats> Třída poskytuje předdefinované názvy formátů pro použití. Můžete také použít vlastní názvy formátů nebo jako svůj formát použít typ objektu. Informace o přidání dat do schránky naleznete v tématu [How to: Přidejte data do schránky](how-to-add-data-to-the-clipboard.md).  
  
 Chcete-li zjistit, zda schránka obsahuje data v konkrétním formátu, použijte jednu `Contains`z metod *formátu* nebo <xref:System.Windows.Forms.Clipboard.GetData%2A> metodu. Chcete-li načíst data ze schránky, použijte jednu z `Get`metod *formátu* nebo <xref:System.Windows.Forms.Clipboard.GetData%2A> metodu. Tyto metody jsou v .NET Framework 2,0 nové.  
  
 Chcete-li získat přístup k datům ze schránky pomocí verzí starších než .NET Framework 2,0, <xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType> použijte metodu a zavolejte metody vrácené. <xref:System.Windows.Forms.IDataObject> Chcete-li určit, zda je v vráceném objektu k dispozici konkrétní formát, například <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> volání metody.  
  
> [!NOTE]
> Všechny aplikace založené na systému Windows sdílejí systémovou schránku. Proto se obsah může změnit při přepnutí na jinou aplikaci.  
>   
>  Třída <xref:System.Windows.Forms.Clipboard> se dá použít jenom v vláknech nastavených na režim sta (Single Thread Apartment). Chcete-li použít tuto třídu, ujistěte `Main` se, že je vaše <xref:System.STAThreadAttribute> Metoda označena atributem.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Načtení dat ze schránky v jednom společném formátu  
  
1. Použijte metodu <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A> ,,<xref:System.Windows.Forms.Clipboard.GetImage%2A>nebo .<xref:System.Windows.Forms.Clipboard.GetText%2A> <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A> Volitelně použijte nejprve odpovídající `Contains`metody *formátu* a určete, zda jsou data k dispozici v konkrétním formátu. Tyto metody jsou k dispozici pouze v .NET Framework 2,0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Načtení dat ze schránky ve vlastním formátu  
  
1. <xref:System.Windows.Forms.Clipboard.GetData%2A> Použijte metodu s názvem vlastního formátu. Tato metoda je k dispozici pouze v .NET Framework 2,0.  
  
     Můžete také použít předdefinované názvy formátů s <xref:System.Windows.Forms.Clipboard.SetData%2A> metodou. Další informace naleznete v tématu <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Načtení dat ze schránky v několika formátech  
  
1. <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> Použijte metodu. Tuto metodu je nutné použít k načtení dat ze schránky ve verzích starších než .NET Framework 2,0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Viz také:

- [Operace přetažení a podpora schránky](drag-and-drop-operations-and-clipboard-support.md)
- [Postupy: Přidat data do schránky](how-to-add-data-to-the-clipboard.md)
