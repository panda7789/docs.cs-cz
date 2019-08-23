---
title: Trasování aktivit v zabezpečení zpráv
ms.date: 03/30/2017
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
ms.openlocfilehash: bb8a4c6782cc52de393eacc2458e216d0f069866
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933518"
---
# <a name="activity-tracing-in-message-security"></a>Trasování aktivit v zabezpečení zpráv
Toto téma popisuje trasování aktivit pro zpracování zabezpečení, ke kterému dochází v následujících třech fázích.  
  
- Vyjednávání/SCT Exchange. K tomu může dojít později při přenosu (prostřednictvím výměny binárních dat) nebo vrstvy zpráv (prostřednictvím výměn zpráv SOAP).  
  
- Šifrování a dešifrování zpráv pomocí ověřování podpisů a ověřování. Trasování se zobrazí v okolí aktivity, obvykle "akce zpracování".  
  
- Autorizaci a ověření. K tomu může dojít místně nebo při komunikaci mezi koncovými body.  
  
## <a name="negotiationsct-exchange"></a>Vyjednávání/SCT Exchange  
 Ve fázi vyjednávání/SCT Exchange se na klientovi vytvoří dva typy aktivit: "Nastavte zabezpečenou relaci" a "Zavřít zabezpečenou relaci". Možnost nastavit zabezpečenou relaci zahrnuje trasování pro výměny zpráv RST/RSTR/SCT, zatímco možnost "uzavřít zabezpečenou relaci" zahrnuje trasování pro zprávu zrušení.  
  
 Na serveru se každý požadavek nebo odpověď pro RST/RSTR/SCT zobrazí ve své vlastní aktivitě. Pokud `propagateActivity` naserverui`true` v klientovi, aktivity na serveru mají stejné ID a společně se zobrazí v části "zabezpečená relace" při zobrazení prostřednictvím prohlížeče trasování služby. =  
  
 Tento model trasování aktivit je platný pro ověřování uživatelského jména a hesla, ověřování certifikátů a ověřování NTLM.  
  
 V následující tabulce jsou uvedeny aktivity a trasování pro vyjednávání a SCT Exchange.  
  
||Čas, kdy dojde k vyjednání/SCT výměně|Aktivity|Trasování|  
|-|-------------------------------------------------|----------------|------------|  
|Zabezpečený přenos<br /><br /> (HTTPS, SSL)|První přijatá zpráva|Trasování jsou vygenerována v okolí aktivity.|– Trasování systému Exchange<br />– Zavedený zabezpečený kanál<br />-Bylo získáno sdílení tajných kódů.|  
|Zabezpečená vrstva zprávy<br /><br /> (WSHTTP)|První přijatá zpráva|Na klientovi:<br /><br /> – "Nastavit zabezpečenou relaci" z "akce procesu" této první zprávy pro každý požadavek/odpověď pro RST/RSTR/SCT.<br />-"Uzavřít zabezpečenou relaci" pro zrušení výměny z "aktivity zavřít proxy". Tato aktivita se může vyskytnout z nějaké jiné aktivity okolí v závislosti na tom, kdy je zabezpečená relace uzavřená.<br /><br /> Na serveru:<br /><br /> -Jedna aktivita zpracovat akci pro každý požadavek nebo odpověď pro RST/SCT/Cancel na serveru. Pokud `propagateActivity` jsouaktivityRST`true`/RSTR/SCT sloučeny s nastavením relace zabezpečení a zrušení je sloučeno s aktivitou "Zavřít" z klienta. =<br /><br /> Pro nastavení zabezpečené relace jsou k dispozici dvě fáze:<br /><br /> 1.  Vyjednávání ověřování. To je volitelné, pokud již klient obsahuje správné přihlašovací údaje. Tuto fázi je možné provést prostřednictvím zabezpečeného přenosu nebo prostřednictvím výměny zpráv. V druhém případě může probíhat výměna 1 nebo 2 RSTR. Pro tyto výměny se trasování generují v nových aktivitách žádostí a odpovědí, jak už bylo navrženo dříve.<br />2.  Vytvoření zabezpečené relace (SCT), ve kterém se tady stane jedna RST/RSTR výměna. To má stejné okolní aktivity, jak je popsáno výše.|– Trasování systému Exchange<br />– Zavedený zabezpečený kanál<br />-Bylo získáno sdílení tajných kódů.|  
  
> [!NOTE]
> V režimu smíšeného zabezpečení se ověřování vyjednávání provádí v binárních výměnách, ale SCT se děje ve výměně zpráv. V režimu čistého přenosu probíhá vyjednávání pouze v přenosu bez dalších aktivit.  
  
## <a name="message-encryption-and-decryption"></a>Šifrování a dešifrování zpráv  
 V následující tabulce jsou uvedeny aktivity a trasování pro šifrování a dešifrování zpráv a také ověřování podpisů.  
  
||Zabezpečený přenos<br /><br /> (HTTPS, SSL) a vrstva zabezpečené zprávy<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|Čas, kdy dojde k šifrování a dešifrování zprávy, i k ověřování podpisů|Při přijetí zprávy|  
|Aktivity|Trasování jsou vydávána v aktivitě ProcessAction na klientovi a serveru.|  
|Trasování|-sendSecurityHeader (odesilatel):<br />– Podepsat zprávu<br />-Šifrovat data požadavku<br />-receiveSecurityHeader (přijímač):<br />-Ověřit podpis<br />-Dešifrovat data odpovědi<br />– Ověřování|  
  
> [!NOTE]
> V režimu čistého přenosu probíhá šifrování a dešifrování zpráv pouze v přenosu bez dalších aktivit.  
  
## <a name="authorization-and-verification"></a>Autorizace a ověřování  
 V následující tabulce jsou uvedeny aktivity a trasování pro autorizaci.  
  
||Čas, kdy dojde k autorizaci|Aktivity|Trasování|  
|-|-------------------------------------|----------------|------------|  
|Místní (výchozí)|Po dešifrování zprávy na serveru|Trasování jsou vydávána v aktivitě ProcessAction na serveru.|Autorizován uživatelem.|  
|Vzdálený|Po dešifrování zprávy na serveru|Trasování jsou generována v nové aktivitě vyvolané aktivitou ProcessAction.|Autorizován uživatelem.|
