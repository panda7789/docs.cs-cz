---
title: 'Postupy: Vyhledávání dat v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 689990ee125c85c3151a4e965b619fde068d220e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>Postupy: Vyhledávání dat v ovládacím prvku DataRepeater (Visual Studio)
Při použití <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek, který obsahuje mnoho záznamů, možná budete chtít hledání umožňují uživatelům pro konkrétní záznam. Namísto vyhledávání data do ovládacího prvku, můžete implementovat hledání pomocí dotazu na <xref:System.Windows.Forms.BindingSource>. Pokud byla položka nalezena, pak můžete použít <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> vlastnost vyberte položku a přejděte do zobrazení.  
  
### <a name="to-implement-search"></a>Implementace hledání  
  
1.  Přetažení <xref:System.Windows.Forms.TextBox> řídit z **sada nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
2.  V okně vlastností změňte **název** vlastnost **SearchTextBox**.  
  
3.  Přetažení <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
4.  V okně vlastností změňte **název** vlastnost **SearchButton**. Změna **Text** vlastnost **vyhledávání**.  
  
5.  Dvakrát klikněte <xref:System.Windows.Forms.Button> řídit k otevření editoru kódu a přidejte následující kód do `SearchButton_Click` obslužné rutiny události.  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Nahraďte *ProductsBindingSource* s názvem <xref:System.Windows.Forms.BindingSource> pro vaše <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>a nahraďte *ProductID* s názvem pole, které chcete vyhledávat.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
