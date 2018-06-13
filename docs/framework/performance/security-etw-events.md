---
title: Události Trasování událostí pro Windows zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e02274b63ddf7df42d26621791de0286df9655b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395509"
---
# <a name="security-etw-events"></a>Události Trasování událostí pro Windows zabezpečení
<a name="top"></a> Události zabezpečení jsou vyvolány během ověřování silných názvů a ověření Authenticode.  
  
 Tato kategorie se skládá z následujících událostí:  
  
-   [StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a>StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Počáteční ověřování silných názvů.|  
|`StrongNameVerificationStop_V1`|182|Konec ověřování silných názvů.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|VerificationFlags|Win: UInt32|Příznaky ověření.|  
|Kód chyby|Win: UInt32|Kód chyby HResult.|  
|FullyQualifiedAssemblyName|Win: UnicodeString|Plně kvalifikovaný název.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a>AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Počáteční ověření Authenticode.|  
|`AuthenticodeVerificationStop_V1`|184|Konec Authenticode ověření.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|VerificationFlags|Win: UInt32|Příznaky ověření.|  
|Kód chyby|Win: UInt32|Kód chyby HResult.|  
|ModulePath|Win: UnicodeString|Cesta k modulu.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
