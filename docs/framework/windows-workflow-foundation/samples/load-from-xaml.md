---
title: "Načtení z XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54acfb1a130c8a790411a05958518665ef790e53
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="load-from-xaml"></a>Načtení z XAML
Tato ukázka ukazuje, jak se dynamicky načíst postupu v XML bez nutnosti spustit nástroj XamlBuildTask. Místo toho ukázka volá <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metoda. Ukázka je [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] klientskou aplikaci, která načte pomocí pracovních postupů XAML <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy a spustí je. Po jejich byly načteny pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třída, <xref:System.Activities.DynamicActivity%601> se vrátí, které mohou být provedeny.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení LoadFromXAML.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`