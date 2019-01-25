---
title: 'Doporučené postupy: Prostředníci'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 8a95bd555e6c1acf896daa77e93d7c735d1f091c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663619"
---
# <a name="best-practices-intermediaries"></a>Doporučené postupy: Prostředníci
Chcete-li správně zpracovávaly chyby při volání metody zprostředkovatele, abyste měli jistotu, že jsou správně uzavřeny kanály na straně služby na zprostředkovatele musí věnovat pozornost.  
  
 Vezměte v úvahu následující scénář. Klient provede volání zprostředkovatele, který pak volá back-end služby.  Back-end služba definuje žádná chyba – kontrakt, tak jakékoli chyby vyvolané z dané služby, bude zacházeno jako netypové selhání.  Vyvolá back-end službu <xref:System.ApplicationException> a WCF správně zruší kanál straně služby. <xref:System.ApplicationException> Potom zobrazí jako <xref:System.ServiceModel.FaultException> , která je vyvolána zprostředkovatelem. Zprostředkovatel znovu vyvolá <xref:System.ApplicationException>. WCF interpretuje jako netypové selhání od zprostředkovatele a předá jej ke klientovi. Při přijetí chyby zprostředkovatele a klient selhání jejich kanály na straně klienta. Zprostředkovatel na straně služby kanálu ale zůstane otevřený, protože WCF neví, že je závažné chyby.  
  
 Osvědčeným postupem v tomto scénáři je zjistit, jestli je závažné chyby pocházející ze služby, a pokud zprostředkovatel tak by měl selhání svůj kanál ze strany služby, jak je znázorněno v následujícím fragmentu kódu.  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také:
- [Zpracování chyb WCF](../../../docs/framework/wcf/wcf-error-handling.md)
- [Určování a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
