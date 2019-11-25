---
title: Události Trasování událostí pro Windows zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1dad042595608a805f978673858acaa5c01130f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974881"
---
# <a name="security-etw-events"></a>Události Trasování událostí pro Windows zabezpečení

Události zabezpečení jsou vyvolány během ověřování silných názvů a při ověřování prostřednictvím technologie Authenticode.  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a>Události StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce. (Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|Obsah|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Začátek ověřování se silným názvem.|  
|`StrongNameVerificationStop_V1`|182|Konec ověřování se silným názvem.|  
  
 V následující tabulce jsou uvedena data události.  
  
|název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|VerificationFlags|Win: UInt32|Příznaky ověřování.|  
|ErrorCode|Win: UInt32|Kód chyby HResult.|  
|FullyQualifiedAssemblyName|Win: UnicodeString|Plně kvalifikovaný název sestavení.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a>Události AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Obsah|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Začátek ověřování Authenticode|  
|`AuthenticodeVerificationStop_V1`|184|Konec ověřování Authenticode|  
  
 V následující tabulce jsou uvedena data události.  
  
|název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|VerificationFlags|Win: UInt32|Příznaky ověřování.|  
|ErrorCode|Win: UInt32|Kód chyby HResult.|  
|ModulePath nastavte|Win: UnicodeString|Cesta k modulu|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
