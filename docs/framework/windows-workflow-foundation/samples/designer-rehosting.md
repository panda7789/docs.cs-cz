---
title: Návrhář opětovného hostování
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 3caff782dcb7ce2434960e24c4586877788da653
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516146"
---
# <a name="designer-rehosting"></a>Návrhář opětovného hostování
Návrhář opětovného hostování je běžný scénář, který odkazuje na hostování na plátno návrhu pracovního postupu uvnitř vlastní aplikaci. Hostování aplikace, které mají zkušenosti se většina lidí je Visual Studio, ale existuje několik scénářů, kdy zobrazující návrháře pracovních postupů v aplikaci může být užitečné:  
  
-   Monitorování aplikací (povolení koncový uživatel k vizualizaci procesu, jakož i běhová data o procesu, jako je například stav aktuálně aktivní, data agregovanou dobu provádění nebo Další informace o instanci pracovního postupu).  
  
-   Aplikace, které uživateli k přizpůsobení procesu s omezenou sadou aktivit.  
  
 Pro podporu těchto typů aplikací, návrháře pracovních postupů se dodává v rozhraní .NET Framework a může být hostovaný v aplikaci WPF nebo v aplikaci WinForms s příslušnou WPF hostování kódu. Tento příklad znázorňuje:  
  
-   Opětovného hostování návrháře WF.  
  
-   Pomocí opětovné hostování nástroje sada nástrojů a vlastnost mřížky také.  
  
## <a name="rehosting-the-designer"></a>Opětovného hostování návrháře  
 Tento příklad ukazuje postup vytvoření rozložení WPF tak, aby obsahovala návrháře, vidět v následujícím rozložení mřížky (sada nástrojů kód vynechání pro riziko z hlediska místa). Všimněte si názvů ohraničení, které obsahují designer a vlastnost mřížky.  
  
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
  
 Další ukázky vytvoří návrháře a přidruží jeho primární <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> s odpovídajícího kontejneru v uživatelském rozhraní. Existuje několik další řádky kódu v následujícím příkladu, které si zasloužila vysvětlení. <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Volání je potřeba přidružit návrháře aktivit výchozí pro aktivity součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> je volána předávat WF položku, kterou chcete upravit. Nakonec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primární plátno) a <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (mřížkou vlastností) jsou umístěny na plochu uživatelské rozhraní.  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>Pomocí sady nástrojů opětovné hostování nástroje  
 Tato ukázka ovládacího prvku opětovné hostování nástroje sada nástrojů používá deklarativně v jazyce XAML. Všimněte si, že v kódu, jeden předat typu k <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktor.  
  
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
  
#### <a name="using-the-sample"></a>Pomocí vzorku  
  
1.  Otevřete řešení DesignerRehosting.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Stisknutím klávesy F5 zkompilování a spuštění aplikace.  
  
3.  Aplikace WPF začíná opětovné hostování nástroje návrháře.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`