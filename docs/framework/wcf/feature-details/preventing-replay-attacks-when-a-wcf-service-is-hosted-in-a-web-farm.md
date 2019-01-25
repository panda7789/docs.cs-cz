---
title: Prevence útoků formou opakovaného přehrávání zprávy, když je služba WCF hostovaná ve webové farmě
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: b0e52624ef4483672abd8cd0995dbc2e58f95ca1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684863"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Prevence útoků formou opakovaného přehrávání zprávy, když je služba WCF hostovaná ve webové farmě
Při použití zabezpečení zpráv WCF zabrání opakované útoky vytvořením hodnotu NONCE z příchozí zprávy a kontrola vnitřní `InMemoryNonceCache` jestli generované hodnoty NONCE je k dispozici. Pokud je zpráva se zahodí jako opětovného přehrání. Když služba WCF je hostovaná ve webové farmě, od té doby `InMemoryNonceCache` nesdílí mezi uzly ve webové farmě, služba je ohrožen útoky opakováním.  Ke zmírnění tohoto scénáře WCF 4.5 poskytuje bod rozšiřitelnosti, který umožňuje implementovat vlastní sdílené mezipaměti NONCE odvozením třídy od abstraktní třídy <xref:System.ServiceModel.Security.NonceCache>.  
  
## <a name="noncecache-implementation"></a>NonceCache Implementation  
 K implementaci sdílené mezipaměti NONCE, odvoďte třídu z <xref:System.ServiceModel.Security.NonceCache> a přepsat <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> a <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> metody. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> zkontroluje, zda určená hodnota NONCE existuje v mezipaměti. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> se pokusí přidat hodnotu NONCE do mezipaměti. Jakmile je implementována třídy, můžete zapojit ji vytvoření instance instance a přiřaďte ho k <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> zjišťování opakování na straně klienta a <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> zjišťování opakování na straně serveru. Není k dispozici žádné předem podporu konfigurace pole pro tuto funkci.  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
