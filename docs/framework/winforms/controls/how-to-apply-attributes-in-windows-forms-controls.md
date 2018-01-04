---
title: "Postupy: Použití atributů v ovládacích prvcích Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e4d5bfb445ce6ed37ad1dc63d92fde833ac9870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Postupy: Použití atributů v ovládacích prvcích Windows Forms
Vyvíjet komponenty a ovládací prvky, které správně komunikují s prostředím návrhu a správně spustit v době běhu, musíte použít atributy správně a členy třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat několik atributů na vlastního ovládacího prvku. Ovládací prvek ukazuje možnosti jednoduché protokolování. Pokud je ovládací prvek vázán ke zdroji dat, zobrazuje hodnoty poslal zdroj dat ve <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pokud hodnota přesahuje hodnotu zadanou pomocí `Threshold` vlastnost, `ThresholdExceeded` událost se vyvolá.  
  
 `AttributesDemoControl` Hodnoty s protokoly `LogEntry` třídy. `LogEntry` Třídy je třída šablony, což znamená Parametrizovaná na typ, který protokoluje. Například pokud `AttributesDemoControl` je protokolování hodnoty typu `float`, každý `LogEntry` instance je deklarovaná a použita následujícím způsobem.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  Protože `LogEntry` Parametrizovaná podle libovolného typu, musí používat reflexe pracovat na typ parametru. Pro funkci prahová hodnota pro práci s typem parametru `T` musí implementovat <xref:System.IComparable> rozhraní.  
  
 Formulář, který je hostitelem `AttributesDemoControl` pravidelně dotazuje čítače výkonu. Každá hodnota je součástí `LogEntry` příslušného typu a přidají se do formuláře <xref:System.Windows.Forms.BindingSource>. `AttributesDemoControl` Obdrží hodnotu prostřednictvím jeho vazby dat a zobrazí se hodnota v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 V prvním příkladu kódu je `AttributesDemoControl` implementace. Druhý příklad kódu ukazuje formuláře, který používá `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Atributy na úrovni třídy  
 Některé atributy jsou použity na úrovni třídy. Následující příklad kódu ukazuje atributy, které se běžně použijí do ovládacího prvku Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>Atribut TypeConverter  
 <xref:System.ComponentModel.TypeConverterAttribute>je jiný atribut běžně používané úrovni třídy. Následující příklad kódu ukazuje pro jeho použití `LogEntry` třídy. Tento příklad také ukazuje implementaci <xref:System.ComponentModel.TypeConverter> pro `LogEntry` typu, s názvem `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Atributy úrovni člena  
 Některé atributy jsou použity na úrovni člena. Následující příklady kódu ukazují některých atributů, které se běžně použijí pro vlastnosti ovládacích prvků Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>Atribut AmbientValue  
 Následující příklad ukazuje <xref:System.ComponentModel.AmbientValueAttribute> a zobrazuje kód, který podporuje jeho interakce s prostředím návrhu. Tato interakce se nazývá *podmínek, za*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Atributy datové vazby  
 Následující příklady ukazují implementace rozšířené datové vazby. Úroveň třída <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, uvedené dříve, určuje `DataSource` a `DataMember` vlastnosti, které chcete použít pro datovou vazbu. <xref:System.ComponentModel.AttributeProviderAttribute> Určuje typ, ke které `DataSource` vytvoří vazbu vlastnosti.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Formulář, který je hostitelem `AttributesDemoControl` vyžaduje odkaz na `AttributesDemoControl` sestavení k sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Atributy v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [Postupy: serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
