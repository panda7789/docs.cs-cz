---
title: "Hostování v aplikaci služby pro Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1f411e0280a1f663e5e001e471eb836208083160
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-in-a-windows-service-application"></a>Hostování v aplikaci služby pro Windows
Služby systému Windows (dříve označované jako služby systému Windows NT) zadejte procesu modelu zvlášť vhodné pro aplikace, které musí za provozu v spustitelný soubor dlouho běžící a nezobrazovat jakoukoli formu uživatelské rozhraní. Doba platnosti procesu systému Windows služby aplikaci spravuje správce řízení služeb (SCM), která umožňuje spustit, zastavit a pozastavit aplikace služby systému Windows. Můžete nakonfigurovat službu procesů systému Windows spustit automaticky při spuštění počítače, takže je vhodné hostitelské prostředí pro aplikace "always on". [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Aplikace služby systému Windows, najdete v části [aplikace služby systému Windows](http://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplikace, které jsou hostiteli dlouho běžící [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby sdílejí mnoho vlastností službou systému Windows. Konkrétně [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby jsou dlouho běžící spustitelné soubory serveru, které není komunikovat přímo s uživatelem a proto neimplementují jakoukoli formu uživatelské rozhraní. Jako takový, který je hostitelem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v rámci aplikace služby systému Windows je jednou z možností pro vytvoření robustní, dlouhotrvajících, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.  
  
 Často [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vývojáři rozhodnout, zda hostitel jejich [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace v rámci aplikace služby systému Windows nebo v rámci Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS) hostitelské prostředí. Měli byste zvážit použití aplikace služby systému Windows za následujících podmínek:  
  
-   Vaše aplikace vyžaduje explicitní aktivace. Například byste měli používat služby systému Windows, když vaše aplikace musíte spustit automaticky při spuštění serveru místo dynamicky spuštění v reakci na první příchozí zprávu.  
  
-   Proces, který je hostitelem vaší aplikace musí zůstat spuštěné jednou spustit. Po spuštění procesu služby systému Windows zůstane spuštěný, pokud není výslovně vypnutí dolů správce serveru pomocí Správce řízení služeb. Aplikace hostované ve službě IIS nebo WAS může být spuštění a zastavení dynamicky optimální využití systémových prostředků. Aplikace, které vyžadují explicitní kontrolu nad životnost jejich hostitelského procesu použijte místo služby IIS nebo WAS služby systému Windows.  
  
-   Vaše [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby musíte spustit na Windows Server 2003 a použít přenosy než HTTP. V systému Windows Server 2003 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] hostování prostředí je omezen na pouze komunikaci pomocí protokolu HTTP. Aplikace služby systému Windows toto omezení se nevztahuje a můžete použít všechny přenosu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje, včetně net.tcp, net.pipe a net.msmq.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>K hostování WCF v rámci aplikace služby systému Windows  
  
1.  Vytvoření aplikace služby systému Windows. Aplikace služby systému Windows může zapisovat do spravovaného kódu pomocí třídy v <xref:System.ServiceProcess> oboru názvů. Tato aplikace musí obsahovat jednu třídu, která dědí z <xref:System.ServiceProcess.ServiceBase>.  
  
2.  Odkaz životnost [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace služby služeb životnost systému Windows. Obvykle je vhodné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby hostované v aplikaci služby pro Windows stane aktivním při spuštění hostování služby, zastavení, naslouchá pro zprávy při zastavení služby hostování a vypnutí, který je hostitelem při zpracování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Služba dojde k chybě. To lze provést následujícím způsobem:  
  
    -   Přepsání <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> otevřete jednu nebo více instancí <xref:System.ServiceModel.ServiceHost>. Jeden aplikace služby systému Windows může být hostitelem více [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, které spuštění a zastavení jako skupina.  
  
    -   Přepsání <xref:System.ServiceProcess.ServiceBase.OnStop%2A> volat <xref:System.ServiceModel.Channels.CommunicationObject.Closed> na <xref:System.ServiceModel.ServiceHost> žádné spuštěná [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, které byly spuštěny při <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Přihlášení k odběru <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> události <xref:System.ServiceModel.ServiceHost> a použít <xref:System.ServiceProcess.ServiceController> třída vypnout aplikaci služby pro Windows v případě chyby.  
  
     Windows aplikace služeb, které hostují [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby jsou nasadit a spravovat stejným způsobem jako aplikace služby systému Windows, které neprovádějte použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceProcess>  
 [Návod: Vytvoření aplikace služby systému Windows v Návrháři součástí](http://go.microsoft.com/fwlink/?LinkId=94875)  
 [Postupy: hostování služby WCF ve spravované službě Windows](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Hostitel služby Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Architektura programování aplikace služby](http://go.microsoft.com/fwlink/?LinkId=94876)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
