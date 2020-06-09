---
title: Nezabezpečený intranetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 591f7db0f6b4e928a991961d3bc7c404f41028bf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579277"
---
# <a name="intranet-unsecured-client-and-service"></a>Nezabezpečený intranetový klient a služba
Následující ilustrace znázorňuje jednoduchou službu Windows Communication Foundation (WCF) vyvinutou pro poskytování informací o zabezpečené privátní síti pro aplikaci WCF. Zabezpečení není vyžadováno, protože data mají nízkou důležitost, očekává se, že síť bude podstatně zabezpečená, nebo že zabezpečení je zajištěno vrstvou pod infrastrukturou WCF.  
  
 ![Intranetový nezabezpečený scénář klienta a služby.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|Charakteristika|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Žádné|  
|Přenos|TCP|  
|Vazba|<xref:System.ServiceModel.NetTcpBinding>|  
|Interoperabilita|Pouze WCF|  
|Authentication|Žádné|  
|Integrita|Žádné|  
|Důvěrnost|Žádné|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte některou z následujících akcí:  
  
- Vytvořte samostatnou službu pomocí kódu bez konfigurace.  
  
- Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod bez zabezpečení:  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód nastaví stejný koncový bod pomocí konfigurace:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte některou z následujících akcí:  
  
- Vytvořte samostatného klienta pomocí kódu (a kódu klienta).  
  
- Vytvořte klienta, který nedefinuje žádné adresy koncových bodů. Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument. Například:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje základního klienta WCF, který přistupuje k nezabezpečenému koncovému bodu pomocí protokolu TCP.  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfigurační kód platí pro klienta:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.NetTcpBinding>
- [Přehled zabezpečení](security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
