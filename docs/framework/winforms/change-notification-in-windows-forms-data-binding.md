---
title: Oznámení změn v datové vazbě rozhraní Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 559cdee1cce84df1c4b838e249d11ba235a0c636
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097574"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Oznámení změn v datové vazbě rozhraní Windows Forms
Jednou z nejdůležitějších pojmů Windows Forms – datová vazba je *oznámení o změně*. Pokud chcete mít jistotu, že zdroj dat a ovládací prvky vázané vždy mít nejnovější data, je nutné přidat oznámení o změně pro datovou vazbu. Konkrétně chcete mít jistotu, že vázané ovládací prvky se zobrazí oznámení o změnách, které byly provedeny na jejich zdroj dat a zdroj dat je oznámení o změnách, které byly provedeny vázané vlastnosti ovládacího prvku.  
  
 Existují různé druhy oznámení o změně, v závislosti na druhu datové vazby:  
  
-   Jednoduchá vazba, ve kterém je vlastnost jeden ovládací prvek vázán na jednu instanci objektu.  
  
-   Vazba založený na seznamu, který může obsahovat jeden ovládací prvek vlastnost vázána na vlastnost položky v seznamu nebo vlastnosti ovládacího prvku vázán na seznam objektů.  
  
 Kromě toho při vytváření ovládacích prvků Windows Forms, který chcete použít pro datové vazby, musíte použít *PropertyName*změnit vzor k ovládacím prvkům tak, aby změny vázané vlastnosti ovládacího prvku se rozšíří na zdroj dat.  
  
## <a name="change-notification-for-simple-binding"></a>Oznámení o změně pro jednoduchých připojení  
 Pro jednoduché vazby, musí pro obchodní objekty poskytují oznámení o změně při změně hodnoty vázané vlastnosti. Uděláte to tak vystavení *PropertyName*změněné události pro každou vlastnost objektu vaší firmy a obchodní objekt vazeb k ovládacím prvkům s <xref:System.Windows.Forms.BindingSource> nebo upřednostňovanou metodou, ve kterém se implementuje obchodní objekt <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní a vyvolá <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události při změně hodnoty vlastnosti. Další informace najdete v tématu [jak: Implementace rozhraní INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md). Při použití objektů implementujících <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní, není nutné používat <xref:System.Windows.Forms.BindingSource> pro vazbu objektu do ovládacího prvku, ale pomocí <xref:System.Windows.Forms.BindingSource> se doporučuje.  
  
## <a name="change-notification-for-list-based-binding"></a>Oznámení o změně pro vazbu založenou na seznam  
 Windows Forms závisí na změnit a vazby seznam poskytnout změnu vlastnosti (změně hodnoty vlastnosti položky seznamu) (položku se odstraní nebo přidat do seznamu) informace, které vázané ovládací prvky. Proto musí implementovat seznamů používané pro vytváření datových vazeb <xref:System.ComponentModel.IBindingList>, která obsahuje oba typy oznámení o změně. <xref:System.ComponentModel.BindingList%601> Je obecnou implementaci <xref:System.ComponentModel.IBindingList> a je určený k použití pomocí Windows Forms – datová vazba. Můžete vytvořit <xref:System.ComponentModel.BindingList%601> obsahující obchodní typ objektu, který implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a v seznamu se automaticky převede <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události <xref:System.ComponentModel.IBindingList.ListChanged> události. Pokud není vázaná seznam <xref:System.ComponentModel.IBindingList>, je třeba svázat seznam objektů k ovládacím prvkům Windows Forms s použitím <xref:System.Windows.Forms.BindingSource> komponenty. <xref:System.Windows.Forms.BindingSource> Komponenty poskytne seznam vlastností převod podobný <xref:System.ComponentModel.BindingList%601>. Další informace najdete v tématu [jak: Vytváření oznámení o změnách pomocí BindingSource a INotifyPropertyChanged – rozhraní](./controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Oznámení o změně pro vlastní ovládací prvky  
 Nakonec na straně ovládacího prvku musí vystavit *PropertyName*změněné události pro každou vlastnost navržené tak, aby vázán na data. Změny vlastnosti ovládacího prvku se pak rozšíří ke zdroji dat vázaná. Další informace najdete v tématu [jak: Použití vzoru PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
- [Zdroje dat podporované rozhraním Windows Forms](data-sources-supported-by-windows-forms.md)
- [Datové vazby a rozhraní Windows Forms](data-binding-and-windows-forms.md)
