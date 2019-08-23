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
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="bbaaa-102">Postupy: Použití atributů v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbaaa-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="bbaaa-103">Chcete-li vyvíjet komponenty a ovládací prvky, které pracují správně s návrhovým prostředím a správně spouštěny v době běhu, je nutné správně použít atributy na třídy a členy.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbaaa-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbaaa-104">Example</span></span>  
 <span data-ttu-id="bbaaa-105">Následující příklad kódu ukazuje, jak použít několik atributů u vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="bbaaa-106">Ovládací prvek znázorňuje jednoduchou schopnost protokolování.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="bbaaa-107">Když je ovládací prvek svázán se zdrojem dat, zobrazí hodnoty odesílané zdrojem dat v <xref:System.Windows.Forms.DataGridView> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="bbaaa-108">Pokud hodnota přesáhne hodnotu určenou `Threshold` vlastností `ThresholdExceeded` , je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="bbaaa-109">Protokoluje hodnoty `LogEntry` pomocí třídy. `AttributesDemoControl`</span><span class="sxs-lookup"><span data-stu-id="bbaaa-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="bbaaa-110">`LogEntry` Třída je třída šablony, což znamená, že je parametrizovaná na typu, který protokoluje.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="bbaaa-111">Například pokud `AttributesDemoControl` je protokolována hodnota typu `float`, každá `LogEntry` instance je deklarována a použita následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="bbaaa-112">Vzhledem `LogEntry` k tomu, že je parametrizovaný libovolným typem, musí použít reflexi pro práci s typem parametru.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="bbaaa-113">Aby funkce prahová hodnota fungovala, musí typ `T` parametru <xref:System.IComparable> implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="bbaaa-114">Formulář, který hostuje `AttributesDemoControl` dotaz na čítač výkonu periodicky.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="bbaaa-115">Každá hodnota je zabalena v `LogEntry` příslušném typu a přidána do <xref:System.Windows.Forms.BindingSource>formuláře.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="bbaaa-116">Získá hodnotu prostřednictvím své datové vazby a zobrazí hodnotu <xref:System.Windows.Forms.DataGridView> v ovládacím prvku. `AttributesDemoControl`</span><span class="sxs-lookup"><span data-stu-id="bbaaa-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="bbaaa-117">První příklad kódu je `AttributesDemoControl` implementace.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="bbaaa-118">Druhý příklad kódu ukazuje formulář, který používá `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="bbaaa-119">Atributy na úrovni třídy</span><span class="sxs-lookup"><span data-stu-id="bbaaa-119">Class-level Attributes</span></span>  
 <span data-ttu-id="bbaaa-120">Některé atributy jsou aplikovány na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="bbaaa-121">Následující příklad kódu ukazuje atributy, které se běžně používají pro ovládací prvek model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="bbaaa-122">TypeConverter – atribut</span><span class="sxs-lookup"><span data-stu-id="bbaaa-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="bbaaa-123"><xref:System.ComponentModel.TypeConverterAttribute>je dalším běžně používaným atributem na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="bbaaa-124">Následující příklad kódu ukazuje jeho použití pro `LogEntry` třídu.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="bbaaa-125">Tento příklad také ukazuje implementaci <xref:System.ComponentModel.TypeConverter> `LogEntry` pro typ s názvem `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="bbaaa-126">Atributy na úrovni člena</span><span class="sxs-lookup"><span data-stu-id="bbaaa-126">Member-level Attributes</span></span>  
 <span data-ttu-id="bbaaa-127">Některé atributy jsou aplikovány na úrovni členů.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="bbaaa-128">Následující příklady kódu ukazují některé atributy, které jsou obvykle aplikovány na vlastnosti model Windows Formsch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="bbaaa-129">AmbientValue – atribut</span><span class="sxs-lookup"><span data-stu-id="bbaaa-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="bbaaa-130">Následující příklad ukazuje <xref:System.ComponentModel.AmbientValueAttribute> a zobrazuje kód, který podporuje jeho interakci s návrhovým prostředím.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="bbaaa-131">Tato interakce se nazývá *Ambience*.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="bbaaa-132">Atributy datové vazby</span><span class="sxs-lookup"><span data-stu-id="bbaaa-132">Databinding Attributes</span></span>  
 <span data-ttu-id="bbaaa-133">Následující příklady ukazují implementaci komplexní datové vazby.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="bbaaa-134">Úroveň <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>třídy, zobrazená dříve, `DataSource` určuje vlastnosti a `DataMember` , které se mají použít pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="bbaaa-135">Určuje typ, na `DataSource` který bude vlastnost navázána. <xref:System.ComponentModel.AttributeProviderAttribute></span><span class="sxs-lookup"><span data-stu-id="bbaaa-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbaaa-136">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bbaaa-136">Compiling the Code</span></span>  
  
- <span data-ttu-id="bbaaa-137">Formulář, který je `AttributesDemoControl` hostitelem, vyžaduje odkaz `AttributesDemoControl` na sestavení, aby jej bylo možné sestavit.</span><span class="sxs-lookup"><span data-stu-id="bbaaa-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbaaa-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbaaa-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="bbaaa-139">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bbaaa-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="bbaaa-140">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbaaa-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="bbaaa-141">[Postupy: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="bbaaa-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
