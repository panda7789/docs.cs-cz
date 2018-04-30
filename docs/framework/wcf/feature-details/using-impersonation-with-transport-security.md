---
title: Použití zosobnění se zabezpečením přenosu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
caps.latest.revision: 12
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: d5610a107a198a3d8fd0517dca6ca7e2f4d22cbb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="using-impersonation-with-transport-security"></a>Použití zosobnění se zabezpečením přenosu
*Zosobnění* přístup je schopnost serverová aplikace na identitu klienta. Je běžné pro služby použít zosobnění při ověření přístupu k prostředkům. Aplikace bude spuštěna pomocí účtu služby, ale když server přijme připojení klienta, zosobňuje klienta tak, aby kontroly přístupu se provádí pomocí pověření klienta. Zabezpečení přenosu je mechanizmus pro předávání přihlašovacích údajů a zabezpečení komunikace pomocí těchto přihlašovacích údajů. Toto téma popisuje pomocí zabezpečení přenosu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] s funkcí zosobnění. Další informace o zosobnění pomocí zabezpečení zpráv najdete v tématu [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Pět úrovní zosobnění  
 Zabezpečení přenosu využívá pět úrovní zosobnění, jak je popsáno v následující tabulce.  
  
|Úroveň zosobnění|Popis|  
|-------------------------|-----------------|  
|Žádné|Aplikace serveru nebude pokoušet o zosobnit klienta.|  
|Anonymní|Aplikace serveru mohou provádět kontroly přístupu na pověření klienta, ale nepřijímá žádné informace o identitu klienta. Tato úroveň zosobnění má smysl pouze pro komunikaci ve počítače, jako jsou pojmenované kanály. Pomocí `Anonymous` s připojení ke vzdálené zvýší úroveň na úroveň zosobnění identifikace.|  
|Identifikace|Serverové aplikace zná identitu klienta a lze provést ověření přístupu na základě pověření klienta, ale nelze zosobnit klienta. Identifikovat je výchozí úroveň zosobnění použít s přihlašovacími údaji SSPI v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Pokud zprostředkovatel tokenu poskytuje různé zosobnění úroveň.|  
|Impersonate|Serverové aplikace můžete přístup k prostředkům na serveru, jako klient kromě provádění kontroly přístupu. Aplikace serveru nemají přístup k prostředkům na vzdálených počítačích pomocí identity klienta, protože zosobněnou token nemá přihlašovací údaje k síti|  
|Delegát|Kromě nutnosti stejné schopnosti jako `Impersonate`, úroveň zosobnění delegát také umožňuje serveru aplikaci přístup k prostředkům na vzdálených počítačích pomocí identity klienta a předávat identity k ostatním aplikacím.<br /><br /> **Důležité** účet domény serveru musí být označen jako důvěryhodný pro delegování na řadič domény, který používá tyto další funkce. Tato úroveň zosobnění nelze použít s účty domény klienta označený jako důvěrné.|  
  
 Úrovně nejčastěji používaná k zabezpečení přenosu jsou `Identify` a `Impersonate`. Úrovně `None` a `Anonymous` typické vhodné používat, a mnoho přenosy nepodporují tyto úrovně pomocí ověřování. `Delegate` Úroveň je výkonné funkce, která by měla být používána opatrně. Jenom důvěryhodných serverů aplikace by měly mít oprávnění k delegování přihlašovacích údajů.  
  
 Použití zosobnění na `Impersonate` nebo `Delegate` úrovně vyžaduje server aplikací mít `SeImpersonatePrivilege` oprávnění. Pokud je spuštěn na účet členem skupiny Administrators nebo na účet s identifikátor SID Service (síťová služba, místní služba nebo Local System), má aplikace ve výchozím nastavení toto oprávnění. Zosobnění nevyžaduje vzájemné ověřování klienta a serveru. Některé schémat ověřování, které podporují zosobnění, jako je například protokol NTLM, nelze použít vzájemné ověření.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Přenos specifické problémy s zosobnění  
 Volba přenosu v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ovlivňuje možné volby pro zosobnění. Tato část popisuje problémy, které mají vliv na standardního protokolu HTTP a s názvem kanálu přenosy v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Vlastní přenosy mají své vlastní omezení na podporu pro zosobnění.  
  
### <a name="named-pipe-transport"></a>S názvem kanálu přenosu  
 Následující položky se používají s přenos pojmenovaný kanál:  
  
-   Pojmenovaný kanál přenosu je určena pro použití pouze v místním počítači. Pojmenovaný kanál přenosu v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitně zakáže připojení mezi počítači.  
  
-   Pojmenované kanály nelze použít s `Impersonate` nebo `Delegate` úroveň zosobnění. Pojmenovaný kanál nelze vynutit záruku na počítače v těchto úrovní zosobnění.  
  
 Další informace o pojmenované kanály najdete v tématu [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
### <a name="http-transport"></a>Přenos HTTP  
 Vazby, které používají přenos HTTP (<xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.BasicHttpBinding>) podporují několik schémat ověřování, jak je popsáno v [ověřování protokolu HTTP Principy](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md). Zosobnění úroveň podporované závisí na schéma ověřování. Následující položky se používají s přenos HTTP:  
  
-   `Anonymous` Schéma ověřování ignoruje zosobnění.  
  
-   `Basic` Schéma ověřování podporuje pouze `Delegate` úroveň. Upgradují všechny nižší úrovně zosobnění.  
  
-   `Digest` Schéma ověřování podporuje pouze `Impersonate` a `Delegate` úrovně.  
  
-   `NTLM` Schéma ověřování, které lze vybírat přímo nebo prostřednictvím vyjednávání, podporuje pouze `Delegate` úrovni v místním počítači.  
  
-   Schéma ověřování protokolu Kerberos, které lze vybrat pouze prostřednictvím vyjednávání, lze použít s libovolnou úroveň zosobnění podporované.  
  
 Další informace o přenos HTTP najdete v tématu [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="see-also"></a>Viz také  
 [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Postupy: Zosobnění klienta ve službě](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [Princip ověřování HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)
