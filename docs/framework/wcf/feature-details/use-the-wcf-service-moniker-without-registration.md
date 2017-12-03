---
title: "Postupy: použití Monikeru služby Windows Communication Foundation bez registrace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9e91889947a17f8cba66d822b857e1c8bc875cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Postupy: použití Monikeru služby Windows Communication Foundation bez registrace
Pro připojení k a komunikovat s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientská aplikace musí mít podrobnosti o adresu služby, konfigurace vazeb a kontrakt služby.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Monikeru služby obvykle získá požadované kontrakt prostřednictvím předchozí registrace požadovaný atribut typy, ale můžou nastat případy, kdy to není možné. Přezdívka místo registrace, můžete získat definici kontraktu ve formě dokumentem definice jazyka WSDL (Web Services) prostřednictvím `wsdl` parametr nebo prostřednictvím Metadata Exchange prostřednictvím použití `mexAddress` parametr.  
  
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
  
 K vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta pro vzdálené služby lze použít následující příklad Přezdívka řetězec.  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 Během provádění klientská aplikace, klient provede `WS-MetadataExchange` poskytnutým `mexAddress`. To může vrátit adresy, vazby a podrobnosti smlouvy pro několik služeb. `address`, `contract`, `contractNamespace`, `binding` a `bindingNamespace` parametry slouží k identifikaci zamýšlené služby. Jakmile tyto parametry byly spárovány, vytvoří Přezdívka [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta s definicí příslušné smlouvy a volání můžete provedeny poté pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, stejně jako u typu kontraktu.  
  
> [!NOTE]
>  Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chyba s oznámením "Neplatná syntaxe". Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: registrace a konfigurace Monikeru služby](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
