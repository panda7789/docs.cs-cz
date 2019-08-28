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
ms.openlocfilehash: 0d9b82f01080d18353ecb91578a8005260bbe739
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044223"
---
# <a name="how-to-add-data-to-the-clipboard"></a>Postupy: Přidání dat do schránky

<xref:System.Windows.Forms.Clipboard> Třída poskytuje metody, které můžete použít k interakci s funkcí schránky operačního systému Windows. Mnoho aplikací používá schránku jako dočasné úložiště pro data. Například procesory aplikace Word používají schránku během operací vyjmutí a vložení. Schránka je užitečná také pro přenos dat z jedné aplikace do jiné.

Když do schránky přidáte data, můžete určit formát dat, aby ostatní aplikace mohli rozpoznat data v případě, že mohou použít tento formát. Můžete také přidat data do schránky v různých formátech a zvýšit tak počet dalších aplikací, které mohou data potenciálně používat.

Formát schránky je řetězec, který určuje formát, aby aplikace, která používá tento formát, mohla načíst přidružená data. <xref:System.Windows.Forms.DataFormats> Třída poskytuje předdefinované názvy formátů pro použití. Můžete také použít vlastní názvy formátů nebo jako svůj formát použít typ objektu.

Chcete-li přidat data do schránky v jednom nebo více formátech, použijte <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metodu. Do této metody můžete předat libovolný objekt, ale chcete-li přidat data do více formátů, je nutné nejprve přidat data do samostatného objektu navrženého pro práci s více formáty. Obvykle budete přidávat data do <xref:System.Windows.Forms.DataObject>, ale můžete použít jakýkoli typ, který <xref:System.Windows.Forms.IDataObject> implementuje rozhraní.

V .NET Framework 2,0 můžete přidat data přímo do schránky pomocí nových metod, které jsou navržené tak, aby byly snadno základní úlohy schránky. Tyto metody použijte při práci s daty v jednom, běžném formátu, jako je text.

> [!NOTE]
> Všechny aplikace založené na systému Windows sdílejí schránku. Proto se obsah může změnit při přepnutí na jinou aplikaci.
>
> Třída <xref:System.Windows.Forms.Clipboard> se dá použít jenom v vláknech nastavených na režim sta (Single Thread Apartment). Chcete-li použít tuto třídu, ujistěte `Main` se, že je vaše <xref:System.STAThreadAttribute> Metoda označena atributem.
>
> Objekt musí být serializovatelný, aby jej bylo možné umístit do schránky. Chcete-li vytvořit serializovatelný typ, označte jej <xref:System.SerializableAttribute> atributem. Pokud předáte Neserializovatelný objekt metodě schránky, metoda selže bez vyvolání výjimky. Další informace o serializaci naleznete v <xref:System.Runtime.Serialization>tématu.

### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Přidání dat do schránky v jednom společném formátu

1. Použijte metodu <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A> ,,<xref:System.Windows.Forms.Clipboard.SetImage%2A>nebo .<xref:System.Windows.Forms.Clipboard.SetText%2A> <xref:System.Windows.Forms.Clipboard.SetAudio%2A> Tyto metody jsou k dispozici pouze v .NET Framework 2,0.

    [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
    [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]

### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Přidání dat do schránky ve vlastním formátu

1. <xref:System.Windows.Forms.Clipboard.SetData%2A> Použijte metodu s názvem vlastního formátu. Tato metoda je k dispozici pouze v .NET Framework 2,0.

    Můžete také použít předdefinované názvy formátů s <xref:System.Windows.Forms.Clipboard.SetData%2A> metodou. Další informace naleznete v tématu <xref:System.Windows.Forms.DataFormats>.

    [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
    [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Přidání dat do schránky v několika formátech

1. Použijte metodu <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType> a předejte <xref:System.Windows.Forms.DataObject> ji, která obsahuje vaše data. Tuto metodu je nutné použít, pokud chcete do schránky přidat data ve verzích starších než .NET Framework 2,0.

    [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
    [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

## <a name="see-also"></a>Viz také:

- [Operace přetažení a podpora schránky](drag-and-drop-operations-and-clipboard-support.md)
- [Postupy: Načtení dat ze schránky](how-to-retrieve-data-from-the-clipboard.md)
