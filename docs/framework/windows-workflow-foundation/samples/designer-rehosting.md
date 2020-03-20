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
# <a name="designer-rehosting"></a>Změna hostování návrháře
Rehosting návrháře je běžný scénář, který odkazuje na hostování plátna návrhu pracovního postupu uvnitř vlastní aplikace. Hostitelská aplikace, kterou většina lidí zná, je Visual Studio, ale existuje řada scénářů, kde může být užitečné zobrazení návrháře pracovních postupů v aplikaci:  
  
- Monitorování aplikací (umožňující koncovému uživateli vizualizovat proces, stejně jako data za běhu o procesu, jako je například aktuálně aktivní stav, agregovaná data doby provádění nebo jiné informace o instanci pracovního postupu).  
  
- Aplikace, které umožňují uživateli přizpůsobit proces s omezenou sadou aktivit.  
  
 Pro podporu těchto typů aplikací se návrhář pracovního postupu dodává uvnitř rozhraní .NET Framework a může být hostován uvnitř aplikace WPF nebo v aplikaci WinForms s příslušným hostitelským kódem WPF. Tento vzorek ukazuje:  
  
- Rehosting návrháře WF.  
  
- Pomocí rehosted panel u nástrojů a mřížky vlastností stejně.  
  
## <a name="rehosting-the-designer"></a>Rehosting návrháře  
 Tato ukázka ukazuje, jak vytvořit rozložení WPF obsahovat návrháře, vidět v následujícím rozložení mřížky (Toolbox kód vynechán pro mezery obavy). Všimněte si pojmenování ohraničení, které obsahují návrháře a mřížky vlastností.  
  
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
  
 Další ukázka vytvoří návrháře a <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> přidruží jeho primární a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> s příslušným kontejnerem v uživatelském rozhraní. Existuje několik dalších řádků kódu v následujícím příkladu, které si zaslouží nějaké vysvětlení. Volání <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> je nutné přidružit výchozí návrháře aktivit pro aktivity dodávané s rozhraním .NET Framework. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>je volána k předání položky WF, která má být upravena. Nakonec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primární plátno) <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> a (mřížka vlastností) jsou umístěny na povrchuživatelského rozhraní.  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>Použití rehostovaného panelu nástrojů  
 Tato ukázka používá rehosted ovládací prvek panelu nástrojů deklarativně v XAML. Všimněte si, že v kódu, <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> jeden může předat typ konstruktoru.  
  
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
  
#### <a name="using-the-sample"></a>Použití vzorku  
  
1. Otevřete řešení DesignerRehosting.sln v sadě Visual Studio 2010.  
  
2. Stisknutím klávesy F5 zkompilujte a spusťte aplikaci.  
  
3. Aplikace WPF začíná rehosted návrháře.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
