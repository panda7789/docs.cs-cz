---
title: "Přenos MSMQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c8f1283a27488c56a866973270409c22efc1fb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="msmq-transport"></a>Přenos MSMQ
Toto téma uvádí všechny výjimky generované přenos MSMQ.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|Ověření vazby pro zprávu se nezdařilo. Klient nemůže odesílat zprávy. Tuto chybu způsobil konflikt ve vlastnostech vazby. Třída UseActiveDirectory je nastavena na hodnotu true a třída QueueTransferProtocol je nastavena na nativní. Chcete-li konflikt vyřešit, opravte jedna z vlastností.|  
|MsmqAuthNoneRequiresProtectionNone|Ověření vazeb pro spuštění služby se nezdařilo. Koncový bod služby nebo klienta nelze spustit. Tuto chybu způsobil konflikt ve vlastnostech vazby. Třída MsmqAuthenticationMode je nastaven na hodnotu None a MsmqProtectionLevel není nastavený na hodnotu None. K vyřešení konfliktu, opravte jedna z vlastností.|  
|MsmqCustomRequiresPerAddDLQ|Ověření vazby pro zprávu se nezdařilo. Klient nemůže odeslat zprávu. DeadLetterQueue je nastaven na hodnotu Custom, ale není zadána třída CustomDeadLetterQueue. Zadejte identifikátor URI fronty nedoručených zpráv pro každou aplikaci ve vlastnosti CustomDeadLetterQueue.|  
|MsmqDeserializationError|Při deserializaci zprávy XML došlo k chybě. Zprávu nelze přijmout a je vyřadit.|  
|MsmqDLQNotWriteable|Ověření vazby pro klienta se nezdařilo. Klient nemůže odeslat zprávu. Zadanou frontu nedoručených zpráv neexistuje nebo nelze zapsat. Zkontrolujte, zda že existuje fronta se správnou autorizací do něj zapisovat.|  
|MsmqGetPrivateComputerInformationError|Kontrola verze se nepovedlo kvůli zadané chybě. Verze služby MSMQ nelze zjistit, že selžou všechny operace, které jsou v kanálu ve frontě. Zajistěte, aby služby MSMQ je nainstalována a je k dispozici.|  
|MsmqNoAssurancesForVolatile|Ověření vazeb pro spuštění služby se nezdařilo. Koncový bod služby nebo klienta nelze spustit. ExactlyOnce je nastavena na hodnotu true a trvanlivé vlastnost nastavena na hodnotu false. To není podporováno. Chcete-li konflikt vyřešit, opravte jednu z těchto vlastností.|  
|MsmqNonTransactionalQueueNeeded|Byla zjištěna neshoda mezi vazby a konfigurace služby MSMQ fronty. Koncový bod služby nelze spustit. Vlastnost ExactlyOnce je nastavena na hodnotu false a čtení zpráv z fronty je fronta transakční. Opravte chybu nastavením vlastnosti ExactlyOnce na hodnotu true nebo vytvoření netransakční vazby.|  
|MsmqOpenError|Došlo k chybě při otevírání zadané frontě. Zprávu nelze odesílat nebo přijímat z fronty. Ujistěte se, že služby MSMQ je nainstalována a spuštěna. Ujistěte se také, že fronty je k dispozici a otevřete s režim požadovaný přístup a autorizace.|  
|MsmqPathLookupError|Došlo k chybě při převodu název cesty fronty zadaný název formátu. Všechny operace v kanálu ve frontě se nezdařilo. Ujistěte se, že adresa fronty je neplatný. MSMQ musí být nainstalován pomocí integrace služby Active Directory, které jsou povolené a přístup k němu je k dispozici.|  
|MsmqPerAppDLQRequiresCustom|Vazba ověření na straně klienta se nezdařilo. Klient nemůže odesílat zprávy. Vlastnost CustomDeadLetterQueue je nastavena, ale vlastnost DeadLetterQueue není nastaven na hodnotu Custom. Nastavte vlastnost DeadLetterQueue na hodnotu Custom.|  
|MsmqPerAppDLQRequiresExactlyOnce|Ověření vazby pro klienta se nezdařilo. Klient nemůže odesílat zprávy. Konflikt ve vlastnostech vazby způsobuje chybu. Chcete-li použít vlastní frontu nedoručených zpráv, musí být ExactlyOnce nastavena na hodnotu true, chcete-li vyřešit konflikt.|  
|MsmqPerAppDLQRequiresMsmq4|Byla zjištěna neshoda mezi vazby a konfigurace služby MSMQ. Klient nemůže odesílat zprávy. Pokud chcete používat vlastní frontu nedoručených zpráv, musí mít MSMQ verze 4.0 nebo vyšší. Pokud nemáte MSMQ verze 4.0 nebo vyšší nastavte vlastnost DeadLetterQueue na systému nebo hodnotu None.|  
|MsmqReceiveError|Došlo k chybě při přijímání zprávy z fronty. Ujistěte se, že služby MSMQ je nainstalována a spuštěna. Zkontrolujte, zda že je k dispozici pro příjem z fronty.|  
|MsmqSameTransactionExpected|Pro tuto relaci došlo k chybě transakce. Došlo k chybě v kanálu relace. Nelze odesílat nebo přijímat zprávy v relaci. Relaci ve frontě nelze přidružit k více než jedné transakci. Ujistěte se, že všechny zprávy v relaci jsou odesílané nebo přijímané pomocí jedné transakce.|  
|MsmqSendError|Došlo k chybě při odesílání do zadané frontě. Ujistěte se, že služby MSMQ je nainstalována a spuštěna. Při odesílání do místní fronty, zkontrolujte, zda že fronta existuje s režim požadovaný přístup a autorizaci.|  
|MsmqTimeSpanTooLarge|Čas zprávy do za provozu je příliš velký. Zprávu nelze odeslat. Zpráva Time To Live (TTL) nesmí překročit maximální hodnota Int32.|  
|MsmqTokenProviderNeededForCertificates|X509SecurityTokenProvider nebyl nalezen. Zprávu nelze odeslat. Režim ověřování certifikátu vyžaduje poskytovatele tokenu X.509. Zkontrolujte, zda že je k dispozici pro nainstalovaný certifikát poskytovatele tokenu zabezpečení.|  
|MsmqTransactedDLQExpected|Došlo k neshodě mezi vazby a konfigurace služby MSMQ. Není možné odesílat zprávy. Zadaná vazba vlastní frontu nedoručených zpráv musí být fronty transakcí. Zajistěte, aby správnost adresy vlastní frontu nedoručených zpráv a je fronta transakční frontou.|  
|MsmqTransactionalQueueNeeded|Došlo k neshodě mezi vazby a konfigurace služby MSMQ fronty. Koncový bod služby nelze spustit. ExactlyOnce je nastavena na hodnotu true a fronty ke čtení zpráv z není transakční. Chcete-li k chybě, nastavte vlastnost ExactlyOnce na false nebo vytvořte transakční fronty pro tuto vazbu.|  
|MsmqTransactionCurrentRequired|Žádná transakce je k dispozici k odeslání zprávy v relaci. Odeslat zprávu v relaci ve frontě vyžaduje transakce. Zajistěte, aby byl oboru transakce k odeslání zprávy v relaci.|  
|MsmqTransactionRequired|Transakce je požadován však není k dispozici. Nelze odesílat nebo přijímat zprávy. Zajistěte, aby byl oboru transakce odesílat nebo přijímat zprávy.|  
|MsmqUnsupportedSerializationFormat|Deserializace došlo k chybě. Zprávu nelze přijmout a je vyřadit. Zadaný formát serializace nepodporuje.|  
|MsmqWrongPrivateQueueSyntax|Adresa URL je neplatná. Adresa URL pro frontu nesmí obsahovat znak "$". Pomocí syntaxe v net.msmq://machine/private/queueName vyřešit soukromou frontu.|
