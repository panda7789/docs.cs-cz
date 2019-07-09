---
title: Atributy transakce ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
ms.openlocfilehash: d4b7482431404241577111d8dd3841319b65696e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663700"
---
# <a name="servicemodel-transaction-attributes"></a>Atributy transakce ServiceModel

Windows Communication Foundation (WCF) poskytuje vlastnosti na tři standardní <xref:System.ServiceModel> atributy, které je možné nakonfigurovat chování transakce služby WCF:

- <xref:System.ServiceModel.TransactionFlowAttribute>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>

- <xref:System.ServiceModel.OperationBehaviorAttribute>

## <a name="transactionflowattribute"></a>TransactionFlowAttribute

<xref:System.ServiceModel.TransactionFlowAttribute> Atribut určuje ochotu operace v kontraktu služby tak, aby přijímal příchozí transakce z klienta. Atribut obsahuje tento ovládací prvek s následující vlastnost: Použití transakce <xref:System.ServiceModel.TransactionFlowOption> výčet k určení, zda je příchozí transakce <xref:System.ServiceModel.TransactionFlowOption.Mandatory>, <xref:System.ServiceModel.TransactionFlowOption.Allowed>, nebo <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.

Toto je jediný atribut, který se týká operace služby na externí interakce s klientem. Atributy, které jsou popsané v následujících částech se týkají použití transakcí v rámci provedení operace.

## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute

<xref:System.ServiceModel.ServiceBehaviorAttribute> Atribut určuje chování při spuštění vnitřní implementace kontraktu služby. Vlastnosti specifické pro transakce tohoto atributu patří:

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> Určuje, jestli se má provést nedokončené transakci po zavření relace. Výchozí hodnota této vlastnosti je `false`. Pokud je tato vlastnost `true`a příchozí relace byla řádně vypnout namísto z důvodu sítě nebo klient zavírání chyb, žádné nedokončené transakce je úspěšně dokončena. Jinak, pokud je tato vlastnost `false` nebo pokud relace nebyl řádně uzavřen, žádné nedokončené transakce se vrátí zpět při zavření relace. Pokud je tato vlastnost `true`, příchozí kanál musí být na základě relace.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> Určuje, zda podkladové instance služby je všeobecně dostupné po dokončení transakce. Výchozí hodnota této vlastnosti je `true`. Další příchozí zprávu způsobí, že nové základní instance má být vytvořen, se zahodí některému ze stavů za transakce, která může mít nachází předchozí instanci. Uvolnění instance služby je interní akce služba má a nemá žádný vliv na existující připojení nebo relace, které může mít vytvořené klienty. Tato funkce je ekvivalentní k funkci just-in-time aktivace, které poskytuje modelu COM +. Pokud je vlastnost `true`, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> musí být rovna <xref:System.ServiceModel.ConcurrencyMode.Single>. V opačném případě služba vyvolá výjimku neplatná konfigurace ověřování během spouštění.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> Určuje úroveň izolace použitou pro transakce v rámci služby; Tato vlastnost má jednu z <xref:System.Transactions.IsolationLevel> hodnoty. Pokud vlastnost úrovně izolace místní se něco jiného než <xref:System.Transactions.IsolationLevel.Unspecified>, úroveň izolace příchozí transakce musí shodovat s nastavením této místní vlastnosti. V opačném případě příchozí transakce byl odmítnut a chybu, je odeslána zpět klientovi. Pokud <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je `true`, a žádná transakce je naplněn, určuje tato vlastnost <xref:System.Transactions.IsolationLevel> hodnotu pro místně vytvořené transakce. Pokud <xref:System.Transactions.IsolationLevel> je nastavena na <xref:System.Transactions.IsolationLevel.Unspecified>, <xref:System.Transactions.IsolationLevel> <xref:System.Transactions.IsolationLevel.Serializable> se používá.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> Určuje časové období, ve kterém musí být vytvořené ve službě nové transakce dokončena. Pokud transakce nebyla dokončena, dosažení tentokrát se přeruší. <xref:System.TimeSpan> Slouží jako <xref:System.Transactions.TransactionScope> vypršení časového limitu pro všechny operace, které mají <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> nastavena na `true` a pro které byl vytvořen novou transakci. Časový limit je maximální povolená doba trvání od vytvoření transakce pro dokončení fáze 1 v protokol dvoufázového potvrzení. Hodnota časového limitu je vždy nižší hodnotu mezi <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> vlastnost a `transactionTimeout` nastavení konfigurace.

## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute

<xref:System.ServiceModel.OperationBehaviorAttribute> Atribut určuje chování metody v implementaci služby. Slouží k označení chování při provádění konkrétní operace. Vlastnosti tohoto atributu nemají vliv na popis webové služby WSDL (Description Language) kontraktu služby a jsou čistě prvky programovacího modelu WCF, které umožňují společné funkce, že mají vývojáři jinak provádět sami.

Tento atribut má následující vlastnosti specifické pro transakce:

- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Určuje, zda metoda musí být spuštěn v rámci rozsahu aktivní transakce. Výchozí hodnota je `false`. Pokud <xref:System.ServiceModel.OperationBehaviorAttribute> atribut není nastaven pro metodu, také znamená, že metoda nebude spuštěno v transakci. Pokud obor transakce není vyžadována pro operace, všechny transakce, která je k dispozici v rámci záhlaví zprávy není aktivovaný a zůstane jako prvek sady <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> z <xref:System.ServiceModel.OperationContext>. Pokud obor transakce je potřeba pro operace, zdroj pro transakci je odvozený od jednoho z následujících akcí:

  - Pokud transakce je plynoucí z klienta, metoda je provedena v rámci oboru transakce vytvořené pomocí této distribuované transakce.

  - S zařazených do fronty přenosu se používá transakce použitá k odstranění z fronty zprávu. Všimněte si, že používá transakce není sdružení probíhajících transakcí v tom, že nebyl zadán původní odesílatel zprávy.

  - Vlastní přenosu může poskytnout transakce prostřednictvím `TransportTransactionProperty`.

  - Pokud žádná z výše uvedené poskytuje externího zdroje pro transakci, nový <xref:System.Transactions.Transaction> bezprostředně před volání metody je vytvořena instance.

- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Určuje, zda je transakce, ve kterém metoda je provedena automaticky dokončit, pokud nejsou vyvolány žádné neošetřené výjimky. Pokud je tato vlastnost `true`, volání infrastruktury automaticky označí transakce, jako "dokončeno", pokud uživatel metoda vrátí bez vyvolání výjimky. Pokud je tato vlastnost `false`, transakce je připojen k instanci a označena jako "Dokončená" volá-li klienta následné metodu, která je označena s touto vlastností rovna `true`, nebo pokud následné metoda explicitně volá <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>. Selhání proveďte některý z těchto výsledků v rámci transakce nikdy se "dokončeno" a omezením pracovní není potvrzené, pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> je nastavena na `true`. Pokud je tato vlastnost nastavená na `true`, je nutné použít kanál s relací a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> musí být nastaveno na <xref:System.ServiceModel.InstanceContextMode.PerSession>.
