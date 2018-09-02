---
title: Změna hostování návrháře
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 1901df62ccdeec3f75ce0d8cd85484f46fac4541
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404097"
---
# <a name="designer-rehosting"></a>Změna hostování návrháře
Změna hostování návrháře je běžný scénář, který odkazuje na hostování pracovního postupu návrhové plátno v rámci vlastní aplikace. Hostování aplikace, kterou většina lidí znají je Visual Studio, ale existuje mnoho scénářů, kdy zobrazení návrháře postupu provádění v aplikaci může být užitečné:  
  
-   Monitorování aplikací (umožňuje koncovým uživatelům vizualizovat proces, jakož i dat získaných za běhu o procesu, jako jsou aktuálně aktivním stavu, data agregovaná doba provádění nebo Další informace o instanci pracovního postupu).  
  
-   Aplikace, které umožňují uživatelům přizpůsobit proces s omezenou sadu aktivit.  
  
 Pro podporu těchto typů aplikací, návrháře postupu provádění se dodává v rozhraní .NET Framework a je možné hostovat v aplikaci WPF nebo aplikace WinForms s odpovídající WPF hostování kódu. V této ukázce:  
  
-   Změna hostování návrháře pracovního postupu.  
  
-   Pomocí provádění se změněným hostováním nástrojů a vlastnost mřížce stejně.  
  
## <a name="rehosting-the-designer"></a>Změna hostování návrháře  
 Tento příklad ukazuje, jak vytvořit rozložení WPF tak, aby obsahovala návrháři vidět v následující rozložení mřížky (nástrojů kódu vynechána obavy místa). Mějte na paměti, pojmenování ohraničení, které obsahují mřížky Návrháře a vlastnosti.  
  
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
  
 Dále ukázka vytvoří návrháře a přidruží jeho primární <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> pomocí odpovídajícího kontejneru v uživatelském rozhraní. Existuje několik další řádky kódu v následujícím příkladu, které si zasloužila vysvětlení. <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Volání je nutné přiřadit výchozí návrháři aktivit pro aktivity, kterou jste dostali se [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> je volána a zajistěte tak předání WF položky bude upravován. Nakonec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primární plátna) a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (mřížky vlastností) jsou umístěné na plochu uživatelské rozhraní.  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>Používání sady nástrojů provádění se změněným hostováním  
 Tato ukázka používá ovládací prvek provádění se změněným hostováním nástrojů deklarativně v XAML. Všimněte si, že v kódu, jeden můžete předat typ <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktoru.  
  
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
  
#### <a name="using-the-sample"></a>Pomocí ukázky  
  
1.  Otevřete řešení DesignerRehosting.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Stiskněte klávesu F5 ke kompilaci a spuštění aplikace.  
  
3.  Aplikace WPF začíná návrháři se změněným hostováním.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`