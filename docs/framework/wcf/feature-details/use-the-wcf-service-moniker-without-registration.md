---
title: 'Postupy: použití Monikeru služby Windows Communication Foundation bez registrace'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: fd61528770b16b13430be3691aef19c1cc743e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497968"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Postupy: použití Monikeru služby Windows Communication Foundation bez registrace
Pro připojení k a komunikovat se službou Windows Communication Foundation (WCF), musí mít klientské aplikace WCF podrobnosti o adresu služby, konfigurace vazeb a kontrakt služby.  
  
 Monikeru služby WCF obvykle získá požadované kontrakt prostřednictvím předchozí registrace požadovaný atribut typy, ale můžou nastat případy, kdy to není možné. Přezdívka místo registrace, můžete získat definici kontraktu ve formě dokumentem definice jazyka WSDL (Web Services) prostřednictvím `wsdl` parametr nebo prostřednictvím Metadata Exchange prostřednictvím použití `mexAddress` parametr.  
  
 To umožňuje scénáře, jako je rozdělení tabulky aplikace Excel, kde některé hodnoty buněk se počítá pomocí interakce webové služby. V tomto scénáři nemusí být vhodný k registraci sestavení kontraktu služby ve všech klientech, které může otevřít dokument. `wsdl` Parametr nebo `mexAddress` parametr povoluje samostatná řešení.  
  
> [!NOTE]
>  Vzájemné ověřování musí použít také k ochraně proti požadavku a odpovědi manipulaci nebo falšování identity. Konkrétně je důležité, aby klienti mohli být jistí, že koncový bod metadat systému Exchange, který odpovídá je určený důvěryhodná strana.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje použití monikeru služby s MEX kontrakt. Služba je následující kontrakt je vystaven s wsHttpBinding.  
  
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
  
 Lze použít k vytvoření klienta WCF pro službu vzdáleného následující příklad Přezdívka řetězec.  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 Během provádění klientská aplikace, klient provede `WS-MetadataExchange` poskytnutým `mexAddress`. To může vrátit adresy, vazby a podrobnosti smlouvy pro několik služeb. `address`, `contract`, `contractNamespace`, `binding` a `bindingNamespace` parametry slouží k identifikaci zamýšlené služby. Jakmile tyto parametry byly spárovány, přezdívka vytvoří klienta WCF s definicí příslušné smlouvy a volání pak lze pomocí klienta WCF, stejně jako u typu kontraktu.  
  
> [!NOTE]
>  Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chyba s oznámením "Neplatná syntaxe". Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Registrace a konfigurace monikeru služby](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
