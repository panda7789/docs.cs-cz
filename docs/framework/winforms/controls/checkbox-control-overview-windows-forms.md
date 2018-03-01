---
title: "CheckBox – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 39645a02cd66d37d61df72028ab129677edb757e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.CheckBox> řízení Určuje, zda je určitá podmínka zapnout nebo vypnout. Běžně se používá k dispozici Ano/Ne nebo hodnotu True nebo False výběru uživatele. Ovládací prvky zaškrtávacích políček ve skupinách, můžete použít k zobrazení více možností, ze kterých uživatel může vybrat jednu nebo více.  
  
 Ovládací prvek zaškrtávací políčko je podobná ovládací prvek přepínač, v tom, že každý slouží k označení výběru, která je vytvořená uživatelem. Se liší, ve které lze vybrat pouze jeden přepínač ve skupině najednou. S ovládací prvek zaškrtávací políčko však může být libovolný počet zaškrtávací políčka vybraný.  
  
 Zaškrtávací políčko může být připojena k prvkům v databázi pomocí jednoduché datové vazby. Více zaškrtávacích políček může být seskupené pomocí <xref:System.Windows.Forms.GroupBox> ovládacího prvku. To je užitečné pro vzhled a také pro návrh uživatelského rozhraní, protože skupina ovládacích prvků lze přesunout společně v návrháři formuláře. Další informace najdete v tématu [Windows Forms datové vazby](../../../../docs/framework/winforms/windows-forms-data-binding.md) a [groupbox – ovládací prvek](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).  
  
 <xref:System.Windows.Forms.CheckBox> Ovládací prvek má dvě důležité vlastnosti <xref:System.Windows.Forms.CheckBox.Checked%2A> a <xref:System.Windows.Forms.CheckBox.CheckState%2A>. <xref:System.Windows.Forms.CheckBox.Checked%2A> Vlastnost vrací buď `true` nebo `false`. <xref:System.Windows.Forms.CheckBox.CheckState%2A> Vlastnost vrací buď <xref:System.Windows.Forms.CheckState.Checked> nebo <xref:System.Windows.Forms.CheckState.Unchecked>; nebo, pokud <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> může také vrátit <xref:System.Windows.Forms.CheckState.Indeterminate>. V neurčitém stavu zobrazí se pole s neaktivní vzhled se indikovat, že možnost není k dispozici.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.CheckBox>  
 [Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [Ovládací prvek CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
