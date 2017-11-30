---
title: "Návrhář opětovného hostování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 005d6f98a7341954801c9b98e9eefdb1f0391d6c
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="designer-rehosting"></a><span data-ttu-id="3a60d-102">Návrhář opětovného hostování</span><span class="sxs-lookup"><span data-stu-id="3a60d-102">Designer ReHosting</span></span>
<span data-ttu-id="3a60d-103">Návrhář opětovného hostování je běžný scénář, který odkazuje na hostování na plátno návrhu pracovního postupu uvnitř vlastní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3a60d-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="3a60d-104">Hostování aplikace, které mají zkušenosti se většina lidí je Visual Studio, ale existuje několik scénářů, kdy zobrazující návrháře pracovních postupů v aplikaci může být užitečné:</span><span class="sxs-lookup"><span data-stu-id="3a60d-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
-   <span data-ttu-id="3a60d-105">Monitorování aplikací (povolení koncový uživatel k vizualizaci procesu, jakož i běhová data o procesu, jako je například stav aktuálně aktivní, data agregovanou dobu provádění nebo Další informace o instanci pracovního postupu).</span><span class="sxs-lookup"><span data-stu-id="3a60d-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
-   <span data-ttu-id="3a60d-106">Aplikace, které uživateli k přizpůsobení procesu s omezenou sadou aktivit.</span><span class="sxs-lookup"><span data-stu-id="3a60d-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="3a60d-107">Pro podporu těchto typů aplikací, návrháře pracovních postupů se dodává v rozhraní .NET Framework a může být hostovaný v aplikaci WPF nebo v aplikaci WinForms s příslušnou WPF hostování kódu.</span><span class="sxs-lookup"><span data-stu-id="3a60d-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="3a60d-108">Tento příklad znázorňuje:</span><span class="sxs-lookup"><span data-stu-id="3a60d-108">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="3a60d-109">Opětovného hostování návrháře WF.</span><span class="sxs-lookup"><span data-stu-id="3a60d-109">Rehosting the WF designer.</span></span>  
  
-   <span data-ttu-id="3a60d-110">Pomocí opětovné hostování nástroje sada nástrojů a vlastnost mřížky také.</span><span class="sxs-lookup"><span data-stu-id="3a60d-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="3a60d-111">Opětovného hostování návrháře</span><span class="sxs-lookup"><span data-stu-id="3a60d-111">Rehosting the designer</span></span>  
 <span data-ttu-id="3a60d-112">Tento příklad ukazuje postup vytvoření rozložení WPF tak, aby obsahovala návrháře, vidět v následujícím rozložení mřížky (sada nástrojů kód vynechání pro riziko z hlediska místa).</span><span class="sxs-lookup"><span data-stu-id="3a60d-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="3a60d-113">Všimněte si názvů ohraničení, které obsahují designer a vlastnost mřížky.</span><span class="sxs-lookup"><span data-stu-id="3a60d-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
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
  
 <span data-ttu-id="3a60d-114">Další ukázky vytvoří návrháře a přidruží jeho primární <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> s odpovídajícího kontejneru v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3a60d-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="3a60d-115">Existuje několik další řádky kódu v následujícím příkladu, které si zasloužila vysvětlení.</span><span class="sxs-lookup"><span data-stu-id="3a60d-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="3a60d-116"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Volání je potřeba přidružit návrháře aktivit výchozí pro aktivity součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a60d-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="3a60d-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>je volána předávat WF položku, kterou chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="3a60d-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="3a60d-118">Nakonec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primární plátno) a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (mřížkou vlastností) jsou umístěny na plochu uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3a60d-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
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
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="3a60d-119">Pomocí sady nástrojů opětovné hostování nástroje</span><span class="sxs-lookup"><span data-stu-id="3a60d-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="3a60d-120">Tato ukázka ovládacího prvku opětovné hostování nástroje sada nástrojů používá deklarativně v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="3a60d-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="3a60d-121">Všimněte si, že v kódu, jeden předat typu k <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="3a60d-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="3a60d-122">Pomocí vzorku</span><span class="sxs-lookup"><span data-stu-id="3a60d-122">Using the sample</span></span>  
  
1.  <span data-ttu-id="3a60d-123">Otevřete řešení DesignerRehosting.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a60d-123">Open the DesignerRehosting.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="3a60d-124">Stisknutím klávesy F5 zkompilování a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a60d-124">Press F5 to compile and run the application.</span></span>  
  
3.  <span data-ttu-id="3a60d-125">Aplikace WPF začíná opětovné hostování nástroje návrháře.</span><span class="sxs-lookup"><span data-stu-id="3a60d-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3a60d-126">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="3a60d-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3a60d-127">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3a60d-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3a60d-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3a60d-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a60d-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3a60d-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`