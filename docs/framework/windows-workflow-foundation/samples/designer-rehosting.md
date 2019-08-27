---
title: Opětovné hostování návrháře
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: ecbea5822825cca5f3f5cf40e20d5d249b17b07c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038193"
---
# <a name="designer-rehosting"></a>Změna hostování návrháře
Opětovné hostování návrháře je běžným scénářem, který odkazuje na hostování plátna pro návrh pracovního postupu v rámci vlastní aplikace. Hostující aplikace je obeznámená se sadou Visual Studio, existuje však několik scénářů, kde se zobrazuje Návrhář pracovního postupu v aplikaci může být užitečný:  
  
- Monitorování aplikací (umožnění koncovému uživateli vizualizovat proces a také běhová data týkající se procesu, jako je aktuálně aktivní stav, agregovaná data času spuštění nebo jiné informace o instanci pracovního postupu).  
  
- Aplikace, které uživateli umožňují přizpůsobit proces pomocí omezené sady aktivit.  
  
 Pro podporu těchto typů aplikací je Návrhář pracovního postupu dodáván uvnitř .NET Framework a lze jej hostovat v aplikaci WPF nebo v aplikaci WinForms s příslušným hostitelským kódem WPF. Tato ukázka demonstruje:  
  
- Opětovné hostování návrháře WF.  
  
- Použijte taky znovu hostující sadu nástrojů a mřížku vlastností.  
  
## <a name="rehosting-the-designer"></a>Opětovné hostování návrháře  
 Tento příklad ukazuje, jak vytvořit rozložení WPF pro zahrnutí návrháře, zobrazeného v následujícím rozložení mřížky (kód sady nástrojů byl vynechán pro prostorové informace). Poznamenejte si pojmenování ohraničení obsahujícího návrháře a mřížku vlastností.  
  
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
  
 Další příklad vytvoří návrháře a přidruží jeho primární <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> k příslušnému kontejneru v uživatelském rozhraní. V následujícím příkladu je několik dalších řádků kódu, které představují nějaké vysvětlení. <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Volání je vyžadováno k přidružení výchozích návrhářů aktivit pro aktivity dodávané s .NET Framework. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>se volá, aby se předávala položka WF, která se má upravit. Nakonec se <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> umístí (primárníplátno)a(Mřížkavlastností)na<xref:System.Activities.Presentation.WorkflowDesigner.View%2A> plochu uživatelského rozhraní.  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>Používání znovu hostované sady nástrojů  
 Tato ukázka používá znovu hostující ovládací prvek sady nástrojů v jazyce XAML. Všimněte si, že v kódu může jeden do <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktoru předat typ.  
  
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
  
#### <a name="using-the-sample"></a>Použití ukázky  
  
1. Otevřete řešení DesignerRehosting. sln v aplikaci Visual Studio 2010.  
  
2. Pro zkompilování a spuštění aplikace stiskněte klávesu F5.  
  
3. Aplikace WPF se spouští s opětovně hostovaným návrhářem.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
