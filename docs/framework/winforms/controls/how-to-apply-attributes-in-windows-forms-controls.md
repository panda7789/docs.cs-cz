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
ms.openlocfilehash: 35cd40a3219c86e8f82f85360bf213d6ef3f9fc6
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583937"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="47e0f-102">Postupy: Použití atributů v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="47e0f-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="47e0f-103">K vývoji komponent a ovládacích prvků, které správně komunikují s prostředím návrhu a za běhu se správně spustit, musíte správně používat atributy třídy a členy.</span><span class="sxs-lookup"><span data-stu-id="47e0f-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47e0f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="47e0f-104">Example</span></span>  
 <span data-ttu-id="47e0f-105">Následující příklad kódu ukazuje, jak použít několik atributů na vlastním ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="47e0f-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="47e0f-106">Ovládací prvek ukazuje možnosti jednoduché protokolování.</span><span class="sxs-lookup"><span data-stu-id="47e0f-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="47e0f-107">Když je ovládací prvek vázán ke zdroji dat, zobrazí odesílají ve zdroji dat v hodnoty <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="47e0f-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="47e0f-108">Pokud hodnota přesahuje hodnotu zadanou proměnnou `Threshold` vlastnost, `ThresholdExceeded` událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="47e0f-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="47e0f-109">`AttributesDemoControl` Protokoly hodnoty `LogEntry` třídy.</span><span class="sxs-lookup"><span data-stu-id="47e0f-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="47e0f-110">`LogEntry` Třídy je třída šablony, což znamená, že je parametrizovány na typ, který protokoluje.</span><span class="sxs-lookup"><span data-stu-id="47e0f-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="47e0f-111">Například pokud `AttributesDemoControl` je protokolování hodnoty typu `float`každá `LogEntry` instance je deklarován a použít takto.</span><span class="sxs-lookup"><span data-stu-id="47e0f-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="47e0f-112">Protože `LogEntry` Parametrizovaná podle libovolného typu, musí používat reflexi k provozu na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="47e0f-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="47e0f-113">Pro funkci prahová hodnota pro práci, typ parametru `T` musí implementovat <xref:System.IComparable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47e0f-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="47e0f-114">Formulář, který je hostitelem `AttributesDemoControl` pravidelně dotazuje čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="47e0f-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="47e0f-115">Každá hodnota je zabalený ve `LogEntry` příslušného typu a přidat do formuláře <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="47e0f-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="47e0f-116">`AttributesDemoControl` Přijímá hodnotu prostřednictvím její datové vazby a zobrazí hodnotu v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="47e0f-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="47e0f-117">V prvním příkladu kódu je `AttributesDemoControl` implementace.</span><span class="sxs-lookup"><span data-stu-id="47e0f-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="47e0f-118">Druhý příklad kódu ukazuje formulář, který používá `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="47e0f-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="47e0f-119">Atributy na úrovni třídy</span><span class="sxs-lookup"><span data-stu-id="47e0f-119">Class-level Attributes</span></span>  
 <span data-ttu-id="47e0f-120">Některé atributy jsou použity na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="47e0f-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="47e0f-121">Následující příklad kódu ukazuje atributy, které se běžně používají k ovládacímu prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="47e0f-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="47e0f-122">Atribut TypeConverter</span><span class="sxs-lookup"><span data-stu-id="47e0f-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="47e0f-123"><xref:System.ComponentModel.TypeConverterAttribute> je jiný atribut běžně používané třídy úrovni.</span><span class="sxs-lookup"><span data-stu-id="47e0f-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="47e0f-124">Následující příklad kódu ukazuje jeho použití pro `LogEntry` třídy.</span><span class="sxs-lookup"><span data-stu-id="47e0f-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="47e0f-125">Tento příklad také ukazuje implementaci <xref:System.ComponentModel.TypeConverter> pro `LogEntry` typ nazvaný `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="47e0f-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="47e0f-126">Atributy úrovně členu</span><span class="sxs-lookup"><span data-stu-id="47e0f-126">Member-level Attributes</span></span>  
 <span data-ttu-id="47e0f-127">Některé atributy jsou použity na úrovni člena.</span><span class="sxs-lookup"><span data-stu-id="47e0f-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="47e0f-128">Následující příklady kódu ukazují některé atributy, které se běžně používají k vlastnostem ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="47e0f-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="47e0f-129">Atribut AmbientValue</span><span class="sxs-lookup"><span data-stu-id="47e0f-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="47e0f-130">Následující příklad ukazuje, <xref:System.ComponentModel.AmbientValueAttribute> a zobrazuje kód, který podporuje jeho interakci s prostředím návrhu.</span><span class="sxs-lookup"><span data-stu-id="47e0f-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="47e0f-131">Tato interakce je volána *podmínek*.</span><span class="sxs-lookup"><span data-stu-id="47e0f-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="47e0f-132">Atributy vázání dat</span><span class="sxs-lookup"><span data-stu-id="47e0f-132">Databinding Attributes</span></span>  
 <span data-ttu-id="47e0f-133">Následující příklady ukazují implementace rozšířené datové vazby.</span><span class="sxs-lookup"><span data-stu-id="47e0f-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="47e0f-134">Úrovni třídy <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, jak je znázorněno dříve, určuje, `DataSource` a `DataMember` vlastnosti, které chcete použít pro vytváření datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="47e0f-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="47e0f-135"><xref:System.ComponentModel.AttributeProviderAttribute> Určuje typ, ke které `DataSource` vytvoří vazbu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="47e0f-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47e0f-136">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="47e0f-136">Compiling the Code</span></span>  
  
-   <span data-ttu-id="47e0f-137">Formulář, který je hostitelem `AttributesDemoControl` vyžaduje přidání odkazu na `AttributesDemoControl` sestavení k sestavení.</span><span class="sxs-lookup"><span data-stu-id="47e0f-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e0f-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47e0f-138">See also</span></span>
- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="47e0f-139">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47e0f-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="47e0f-140">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="47e0f-140">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
- <span data-ttu-id="47e0f-141">[Postupy: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="47e0f-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
