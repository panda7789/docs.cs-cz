---
title: Oznámení změn v datové vazbě rozhraní Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 79ad52b6db8cb7be7f4e3162b8f726e8cbe22dcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Oznámení změn v datové vazbě rozhraní Windows Forms
Jedním z nejdůležitějších konceptů Windows Forms – datová vazba je *upozornění na změnu*. Aby se zajistilo, že zdroj dat a vázané ovládací prvky vždy mít nejnovější data, je nutné přidat oznámení o změně pro datovou vazbu. Konkrétně chcete zajistit, že jsou vázané ovládací prvky upozorněni na změny, které byly provedeny k jejich zdroji dat a zdroj dat je upozornění na změny, které byly provedeny na vázané vlastnosti ovládacího prvku.  
  
 Existují různé druhy oznámení o změně, v závislosti na druhu datové vazby:  
  
-   Jednoduchá vazba, ve kterém jeden řídicí vlastnost je vázána na jednu instanci objektu.  
  
-   Vazba na základě seznamu, která může zahrnovat vlastnost jeden ovládací prvek vázán vlastnost položky v seznamu nebo vlastnost ovládací prvek vázán na seznam objektů.  
  
 Kromě toho při vytváření ovládacích prvků Windows Forms, které chcete použít pro datovou vazbu, musíte použít *PropertyName*změnilo vzor ovládacích prvků, tak, že změny vázané vlastnosti ovládacího prvku rozšířeny zdroj dat.  
  
## <a name="change-notification-for-simple-binding"></a>Oznámení o změně pro jednoduchá vazba  
 Jednoduchá vazba obchodní objekty musí zadejte oznámení o změně při změně hodnoty vázané vlastnosti. Můžete to provést pomocí vystavení *PropertyName*změněno událost pro každou vlastnost objektu vaší firmy a objekt obchodní vytvoření vazby na ovládací prvky s <xref:System.Windows.Forms.BindingSource> nebo upřednostňovanou metodou, ve kterém se implementuje obchodní objekt <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní a vyvolá <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události při změně hodnoty vlastnosti. Další informace najdete v tématu [postupy: implementace rozhraní INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md). Při použití objektů implementujících <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní, není nutné použít <xref:System.Windows.Forms.BindingSource> o vázání objektu do ovládacího prvku, ale pomocí <xref:System.Windows.Forms.BindingSource> se doporučuje.  
  
## <a name="change-notification-for-list-based-binding"></a>Oznámení o změně pro vazbu na základě seznamu  
 Windows Forms závisí na změnit a vázané seznam zajistit změnu vlastnosti (změní hodnotu vlastnosti položky seznamu) (položka je odstranit nebo přidat do seznamu) informace, které vázané ovládací prvky. Proto musí implementovat seznamy použitá k vazbě dat <xref:System.ComponentModel.IBindingList>, který poskytuje oba typy oznámení o změně. <xref:System.ComponentModel.BindingList%601> Je obecnou implementaci <xref:System.ComponentModel.IBindingList> a je určená pro použití s Windows Forms – datová vazba. Můžete vytvořit <xref:System.ComponentModel.BindingList%601> obsahující obchodní typ objektu, který implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a seznamu automaticky převede <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události <xref:System.ComponentModel.IBindingList.ListChanged> události. Pokud není seznam vázané <xref:System.ComponentModel.IBindingList>, je třeba svázat seznam objektů k ovládacím prvkům Windows Forms pomocí <xref:System.Windows.Forms.BindingSource> součásti. <xref:System.Windows.Forms.BindingSource> Součást poskytne seznam vlastností převod podobná <xref:System.ComponentModel.BindingList%601>. Další informace najdete v tématu [postupy: vytváření oznámení o změnách pomocí BindingSource a INotifyPropertyChanged rozhraní](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Oznámení o změně pro vlastní ovládací prvky  
 Nakonec ze strany řízení musí vystavit *PropertyName*změněno událost pro každou vlastnost navržený tak, aby se vázané na data. Změny vlastností ovládacího prvku rozšířeny pak vázaný datový zdroj. Další informace najdete v tématu [postupy: použití vzoru PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 <xref:System.ComponentModel.BindingList%601>  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Zdroje dat podporované rozhraním Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Datové vazby a Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
