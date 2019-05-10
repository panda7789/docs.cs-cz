---
title: Hostování v aplikaci služby pro Windows
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: b5167e61bd825ce56905149237dae05ebb44b134
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613310"
---
# <a name="hosting-in-a-windows-service-application"></a>Hostování v aplikaci služby pro Windows
Služby Windows (dříve označovaná jako služba systému Windows NT) najdete postup, model zvlášť vhodné pro aplikace, které musí být aktivní ve spustitelném souboru dlouho běžící a nezobrazují žádné formulář, uživatelského rozhraní. Životnosti procesu Windows service aplikaci spravuje správce řízení služeb (SCM), který umožňuje spuštění, zastavení a pozastavení aplikace služby Windows. Můžete nakonfigurovat procesů služeb Windows na automatické spuštění při spuštění počítače, takže vhodný hostitelské prostředí pro aplikace "always on". Další informace o aplikacích pro službu Windows najdete v tématu [aplikace služby Windows](https://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplikace, které hostují služby Windows Communication Foundation (WCF) dlouho běžící sdílet mnoho vlastností se službami Windows. Zejména WCF services jsou dlouhotrvající server spustitelné programy není komunikovat přímo s uživatelem a proto neimplementuje žádnou formu uživatelské rozhraní. Hostování služby WCF v rámci aplikace služby Windows v důsledku toho je jednou z možností pro vytváření aplikací WCF robustní, dlouho probíhající.  
  
 WCF vývojáři často, musíte rozhodnout, zda hostovat svoje aplikace WCF v rámci aplikace služby Windows nebo uvnitř hostitelského prostředí Internetové informační služby (IIS) nebo Windows Process Activation Service (WAS). Měli byste zvážit použití aplikace služeb Windows za následujících podmínek:  
  
- Vaše aplikace vyžaduje explicitní aktivace. Například měli byste používat služby Windows, když vaše aplikace musí začínat automaticky při spuštění serveru místo dynamicky se spouští v reakci na první příchozí zprávy.  
  
- Proces, který je hostitelem vaší aplikace musí zůstat spuštěné po spuštění. Po zahájení procesu služby Windows zůstane spuštěný, není-li explicitně vypnutí správce serveru pomocí Správce řízení služeb. Aplikace hostované službou IIS nebo WAS může spuštění a zastavení dynamicky optimální využití systémových prostředků. Aplikace, které vyžadují explicitní kontrolu nad životnost jejich hostitelský proces byste používat služby Windows namísto služby IIS nebo WAS.  
  
- Služby WCF, musíte spustit na Windows Server 2003 a použít přenosy jiné než HTTP. V systému Windows Server 2003 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] hostitelského prostředí je omezen na pouze komunikaci pomocí protokolu HTTP. Aplikace služby Windows se nevztahují tato omezení a můžete použít libovolný přenos WCF podporuje, včetně net.tcp, net.pipe a net.msmq.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>K hostování WCF v rámci aplikace služby Windows  
  
1. Vytvoření aplikace služby Windows. Můžete psát aplikace služby Windows ve spravovaném kódu použitím tříd v <xref:System.ServiceProcess> oboru názvů. Tato aplikace musí obsahovat jednu třídu, která dědí z <xref:System.ServiceProcess.ServiceBase>.  
  
2. Odkaz na životnost aplikace služby Windows životního cyklu služeb WCF. Obvykle je vhodné služby WCF hostované v aplikaci služby Windows aktivuje při spuštění hostitelské služby, zastavil naslouchání pro zprávy, když hostitelská služba je zastavena a vypnout hostitelský proces, když dojde k chybě služby WCF. To lze provést následujícím způsobem:  
  
    - Přepsat <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> otevřít jeden nebo víc instancí <xref:System.ServiceModel.ServiceHost>. Jednu aplikaci služby Windows může hostovat více služeb WCF, které spouští a zastavují jako skupinu.  
  
    - Přepsat <xref:System.ServiceProcess.ServiceBase.OnStop%2A> volat <xref:System.ServiceModel.Channels.CommunicationObject.Closed> na <xref:System.ServiceModel.ServiceHost> všechny spuštěné služby WCF, které se spustily během <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    - Přihlaste se k odběru <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> událost <xref:System.ServiceModel.ServiceHost> a použít <xref:System.ServiceProcess.ServiceController> třídy pro vypnutí aplikace služby Windows v případě chyby.  
  
     Aplikace služby Windows, které hostují služby WCF se nasazují a spravují stejným způsobem jako aplikace služby Windows, které Nedovolte, aby byly použijte služby WCF.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceProcess>
- [Návod: Vytvoření aplikace služby Windows v Návrháři součástí](https://go.microsoft.com/fwlink/?LinkId=94875)
- [Postupy: Hostování služby WCF ve spravované Windows Service](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Hostitel služby Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)
- [Architektura programování aplikace služby](https://go.microsoft.com/fwlink/?LinkId=94876)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
