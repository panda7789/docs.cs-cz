---
title: "Trasování aktivit v zabezpečení zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: db9b05217bbbf91bfc3cd315801b4e511f82d04c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="activity-tracing-in-message-security"></a>Trasování aktivit v zabezpečení zpráv
Toto téma popisuje aktivity trasování pro zpracování zabezpečení, který se stane následující tři fáze.  
  
-   Vyjednávání/SCT exchange. Tomu může dojít při přenosu později (prostřednictvím binární data exchange) nebo zpráva vrstvy (prostřednictvím výměny zpráv protokolu SOAP).  
  
-   Zpráva šifrování a dešifrování, s ověření podpisu a ověřování. Trasování se zobrazí v vedlejším aktivity, obvykle "procesu akce."  
  
-   Autorizace a ověření. K tomu dochází místně nebo při komunikaci mezi koncovými body.  
  
## <a name="negotiationsct-exchange"></a>Vyjednávání/SCT exchange  
 Ve fázi exchange vyjednávání/SCT jsou vytvořeny dva typy aktivit v klientovi: "Nastavit až zabezpečené relace" a "Zavřít zabezpečené relace." "Nastavení zabezpečení relace" zahrnuje trasování pro výměny zpráv RVNÍ/RSTR/SCT, zatímco "Zavřít zabezpečené relace" zahrnuje trasování pro zprávu zrušit.  
  
 Na serveru zobrazí se každý požadavek nebo odpověď pro RVNÍ/RSTR/SCT ve svých vlastních aktivit. Pokud `propagateActivity` = `true` na serveru a klienta, aktivity na serveru se stejným ID a objeví spolu "Instalační program zabezpečené relace" při zobrazit pomocí prohlížeče trasování služeb.  
  
 Tento model aktivity trasování je platný pro uživatelské jméno a heslo ověřování, ověřování certifikátů a ověřování protokolem NTLM.  
  
 Následující tabulka uvádí aktivity a trasování pro vyjednávání a SCT exchange.  
  
||Čas, kdy se stane vyjednávání/SCT exchange|Aktivity|Trasování|  
|-|-------------------------------------------------|----------------|------------|  
|Zabezpečení přenosu<br /><br /> (HTTPS, SSL)|Na první byla přijata zpráva.|Trasování jsou vygenerované v vedlejším aktivity.|– Trasování Exchange<br />-Zabezpečený kanál vytvořit<br />-Sdílet získat tajných klíčů.|  
|Zabezpečenou zprávu vrstvy<br /><br /> (WSHTTP)|Na první byla přijata zpráva.|Na straně klienta:<br /><br /> -"Instalační program zabezpečené relace" z "Proces Action", že první zprávy pro každý požadavek nebo odpověď pro RVNÍ/RSTR/SCT.<br />-"Zavřete zabezpečené relace" pro server exchange zrušit, mimo "Zavřít Proxy činnost." Tato aktivita může dojít mimo některých dalších vedlejším aktivit, v závislosti na tom, kdy je uzavřený zabezpečené relace.<br /><br /> Na serveru:<br /><br /> -Jednu aktivitu "Proces Action" pro každý požadavek nebo odpověď pro RVNÍ/SCT nebo zrušit na serveru. Pokud `propagateActivity` = `true`RVNÍ/RSTR/SCT aktivity jsou sloučeny s "Nastavit až zabezpečení relace" a Storno je sloučen s "Zavřít" aktivity z klienta.<br /><br /> Existují dvě fáze pro "Nastavit až zabezpečené relace":<br /><br /> 1.  Vyjednávání ověřování. Tato položka je nepovinná, pokud má klient již správné přihlašovací údaje. Tato fáze lze provést prostřednictvím zabezpečeného přenosu nebo prostřednictvím výměny zpráv. V takovém případě může dojít, 1 nebo 2 RVNÍ/RSTR výměnu. Pro tyto výměny informací jsou trasování vygenerované v nové aktivity požadavek nebo odpověď jako dříve určené.<br />2.  Zabezpečte vytvoření relace (SCT), ve kterém jeden RVNÍ/RSTR exchange se stane, zde. To má stejné vedlejším aktivity, jak je popsáno výše.|– Trasování Exchange<br />-Zabezpečený kanál vytvořit<br />-Sdílet získat tajných klíčů.|  
  
> [!NOTE]
>  V režimu smíšených zabezpečení vyjednávání ověřování probíhá binární výměnu, ale SCT probíhá výměna zpráv. V čistě transportní režim vyjednávání dochází pouze v přenosu s žádné další aktivity.  
  
## <a name="message-encryption-and-decryption"></a>Zpráva šifrování a dešifrování  
 Následující tabulka obsahuje seznam aktivit a trasování pro zprávu šifrování a dešifrování, jakož i ověřování podpisu.  
  
||Zabezpečení přenosu<br /><br /> (Protokol HTTPS, SSL) a zabezpečit zprávy vrstvy<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|Čas, kdy zprávy šifrování a dešifrování, stejně jako se stane, ověřování podpisu|Na přijata zpráva|  
|Aktivity|Trasování jsou vydávány v aktivitě ProcessAction na klientovi a serveru.|  
|Trasování|-sendSecurityHeader (odesílatel):<br />– Sign zpráva<br />-Šifrování dat požadavku<br />-receiveSecurityHeader (příjemce):<br />-Ověření podpisu<br />-Dešifrovat data odpovědi<br />-Ověřování|  
  
> [!NOTE]
>  V režimu čistý přenosu zpráv šifrování a dešifrování probíhá pouze přenos s žádné další aktivity.  
  
## <a name="authorization-and-verification"></a>Autorizace a ověření  
 Následující tabulka uvádí aktivity a trasování pro ověřování.  
  
||Čas, když se stane autorizace|Aktivity|Trasování|  
|-|-------------------------------------|----------------|------------|  
|Místní (výchozí)|Po zprávy se dešifrují na serveru|Trasování jsou vygenerované v ProcessAction aktivity na serveru.|Uživatel oprávnění.|  
|Vzdálené|Po zprávy se dešifrují na serveru|Trasování jsou vygenerované v novou aktivitu vyvolat ProcessAction aktivity.|Uživatel oprávnění.|
