---
title: "Prevence útoků formou opakovaného přehrávání zprávy, když je služba WCF hostovaná ve webové farmě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ecf37ffb87ddfdd483cebcac3f5892bab43dcd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Prevence útoků formou opakovaného přehrávání zprávy, když je služba WCF hostovaná ve webové farmě
Při použití zabezpečení zpráv WCF brání provedení útoku formou opakovaného vytvořením hodnotu NONCE mimo příchozí zprávy a kontrola interní `InMemoryNonceCache` zobrazíte, když generovaného hodnotu NONCE nachází. Pokud se jedná, zpráva se zahodí jako opětovného přehrání. Pokud služby WCF je hostovaná ve webové farmě, protože `InMemoryNonceCache` není sdílená mezi uzly ve webové farmě, služba je ohrožena útoky opakováním.  Tento scénář zmírnit WCF 4.5 poskytuje bod rozšíření, která umožňuje implementovat vlastní sdílené mezipaměti hodnotu NONCE odvozením třídy od abstraktní třídy <xref:System.ServiceModel.Security.NonceCache>.  
  
## <a name="noncecache-implementation"></a>Implementace NonceCache  
 Pokud chcete implementovat vlastní sdílené mezipaměti hodnotu NONCE, odvození třídy z <xref:System.ServiceModel.Security.NonceCache> a přepsat <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> a <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> metody. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A>zkontroluje, zda zadaný hodnotu NONCE existuje v mezipaměti. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A>se pokusí přidat hodnotu NONCE do mezipaměti. Jakmile se implementuje třídu, můžete spojit se vytváření instancí instance a jeho k přiřazení <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> pro stranu klienta zjišťování opakování a <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> na straně serveru zjišťování opakování. Neexistuje žádné mimo podporu konfigurace políčko pro tuto funkci.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [Prvek SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
