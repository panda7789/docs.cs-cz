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
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="9b0d6-102">Postupy: Použití atributů v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b0d6-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="9b0d6-103">Chcete-li vyvíjet komponenty a ovládací prvky, které pracují správně s návrhovým prostředím a správně spouštěny v době běhu, je nutné správně použít atributy na třídy a členy.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b0d6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b0d6-104">Example</span></span>  
 <span data-ttu-id="9b0d6-105">Následující příklad kódu ukazuje, jak použít několik atributů u vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="9b0d6-106">Ovládací prvek znázorňuje jednoduchou schopnost protokolování.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="9b0d6-107">Když je ovládací prvek svázán se zdrojem dat, zobrazí hodnoty odesílané zdrojem dat v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9b0d6-108">Pokud hodnota překročí hodnotu určenou vlastností `Threshold`, vyvolá se událost `ThresholdExceeded`.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="9b0d6-109">`AttributesDemoControl` protokoluje hodnoty pomocí `LogEntry` třídy.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="9b0d6-110">Třída `LogEntry` je třída šablony, což znamená, že je parametrizovaná na typu, který protokoluje.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="9b0d6-111">Například pokud `AttributesDemoControl` protokoluje hodnoty typu `float`, každá instance `LogEntry` je deklarována a použita následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="9b0d6-112">Vzhledem k tomu, že `LogEntry` je Parametrizovaná podle libovolného typu, musí použít reflexi pro práci s typem parametru.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="9b0d6-113">Aby funkce prahová hodnota fungovala, typ parametru `T` musí implementovat rozhraní <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="9b0d6-114">Formulář, který hostuje `AttributesDemoControl` se pravidelně dotazuje na čítač výkonu.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="9b0d6-115">Každá hodnota je zabalena v `LogEntry` příslušného typu a přidána do <xref:System.Windows.Forms.BindingSource>formuláře.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="9b0d6-116">`AttributesDemoControl` přijímá hodnotu prostřednictvím své datové vazby a zobrazuje hodnotu v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="9b0d6-117">První příklad kódu je implementace `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="9b0d6-118">Druhý příklad kódu ukazuje formulář, který používá `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="9b0d6-119">Atributy na úrovni třídy</span><span class="sxs-lookup"><span data-stu-id="9b0d6-119">Class-level Attributes</span></span>  
 <span data-ttu-id="9b0d6-120">Některé atributy jsou aplikovány na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="9b0d6-121">Následující příklad kódu ukazuje atributy, které se běžně používají pro ovládací prvek model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="9b0d6-122">TypeConverter – atribut</span><span class="sxs-lookup"><span data-stu-id="9b0d6-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="9b0d6-123"><xref:System.ComponentModel.TypeConverterAttribute> je další běžně používaný atribut na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="9b0d6-124">Následující příklad kódu ukazuje jeho použití pro třídu `LogEntry`.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="9b0d6-125">Tento příklad také ukazuje implementaci <xref:System.ComponentModel.TypeConverter> pro `LogEntry` typ s názvem `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="9b0d6-126">Atributy na úrovni člena</span><span class="sxs-lookup"><span data-stu-id="9b0d6-126">Member-level Attributes</span></span>  
 <span data-ttu-id="9b0d6-127">Některé atributy jsou aplikovány na úrovni členů.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="9b0d6-128">Následující příklady kódu ukazují některé atributy, které jsou obvykle aplikovány na vlastnosti model Windows Formsch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="9b0d6-129">AmbientValue – atribut</span><span class="sxs-lookup"><span data-stu-id="9b0d6-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="9b0d6-130">Následující příklad ukazuje <xref:System.ComponentModel.AmbientValueAttribute> a zobrazuje kód, který podporuje jeho interakci s návrhovým prostředím.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="9b0d6-131">Tato interakce se nazývá *Ambience*.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="9b0d6-132">Atributy datové vazby</span><span class="sxs-lookup"><span data-stu-id="9b0d6-132">Databinding Attributes</span></span>  
 <span data-ttu-id="9b0d6-133">Následující příklady ukazují implementaci komplexní datové vazby.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="9b0d6-134"><xref:System.ComponentModel.ComplexBindingPropertiesAttribute>na úrovni třídy, zobrazené dříve, určuje vlastnosti `DataSource` a `DataMember`, které se mají použít pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="9b0d6-135"><xref:System.ComponentModel.AttributeProviderAttribute> určuje typ, do kterého bude navázána vlastnost `DataSource`.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b0d6-136">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9b0d6-136">Compiling the Code</span></span>  
  
- <span data-ttu-id="9b0d6-137">Formulář, který je hostitelem `AttributesDemoControl`, vyžaduje odkaz na sestavení `AttributesDemoControl`, aby bylo možné ho sestavit.</span><span class="sxs-lookup"><span data-stu-id="9b0d6-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0d6-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b0d6-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="9b0d6-139">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9b0d6-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="9b0d6-140">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b0d6-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="9b0d6-141">[Postupy: serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9b0d6-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
