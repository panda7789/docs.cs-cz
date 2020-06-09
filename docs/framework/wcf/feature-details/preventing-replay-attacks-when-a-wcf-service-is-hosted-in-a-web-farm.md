---
title: Prevence útoků formou opakovaného přehrávání zprávy, když je služba WCF hostovaná ve webové farmě
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: 07743795effd3da9a241fd778756dd92d99d78f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596783"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Prevence útoků formou opakovaného přehrávání zprávy, když je služba WCF hostovaná ve webové farmě
Při použití služby Message Security WCF zabráníte útokům pomocí vytvoření hodnoty NONCE z příchozí zprávy a kontrolou interního, `InMemoryNonceCache` abyste zjistili, zda je vygenerovaná hodnota nonce k dispozici. Pokud je, zpráva se zahodí jako opakované přehrání. Když je služba WCF hostovaná ve webové farmě, protože není `InMemoryNonceCache` sdílená napříč uzly ve webové farmě, je tato služba zranitelná vůči útokům přes opakované přehrání.  Chcete-li zmírnit tento scénář, WCF 4,5 poskytuje bod rozšiřitelnosti, který umožňuje implementovat vlastní sdílenou mezipaměť NONCE odvozením třídy z abstraktní třídy <xref:System.ServiceModel.Security.NonceCache> .  
  
## <a name="noncecache-implementation"></a>Implementace NonceCache  
 Chcete-li implementovat vlastní sdílenou mezipaměť NONCE, odvodit třídu z <xref:System.ServiceModel.Security.NonceCache> a <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> Přepsat <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> metody a. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A>zkontroluje, jestli zadaná hodnota NONCE v mezipaměti existuje. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A>se pokusí přidat hodnotu NONCE do mezipaměti. Jakmile je třída implementovaná, připojíte ji pomocí instance instance a přiřadíte ji k <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> detekci opětovného přehrání na straně klienta a <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> k detekci opětovného přehrání na straně serveru. Pro tuto funkci není dostupná žádná podpora konfigurace v krabicích.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení zpráv](message-security-in-wcf.md)
- [SymmetricSecurityBindingElement](../diagnostics/wmi/symmetricsecuritybindingelement.md)
