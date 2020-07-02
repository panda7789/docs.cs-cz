---
title: 'Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky'
description: Naučte se snižovat blikání grafiky pomocí dvojího ukládání do vyrovnávací paměti pro model Windows Forms a používat ovládací prvky pro řešení problémů blikání přidružených k operacím vykreslování.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: f7c0425729f8a1a780124621788a1c49e06e0c4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618126"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky
Dvojité ukládání do vyrovnávací paměti používá vyrovnávací paměť k řešení problémů blikání spojených s více operacemi malování. Pokud je povoleno dvojité ukládání do vyrovnávací paměti, všechny operace Malování se nejprve vykreslí do vyrovnávací paměti místo kresby na obrazovce. Po dokončení všech operací Malování se vyrovnávací paměť zkopíruje přímo na kreslicí plochu, která je k ní přidružená. Vzhledem k tomu, že se na obrazovce provádí jenom jedna operace grafiky, odstraní se blikání obrázku přidruženého k složitým operacím malování. U většiny aplikací nabízí výchozí dvojité ukládání do vyrovnávací paměti, které poskytuje .NET Framework, nejlepší výsledky. Standardní ovládací prvky model Windows Forms jsou ve výchozím nastavení dvojitě uloženy do vyrovnávací paměti. Ve formulářích můžete povolit výchozí dvojité ukládání do vyrovnávací paměti a vytvořené ovládací prvky dvěma způsoby. Můžete buď nastavit <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost na `true` , nebo můžete zavolat <xref:System.Windows.Forms.Control.SetStyle%2A> metodu pro nastavení <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznaku na `true` . Obě metody povolí výchozí dvojité ukládání do vyrovnávací paměti pro formulář nebo ovládací prvek a poskytuje vykreslování grafiky bez blikání. Volání <xref:System.Windows.Forms.Control.SetStyle%2A> metody je doporučeno pouze pro vlastní ovládací prvky, pro které jste napsali veškerý kód vykreslování.  
  
 Pro pokročilejší scénáře s dvojitou vyrovnávací pamětí, jako je například animace nebo Pokročilá správa paměti, můžete implementovat svou vlastní dvojitou logiku ukládání do vyrovnávací paměti. Další informace naleznete v tématu [How to: manualed Graphics Buffered](how-to-manually-manage-buffered-graphics.md).  
  
### <a name="to-reduce-flicker"></a>Snížení blikání  
  
- Nastavte <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost na hodnotu `true` .  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \-ani  
  
- Zavolejte <xref:System.Windows.Forms.Control.SetStyle%2A> metodu pro nastavení <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznaku na `true` .  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [Grafiky s dvojitou vyrovnávací pamětí](double-buffered-graphics.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
