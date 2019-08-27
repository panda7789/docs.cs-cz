---
title: Načtení z XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: 2f45beb398e6d6b91bf7444dd590b862ff8c7515
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038088"
---
# <a name="load-from-xaml"></a>Načtení z XAML
Tato ukázka předvádí, jak dynamicky načíst pracovní postup XAML bez nutnosti spuštění nástroje XamlBuildTask. Místo toho ukázka volá <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metodu. Ukázka je klientská aplikace Windows Presentation Foundation (WPF), která načte pracovní postupy XAML pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy a provede je. Poté, co byly načteny pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy <xref:System.Activities.DynamicActivity%601> , je vráceno, které lze provést.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení LoadFromXAML. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
