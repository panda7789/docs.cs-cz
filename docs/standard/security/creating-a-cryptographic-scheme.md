---
title: Vytváření šifrovacích schémat
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2db6d4229ac777801aff792c86fe0e5e9a1b4994
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964381"
---
# <a name="creating-a-cryptographic-scheme"></a>Vytváření šifrovacích schémat
Kryptografické součásti rozhraní .NET Framework mohou být kombinovány pro vytvoření různých schémat k šifrování a dešifrování dat.  
  
 Jednoduché šifrovacích schémat pro šifrování a dešifrování dat například zadat následující kroky:  
  
1.  Každá ze smluvních stran generuje pár veřejného a privátního klíče.  
  
2.  Smluvní strany vyměňují své veřejné klíče.  
  
3.  Každá ze smluvních stran vygeneruje tajný klíč pro šifrování TripleDES, například a nově vytvořený klíč zašifruje pomocí veřejného klíče druhé strany.  
  
4.  Každá ze smluvních stran odesílá data do jiné a zkombinuje tajný klíč druhé strany s vlastní, v určitém pořadí, chcete-li vytvořit nový tajný klíč.  
  
5.  Smluvní strany souhlasí potom zahájit konverzaci pomocí symetrického šifrování.  
  
 Vytváření šifrovacích schémat není jednoduchý úkol. Další informace o používání kryptografie naleznete v tématu šifrování v dokumentaci Platform SDK na http://msdn.microsoft.com/library.  
  
## <a name="see-also"></a>Viz také:

- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
