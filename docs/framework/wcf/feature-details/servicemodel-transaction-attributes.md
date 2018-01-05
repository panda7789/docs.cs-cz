---
title: Atributy transakce ServiceModel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aac52f3c542f88adbca40c6cbbdddc734e12903b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="servicemodel-transaction-attributes"></a>Atributy transakce ServiceModel
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytne vlastnosti, na tři standard <xref:System.ServiceModel> atributy, které vám umožní nakonfigurovat chování transakce [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby:  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute>  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute>  
  
## <a name="transactionflowattribute"></a>TransactionFlowAttribute  
 <xref:System.ServiceModel.TransactionFlowAttribute> Atribut určuje ochoty operace v kontraktu služby tak, aby přijímal příchozí transakce z klienta. Atribut obsahuje tento ovládací prvek s následující vlastnost: použijte transakce <xref:System.ServiceModel.TransactionFlowOption> výčtu k určení, zda je příchozí transakce <xref:System.ServiceModel.TransactionFlowOption.Mandatory>, <xref:System.ServiceModel.TransactionFlowOption.Allowed>, nebo <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.  
  
 Toto je pouze atribut, který se vztahuje na externí interakce s klientem služby operací. Atributy popsané v následujících částech se týkají použití transakce v rámci provedení operace.  
  
## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute  
 <xref:System.ServiceModel.ServiceBehaviorAttribute> Atribut určuje chování vnitřní spuštění implementaci kontraktu služby. Vlastnosti specifické pro transakci tohoto atributu:  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A>Určuje, zda chcete provést nedokončené transakci po ukončení relace. Výchozí hodnota pro tuto vlastnost je `false`. Pokud je tato vlastnost `true`a příchozí relace byla korektně vypnout místo ukončování z důvodu sítě nebo klienta chyb, jakékoli nedokončené transakce je úspěšně dokončen. Jinak, pokud je tato vlastnost `false` nebo pokud relace nebyl řádně uzavřen, všechny nedokončené transakce je vrácena zpět při ukončení relace. Pokud je tato vlastnost `true`, příchozí kanál musí být na bázi relací.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A>Určuje, zda je základní instance služby vydané po dokončení transakce. Výchozí hodnota pro tuto vlastnost je `true`. Další příchozí zprávy způsobí, že nová instance základní má být vytvořen, zahození všechny jednotlivé transakce stavu, který může mít uchovávat předchozí instanci. Uvolnění instance služby je interní akce služba má a nemá žádný vliv na všechny existující připojení nebo relací, které mohou mít klienti navázat. Tato funkce je ekvivalentní volání funkce aktivace za běhu, kterou poskytuje modelu COM +. Pokud je vlastnost `true`, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> musí být roven <xref:System.ServiceModel.ConcurrencyMode.Single>. Služba, jinak hodnota vyvolá výjimku neplatná konfigurace ověřování během spouštění.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>Určuje úroveň izolace, který chcete použít pro transakce v rámci služby; Tato vlastnost má jeden z <xref:System.Transactions.IsolationLevel> hodnoty. Pokud vlastnost úroveň izolace místní je jiné než <xref:System.Transactions.IsolationLevel.Unspecified>, úroveň izolace transakce příchozí musí shodovat s nastavením této vlastnosti místní. Jinak se odmítne příchozí transakce a chybu budou odeslána zpět do klienta. Pokud <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je `true`, a neexistují žádné transakce je naplněn, určuje tato vlastnost <xref:System.Transactions.IsolationLevel> hodnotu pro místně vytvořené transakce. Pokud <xref:System.Transactions.IsolationLevel> je nastaven na <xref:System.Transactions.IsolationLevel.Unspecified>, <xref:System.Transactions.IsolationLevel> <xref:System.Transactions.IsolationLevel.Serializable> se používá.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>Určuje časové období, ve kterém musí dokončit v službě vytvořit novou transakci. Pokud je dosaženo této doby a transakce nebyla dokončena, bude přerušeno. <xref:System.TimeSpan> Slouží jako <xref:System.Transactions.TransactionScope> časový limit pro žádné operace, které mají <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> nastavena na `true` a pro novou transakci byla vytvořena. Časový limit je maximální povolená doba od vytvoření transakce pro dokončení fáze 1 dvoufázového protokolu. Hodnota časového limitu, používá je vždy nižší hodnota mezi hodnotami <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> vlastnost a `transactionTimeout` nastavení konfigurace.  
  
## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute  
 <xref:System.ServiceModel.OperationBehaviorAttribute> Atribut určuje chování metody k implementaci služby. Můžete se k označení chování při spuštění konkrétní operace. Vlastnosti tohoto atributu neovlivní popis webové služby popis Language (WSDL) kontrakt služby a jsou čistě prvky [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programovací model, který povolit běžné funkce, které vývojáři jinak mají k implementaci sami.  
  
 Tento atribut má následující vlastnosti specifické pro transakce:  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>Určuje, zda metoda musí být spuštěn v rámci rozsahu aktivní transakce. Výchozí hodnota je `false`. Pokud <xref:System.ServiceModel.OperationBehaviorAttribute> atribut není nastaven pro metodu, také znamená, že metoda nebude provést v transakci. Pokud oboru transakce není potřeba pro operace, všechny transakce, která se nachází v záhlaví zprávy není aktivován a zůstane jako element <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> z <xref:System.ServiceModel.OperationContext>. Pokud oboru transakce je zapotřebí pro operace, zdroj pro transakce je odvozený z jednoho z následujících akcí:  
  
    -   Pokud transakce je plynoucích z klienta, tuto metodu je spustit v oboru transakce vytvořené pomocí této distribuované transakce.  
  
    -   S zařazených do fronty přenosu se používá na transakci použité k dequeue – zpráva. Všimněte si, že používá transakce není sdružení probíhajících transakcí v tom, že nebyl zadán původní odesílatel zprávy.  
  
    -   Vlastní přenos může poskytnout transakce prostřednictvím `TransportTransactionProperty`.  
  
    -   Pokud žádná z výše uvedeného poskytuje externího zdroje pro transakci, nový <xref:System.Transactions.Transaction> bezprostředně před volání metody se vytvoří instance.  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>Určuje, zda je transakce, ve kterém metoda spustí automaticky dokončit, pokud jsou vyvolány žádné neošetřené výjimky. Pokud je tato vlastnost `true`, volání infrastruktury automaticky označí transakce, jako "dokončeno", pokud uživatel metoda vrátí bez způsobení výjimky. Pokud je tato vlastnost `false`, transakce je připojen k instanci a je pouze označena jako "dokončeno", pokud klient volá následné metodu, která je označena tato vlastnost rovna `true`, nebo pokud následné metoda explicitně volá <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>. Nepodařilo se provést některý z těchto výsledků v transakci nikdy se "dokončeno" a omezením pracovní není potvrdit, pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> je nastavena na `true`. Pokud je tato vlastnost nastavena na `true`, je nutné použít kanál s relací a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> musí být nastavena na <xref:System.ServiceModel.InstanceContextMode.PerSession>.
