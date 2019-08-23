---
title: 'Postupy: Použití monikeru služby Windows Communication Foundation bez registrace'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: 16f428b614fe331faffabab477c6584fb682801d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955235"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Postupy: Použití monikeru služby Windows Communication Foundation bez registrace
Chcete-li se připojit ke službě Windows Communication Foundation (WCF) a komunikovat s ní, musí mít klientská aplikace WCF podrobné informace o adrese služby, konfiguraci vazby a kontraktu služby.  
  
 Moniker služby WCF obvykle získá požadovanou kontrakt prostřednictvím předchozí registrace požadovaných typů atributů, ale v některých případech mohou nastat případy, kdy to není proveditelné. Místo registrace může moniker získat definici kontraktu ve formě dokumentu WSDL (Web Services Definition Language), prostřednictvím použití `wsdl` parametru nebo prostřednictvím výměny metadat prostřednictvím použití `mexAddress` ukazatele.  
  
 To umožňuje scénáře, jako je například distribuce excelové tabulky, kde se některé hodnoty buňky vypočítávají prostřednictvím interakcí webové služby. V tomto scénáři nemusí být možné zaregistrovat sestavení kontraktu služby na všech klientech, kteří můžou dokument otevřít. `wsdl` Parametr`mexAddress` nebo parametr umožňuje samostatně obsažené řešení.  
  
> [!NOTE]
> Vzájemné ověřování se musí použít k ochraně proti manipulaci s žádostmi a falšování nebo falšování identity. Konkrétně je důležité, aby klienti měli jistotu, že koncový bod výměny metadat, který odpovídá, je zamýšlená důvěryhodná strana.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje použití monikeru služby se smlouvou MEX. Služba s následujícím kontraktem se zveřejňuje s wsHttpBinding.  
  
```  
using System.ServiceModel;  
  
...  
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 Chcete-li vytvořit klienta WCF pro vzdálenou službu, lze použít následující vzorový řetězec monikeru.  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 Během provádění klientské aplikace provede `WS-MetadataExchange` klient s poskytnutou `mexAddress`součástí. To může vracet adresu, vazbu a podrobnosti o kontraktu pro určitý počet služeb. `binding` `contract` `contractNamespace`K identifikaci zamýšlené služby se `bindingNamespace` používají parametry,, a. `address` Jakmile se tyto parametry shodují, moniker vytvoří klienta WCF s příslušnou definicí kontraktu a volání se pak dá pomocí klienta WCF použít jako se zadaným kontraktem.  
  
> [!NOTE]
> Pokud je moniker poškozený nebo pokud není služba k dispozici, volání vrátí chybu `GetObject` s názvem neplatná syntaxe. Pokud se zobrazí tato chyba, ujistěte se, že moniker, který používáte, je správný a služba je k dispozici.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Registrace a konfigurace monikeru služby](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
