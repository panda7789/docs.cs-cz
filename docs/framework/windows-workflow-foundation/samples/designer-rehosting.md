---
title: Změna hostování návrháře
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 885590604532fba76fc9ab3f6bcc69e077868403
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837351"
---
# <a name="designer-rehosting"></a><span data-ttu-id="95832-102">Změna hostování návrháře</span><span class="sxs-lookup"><span data-stu-id="95832-102">Designer Rehosting</span></span>
<span data-ttu-id="95832-103">Změna hostování návrháře je běžný scénář, který odkazuje na hostování pracovního postupu návrhové plátno v rámci vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="95832-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="95832-104">Hostování aplikace, kterou většina lidí znají je Visual Studio, ale existuje mnoho scénářů, kdy zobrazení návrháře postupu provádění v aplikaci může být užitečné:</span><span class="sxs-lookup"><span data-stu-id="95832-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
-   <span data-ttu-id="95832-105">Monitorování aplikací (umožňuje koncovým uživatelům vizualizovat proces, jakož i dat získaných za běhu o procesu, jako jsou aktuálně aktivním stavu, data agregovaná doba provádění nebo Další informace o instanci pracovního postupu).</span><span class="sxs-lookup"><span data-stu-id="95832-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
-   <span data-ttu-id="95832-106">Aplikace, které umožňují uživatelům přizpůsobit proces s omezenou sadu aktivit.</span><span class="sxs-lookup"><span data-stu-id="95832-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="95832-107">Pro podporu těchto typů aplikací, návrháře postupu provádění se dodává v rozhraní .NET Framework a je možné hostovat v aplikaci WPF nebo aplikace WinForms s odpovídající WPF hostování kódu.</span><span class="sxs-lookup"><span data-stu-id="95832-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="95832-108">V této ukázce:</span><span class="sxs-lookup"><span data-stu-id="95832-108">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="95832-109">Změna hostování návrháře pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="95832-109">Rehosting the WF designer.</span></span>  
  
-   <span data-ttu-id="95832-110">Pomocí provádění se změněným hostováním nástrojů a vlastnost mřížce stejně.</span><span class="sxs-lookup"><span data-stu-id="95832-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="95832-111">Změna hostování návrháře</span><span class="sxs-lookup"><span data-stu-id="95832-111">Rehosting the designer</span></span>  
 <span data-ttu-id="95832-112">Tento příklad ukazuje, jak vytvořit rozložení WPF tak, aby obsahovala návrháři vidět v následující rozložení mřížky (nástrojů kódu vynechána obavy místa).</span><span class="sxs-lookup"><span data-stu-id="95832-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="95832-113">Mějte na paměti, pojmenování ohraničení, které obsahují mřížky Návrháře a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95832-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 <span data-ttu-id="95832-114">Dále ukázka vytvoří návrháře a přidruží jeho primární <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> pomocí odpovídajícího kontejneru v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="95832-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="95832-115">Existuje několik další řádky kódu v následujícím příkladu, které si zasloužila vysvětlení.</span><span class="sxs-lookup"><span data-stu-id="95832-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="95832-116"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Volání je nutné přiřadit výchozí návrháři aktivit pro aktivity, kterou jste dostali se [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95832-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="95832-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> je volána a zajistěte tak předání WF položky bude upravován.</span><span class="sxs-lookup"><span data-stu-id="95832-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="95832-118">Nakonec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primární plátna) a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (mřížky vlastností) jsou umístěné na plochu uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="95832-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="95832-119">Používání sady nástrojů provádění se změněným hostováním</span><span class="sxs-lookup"><span data-stu-id="95832-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="95832-120">Tato ukázka používá ovládací prvek provádění se změněným hostováním nástrojů deklarativně v XAML.</span><span class="sxs-lookup"><span data-stu-id="95832-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="95832-121">Všimněte si, že v kódu, jeden můžete předat typ <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="95832-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a><span data-ttu-id="95832-122">Pomocí ukázky</span><span class="sxs-lookup"><span data-stu-id="95832-122">Using the sample</span></span>  
  
1.  <span data-ttu-id="95832-123">Otevřete DesignerRehosting.sln řešení v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="95832-123">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2.  <span data-ttu-id="95832-124">Stiskněte klávesu F5 ke kompilaci a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="95832-124">Press F5 to compile and run the application.</span></span>  
  
3.  <span data-ttu-id="95832-125">Aplikace WPF začíná návrháři se změněným hostováním.</span><span class="sxs-lookup"><span data-stu-id="95832-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="95832-126">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="95832-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="95832-127">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="95832-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="95832-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="95832-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95832-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="95832-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`