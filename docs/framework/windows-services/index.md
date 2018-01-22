---
title: "Vývoj aplikací spouštěných jako služby systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 325e43f4b1734bc6ab8753285e5069f36b0fda51
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="developing-windows-service-applications"></a>Vývoj aplikací spouštěných jako služby systému Windows
Pomocí Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] nebo Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, můžete snadno vytvořit služby tak, že vytvoříte aplikaci, která je nainstalován jako služba. Tento typ aplikace se nazývá služby systému Windows. S funkcemi framework můžete vytvořit služby, je, nainstalovat a spustit, zastavit a jinak řídit jejich chování.  
  
> [!WARNING]
>  Šablony služeb systému Windows pro jazyk C++ nebyla obsažena v sadě Visual Studio 2010. K vytvoření služby systému Windows, můžete buď vytvořit službu ve spravovaném kódu v jazyce Visual C# nebo Visual Basic, který může spolupracovat s existujícího kódu C++ v případě potřeby, nebo služby systému Windows můžete vytvořit v nativním kódu C++ pomocí [–PrůvodceprojektemknihovnyATL](/cpp/atl/reference/atl-project-wizard).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 Poskytuje přehled aplikace služby systému Windows, doba platnosti služby a jak aplikace služby se liší od jiných běžné typy projektů.  
  
 [Návod: Vytvoření aplikace služby systému Windows v návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 Poskytuje příklad vytvoření služby v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] a Visual C#.  
  
 [Architektura programování aplikace služby](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 Vysvětluje prvky jazyka, používané v programování služby.  
  
 [Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 Popisuje postup vytvoření a konfigurace služby systému Windows pomocí šablony projektu služeb systému Windows.  
  
## <a name="related-sections"></a>Související oddíly  
 <xref:System.ServiceProcess.ServiceBase>  
 Popisuje hlavní funkce <xref:System.ServiceProcess.ServiceBase> třídy, která se používá k vytvoření služby.  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídy, která se používá spolu s <xref:System.ServiceProcess.ServiceInstaller> třída k instalaci a odinstalaci vašich služeb.  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídy, která se používá spolu s <xref:System.ServiceProcess.ServiceProcessInstaller> třída k instalaci a odinstalaci služby.  
  
 [NIB vytváření projektů ze šablon](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 Popisuje projektů typy používané v této kapitoly a jak vybrat mezi nimi.
