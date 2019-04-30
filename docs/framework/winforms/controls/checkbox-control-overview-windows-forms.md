---
title: CheckBox – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: 2a18327d9836d1dbbcd5d5d6e73f217637736d20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938967"
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.CheckBox> ovládací prvek označuje, zda je určitá podmínka zapnutí nebo vypnutí. Se běžně používá k prezentaci Ano/Ne nebo výběr True/False pro uživatele. Ovládací prvky zaškrtávacích políček ve skupinách slouží k zobrazení více možností, ze kterého může uživatel vybrat jeden nebo více.  
  
 Ovládací prvek zaškrtávací políčko je podobný ovládací prvek přepínač v tom, že každý se používá k označení výběr, který je provedené uživatelem. Liší se v, které lze najednou vybrat pouze jeden přepínací tlačítka ve skupině. Pomocí ovládacího prvku zaškrtávací políčko ale může být libovolný počet zaškrtávací políčka zaškrtnuto.  
  
 Zaškrtávací políčko může být připojen k prvků v databázi pomocí jednoduché datové vazby. Více zaškrtávacích políček mohou být seskupeny pomocí <xref:System.Windows.Forms.GroupBox> ovládacího prvku. To je užitečné pro vzhled a také pro návrh uživatelského rozhraní, protože seskupené ovládací prvky lze přesunout společně na Návrhář formulářů. Další informace najdete v tématu [Windows Forms datové vazby](../windows-forms-data-binding.md) a [groupbox – ovládací prvek](groupbox-control-windows-forms.md).  
  
 <xref:System.Windows.Forms.CheckBox> Ovládací prvek má dvě důležité vlastnosti <xref:System.Windows.Forms.CheckBox.Checked%2A> a <xref:System.Windows.Forms.CheckBox.CheckState%2A>. <xref:System.Windows.Forms.CheckBox.Checked%2A> Vlastnost vrací buď `true` nebo `false`. <xref:System.Windows.Forms.CheckBox.CheckState%2A> Vlastnost vrací buď <xref:System.Windows.Forms.CheckState.Checked> nebo <xref:System.Windows.Forms.CheckState.Unchecked>; nebo, pokud <xref:System.Windows.Forms.CheckBox.ThreeState%2A> je nastavena na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> může také vracet <xref:System.Windows.Forms.CheckState.Indeterminate>. V neurčitém stavu bude zobrazeno šedě vzhledu označující, že není k dispozici.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.CheckBox>
- [Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Postupy: Reakce na Windows Forms kliknutí na zaškrtávací políčko](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Ovládací prvek CheckBox](checkbox-control-windows-forms.md)
