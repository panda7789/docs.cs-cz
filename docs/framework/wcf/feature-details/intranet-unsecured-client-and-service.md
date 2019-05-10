---
title: Nezabezpečený intranetový klient a služba
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 65b8597727da256e832351792b9d5d9bd016eb28
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587009"
---
# <a name="intranet-unsecured-client-and-service"></a>Nezabezpečený intranetový klient a služba
Následující obrázek znázorňuje jednoduchý služby Windows Communication Foundation (WCF) vyvinuta poskytují informace o zabezpečené privátní sítě pro aplikace WCF. Zabezpečení není povinné, protože data jsou s nízkou důležitostí, síť má být ze své podstaty bezpečné nebo poskytuje zabezpečení vrstvy pod infrastruktura WCF.  
  
 ![Nezabezpečený intranetový klient a služba scénář.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|Vlastnost|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Žádné|  
|Přenos|TCP|  
|Vazba|<xref:System.ServiceModel.NetTcpBinding>|  
|Interoperabilita|Pouze WCF|  
|Ověřování|Žádné|  
|Integrita|Žádný|  
|Důvěrnost|Žádné|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace mají běžet nezávisle. Proveďte jednu z těchto akcí:  
  
- Vytvoření samostatné služby pomocí kódu bez konfigurace.  
  
- Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod se zabezpečení:  
  
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
 Následující kód a konfigurace mají běžet nezávisle. Proveďte jednu z těchto akcí:  
  
- Vytvoření samostatného klienta pomocí kódu (a kód klienta).  
  
- Vytvoření klienta, která nedefinuje žádné adresy koncových bodů. Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace. Příklad:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje základní klienta WCF, který přistupuje k koncový bod zabezpečená pomocí protokolu TCP.  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód konfigurace platí pro klienta:  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.NetTcpBinding>
- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
