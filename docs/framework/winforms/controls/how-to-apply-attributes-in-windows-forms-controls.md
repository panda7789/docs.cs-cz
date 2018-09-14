---
title: 'Postupy: Použití atributů v ovládacích prvcích Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 1ab54b0c6828a0648fecfc293b6a7143b012ad6a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45592957"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Postupy: Použití atributů v ovládacích prvcích Windows Forms
K vývoji komponent a ovládacích prvků, které správně komunikují s prostředím návrhu a za běhu se správně spustit, musíte správně používat atributy třídy a členy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak použít několik atributů na vlastním ovládacím prvku. Ovládací prvek ukazuje možnosti jednoduché protokolování. Když je ovládací prvek vázán ke zdroji dat, zobrazí odesílají ve zdroji dat v hodnoty <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pokud hodnota přesahuje hodnotu zadanou proměnnou `Threshold` vlastnost, `ThresholdExceeded` událost se vyvolá.  
  
 `AttributesDemoControl` Protokoly hodnoty `LogEntry` třídy. `LogEntry` Třídy je třída šablony, což znamená, že je parametrizovány na typ, který protokoluje. Například pokud `AttributesDemoControl` je protokolování hodnoty typu `float`každá `LogEntry` instance je deklarován a použít takto.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  Protože `LogEntry` Parametrizovaná podle libovolného typu, musí používat reflexi k provozu na typ parametru. Pro funkci prahová hodnota pro práci, typ parametru `T` musí implementovat <xref:System.IComparable> rozhraní.  
  
 Formulář, který je hostitelem `AttributesDemoControl` pravidelně dotazuje čítače výkonu. Každá hodnota je zabalený ve `LogEntry` příslušného typu a přidat do formuláře <xref:System.Windows.Forms.BindingSource>. `AttributesDemoControl` Přijímá hodnotu prostřednictvím její datové vazby a zobrazí hodnotu v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 V prvním příkladu kódu je `AttributesDemoControl` implementace. Druhý příklad kódu ukazuje formulář, který používá `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Atributy na úrovni třídy  
 Některé atributy jsou použity na úrovni třídy. Následující příklad kódu ukazuje atributy, které se běžně používají k ovládacímu prvku Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>Atribut TypeConverter  
 <xref:System.ComponentModel.TypeConverterAttribute> je jiný atribut běžně používané třídy úrovni. Následující příklad kódu ukazuje jeho použití pro `LogEntry` třídy. Tento příklad také ukazuje implementaci <xref:System.ComponentModel.TypeConverter> pro `LogEntry` typ nazvaný `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Atributy úrovně členu  
 Některé atributy jsou použity na úrovni člena. Následující příklady kódu ukazují některé atributy, které se běžně používají k vlastnostem ovládacích prvků Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>Atribut AmbientValue  
 Následující příklad ukazuje, <xref:System.ComponentModel.AmbientValueAttribute> a zobrazuje kód, který podporuje jeho interakci s prostředím návrhu. Tato interakce je volána *podmínek*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Atributy vázání dat  
 Následující příklady ukazují implementace rozšířené datové vazby. Úrovni třídy <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, jak je znázorněno dříve, určuje, `DataSource` a `DataMember` vlastnosti, které chcete použít pro vytváření datových vazeb. <xref:System.ComponentModel.AttributeProviderAttribute> Určuje typ, ke které `DataSource` vytvoří vazbu vlastnosti.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Formulář, který je hostitelem `AttributesDemoControl` vyžaduje přidání odkazu na `AttributesDemoControl` sestavení k sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Atributy v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [Postupy: serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
