---
title: Změna oznámení v datové vazbě
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 2dffea46bf0db54d28ef55e507767d88bd29ebc2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746350"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Oznámení změn v datové vazbě rozhraní Windows Forms
Jedním z nejdůležitějších konceptů model Windows Forms datové vazby je *oznámení o změně*. Aby bylo zajištěno, že datové zdroje a vázané ovládací prvky mají vždy nejaktuálnější data, je třeba přidat oznámení o změně pro datovou vazbu. Konkrétně chcete zajistit, aby vázané ovládací prvky byly upozorňovány na změny provedené ve zdroji dat, a zdroj dat je upozorněn na změny, které byly provedeny v rámci vázaných vlastností ovládacího prvku.  
  
 Existují různé druhy oznámení o změně v závislosti na druhu datové vazby:  
  
- Jednoduchá vazba, ve které je jedna vlastnost ovládacího prvku svázána s jednou instancí objektu.  
  
- Vazba založená na seznamu, která může obsahovat jednu vlastnost ovládacího prvku svázanou s vlastností položky v seznamu nebo vlastností ovládacího prvku svázaného se seznamem objektů.  
  
 Kromě toho, pokud vytváříte model Windows Forms ovládací prvky, které chcete použít pro datovou vazbu, je nutné použít vzor *PropertyName*změněn na ovládací prvky, aby se změny vlastnosti Bound ovládacího prvku rozšířily do zdroje dat.  
  
## <a name="change-notification-for-simple-binding"></a>Změna oznámení pro jednoduchou vazbu  
 Pro jednoduchou vazbu musí obchodní objekty poskytnout oznámení o změně při změně hodnoty vlastnosti Bound. To můžete provést vyvoláním události *PropertyName*změněné pro každou vlastnost obchodního objektu a vytvořením vazby obchodního objektu k ovládacím prvkům s <xref:System.Windows.Forms.BindingSource> nebo upřednostňovanou metodou, ve které váš obchodní objekt implementuje rozhraní <xref:System.ComponentModel.INotifyPropertyChanged> a vyvolá událost <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> při změně hodnoty vlastnosti. Další informace naleznete v tématu [How to: Implementing the INotifyPropertyChanged Interface](how-to-implement-the-inotifypropertychanged-interface.md). Pokud používáte objekty, které implementují rozhraní <xref:System.ComponentModel.INotifyPropertyChanged>, nemusíte používat <xref:System.Windows.Forms.BindingSource> k navázání objektu k ovládacímu prvku, ale doporučujeme použít <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="change-notification-for-list-based-binding"></a>Oznámení změny pro vazbu založenou na seznamu  
 Model Windows Forms závisí na vázaném seznamu k poskytnutí změny vlastnosti (Změna hodnoty vlastnosti položky seznamu) a změně seznamu (položka je odstraněna nebo přidána do seznamu) k ovládacím prvkům vázaným na. Proto seznamy používané pro datovou vazbu musí implementovat <xref:System.ComponentModel.IBindingList>, který poskytuje oba typy oznámení o změně. <xref:System.ComponentModel.BindingList%601> je Obecná implementace <xref:System.ComponentModel.IBindingList> a je navržena pro použití s model Windows Forms datovou vazbou. Můžete vytvořit <xref:System.ComponentModel.BindingList%601> obsahující typ obchodního objektu, který implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a seznam automaticky převede <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události na <xref:System.ComponentModel.IBindingList.ListChanged> události. Pokud není vázaný seznam <xref:System.ComponentModel.IBindingList>, je nutné svázat seznam objektů s model Windows Forms ovládacími prvky pomocí komponenty <xref:System.Windows.Forms.BindingSource>. Komponenta <xref:System.Windows.Forms.BindingSource> poskytne převod vlastností na seznam podobný tomu <xref:System.ComponentModel.BindingList%601>. Další informace naleznete v tématu [How to: vyvolání oznámení o změně pomocí objektu BindingSource a rozhraní INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Změna oznámení pro vlastní ovládací prvky  
 Nakonec je třeba ze strany ovládacího prvku zveřejnit událost *PropertyName*změněné pro každou vlastnost navrženou tak, aby byla vázána na data. Změny vlastnosti ovládacího prvku jsou následně šířeny do vázaného zdroje dat. Další informace najdete v tématu [Postupy: použití vzoru PropertyNameChanged.](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
- [Zdroje dat podporované rozhraním Windows Forms](data-sources-supported-by-windows-forms.md)
- [Datové vazby a Windows Forms](data-binding-and-windows-forms.md)
