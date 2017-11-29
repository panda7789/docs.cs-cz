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
ms.openlocfilehash: 4697ef7a74916bcc7b922f265262a83b8f0316d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="1029e-102">Postupy: Použití atributů v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1029e-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="1029e-103">Vyvíjet komponenty a ovládací prvky, které správně komunikují s prostředím návrhu a správně spustit v době běhu, musíte použít atributy správně a členy třídy.</span><span class="sxs-lookup"><span data-stu-id="1029e-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1029e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1029e-104">Example</span></span>  
 <span data-ttu-id="1029e-105">Následující příklad kódu ukazuje, jak používat několik atributů na vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1029e-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="1029e-106">Ovládací prvek ukazuje možnosti jednoduché protokolování.</span><span class="sxs-lookup"><span data-stu-id="1029e-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="1029e-107">Pokud je ovládací prvek vázán ke zdroji dat, zobrazuje hodnoty poslal zdroj dat ve <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1029e-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1029e-108">Pokud hodnota přesahuje hodnotu zadanou pomocí `Threshold` vlastnost, `ThresholdExceeded` událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="1029e-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="1029e-109">`AttributesDemoControl` Hodnoty s protokoly `LogEntry` třídy.</span><span class="sxs-lookup"><span data-stu-id="1029e-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="1029e-110">`LogEntry` Třídy je třída šablony, což znamená Parametrizovaná na typ, který protokoluje.</span><span class="sxs-lookup"><span data-stu-id="1029e-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="1029e-111">Například pokud `AttributesDemoControl` je protokolování hodnoty typu `float`, každý `LogEntry` instance je deklarovaná a použita následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="1029e-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="1029e-112">Protože `LogEntry` Parametrizovaná podle libovolného typu, musí používat reflexe pracovat na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="1029e-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="1029e-113">Pro funkci prahová hodnota pro práci s typem parametru `T` musí implementovat <xref:System.IComparable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1029e-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="1029e-114">Formulář, který je hostitelem `AttributesDemoControl` pravidelně dotazuje čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="1029e-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="1029e-115">Každá hodnota je součástí `LogEntry` příslušného typu a přidají se do formuláře <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="1029e-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="1029e-116">`AttributesDemoControl` Obdrží hodnotu prostřednictvím jeho vazby dat a zobrazí se hodnota v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1029e-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="1029e-117">V prvním příkladu kódu je `AttributesDemoControl` implementace.</span><span class="sxs-lookup"><span data-stu-id="1029e-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="1029e-118">Druhý příklad kódu ukazuje formuláře, který používá `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="1029e-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="1029e-119">Atributy na úrovni třídy</span><span class="sxs-lookup"><span data-stu-id="1029e-119">Class-level Attributes</span></span>  
 <span data-ttu-id="1029e-120">Některé atributy jsou použity na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="1029e-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="1029e-121">Následující příklad kódu ukazuje atributy, které se běžně použijí do ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1029e-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="1029e-122">Atribut TypeConverter</span><span class="sxs-lookup"><span data-stu-id="1029e-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="1029e-123"><xref:System.ComponentModel.TypeConverterAttribute>je jiný atribut běžně používané úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="1029e-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="1029e-124">Následující příklad kódu ukazuje pro jeho použití `LogEntry` třídy.</span><span class="sxs-lookup"><span data-stu-id="1029e-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="1029e-125">Tento příklad také ukazuje implementaci <xref:System.ComponentModel.TypeConverter> pro `LogEntry` typu, s názvem `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="1029e-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="1029e-126">Atributy úrovni člena</span><span class="sxs-lookup"><span data-stu-id="1029e-126">Member-level Attributes</span></span>  
 <span data-ttu-id="1029e-127">Některé atributy jsou použity na úrovni člena.</span><span class="sxs-lookup"><span data-stu-id="1029e-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="1029e-128">Následující příklady kódu ukazují některých atributů, které se běžně použijí pro vlastnosti ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1029e-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="1029e-129">Atribut AmbientValue</span><span class="sxs-lookup"><span data-stu-id="1029e-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="1029e-130">Následující příklad ukazuje <xref:System.ComponentModel.AmbientValueAttribute> a zobrazuje kód, který podporuje jeho interakce s prostředím návrhu.</span><span class="sxs-lookup"><span data-stu-id="1029e-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="1029e-131">Tato interakce se nazývá *podmínek, za*.</span><span class="sxs-lookup"><span data-stu-id="1029e-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="1029e-132">Atributy datové vazby</span><span class="sxs-lookup"><span data-stu-id="1029e-132">Databinding Attributes</span></span>  
 <span data-ttu-id="1029e-133">Následující příklady ukazují implementace rozšířené datové vazby.</span><span class="sxs-lookup"><span data-stu-id="1029e-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="1029e-134">Úroveň třída <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, uvedené dříve, určuje `DataSource` a `DataMember` vlastnosti, které chcete použít pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="1029e-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="1029e-135"><xref:System.ComponentModel.AttributeProviderAttribute> Určuje typ, ke které `DataSource` vytvoří vazbu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1029e-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1029e-136">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1029e-136">Compiling the Code</span></span>  
  
-   <span data-ttu-id="1029e-137">Formulář, který je hostitelem `AttributesDemoControl` vyžaduje odkaz na `AttributesDemoControl` sestavení k sestavení.</span><span class="sxs-lookup"><span data-stu-id="1029e-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1029e-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="1029e-138">See Also</span></span>  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="1029e-139">Vývoj vlastních Windows Forms – ovládací prvky s rozhraním .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1029e-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="1029e-140">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1029e-140">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="1029e-141">Postupy: serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="1029e-141">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
