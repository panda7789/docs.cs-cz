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
ms.openlocfilehash: 3ef3741ef5cec720c2fb285c9aa60d610acc0be9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909386"
---
# <a name="creating-a-cryptographic-scheme"></a>Vytváření šifrovacích schémat
Kryptografické součásti rozhraní .NET Framework mohou být kombinovány pro vytvoření různých schémat k šifrování a dešifrování dat.  
  
 Jednoduché šifrovacích schémat pro šifrování a dešifrování dat například zadat následující kroky:  
  
1. Každá ze smluvních stran generuje pár veřejného a privátního klíče.  
  
2. Smluvní strany vyměňují své veřejné klíče.  
  
3. Každá ze smluvních stran vygeneruje tajný klíč pro šifrování TripleDES, například a nově vytvořený klíč zašifruje pomocí veřejného klíče druhé strany.  
  
4. Každá ze smluvních stran odesílá data do jiné a zkombinuje tajný klíč druhé strany s vlastní, v určitém pořadí, chcete-li vytvořit nový tajný klíč.  
  
5. Smluvní strany souhlasí potom zahájit konverzaci pomocí symetrického šifrování.  
  
 Vytváření šifrovacích schémat není jednoduchý úkol.
  
## <a name="see-also"></a>Viz také:

- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
