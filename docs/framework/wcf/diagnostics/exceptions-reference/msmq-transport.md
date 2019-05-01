---
title: Přenos MSMQ
ms.date: 03/30/2017
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
ms.openlocfilehash: a2e5384808b82f48bd1d4856bf893130da8c5f1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959416"
---
# <a name="msmq-transport"></a>Přenos MSMQ
Toto téma uvádí všechny výjimky generované přenosu služby MSMQ.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|Ověření vazby zprávy se nezdařilo. Klient nemůže odesílat zprávy. Tuto chybu způsobil konflikt ve vlastnostech vazby. Třída UseActiveDirectory je nastavena na hodnotu true a třída QueueTransferProtocol je nastavena na nativní. Jak vyřešit konflikt opravou některé z vlastností.|  
|MsmqAuthNoneRequiresProtectionNone|Ověření vazby služby se nezdařilo. Koncový bod služby nebo klienta nelze spustit. Tuto chybu způsobil konflikt ve vlastnostech vazby. Třída MsmqAuthenticationMode je nastavena na hodnotu None a třída MsmqProtectionLevel není nastavena na hodnotu None. Pro tento konflikt opravou některé z vlastností.|  
|MsmqCustomRequiresPerAddDLQ|Ověření vazby zprávy se nezdařilo. Klient nemůže odesílat zprávy. DeadLetterQueue je nastavena na hodnotu Custom, ale třída CustomDeadLetterQueue není zadán. Zadejte identifikátor URI fronty nedoručených zpráv pro každou aplikaci ve vlastnosti CustomDeadLetterQueue.|  
|MsmqDeserializationError|Při rušení serializace zprávy XML došlo k chybě. Zprávu nelze přijmout a se zahodí.|  
|MsmqDLQNotWriteable|Ověření vazby pro klienta se nezdařilo. Klient nemůže odesílat zprávy. Zadaná fronta nedoručených zpráv neexistuje nebo se nedá zapisovat. Zkontrolujte, jestli že existuje fronta se správnou autorizací zápisu.|  
|MsmqGetPrivateComputerInformationError|Kontrola verze selhala kvůli zadané chybě. Verze služby MSMQ nelze zjistit, že všechny operace, které jsou na kanálu s frontou selžou. Ujistěte se, že služba MSMQ je nainstalována a je k dispozici.|  
|MsmqNoAssurancesForVolatile|Ověření vazby služby se nezdařilo. Koncový bod služby nebo klienta nelze spustit. ExactlyOnce je nastavena na hodnotu true a vlastnost Durable je nastavena na hodnotu false. To není podporováno. Jak vyřešit konflikt opravou některé z těchto vlastností.|  
|MsmqNonTransactionalQueueNeeded|Byla zjištěna neshoda mezi vazbou a konfigurací fronty MSMQ. Koncový bod služby nelze spustit. Vlastnost ExactlyOnce je nastavena na hodnotu false a čtení zpráv z fronty je fronta transakční. Chybu lze opravte nastavením vlastnosti ExactlyOnce na hodnotu true nebo vytvořením netransakční vazby.|  
|MsmqOpenError|Došlo k chybě při otevírání zadanou frontu. Zprávu nelze odeslat ani přijmout z fronty. Ujistěte se, že je služba MSMQ nainstalovaná a spuštěná. Také se ujistěte, že je fronta dostupná pro otevření s požadovaným režimem přístupu a autorizaci.|  
|MsmqPathLookupError|Došlo k chybě při převodu název cesty fronty zadaný název formátu. Všechny operace na kanálu ve frontě se nezdařilo. Ujistěte se, že je adresa fronty platná. Služba MSMQ musí být nainstalována s povolenou integrací služby Active Directory a přístup k němu je k dispozici.|  
|MsmqPerAppDLQRequiresCustom|Ověření vazby na straně klienta se nezdařilo. Klient nemůže odesílat zprávy. Vlastnost CustomDeadLetterQueue je nastavena, ale vlastnost DeadLetterQueue není nastavena na hodnotu Custom. Nastavte vlastnost DeadLetterQueue na hodnotu Custom.|  
|MsmqPerAppDLQRequiresExactlyOnce|Ověření vazby pro klienta se nezdařilo. Klient nemůže odesílat zprávy. Chybu způsobuje konflikt ve vlastnostech vazby. Pokud chcete používat vlastní frontu nedoručených zpráv, musí být ExactlyOnce nastavena na hodnotu true. Tento konflikt.|  
|MsmqPerAppDLQRequiresMsmq4|Byla zjištěna neshoda mezi vazbou a konfigurací služby MSMQ. Klient nemůže odesílat zprávy. Pokud chcete používat vlastní frontu nedoručených zpráv, musíte mít službu MSMQ verze 4.0 nebo vyšší. Pokud nemáte službu MSMQ verze 4.0 nebo vyšší, nastavte vlastnost DeadLetterQueue na systém nebo žádný.|  
|MsmqReceiveError|Během příjmu zprávy z fronty došlo k chybě. Ujistěte se, že je služba MSMQ nainstalovaná a spuštěná. Ujistěte se, že je k dispozici pro příjem z fronty.|  
|MsmqSameTransactionExpected|Pro tuto relaci došlo k chybě transakce. Kanál relace došlo k chybě. Zprávy v relaci nelze odeslat ani přijmout. Relaci ve frontě nelze přidružit více než jedné transakce. Ujistěte se, že všechny zprávy v relaci odeslány nebo přijaty pomocí jedné transakce.|  
|MsmqSendError|Při odesílání do zadané fronty došlo k chybě. Ujistěte se, že je služba MSMQ nainstalovaná a spuštěná. Pokud odesíláte do místní fronty, ujistěte se, že fronta existuje s požadovaným režimem přístupu a autorizace.|  
|MsmqTimeSpanTooLarge|Hodnota time to live je moc velká. Zprávu nelze odeslat. Čas To Live (TTL) zprávy nesmí překročit maximální hodnotu typu Int32.|  
|MsmqTokenProviderNeededForCertificates|X509SecurityTokenProvider nebyl nalezen. Zprávu nelze odeslat. Režim ověřování certifikátu vyžaduje poskytovatele tokenu X.509. Ujistěte se, že je k dispozici pro nainstalovaný certifikát poskytovatele tokenu zabezpečení.|  
|MsmqTransactedDLQExpected|Došlo k neshodě mezi vazbou a konfigurací služby MSMQ. Zprávu nelze odeslat. Vlastní frontu nedoručených zpráv určená ve vazbě musí být transakční fronta. Ujistěte se, že je adresa vlastní fronty nedoručených zpráv správná a zda je fronta transakční.|  
|MsmqTransactionalQueueNeeded|Došlo k neshodě mezi vazbou a konfigurací fronty MSMQ. Koncový bod služby nelze spustit. ExactlyOnce je nastavena na hodnotu true a fronty ke čtení zpráv z není transakční. Chcete-li k chybě, nastavte vlastnosti ExactlyOnce na hodnotu false nebo vytvoření transakční fronty pro tuto vazbu.|  
|MsmqTransactionCurrentRequired|Žádná transakce není možné odesílat zprávy v relaci. Odeslání zprávy v relaci ve frontě vyžaduje transakci. Ujistěte se, že obor transakcí určen k odeslání zprávy v relaci.|  
|MsmqTransactionRequired|Transakce je povinný, ale není k dispozici. Zprávy nelze odeslat ani přijmout. Ujistěte se, že obor transakcí určen k odesílání nebo příjmu zpráv.|  
|MsmqUnsupportedSerializationFormat|Došlo k chybě rekonstrukce. Zprávu nelze přijmout a se zahodí. Zadaný formát serializace se nepodporuje.|  
|MsmqWrongPrivateQueueSyntax|Adresa URL je neplatná. Adresa URL pro frontu nesmí obsahovat znak "$". Použijte syntaxi v adrese NET.MSMQ://machine/private/queueName k adresování soukromé fronty.|
