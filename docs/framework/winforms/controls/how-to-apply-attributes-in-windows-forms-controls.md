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
ms.openlocfilehash: 273d32927582f4467a92cd3b8f87e699c1f167d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922785"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Postupy: Použití atributů v ovládacích prvcích Windows Forms
Chcete-li vyvíjet komponenty a ovládací prvky, které pracují správně s návrhovým prostředím a správně spouštěny v době běhu, je nutné správně použít atributy na třídy a členy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak použít několik atributů u vlastního ovládacího prvku. Ovládací prvek znázorňuje jednoduchou schopnost protokolování. Když je ovládací prvek svázán se zdrojem dat, zobrazí hodnoty odesílané zdrojem dat v <xref:System.Windows.Forms.DataGridView> ovládacím prvku. Pokud hodnota přesáhne hodnotu určenou `Threshold` vlastností `ThresholdExceeded` , je vyvolána událost.  
  
 Protokoluje hodnoty `LogEntry` pomocí třídy. `AttributesDemoControl` `LogEntry` Třída je třída šablony, což znamená, že je parametrizovaná na typu, který protokoluje. Například pokud `AttributesDemoControl` je protokolována hodnota typu `float`, každá `LogEntry` instance je deklarována a použita následujícím způsobem.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> Vzhledem `LogEntry` k tomu, že je parametrizovaný libovolným typem, musí použít reflexi pro práci s typem parametru. Aby funkce prahová hodnota fungovala, musí typ `T` parametru <xref:System.IComparable> implementovat rozhraní.  
  
 Formulář, který hostuje `AttributesDemoControl` dotaz na čítač výkonu periodicky. Každá hodnota je zabalena v `LogEntry` příslušném typu a přidána do <xref:System.Windows.Forms.BindingSource>formuláře. Získá hodnotu prostřednictvím své datové vazby a zobrazí hodnotu <xref:System.Windows.Forms.DataGridView> v ovládacím prvku. `AttributesDemoControl`  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 První příklad kódu je `AttributesDemoControl` implementace. Druhý příklad kódu ukazuje formulář, který používá `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Atributy na úrovni třídy  
 Některé atributy jsou aplikovány na úrovni třídy. Následující příklad kódu ukazuje atributy, které se běžně používají pro ovládací prvek model Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter – atribut  
 <xref:System.ComponentModel.TypeConverterAttribute>je dalším běžně používaným atributem na úrovni třídy. Následující příklad kódu ukazuje jeho použití pro `LogEntry` třídu. Tento příklad také ukazuje implementaci <xref:System.ComponentModel.TypeConverter> `LogEntry` pro typ s názvem `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Atributy na úrovni člena  
 Některé atributy jsou aplikovány na úrovni členů. Následující příklady kódu ukazují některé atributy, které jsou obvykle aplikovány na vlastnosti model Windows Formsch ovládacích prvků.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue – atribut  
 Následující příklad ukazuje <xref:System.ComponentModel.AmbientValueAttribute> a zobrazuje kód, který podporuje jeho interakci s návrhovým prostředím. Tato interakce se nazývá *Ambience*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Atributy datové vazby  
 Následující příklady ukazují implementaci komplexní datové vazby. Úroveň <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>třídy, zobrazená dříve, `DataSource` určuje vlastnosti a `DataMember` , které se mají použít pro datovou vazbu. Určuje typ, na `DataSource` který bude vlastnost navázána. <xref:System.ComponentModel.AttributeProviderAttribute>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Formulář, který je `AttributesDemoControl` hostitelem, vyžaduje odkaz `AttributesDemoControl` na sestavení, aby jej bylo možné sestavit.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
- [Atributy v ovládacích prvcích Windows Forms](attributes-in-windows-forms-controls.md)
- [Postupy: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
