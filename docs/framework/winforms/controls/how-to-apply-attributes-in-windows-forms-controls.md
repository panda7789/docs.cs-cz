---
title: Použití atributů v ovládacích prvcích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: b8ecd516cf6bb189c6ad1b208dd8e3a5444f001c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741489"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Postupy: Použití atributů v ovládacích prvcích Windows Forms
Chcete-li vyvíjet komponenty a ovládací prvky, které pracují správně s návrhovým prostředím a správně spouštěny v době běhu, je nutné správně použít atributy na třídy a členy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak použít několik atributů u vlastního ovládacího prvku. Ovládací prvek znázorňuje jednoduchou schopnost protokolování. Když je ovládací prvek svázán se zdrojem dat, zobrazí hodnoty odesílané zdrojem dat v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Pokud hodnota překročí hodnotu určenou vlastností `Threshold`, vyvolá se událost `ThresholdExceeded`.  
  
 `AttributesDemoControl` protokoluje hodnoty pomocí `LogEntry` třídy. Třída `LogEntry` je třída šablony, což znamená, že je parametrizovaná na typu, který protokoluje. Například pokud `AttributesDemoControl` protokoluje hodnoty typu `float`, každá instance `LogEntry` je deklarována a použita následujícím způsobem.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> Vzhledem k tomu, že `LogEntry` je Parametrizovaná podle libovolného typu, musí použít reflexi pro práci s typem parametru. Aby funkce prahová hodnota fungovala, typ parametru `T` musí implementovat rozhraní <xref:System.IComparable>.  
  
 Formulář, který hostuje `AttributesDemoControl` se pravidelně dotazuje na čítač výkonu. Každá hodnota je zabalena v `LogEntry` příslušného typu a přidána do <xref:System.Windows.Forms.BindingSource>formuláře. `AttributesDemoControl` přijímá hodnotu prostřednictvím své datové vazby a zobrazuje hodnotu v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 První příklad kódu je implementace `AttributesDemoControl`. Druhý příklad kódu ukazuje formulář, který používá `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Atributy na úrovni třídy  
 Některé atributy jsou aplikovány na úrovni třídy. Následující příklad kódu ukazuje atributy, které se běžně používají pro ovládací prvek model Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter – atribut  
 <xref:System.ComponentModel.TypeConverterAttribute> je další běžně používaný atribut na úrovni třídy. Následující příklad kódu ukazuje jeho použití pro třídu `LogEntry`. Tento příklad také ukazuje implementaci <xref:System.ComponentModel.TypeConverter> pro `LogEntry` typ s názvem `LogEntryTypeConverter`.  
  
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
 Následující příklady ukazují implementaci komplexní datové vazby. <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>na úrovni třídy, zobrazené dříve, určuje vlastnosti `DataSource` a `DataMember`, které se mají použít pro datovou vazbu. <xref:System.ComponentModel.AttributeProviderAttribute> určuje typ, do kterého bude navázána vlastnost `DataSource`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Formulář, který je hostitelem `AttributesDemoControl`, vyžaduje odkaz na sestavení `AttributesDemoControl`, aby bylo možné ho sestavit.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
- [Atributy v ovládacích prvcích Windows Forms](attributes-in-windows-forms-controls.md)
- [Postupy: serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
