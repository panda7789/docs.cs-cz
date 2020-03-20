---
title: Změna hostování návrháře
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: b72e3450799db40988c8b99e4db3707de330d8ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182824"
---
# <a name="designer-rehosting"></a><span data-ttu-id="0723a-102">Změna hostování návrháře</span><span class="sxs-lookup"><span data-stu-id="0723a-102">Designer Rehosting</span></span>
<span data-ttu-id="0723a-103">Rehosting návrháře je běžný scénář, který odkazuje na hostování plátna návrhu pracovního postupu uvnitř vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="0723a-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="0723a-104">Hostitelská aplikace, kterou většina lidí zná, je Visual Studio, ale existuje řada scénářů, kde může být užitečné zobrazení návrháře pracovních postupů v aplikaci:</span><span class="sxs-lookup"><span data-stu-id="0723a-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="0723a-105">Monitorování aplikací (umožňující koncovému uživateli vizualizovat proces, stejně jako data za běhu o procesu, jako je například aktuálně aktivní stav, agregovaná data doby provádění nebo jiné informace o instanci pracovního postupu).</span><span class="sxs-lookup"><span data-stu-id="0723a-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="0723a-106">Aplikace, které umožňují uživateli přizpůsobit proces s omezenou sadou aktivit.</span><span class="sxs-lookup"><span data-stu-id="0723a-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="0723a-107">Pro podporu těchto typů aplikací se návrhář pracovního postupu dodává uvnitř rozhraní .NET Framework a může být hostován uvnitř aplikace WPF nebo v aplikaci WinForms s příslušným hostitelským kódem WPF.</span><span class="sxs-lookup"><span data-stu-id="0723a-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="0723a-108">Tento vzorek ukazuje:</span><span class="sxs-lookup"><span data-stu-id="0723a-108">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="0723a-109">Rehosting návrháře WF.</span><span class="sxs-lookup"><span data-stu-id="0723a-109">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="0723a-110">Pomocí rehosted panel u nástrojů a mřížky vlastností stejně.</span><span class="sxs-lookup"><span data-stu-id="0723a-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="0723a-111">Rehosting návrháře</span><span class="sxs-lookup"><span data-stu-id="0723a-111">Rehosting the designer</span></span>  
 <span data-ttu-id="0723a-112">Tato ukázka ukazuje, jak vytvořit rozložení WPF obsahovat návrháře, vidět v následujícím rozložení mřížky (Toolbox kód vynechán pro mezery obavy).</span><span class="sxs-lookup"><span data-stu-id="0723a-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="0723a-113">Všimněte si pojmenování ohraničení, které obsahují návrháře a mřížky vlastností.</span><span class="sxs-lookup"><span data-stu-id="0723a-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
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
  
 <span data-ttu-id="0723a-114">Další ukázka vytvoří návrháře a <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> přidruží jeho primární a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> s příslušným kontejnerem v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0723a-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="0723a-115">Existuje několik dalších řádků kódu v následujícím příkladu, které si zaslouží nějaké vysvětlení.</span><span class="sxs-lookup"><span data-stu-id="0723a-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="0723a-116">Volání <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> je nutné přidružit výchozí návrháře aktivit pro aktivity dodávané s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0723a-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="0723a-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>je volána k předání položky WF, která má být upravena.</span><span class="sxs-lookup"><span data-stu-id="0723a-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="0723a-118">Nakonec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primární plátno) <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> a (mřížka vlastností) jsou umístěny na povrchuživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0723a-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
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
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="0723a-119">Použití rehostovaného panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="0723a-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="0723a-120">Tato ukázka používá rehosted ovládací prvek panelu nástrojů deklarativně v XAML.</span><span class="sxs-lookup"><span data-stu-id="0723a-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="0723a-121">Všimněte si, že v kódu, <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> jeden může předat typ konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0723a-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="0723a-122">Použití vzorku</span><span class="sxs-lookup"><span data-stu-id="0723a-122">Using the sample</span></span>  
  
1. <span data-ttu-id="0723a-123">Otevřete řešení DesignerRehosting.sln v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="0723a-123">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="0723a-124">Stisknutím klávesy F5 zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0723a-124">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="0723a-125">Aplikace WPF začíná rehosted návrháře.</span><span class="sxs-lookup"><span data-stu-id="0723a-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0723a-126">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="0723a-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0723a-127">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="0723a-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0723a-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0723a-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0723a-129">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0723a-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
