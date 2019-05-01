---
title: Použití zosobnění se zabezpečením přenosu
ms.date: 03/30/2017
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
ms.openlocfilehash: 6209007b60effe5403caf3db8855f029d0c47a0e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050672"
---
# <a name="using-impersonation-with-transport-security"></a>Použití zosobnění se zabezpečením přenosu
*Zosobnění* je schopnost serveru aplikace, abyste mohli na identity klienta. Je běžné, že služby pro použití zosobnění při ověření přístupu k prostředkům. Serverová aplikace běží, pomocí účtu služby, ale pokud server přijme připojení klienta, klient zosobní tak, aby kontroly přístupu se provádí pomocí přihlašovacích údajů klienta. Zabezpečení přenosu sítí je mechanismus pro předávání přihlašovacích údajů a zabezpečení komunikace pomocí těchto přihlašovacích údajů. Toto téma popisuje pomocí zabezpečení přenosu pomocí zosobnění funkce ve Windows Communication Foundation (WCF). Další informace o zosobnění pomocí zabezpečení zpráv, najdete v části [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Pět úrovní zosobnění  
 Zabezpečení přenosu využívá pět úrovní zosobnění, jak je popsáno v následující tabulce.  
  
|Úroveň zosobnění|Popis|  
|-------------------------|-----------------|  
|Žádné|Serverová aplikace nebude pokoušet o zosobnit klienta.|  
|Anonymní|Serverová aplikace může provádět kontroly přístupu na pověření klienta, ale nepřijímá žádné informace o identitu klienta. Tato úroveň zosobnění má smysl pouze pro komunikaci na počítači, jako jsou pojmenované kanály. Pomocí `Anonymous` pomocí připojení vzdálené povýší úroveň zosobnění k identifikovat.|  
|Identifikace|Serverová aplikace zná identitu klienta a můžete provádět ověření přístupu na základě přihlašovacích údajů klienta, ale nelze zosobnit klienta. Identifikujte je výchozí úroveň zosobnění použít s přihlašovacími údaji SSPI ve službě WCF, pokud poskytovatel tokenu poskytuje úroveň zosobnění jiný.|  
|Impersonate|Serverová aplikace může přistupovat k prostředkům počítače serveru jako klienta kromě provádění kontroly přístupu. Serverová aplikace nemá přístup k prostředkům na vzdálených počítačích pomocí identity klienta, protože zosobněného token nemá žádné přihlašovací údaje k síti|  
|Delegát|Kromě stejné funkce jako `Impersonate`, úroveň zosobnění delegát rovněž umožňuje aplikaci server pro přístup k prostředkům na vzdálených počítačích pomocí identity klienta a k předání identity k ostatním aplikacím.<br /><br /> **Důležité** účet domény serveru musí být označen jako důvěryhodný pro delegování na řadiči domény, který chcete použít tyto další funkce. Tato úroveň zosobnění nelze použít s označené jako citlivé účty domény klienta.|  
  
 Existují tyto úrovně zabezpečení přenosu nejčastěji používaná `Identify` a `Impersonate`. Úrovně `None` a `Anonymous` nedoporučují pro běžné použití, a mnoho přenosy nepodporují použití těchto úrovních s ověřením. `Delegate` Úroveň je výkonná funkce, která by měla být používána opatrně. Jenom důvěryhodných serverů aplikace by měly mít oprávnění k delegování přihlašovacích údajů.  
  
 Použití zosobnění na `Impersonate` nebo `Delegate` úrovně vyžaduje se serverová aplikace mohla mít `SeImpersonatePrivilege` oprávnění. Aplikace toto oprávnění má ve výchozím nastavení, pokud je spuštěn na účet členem skupiny Administrators nebo v rámci účtu s SID služby (síťová služba, místní služba nebo místního systému). Zosobnění nevyžaduje vzájemného ověřování klienta a serveru. Některé schémata ověřování, které podporují zosobnění, jako je například ověřování NTLM, nemohou být součástí vzájemného ověřování.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Vyhledávají chyby specifické pro přenos pomocí zosobnění  
 Volba přenosu ve službě WCF ovlivňuje zvolit je možné pro zosobnění. Tato část popisuje problémy neovlivňují standardního protokolu HTTP a s názvem přenosy kanálu ve službě WCF. Vlastní přenosy mít vlastní omezení podpory pro zosobnění.  
  
### <a name="named-pipe-transport"></a>S názvem kanál přenosu  
 Následující položky se používají s pojmenovaný kanál přenosu:  
  
- Pojmenovaný kanál přenosu je určen pro použití pouze v místním počítači. Pojmenovaný kanál přenosu ve službě WCF výslovně zakazuje připojení mezi počítači.  
  
- Pojmenované kanály nelze použít s `Impersonate` nebo `Delegate` úroveň zosobnění. Pojmenovaný kanál nelze vynutit záruka na počítači, na těchto úrovních zosobnění.  
  
 Další informace o pojmenovaných kanálů najdete v tématu [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
### <a name="http-transport"></a>Přenos pomocí protokolu HTTP  
 Vazby, které používají přenos pomocí protokolu HTTP (<xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.BasicHttpBinding>) podporují více schémat ověřování, jak je vysvětleno v [Princip ověřování HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md). Nepodporuje úroveň zosobnění závisí na schéma ověřování. Následující položky se používají s přenos pomocí protokolu HTTP:  
  
- `Anonymous` Schéma ověřování ignoruje zosobnění.  
  
- `Basic` Schéma ověřování podporuje pouze `Delegate` úroveň. Budou upgradovat všechny nižší úrovně zosobnění.  
  
- `Digest` Schéma ověřování podporuje pouze `Impersonate` a `Delegate` úrovně.  
  
- `NTLM` Schéma ověřování, lze vybrat buď přímo nebo prostřednictvím vyjednávání, podporuje jenom `Delegate` úrovně v místním počítači.  
  
- Schéma ověřování protokolu Kerberos, které lze vybrat pouze prostřednictvím vyjednávání, jde použít s libovolnou úroveň zosobnění podporované.  
  
 Další informace o přenos pomocí protokolu HTTP, naleznete v tématu [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="see-also"></a>Viz také:

- [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Postupy: Zosobnění klienta ve službě](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [Princip ověřování HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)
