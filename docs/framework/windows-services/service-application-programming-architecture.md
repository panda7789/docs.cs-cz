---
title: "Architektura programování aplikace služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e9c16f2e603a3ce9bbc59be4e01aa492239d2c63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="service-application-programming-architecture"></a>Architektura programování aplikace služby
Aplikace služby systému Windows jsou založené na třídu, která dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> třídy. Přepsání metody z této třídy a definovat funkce pro ně k určení chování služby.  
  
 Hlavní třídy účastnící se vytváření služby jsou:  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>– Můžete přepsat metody ze <xref:System.ServiceProcess.ServiceBase> třídy při vytváření služby a zadejte kód, určit, jak funkce služby v tomto zděděná třída.  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType>a <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> – tyto třídy slouží k instalaci a odinstalaci služby.  
  
 Kromě toho třída s názvem <xref:System.ServiceProcess.ServiceController> lze použít k manipulaci s samotné služby. Tato třída není zahrnut do vytváření služby, ale lze spustit a zastavit službu, předejte příkazy k němu a vrátit řadu výčty.  
  
## <a name="defining-your-services-behavior"></a>Definování chování služby  
 Ve třídě služby přepsat funkce základní třídy, které určují, co se stane při změně stavu služby ve správci řízení služeb. <xref:System.ServiceProcess.ServiceBase> Třída poskytuje následující metody, které pokud chcete přidat vlastní chování můžete přepsat.  
  
|Metoda|Přepsání nastavení za účelem|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Označuje, jaké akce by měla být provedena při spuštění služby. V tomto postupu pro vaši službu pro práci užitečné musíte napsat kód.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Označuje, co by měl stane, když vaše služba je pozastavena.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Označuje, co by měl stane, když se zastaví služby.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Označuje, co by měl stane, když vaše služba obnoví normální fungování po jejím pozastavení.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Označuje, co by měl stane těsně před systému vypíná, pokud vaše služba běží v daném čase.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Označuje, co by měl stane, když vaše služba přijímá vlastního příkazu. Další informace o vlastní příkazy v MSDN online.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Označuje, jak má služba odpovědět odeslaná událostí řízení spotřeby, jako je nízký stav baterie nebo pozastavený operaci.|  
  
> [!NOTE]
>  Tyto metody představují stavy, které služba prochází přes v celé jeho životnosti; přechody služby z jednoho stavu na další. Například se nikdy získat službu reagovat na <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> příkazu před <xref:System.ServiceProcess.ServiceBase.OnStart%2A> byla volána.  
  
 Existuje několik vlastnosti a metody, které jsou pro ně. Mezi ně patří:  
  
-   <xref:System.ServiceProcess.ServiceBase.Run%2A> Metodu <xref:System.ServiceProcess.ServiceBase> třídy. Toto je hlavní vstupní bod pro službu. Když vytváříte službu pomocí šablony služeb systému Windows, kód je vložen do vaší aplikace `Main` metodu pro spuštění služby. Tento kód vypadá takto:  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  Tyto příklady použití pole typu <xref:System.ServiceProcess.ServiceBase>, do které každá služba, která obsahuje aplikaci lze přidat a pak všechny služby, lze spustit společně. Pokud vytváříte jen jedné služby, ale může rozhodnete použít pole a jednoduše deklarovat nový objekt, který dědí z <xref:System.ServiceProcess.ServiceBase> a spusťte jej. Příklad, naleznete v části [postupy: zápis služeb prostřednictvím kódu programu](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
-   Řadu vlastnosti <xref:System.ServiceProcess.ServiceBase> třídy. Tyto určují, jaké metody lze volat na vaši službu. Například když <xref:System.ServiceProcess.ServiceBase.CanStop%2A> je nastavena na `true`, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> nelze volat metodu vaší služby. Když <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> je nastavena na `true`, <xref:System.ServiceProcess.ServiceBase.OnPause%2A> a <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> lze volat metody. Když nastavíte jednu z těchto vlastností na `true`, pak by měly přepsat a definovat zpracování pro související metody.  
  
    > [!NOTE]
    >  Služby musí přepsat alespoň <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> být užitečné.  
  
 Můžete také použít komponenty s názvem <xref:System.ServiceProcess.ServiceController> řídí chování existující službu a komunikovat s.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikace služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
