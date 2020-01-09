---
title: Vytváření šifrovacích schémat
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 00fff5f346633a9682d75cf6a3be7e8e7d5db7e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706289"
---
# <a name="creating-a-cryptographic-scheme"></a>Vytváření šifrovacích schémat
Kryptografické komponenty .NET Framework mohou být kombinovány pro vytváření různých schémat pro šifrování a dešifrování dat.  
  
 Jednoduché kryptografické schéma pro šifrování a dešifrování dat může určovat následující kroky:  
  
1. Každá strana vygeneruje pár veřejného a privátního klíče.  
  
2. Smluvní strany si vyměňují jejich veřejné klíče.  
  
3. Každá ze smluvních stran generuje tajný klíč pro šifrování TripleDES, například a zašifruje nově vytvořený klíč pomocí veřejného klíče druhého.  
  
4. Každá ze smluvních stran odesílá data do druhé a kombinuje tajný klíč druhé s vlastním tajným klíčem, a to v konkrétním pořadí pro vytvoření nového tajného klíče.  
  
5. Strany pak iniciují konverzaci pomocí symetrického šifrování.  
  
 Vytváření šifrovacího schématu není triviální úloha.
  
## <a name="see-also"></a>Viz také:

- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
