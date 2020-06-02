---
title: Vytváření šifrovacích schémat
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 1478873c1c2dc73ca31c9078e39a3902966bf674
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288417"
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
  
## <a name="see-also"></a>Viz také

- [Kryptografické služby](cryptographic-services.md)
