---
title: Použití zosobnění se zabezpečením přenosu
ms.date: 03/30/2017
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
ms.openlocfilehash: 1d33bfbbb74266aefa538166b4e1aca7d7e315ef
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594969"
---
# <a name="using-impersonation-with-transport-security"></a>Použití zosobnění se zabezpečením přenosu
*Zosobnění* je schopnost serverové aplikace převzít identitu klienta. Pro služby, které se používají při ověřování přístupu k prostředkům, je běžné použití zosobnění. Serverová aplikace se spouští pomocí účtu služby, ale když server akceptuje připojení klienta, zosobní klienta, aby se kontroly přístupu prováděly pomocí přihlašovacích údajů klienta. Zabezpečení přenosu je mechanismus pro předávání přihlašovacích údajů a zabezpečení komunikace pomocí těchto přihlašovacích údajů. Toto téma popisuje použití zabezpečení přenosu v Windows Communication Foundation (WCF) s funkcí zosobnění. Další informace o zosobnění pomocí zabezpečení zpráv najdete v tématu [delegování a zosobnění](delegation-and-impersonation-with-wcf.md).  
  
## <a name="five-impersonation-levels"></a>Pět úrovní zosobnění  
 Zabezpečení přenosu využívá pět úrovní zosobnění, jak je popsáno v následující tabulce.  
  
|Úroveň zosobnění|Popis|  
|-------------------------|-----------------|  
|Žádné|Serverová aplikace se nepokouší zosobnit klienta.|  
|Anonymní|Serverová aplikace může provádět kontroly přístupu proti přihlašovacím údajům klienta, ale neobdrží žádné informace o identitě klienta. Úroveň zosobnění je smysluplná jenom pro komunikaci v počítači, jako jsou pojmenované kanály. Použití `Anonymous` se vzdáleným připojením zvyšuje úroveň zosobnění k identifikaci.|  
|Identifikace|Serverová aplikace zná identitu klienta a může provádět ověřování přístupu proti přihlašovacím údajům klienta, ale nemůže zosobnit klienta. Identifikace je výchozí úroveň zosobnění, která se používá pro přihlašovací údaje SSPI v WCF, pokud poskytovatel tokenů neposkytuje jinou úroveň zosobnění.|  
|Impersonate|Serverová aplikace má kromě provádění kontrol přístupu taky přístup k prostředkům na serverovém počítači jako klient. Serverová aplikace nemůže získat přístup k prostředkům na vzdálených počítačích pomocí identity klienta, protože zosobněný token nemá síťové přihlašovací údaje.|  
|Delegát|Kromě toho, že mají stejné možnosti jako `Impersonate` , úroveň zosobnění delegáta taky umožňuje serverové aplikaci přístup k prostředkům na vzdálených počítačích pomocí identity klienta a předání identity jiným aplikacím.<br /><br /> **Důležité** informace Aby bylo možné používat tyto další funkce, musí být účet domény serveru označen jako důvěryhodný pro delegování na řadiči domény. Tuto úroveň zosobnění nelze použít s účty domény klienta označenými jako citlivé.|  
  
 Úrovně nejčastěji používané při zabezpečení přenosu jsou `Identify` a `Impersonate` . Tyto úrovně `None` se `Anonymous` nedoporučují pro typické použití a mnoho přenosů nepodporuje používání těchto úrovní s ověřováním. `Delegate`Úroveň je výkonná funkce, která by se měla používat s péčí. Oprávnění delegovat přihlašovací údaje by měly být udělena pouze důvěryhodné serverové aplikace.  
  
 Použití zosobnění na úrovni `Impersonate` nebo vyžaduje, aby `Delegate` Serverová aplikace měla `SeImpersonatePrivilege` oprávnění. Aplikace má toto oprávnění ve výchozím nastavení, pokud je spuštěna na účtu ve skupině Administrators nebo v účtu s identifikátorem SID služby (síťová služba, místní služba nebo místní systém). Zosobnění nevyžaduje vzájemné ověřování klienta a serveru. Některá schémata ověřování, která podporují zosobnění, jako je například NTLM, nelze použít se vzájemným ověřováním.  
  
## <a name="transport-specific-issues-with-impersonation"></a>Problémy týkající se přenosu s zosobněním  
 Volba přenosu v WCF ovlivňuje možné volby pro zosobnění. Tato část popisuje problémy ovlivňující standardní přenosy HTTP a pojmenovaného kanálu ve službě WCF. Vlastní přenosy mají svá vlastní omezení podpory zosobnění.  
  
### <a name="named-pipe-transport"></a>Přenos pojmenovaného kanálu  
 S přenosem pojmenovaného kanálu se používají tyto položky:  
  
- Přenos pojmenovaného kanálu je určený jenom pro použití na místním počítači. Přenos pojmenovaného kanálu ve službě WCF explicitně nepovoluje připojení mezi počítači.  
  
- Pojmenované kanály nelze použít s `Impersonate` `Delegate` úrovní nebo zosobnění. Pojmenovaný kanál nemůže na těchto úrovních zosobnění vymáhat záruku na počítač.  
  
 Další informace o pojmenovaných kanálech najdete v tématu [Volba přenosu](choosing-a-transport.md).  
  
### <a name="http-transport"></a>Přenos HTTP  
 Vazby, které používají přenos přes protokol HTTP ( <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.BasicHttpBinding> ) podporují několik schémat ověřování, jak je vysvětleno v tématu [Principy ověřování protokolem HTTP](understanding-http-authentication.md). Podporovaná úroveň zosobnění závisí na schématu ověřování. S přenosem HTTP se používají tyto položky:  
  
- `Anonymous`Schéma ověřování ignoruje zosobnění.  
  
- `Basic`Schéma ověřování podporuje pouze `Delegate` úroveň. Všechny nižší úrovně zosobnění jsou upgradovány.  
  
- `Digest`Schéma ověřování podporuje pouze `Impersonate` `Delegate` úrovně a.  
  
- `NTLM`Schéma ověřování, které lze vybrat buď přímo, nebo prostřednictvím vyjednávání, podporuje pouze `Delegate` úroveň v místním počítači.  
  
- Schéma ověřování protokolu Kerberos, které lze vybrat pouze prostřednictvím vyjednávání, lze použít s libovolnou podporovanou úrovní zosobnění.  
  
 Další informace o přenosu HTTP najdete v tématu [Volba přenosu](choosing-a-transport.md).  
  
## <a name="see-also"></a>Viz také

- [Delegace a zosobnění](delegation-and-impersonation-with-wcf.md)
- [Autorizace](authorization-in-wcf.md)
- [Postupy: Zosobnění klienta ve službě](../how-to-impersonate-a-client-on-a-service.md)
- [Princip ověřování HTTP](understanding-http-authentication.md)
