---
title: Hostování v aplikaci služby pro Windows
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: a07aade4619b644dadd1d5acdcb5252b305b94d0
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964494"
---
# <a name="hosting-in-a-windows-service-application"></a>Hostování v aplikaci služby pro Windows
Služby systému Windows (dříve označované jako služby systému Windows NT) poskytují model procesu, zvláště vhodný pro aplikace, které musí být spuštěny v dlouhodobém spustitelném souboru a nezobrazují žádnou formu uživatelského rozhraní. Doba platnosti procesu aplikace služby systému Windows je spravována správcem řízení služeb (SCM), který umožňuje spustit, zastavit a pozastavit aplikace služby systému Windows. Proces služby systému Windows můžete nakonfigurovat tak, aby se spouštěl automaticky při spuštění počítače a aby byl vhodný hostující prostředí pro aplikace "Always On". Další informace o aplikacích služby systému Windows najdete v tématu [aplikace služby systému Windows](https://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplikace, které hostují dlouhodobě běžící služby Windows Communication Foundation (WCF), sdílejí mnoho vlastností se službami systému Windows. Konkrétně služby WCF jsou dlouhodobě běžící spustitelné soubory, které nekomunikují přímo s uživatelem, a proto neimplementují žádné formy uživatelského rozhraní. V takovém případě hostující služby WCF uvnitř aplikace služby systému Windows je jednou z možností pro vytváření robustních a dlouhotrvajících aplikací WCF.  
  
 Vývojáři WCF se často musí rozhodnout, jestli mají hostovat svoji aplikaci WCF v rámci aplikace služby systému Windows nebo uvnitř hostitelského prostředí služby Internetová informační služba (IIS) nebo aktivační služba procesů systému Windows (WAS). Je vhodné zvážit použití aplikací služby systému Windows za následujících podmínek:  
  
- Vaše aplikace vyžaduje explicitní aktivaci. Například byste měli použít služby systému Windows, pokud se vaše aplikace musí spustit automaticky při spuštění serveru namísto dynamického spuštění v reakci na první příchozí zprávu.  
  
- Proces, který hostuje vaši aplikaci, musí po spuštění zůstat spuštěný. Po spuštění zůstane proces služby systému Windows spuštěný, pokud explicitně nevypne správce serveru pomocí Správce řízení služeb. Aplikace hostované ve službě IIS nebo byly spouštěny a dynamicky zastaveny, aby bylo možné využívat systémové prostředky k optimálnímu využití. Aplikace, které vyžadují explicitní kontrolu nad životností hostitelského procesu, by měly používat služby systému Windows namísto služby IIS nebo WAS.  
  
- Vaše služba WCF musí běžet na Windows serveru 2003 a používat jiné přenosy než HTTP. Ve Windows serveru 2003 je hostitelské prostředí IIS 6,0 omezené jenom na komunikaci HTTP. Aplikacím služeb systému Windows se nevztahují toto omezení a mohou používat přenos přes WCF podporované, včetně NET. TCP, NET. pipe a NET. MSMQ.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Hostování technologie WCF v rámci aplikace služby systému Windows  
  
1. Vytvořte aplikaci služby systému Windows. Můžete psát aplikace služby systému Windows ve spravovaném kódu pomocí tříd v oboru názvů <xref:System.ServiceProcess>. Tato aplikace musí zahrnovat jednu třídu, která dědí z <xref:System.ServiceProcess.ServiceBase>.  
  
2. Propojte životnost služeb WCF s životností aplikace služby systému Windows. Obvykle chcete, aby služby WCF hostované v aplikaci služby systému Windows byly aktivní při spuštění hostující služby, zastavily naslouchání zpráv při zastavení hostitelské služby a vypnutí hostitelského procesu, když služba WCF narazí na chybu. To lze provést následujícím způsobem:  
  
    - Přepište <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> pro otevření jedné nebo více instancí <xref:System.ServiceModel.ServiceHost>. Jedna aplikace služby systému Windows může hostovat několik služeb WCF, které se spouštějí a zastavují jako skupina.  
  
    - Přepsat <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pro volání <xref:System.ServiceModel.Channels.CommunicationObject.Closed> na <xref:System.ServiceModel.ServiceHost> všechny spuštěné služby WCF, které byly spuštěny během <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    - Přihlaste se k odběru události <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> <xref:System.ServiceModel.ServiceHost> a použijte třídu <xref:System.ServiceProcess.ServiceController> k ukončení aplikace služby systému Windows v případě chyby.  
  
     Aplikace služby systému Windows, které hostují služby WCF, se nasazují a spravují stejným způsobem jako aplikace služby systému Windows, které nevyužívají WCF.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceProcess>
- [Návod: Vytvoření aplikace služby systému Windows v návrháři součástí](https://go.microsoft.com/fwlink/?LinkId=94875)
- [Postupy: Hostování služby WCF ve spravované službě Windows](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Hostitel služby Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)
- [Architektura programování aplikace služby](https://go.microsoft.com/fwlink/?LinkId=94876)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
