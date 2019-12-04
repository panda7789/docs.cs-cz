---
title: Načtení z XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: c46c9020f07731d3d833332d77fd46a162ccb6dc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715952"
---
# <a name="load-from-xaml"></a>Načtení z XAML
Tato ukázka předvádí, jak dynamicky načíst pracovní postup XAML bez nutnosti spuštění nástroje XamlBuildTask. Místo toho ukázka volá metodu <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>. Ukázka je klientská aplikace Windows Presentation Foundation (WPF), která načte pracovní postupy XAML pomocí třídy <xref:System.Activities.XamlIntegration.ActivityXamlServices> a provede je. Po načtení pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy se vrátí <xref:System.Activities.DynamicActivity%601>, který lze spustit.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení LoadFromXAML. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
