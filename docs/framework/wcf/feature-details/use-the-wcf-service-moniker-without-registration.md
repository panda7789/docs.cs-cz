---
title: 'Postupy: Použití monikeru služby Windows Communication Foundation bez registrace'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: be4798663d0b39301ec496df45a4a7a5bf9c88e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918581"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Postupy: Použití monikeru služby Windows Communication Foundation bez registrace
K připojení a komunikovat se službou Windows Communication Foundation (WCF), musí mít klientská aplikace WCF podrobnosti adresu služby, konfigurace vazby a kontrakt služby.  
  
 Monikeru služby WCF obvykle získá požadované smlouvy prostřednictvím předchozí registrace typů požadovaný atribut, ale můžou nastat případy, kdy to není proveditelné. Zástupný název místo registrace, můžete získat definici kontraktu ve formě dokumentem definice jazyka WSDL (Web Services) prostřednictvím `wsdl` parametr nebo prostřednictvím výměny metadat prostřednictvím použití `mexAddress` parametr.  
  
 To umožňuje scénáře, jako je distribuce tabulky aplikace Excel, kde některé z hodnot buňky se počítají prostřednictvím interakce webové služby. V tomto scénáři nemusí být možné zaregistrovat sestavení kontraktu služby ve všech klientech, které může otevřít dokument. `wsdl` Parametr nebo `mexAddress` parametr povoluje samostatná řešení.  
  
> [!NOTE]
>  Vzájemné ověřování musí použít pro ochranu před žádostí a odpovědí, manipulaci nebo falšování identity. Konkrétně je důležité pro klienty být jistí, že je koncový bod výměny metadat, který odpovídá určené důvěryhodná strana.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje použití monikeru služby s kontraktem MEX. Služba s tímto kontraktem je vystavena s wsHttpBinding.  
  
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
  
 Lze použít k vytvoření klienta WCF pro vzdálené služby řetězce monikeru následující příklad.  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 Při spuštění klientské aplikace, klient provádí `WS-MetadataExchange` za poskytnutý `mexAddress`. To může vrátit adresy, vazby a podrobnosti o kontraktu pro celou řadou služeb. `address`, `contract`, `contractNamespace`, `binding` a `bindingNamespace` parametry slouží k identifikaci určené služby. Jakmile tyto parametry pravá složená závorka, zástupný název vytvoří klienta WCF s definicí příslušné smlouvy a volání je pak možné provádět pomocí klienta WCF stejně jako u typu kontraktu.  
  
> [!NOTE]
>  Pokud je moniker je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chyba s oznámením "Neplatná syntaxe". Pokud se zobrazí tato chyba, ujistěte se, že zástupný název, který používáte, je správná a služba není k dispozici.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Registrace a konfigurace Monikeru služby](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
