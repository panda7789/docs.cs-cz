---
title: Hostování v aplikaci služby pro Windows
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: e440961055ccd40bf56b4b88ea73d167f1903245
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-in-a-windows-service-application"></a>Hostování v aplikaci služby pro Windows
Služby systému Windows (dříve označované jako služby systému Windows NT) zadejte procesu modelu zvlášť vhodné pro aplikace, které musí za provozu v spustitelný soubor dlouho běžící a nezobrazovat jakoukoli formu uživatelské rozhraní. Doba platnosti procesu systému Windows služby aplikaci spravuje správce řízení služeb (SCM), která umožňuje spustit, zastavit a pozastavit aplikace služby systému Windows. Můžete nakonfigurovat službu procesů systému Windows spustit automaticky při spuštění počítače, takže je vhodné hostitelské prostředí pro aplikace "always on". Další informace o aplikace služby systému Windows najdete v tématu [aplikace služby systému Windows](http://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplikace, které jsou hostiteli služby Windows Communication Foundation (WCF) dlouho běžící sdílejí mnoho vlastností službou systému Windows. Služby WCF na konkrétní jsou dlouho běžící spustitelné soubory serveru, které není komunikovat přímo s uživatelem a proto neimplementují jakoukoli formu uživatelské rozhraní. Hostování služby WCF v rámci aplikace služby systému Windows jako takový je jednou z možností pro vytváření aplikací WCF robustní a časově náročné.  
  
 Často WCF vývojáři rozhodnout, zda hostitel jejich aplikace WCF v rámci aplikace služby systému Windows nebo v rámci Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS) hostitelské prostředí. Měli byste zvážit použití aplikace služby systému Windows za následujících podmínek:  
  
-   Vaše aplikace vyžaduje explicitní aktivace. Například byste měli používat služby systému Windows, když vaše aplikace musíte spustit automaticky při spuštění serveru místo dynamicky spuštění v reakci na první příchozí zprávu.  
  
-   Proces, který je hostitelem vaší aplikace musí zůstat spuštěné jednou spustit. Po spuštění procesu služby systému Windows zůstane spuštěný, pokud není výslovně vypnutí dolů správce serveru pomocí Správce řízení služeb. Aplikace hostované ve službě IIS nebo WAS může být spuštění a zastavení dynamicky optimální využití systémových prostředků. Aplikace, které vyžadují explicitní kontrolu nad životnost jejich hostitelského procesu použijte místo služby IIS nebo WAS služby systému Windows.  
  
-   Služby WCF musí spustit v systému Windows Server 2003 a použít přenosy než HTTP. V systému Windows Server 2003 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] hostování prostředí je omezen na pouze komunikaci pomocí protokolu HTTP. Aplikace služby systému Windows toto omezení se nevztahuje a můžete použít všechny přenos podporuje WCF, včetně net.tcp, net.pipe a net.msmq.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>K hostování WCF v rámci aplikace služby systému Windows  
  
1.  Vytvoření aplikace služby systému Windows. Aplikace služby systému Windows může zapisovat do spravovaného kódu pomocí třídy v <xref:System.ServiceProcess> oboru názvů. Tato aplikace musí obsahovat jednu třídu, která dědí z <xref:System.ServiceProcess.ServiceBase>.  
  
2.  Doba platnosti služeb WCF propojte životního cyklu aplikace služby systému Windows. Obvykle je vhodné služby WCF hostované v aplikaci služby pro Windows aktivuje při spuštění hostování služby, zastavil naslouchání pro zprávy, když hostitelská služba je zastavena a vypnout hostitelského procesu, když dojde k chybě služby WCF. To lze provést následujícím způsobem:  
  
    -   Přepsání <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> otevřete jednu nebo více instancí <xref:System.ServiceModel.ServiceHost>. Jeden aplikace služby systému Windows, může hostovat více služeb WCF, které spuštění a zastavení jako skupina.  
  
    -   Přepsání <xref:System.ServiceProcess.ServiceBase.OnStop%2A> volat <xref:System.ServiceModel.Channels.CommunicationObject.Closed> na <xref:System.ServiceModel.ServiceHost> žádné spuštěné služby WCF, které byly spuštěny při <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Přihlášení k odběru <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> události <xref:System.ServiceModel.ServiceHost> a použít <xref:System.ServiceProcess.ServiceController> třída vypnout aplikaci služby pro Windows v případě chyby.  
  
     Aplikace služby systému Windows, které jsou hostiteli služby WCF se nasadit a spravovat stejným způsobem jako aplikace služby systému Windows, které neprovádějte použijte služby WCF.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceProcess>  
 [Návod: Vytvoření aplikace služby systému Windows v návrháři součástí](http://go.microsoft.com/fwlink/?LinkId=94875)  
 [Postupy: Hostování služby WCF ve spravované službě Windows](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Hostitel služby Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Architektura programování aplikace služby](http://go.microsoft.com/fwlink/?LinkId=94876)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
