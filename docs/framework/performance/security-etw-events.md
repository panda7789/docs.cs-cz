---
title: Události Trasování událostí pro Windows zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2ea19c88ff8b854b09ed372b35bf8c45d994585
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583657"
---
# <a name="security-etw-events"></a>Události Trasování událostí pro Windows zabezpečení
<a name="top"></a> Události zabezpečení jsou aktivovány v průběhu ověřování silných názvů a ověření pomocí technologie Authenticode.  
  
 Tato kategorie se skládá z následujících událostí:  
  
- [StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a>StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Začátek ověřování silných názvů.|  
|`StrongNameVerificationStop_V1`|182|Konec ověřování silných názvů.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|Příznaky ověření.|  
|Kód chyby|win:UInt32|Kód chyby HResult.|  
|FullyQualifiedAssemblyName|win:UnicodeString|Plně kvalifikovaný název.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a>AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Bylo zahájeno ověřování Authenticode.|  
|`AuthenticodeVerificationStop_V1`|184|Konec ověření pomocí technologie Authenticode.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|Příznaky ověření.|  
|Kód chyby|win:UInt32|Kód chyby HResult.|  
|ModulePath|win:UnicodeString|Cesta modulu.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
