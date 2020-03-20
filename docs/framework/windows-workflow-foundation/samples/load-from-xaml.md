---
title: Načtení z XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: d07ddef8fb982aa0bf707cb688cd23f04bb231d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142716"
---
# <a name="load-from-xaml"></a>Načtení z XAML
Tato ukázka ukazuje, jak dynamicky načíst pracovní postup XAML bez nutnosti spouštět nástroj XamlBuildTask. Místo toho ukázka <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> volá metodu. Ukázka je klientská aplikace WPF (Windows Presentation Foundation), která <xref:System.Activities.XamlIntegration.ActivityXamlServices> načte pracovní postupy XAML pomocí třídy a provede je. Poté, co byly <xref:System.Activities.XamlIntegration.ActivityXamlServices> načteny <xref:System.Activities.DynamicActivity%601> pomocí třídy, je vrácena, která může být provedena.

#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení LoadFromXAML.sln.

2. Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.

3. Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
