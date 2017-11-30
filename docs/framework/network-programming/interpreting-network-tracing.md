---
title: "Interpretace trasování sítě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: deb191f18bda5b00ef4a967f50e8e983289882a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="interpreting-network-tracing"></a>Interpretace trasování sítě
Pokud je povoleno sledování sítě, můžete použít trasování pro zachycení volání vaše aplikace provede na různých <xref:System.Net> třídy členy. Výstup z těchto volání může být podobná následující příklady.  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 V předchozím příkladu [588] je jedinečný identifikátor pro aktuální vlákno. (4357) a (4387) jsou časová razítka představující počet milisekund, po které uplynuly od spuštění aplikace. Data následující časové razítko zobrazují aplikace vstupující do a vystupující metodu **Socket.Send**. Objekt provádění **odeslat** metoda má 33574638 jako svůj jedinečný identifikátor. Konec trasování metoda obsahuje vrácenou hodnotu (61 v předchozím příkladu).  
  
 Trasování sítě můžete zaznamenat síťový provoz, který se odesílá z nebo přijímá vaše aplikace využívá protokoly na úrovni aplikace jako je například protokol HTTP (Hypertext Transfer). Tato data se dají zachytit jako text a volitelně hexadecimální data. Hexadecimální dat je k dispozici, když zadáte **includehex** jako hodnotu **tracemode** atribut. (Podrobné informace o tento atribut najdete v tématu [postupy: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) Následující příklad trasování byla generována pomocí **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Vynechat hexadecimální data, zadejte **protocolonly** hodnotu **tracemode** atribut. Následující příklad ukazuje trasování při **protocolonly** je zadán.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Viz také  
 [Povolení trasování sítě](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Postupy: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)  
 [Trasování sítě v rozhraní .NET Framework](../../../docs/framework/network-programming/network-tracing.md)
