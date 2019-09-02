---
title: Provedení obnovení
ms.date: 03/30/2017
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
ms.openlocfilehash: fe0e096c31b2ef62a1bc50d40c87f2e12c87343f
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205881"
---
# <a name="performing-recovery"></a>Provedení obnovení
Správce prostředků usnadňuje řešení trvalý zařazení v transakci tím, že reenlisting účastník transakce po selhání prostředku.  
  
## <a name="the-recovery-process"></a>Proces obnovení  
 Trvale zařazení prostředek do (popsaného implementace <xref:System.Transactions.IEnlistmentNotification> rozhraní), může být později oprávněné pro obnovení, měli byste zavolat <xref:System.Transactions.Transaction.EnlistDurable%2A> metody. Kromě toho je třeba zadat <xref:System.Transactions.Transaction.EnlistDurable%2A> metodu se identifikátor správce prostředků ( <xref:System.Guid>) používané při konzistentně popisek účastník transakce v případě selhání prostředku. Z <xref:System.Guid> tohoto důvodu by měl být poskytnutý počátečnímu volání metody zařazení totožný s parametrem *identifikátor resourceManagerIdentifier* ve <xref:System.Transactions.TransactionManager.Reenlist%2A> volání během obnovování. V opačném <xref:System.Transactions.TransactionException> je vyvolána. Další informace o trvalých zařazení najdete v tématu [zařazení prostředků jako účastníků v transakci](enlisting-resources-as-participants-in-a-transaction.md) .  
  
 Ve fázi prepare (fáze 1) protokolu 2PC, jakmile obdrží implementace správce trvalý prostředků <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> oznámení, jeho záznam připravit ji by měl protokolu v průběhu této fáze. Záznam by měl obsahovat všechny informace, které jsou nezbytné pro dokončení transakce na potvrzení. K přípravné záznamu lze později během obnovy přejít <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> načtením vlastnosti zpětného volání *preparingEnlistment* . Není třeba provádět v rámci záznamu protokolování <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> jako správce prostředků metodu to lze provést v pracovní podproces.  
  
 Proces obnovení se skládá ze dvou kroků:  
  
### <a name="step-1---reenlist"></a>Krok 1 – ReEnlist  
 Správce prostředků prozkoumá záznamu Příprava informací pro každou zařazení, který je nejistoty. To lze provést prostřednictvím zkoušení <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> vlastnost <xref:System.Transactions.PreparingEnlistment> zpětné volání, které je předán správce prostředků v <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> oznámení během fáze 1.  
  
 Pro každou takové zařazení zkontroluje, vyvolá <xref:System.Transactions.TransactionManager.Reenlist%2A> na správce transakcí. Tato metoda předává na jedinečné <xref:System.Guid> který identifikuje správce prostředků, stejně jako informace zařazení v bajtové pole. Nový <xref:System.Transactions.Enlistment> je vrácen objekt. Pokud reenlistment selže s výjimku, bude nutné správce prostředků se zkuste připojit znovu později.  
  
 By měla volat pouze <xref:System.Transactions.TransactionManager.Reenlist%2A> metodu po restartování správce prostředků z selhání. Kromě toho by měla pouze reenlist nepřeloženého transakce zapsané podle správce prostředků během počátečního Prepare fáze dvoufázového potvrzení. Jakékoli pokusy o tuto metodu lze volat v neplatný časech může chybné výsledkům.  
  
 Když je účastník reenlisted pomocí této metody metody fáze 2 <xref:System.Transactions.IEnlistmentNotification> která odpovídají výstup transakce (to znamená, <xref:System.Transactions.IEnlistmentNotification.Commit%2A> , <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> nebo <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> ) se nazývají podle potřeby.  
  
### <a name="step-2---completing-the-recovery"></a>Krok 2 – dokončení obnovení  
 Po dokončení všech reenlistments volá správce prostředků <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> metody. Tato metoda se dokončí obnovení a informuje správce transakcí, aby správce prostředků nemá žádné další transakce nejistoty. Tímto způsobem správce prostředků zaručuje, že nebude volat <xref:System.Transactions.TransactionManager.Reenlist%2A> metoda znovu.  
  
 Správce prostředků není nutné před zapsání v nové transakce vyřešit všechny transakce nejistoty. První krok lze provést kdykoli poté, co správce prostředků vytvoří relaci se správcem transakcí, ale po <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> vyvolání (krok 2); krok 1 nelze provést znovu. Krok 2 lze opakovat bez dopadu výsledku transakcí více než jednou.
