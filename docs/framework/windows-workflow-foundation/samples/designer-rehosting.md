---
title: Opětovné hostování návrháře
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: f98b1823c74471c96f6d4b67ec47637bb0785d8f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715239"
---
# <a name="designer-rehosting"></a><span data-ttu-id="f6b1c-102">Změna hostování návrháře</span><span class="sxs-lookup"><span data-stu-id="f6b1c-102">Designer Rehosting</span></span>
<span data-ttu-id="f6b1c-103">Opětovné hostování návrháře je běžným scénářem, který odkazuje na hostování plátna pro návrh pracovního postupu v rámci vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="f6b1c-104">Hostující aplikace je obeznámená se sadou Visual Studio, existuje však několik scénářů, kde se zobrazuje Návrhář pracovního postupu v aplikaci může být užitečný:</span><span class="sxs-lookup"><span data-stu-id="f6b1c-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="f6b1c-105">Monitorování aplikací (umožnění koncovému uživateli vizualizovat proces a také běhová data týkající se procesu, jako je aktuálně aktivní stav, agregovaná data času spuštění nebo jiné informace o instanci pracovního postupu).</span><span class="sxs-lookup"><span data-stu-id="f6b1c-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="f6b1c-106">Aplikace, které uživateli umožňují přizpůsobit proces pomocí omezené sady aktivit.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="f6b1c-107">Pro podporu těchto typů aplikací je Návrhář pracovního postupu dodáván uvnitř .NET Framework a lze jej hostovat v aplikaci WPF nebo v aplikaci WinForms s příslušným hostitelským kódem WPF.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="f6b1c-108">Tato ukázka demonstruje:</span><span class="sxs-lookup"><span data-stu-id="f6b1c-108">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="f6b1c-109">Opětovné hostování návrháře WF.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-109">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="f6b1c-110">Použijte taky znovu hostující sadu nástrojů a mřížku vlastností.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="f6b1c-111">Opětovné hostování návrháře</span><span class="sxs-lookup"><span data-stu-id="f6b1c-111">Rehosting the designer</span></span>  
 <span data-ttu-id="f6b1c-112">Tento příklad ukazuje, jak vytvořit rozložení WPF pro zahrnutí návrháře, zobrazeného v následujícím rozložení mřížky (kód sady nástrojů byl vynechán pro prostorové informace).</span><span class="sxs-lookup"><span data-stu-id="f6b1c-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="f6b1c-113">Poznamenejte si pojmenování ohraničení obsahujícího návrháře a mřížku vlastností.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
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
  
 <span data-ttu-id="f6b1c-114">V dalším příkladu vytvoří návrháře a přidruží jeho primární <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> k příslušnému kontejneru v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="f6b1c-115">V následujícím příkladu je několik dalších řádků kódu, které představují nějaké vysvětlení.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="f6b1c-116">Aby bylo možné přidružit návrháře výchozích aktivit pro aktivity dodávané s .NET Framework, je nutné <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> volání.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="f6b1c-117">k předání položky WF, která se má upravit, se volá <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="f6b1c-118">Nakonec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primární plátno) a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (Mřížka vlastností) se umístí na plochu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
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
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="f6b1c-119">Používání znovu hostované sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="f6b1c-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="f6b1c-120">Tato ukázka používá znovu hostující ovládací prvek sady nástrojů v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="f6b1c-121">Všimněte si, že v kódu může jeden předat typ konstruktoru <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper>.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="f6b1c-122">Použití ukázky</span><span class="sxs-lookup"><span data-stu-id="f6b1c-122">Using the sample</span></span>  
  
1. <span data-ttu-id="f6b1c-123">Otevřete řešení DesignerRehosting. sln v aplikaci Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-123">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="f6b1c-124">Pro zkompilování a spuštění aplikace stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-124">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="f6b1c-125">Aplikace WPF se spouští s opětovně hostovaným návrhářem.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f6b1c-126">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f6b1c-127">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-127">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f6b1c-128">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6b1c-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f6b1c-129">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
