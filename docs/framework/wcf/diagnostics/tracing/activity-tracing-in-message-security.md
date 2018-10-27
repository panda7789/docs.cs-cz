---
title: Trasování aktivit v zabezpečení zpráv
ms.date: 03/30/2017
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
ms.openlocfilehash: c3bd36598fd903dc016959149e563174624d084b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181326"
---
# <a name="activity-tracing-in-message-security"></a>Trasování aktivit v zabezpečení zpráv
Toto téma popisuje trasování aktivity pro zpracování zabezpečení, který se tyto tři fáze.  
  
-   Vyjednávání/SCT exchange. To může nastat při přenosu později (prostřednictvím výměny binární data) nebo zpráva vrstvy (prostřednictvím výměny zpráv SOAP).  
  
-   Zpráva šifrování a dešifrování, ověřování podpisů a ověřování. Trasování se zobrazí v okolí aktivity, obvykle "procesu akce."  
  
-   Autorizace a ověření. To může nastat, místně nebo při komunikaci mezi koncovými body.  
  
## <a name="negotiationsct-exchange"></a>Vyjednávání/SCT exchange  
 V systému exchange fáze vyjednávání/SCT jsou vytvořeny dva typy aktivit na straně klienta: "Nastavit až zabezpečenou relaci" a "Zavřít zabezpečenou relaci." "Nastavte zabezpečenou relaci" zahrnuje trasování pro výměny zpráv RVNÍ/RSTR/SCT, sice "Ukončení relace Secure" zahrnuje trasování pro zprávu zrušit.  
  
 Na serveru se zobrazí každý požadavek/odpověď pro RVNÍ/RSTR/SCT ve svých vlastních aktivit. Pokud `propagateActivity` = `true` na serveru a klienta, se stejným ID aktivity na serveru a společně se zobrazí v "Nastavení zabezpečené relaci" při zobrazit pomocí prohlížeče trasování služeb.  
  
 Tento model trasování aktivity je platné uživatelské jméno/heslo ověřování, ověřování certifikátů a ověřování protokolem NTLM.  
  
 V následující tabulce jsou uvedeny aktivity a trasování pro vyjednávání a SCT exchange.  
  
||Čas, když se stane vyjednávání/SCT exchange|Aktivity|trasování|  
|-|-------------------------------------------------|----------------|------------|  
|Zabezpečení přenosu<br /><br /> (PROTOKOL HTTPS, SSL)|Na první byla přijata zpráva.|Trasování jsou emitovány v okolí aktivity.|– Trasování Exchange<br />-Zabezpečený kanál vytvořeno<br />-Sdílení získali tajných kódů.|  
|Vrstva zabezpečenou zprávu<br /><br /> (WSHTTP)|Na první byla přijata zpráva.|Na straně klienta:<br /><br /> -"Nastavení zabezpečenou relaci" z "Proces Action" první zprávy, pro každý požadavek nebo odpověď pro RVNÍ/RSTR/SCT.<br />-"Zavřít zabezpečenou relaci" Storno výměny "Zavřít Proxy aktivita." Tato aktivita se může stát některé další okolí aktivita, v závislosti na tom, kdy je uzavřena zabezpečenou relaci.<br /><br /> Na serveru:<br /><br /> -"Procesu" aktivit akcí pro každý požadavek/odpověď pro RVNÍ/SCT/zrušit na serveru. Pokud `propagateActivity` = `true`RVNÍ/RSTR/SCT aktivity jsou sloučeny s "Nastavit až relace zabezpečení" a zrušit je sloučen s "Zavřít" aktivitu z klienta.<br /><br /> Existují dvě fáze pro "Nastavit až zabezpečenou relaci":<br /><br /> 1.  Ověřování vyjednávání. Tato položka je nepovinná, pokud klient již má správné přihlašovací údaje. Tato fáze lze provést prostřednictvím zabezpečeného přenosu, nebo výměny zpráv. V takovém případě může dojít, 1 nebo 2 RVNÍ/RSTR výměny. Pro tyto výměny zpracovávají jsou emitovány trasování v nové aktivity požadavek/odpověď navržena jako dříve.<br />2.  Zabezpečte vytvoření relace (SCT), ve kterém jeden RVNÍ/RSTR exchange se tady děje. To má stejné okolí aktivity, jak je popsáno výše.|– Trasování Exchange<br />-Zabezpečený kanál vytvořeno<br />-Sdílení získali tajných kódů.|  
  
> [!NOTE]
>  V režimu smíšených zabezpečení vyjednávání ověřování probíhá výměna binární, ale SCT probíhá výměna zpráv. V režimu čistě přenosu vyjednávání dochází pouze v přenosu se žádné další aktivity.  
  
## <a name="message-encryption-and-decryption"></a>Šifrování a dešifrování  
 V následující tabulce jsou uvedeny aktivity a trasování pro šifrování a dešifrování zprávy, jakož i ověřování podpisu.  
  
||Zabezpečení přenosu<br /><br /> (Protokol HTTPS, SSL) a zabezpečení vrstvy zprávy<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|Čas, kdy zprávy šifrování a dešifrování, stejně jako využíváno ověření podpisu|Na byla přijata zpráva|  
|Aktivity|Trasování jsou zaznamenávány do ProcessAction aktivitu na klienta a serveru.|  
|trasování|-sendSecurityHeader (odesílatel):<br />– Sign zpráva<br />-Šifrování dat požadavku<br />-receiveSecurityHeader (příjemce):<br />– Ověření podpisu<br />-Dešifrovat data odpovědi<br />-Ověřování|  
  
> [!NOTE]
>  V režimu čistě přenosu zprávy šifrování a dešifrování dochází pouze v přenosu se žádné další aktivity.  
  
## <a name="authorization-and-verification"></a>Autorizace a ověření  
 V následující tabulce jsou uvedeny aktivity a trasování pro autorizaci.  
  
||Čas, když se stane autorizace|Aktivity|trasování|  
|-|-------------------------------------|----------------|------------|  
|Místní (výchozí)|Po zprávy se dešifrují na serveru|Trasování jsou zaznamenávány do ProcessAction aktivity na serveru.|Uživatel autorizován.|  
|Vzdálený|Po zprávy se dešifrují na serveru|Trasování jsou zaznamenávány do vyvolané aktivitou ProcessAction novou aktivitu.|Uživatel autorizován.|
