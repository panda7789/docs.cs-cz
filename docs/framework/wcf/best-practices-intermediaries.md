---
title: 'Doporučené postupy: Prostředníci'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: a7c037b5942a404b1ff790638979a8e430394151
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320789"
---
# <a name="best-practices-intermediaries"></a>Doporučené postupy: Prostředníci
Při volání zprostředkovatelů, aby bylo zajištěno, že kanály na straně služby na straně zprostředkovatele jsou správně uzavřeny, je nutné vzít v potaz správné zpracování chyb.  
  
 Vezměte v úvahu následující scénář. Klient provede volání do zprostředkovatele, který pak zavolá back-end službu.  Back-endové služba nedefinuje žádnou kontrakt selhání, takže jakákoli chyba vyvolaná z této služby bude považována za chybu bez typu.  Back-endové služba vyvolá <xref:System.ApplicationException> a WCF správně přerušuje kanál na straně služby. @No__t-0 pak povrchy jako <xref:System.ServiceModel.FaultException>, které se vyvolaly zprostředkovateli. Zprostředkovatel znovu vyvolá <xref:System.ApplicationException>. Služba WCF interpretuje tuto chybu jako netypovou chybu ze zprostředkovatele a předá ji klientovi. Po obdržení chyby je to jak zprostředkovatel, tak Chyba klienta na straně klienta. Kanál na straně služby zprostředkujícího poskytovatele zůstane otevřený, protože služba WCF neví, že chyba je závažná.  
  
 Osvědčeným postupem v tomto scénáři je zjistit, zda chyba přicházející ze služby je závažná, a pokud by zprostředkovatel neměl chybu kanálu na straně služby, jak je znázorněno v následujícím fragmentu kódu.  
  
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

- [Zpracování chyb WCF](wcf-error-handling.md)
- [Určování a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md)
