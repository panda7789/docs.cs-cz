---
title: 'Postupy: Změna rozložení ovládacího prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: 3389daa6383444b48faab4c5383b281e44349bce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625598"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a>Postupy: Změna rozložení ovládacího prvku DataRepeater (Visual Studio)
<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Ovládací prvek lze zobrazit ve svislé (položky posunout svisle) nebo vodorovně (posunutí položky vodorovně) orientace. Orientace v době návrhu nebo za běhu můžete změnit tak, že změníte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> vlastnost. Pokud změníte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> vlastnost v době běhu, můžete také změnit velikost <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> a přemístění podřízené ovládací prvky.  
  
> [!NOTE]
>  Pokud umístění ovládacích prvků na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> za běhu, je potřeba volat <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody na začátek a konec bloku kódu, který přemístí ovládací prvky.  
  
### <a name="to-change-the-layout-at-design-time"></a>Chcete-li změnit rozložení v době návrhu  
  
1.  V Návrháři formulářů Windows, vyberte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
    > [!NOTE]
    >  Je nutné vybrat vnější okraj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku v dolní oblasti ovládacího prvku, ne v horním rohu klikněte na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> oblasti.  
  
2.  V okně Vlastnosti nastavte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> vlastnost buď <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> nebo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.  
  
### <a name="to-change-the-layout-at-run-time"></a>Chcete-li změnit rozložení v době běhu  
  
1.  Přidejte následující kód k tlačítka nebo nabídka `Click` obslužné rutiny události:  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  Ve většině případů budete chtít přidat kód, který se zobrazí v oddíle Příklad pro změnu velikosti podobný <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> a změna uspořádání ovládacích prvků podle nového orientace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak reagovat na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> události v obslužné rutině události. Tento příklad vyžaduje, abyste měli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek s názvem `DataRepeater1` na formuláři a že jeho <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> obsahovat dva <xref:System.Windows.Forms.TextBox> ovládací prvky s názvem `TextBox1` a `TextBox2`.  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>
- [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
