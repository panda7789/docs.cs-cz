---
title: 'Postupy: Vyhledávání dat v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 514e72afc9570071f57e385574456ff7d716bad7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654383"
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>Postupy: Vyhledávání dat v ovládacím prvku DataRepeater (Visual Studio)
Při použití <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek, který obsahuje mnoho záznamů, možná budete chtít umožňují uživatelům vyhledat konkrétní záznam. Místo vyhledávání dat v samotném ovládacím prvku, lze implementovat hledání pomocí dotazu na <xref:System.Windows.Forms.BindingSource>. Pokud se položka nenajde, pak můžete použít <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> vlastnosti vyberte položku a přejděte do zobrazení.  
  
### <a name="to-implement-search"></a>Implementace hledání  
  
1.  Přetáhněte <xref:System.Windows.Forms.TextBox> ovládacího prvku **nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
2.  V okně Vlastnosti změňte **název** vlastnost **SearchTextBox**.  
  
3.  Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
4.  V okně Vlastnosti změňte **název** vlastnost **SearchButton**. Změnit **Text** vlastnost **hledání**.  
  
5.  Dvakrát klikněte <xref:System.Windows.Forms.Button> ovládací prvek, otevře se Editor kódu a přidejte následující kód, který `SearchButton_Click` obslužné rutiny události.  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Nahraďte *ProductsBindingSource* názvem <xref:System.Windows.Forms.BindingSource> pro vaše <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>a nahraďte *ProductID* s názvem pole, které chcete vyhledávat.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Postupy: Změna vzhledu ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
