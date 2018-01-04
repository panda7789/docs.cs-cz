---
title: "Vytváření šifrovacích schémat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b0aabdc9150aea73ad9078b0e9ee92b2abd03e17
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="creating-a-cryptographic-scheme"></a>Vytváření šifrovacích schémat
K vytvoření různých schémat k šifrování a dešifrování dat mohou být kombinovány kryptografické součásti rozhraní .NET Framework.  
  
 Jednoduchý kryptografických sloužící k šifrování a dešifrování dat může určit následující kroky:  
  
1.  Každá strana vygeneruje pár veřejného a privátního klíče.  
  
2.  Strany vyměňují své veřejné klíče.  
  
3.  Každá strana vygeneruje tajný klíč pro šifrování TripleDES, například a nově vytvořený klíč zašifruje pomocí veřejného klíče druhé strany.  
  
4.  Každá strana odesílá data na druhý a kombinují jiný tajný klíč s vlastní, v konkrétní pořadí, chcete-li vytvořit nový tajný klíč.  
  
5.  Strany poté zahájit konverzaci pomocí symetrického šifrování.  
  
 Vytvoření kryptografických schémat není jednoduchý úkol. Další informace o používání šifrování najdete v tématu Kryptografie v dokumentaci platformy sady SDK na http://msdn.microsoft.com/library.  
  
## <a name="see-also"></a>Viz také  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
