---
title: Přehled ovládacího prvku CheckBox
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: b42816cf1bc0ce1ab6db0a2a436b17b0d4370d59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737090"
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.CheckBox> označuje, zda je konkrétní podmínka zapnutá nebo vypnutá. Často se používá k zobrazení výběru ano/ne nebo true/false pro uživatele. Pomocí ovládacích prvků zaškrtávací políčko ve skupinách můžete zobrazit více možností, ze kterých může uživatel vybrat jednu nebo více.  
  
 Ovládací prvek zaškrtávací políčko je podobný ovládacímu prvku přepínač v tom, že každý je použit k označení výběru, který je proveden uživatelem. Liší se v tom, že v jednom okamžiku lze vybrat pouze jeden přepínač ve skupině. V ovládacím prvku zaškrtávací políčko však může být vybrán libovolný počet zaškrtávacích políček.  
  
 Zaškrtávací políčko může být připojeno k prvkům v databázi pomocí jednoduché datové vazby. Pomocí ovládacího prvku <xref:System.Windows.Forms.GroupBox> lze seskupit vícenásobná zaškrtávací políčka. To je užitečné pro vizuální vzhled a také pro návrh uživatelského rozhraní, protože seskupené ovládací prvky lze přesouvat v Návrháři formulářů společně. Další informace najdete v tématu [model Windows Forms datovou vazbu](../windows-forms-data-binding.md) a [ovládací prvek skupinový rámeček](groupbox-control-windows-forms.md).  
  
 Ovládací prvek <xref:System.Windows.Forms.CheckBox> má dvě důležité vlastnosti, <xref:System.Windows.Forms.CheckBox.Checked%2A> a <xref:System.Windows.Forms.CheckBox.CheckState%2A>. Vlastnost <xref:System.Windows.Forms.CheckBox.Checked%2A> vrací buď hodnotu `true` nebo `false`. Vlastnost <xref:System.Windows.Forms.CheckBox.CheckState%2A> vrací buď hodnotu <xref:System.Windows.Forms.CheckState.Checked> nebo <xref:System.Windows.Forms.CheckState.Unchecked>; nebo, pokud je vlastnost <xref:System.Windows.Forms.CheckBox.ThreeState%2A> nastavena na hodnotu `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> může také vrátit <xref:System.Windows.Forms.CheckState.Indeterminate>. V neurčitém stavu se pole zobrazí s ztlumeným vzhledem k označení možnosti není k dispozici.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.CheckBox>
- [Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Ovládací prvek CheckBox](checkbox-control-windows-forms.md)
