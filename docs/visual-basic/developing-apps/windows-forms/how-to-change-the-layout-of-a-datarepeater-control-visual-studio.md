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
ms.openlocfilehash: fa780ee40171143c17b5bdbda4a97179ed5f2151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a>Postupy: Změna rozložení ovládacího prvku DataRepeater (Visual Studio)
<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Řízení lze zobrazit v svislé (posunutí položky svisle) nebo vodorovné (posunutí vodorovně) orientace. Orientace v době návrhu nebo v době běhu můžete změnit změnou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> vlastnost. Pokud změníte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> vlastnost za běhu, můžete také změnit velikost <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> a změnit umístění podřízených ovládacích prvků.  
  
> [!NOTE]
>  Pokud umístění ovládacích prvků na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> za běhu, budete muset volat <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody na začátku a konci bloku kódu, který přemístí ovládací prvky.  
  
### <a name="to-change-the-layout-at-design-time"></a>Chcete-li změnit rozložení v době návrhu  
  
1.  V Návrháři formulářů Windows, vyberte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
    > [!NOTE]
    >  Je nutné vybrat vnější ohraničení <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení kliknutím v oblasti nižší ovládacího prvku, ne v horní <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> oblast.  
  
2.  V okně vlastnosti nastavit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> vlastnost, která má buď <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> nebo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.  
  
### <a name="to-change-the-layout-at-run-time"></a>Chcete-li změnit rozložení v době běhu  
  
1.  Přidejte následující kód do tlačítka nebo nabídky `Click` obslužné rutiny události:  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  Ve většině případů budete chtít přidat kód podobný uvedenému v části Příklad ke změně velikosti <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> a změna uspořádání ovládacích prvků podle nové orientaci.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak reagovat na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> událost v obslužné rutiny události. Tento příklad vyžaduje, abyste měli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek s názvem `DataRepeater1` na formuláři a že jeho <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> obsahovat dva <xref:System.Windows.Forms.TextBox> ovládací prvky s názvem `TextBox1` a `TextBox2`.  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
