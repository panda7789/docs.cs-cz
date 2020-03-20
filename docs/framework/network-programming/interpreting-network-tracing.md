---
title: Interpretace trasování sítě
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: fd617e152b1e86cc71dd8e3cc8a01f1d2f52c30a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047894"
---
# <a name="interpreting-network-tracing"></a>Interpretace trasování sítě
Pokud je povoleno trasování sítě, můžete použít trasování k <xref:System.Net> zachycení volání aplikace provede na různé členy třídy. Výstup z těchto volání může být podobný následujícím příkladům.  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 V předchozím příkladu [588] je jedinečný identifikátor aktuálního vlákna. (4357) a (4387) jsou časová razítka označující počet milisekund, které uplynuly od spuštění aplikace. Data následující časové razítko zobrazuje aplikace zadání a ukončení metody **Socket.Send**. Objekt provádějící **Send** metoda má 33574638 jako jeho jedinečný identifikátor. Trasování ukončení metody zahrnuje vrácenou hodnotu (61 v předchozím příkladu).  
  
 Trasování sítě mohou zachytit síťový provoz odeslaný nebo přijatý aplikací pomocí protokolů na úrovni aplikace, jako je protokol HTTP (Hypertext Transfer Protocol). Tato data mohou být zachycena jako text a volitelně šestnáctková data. Šestnáctková data jsou k dispozici, pokud zadáte **includehex** jako hodnotu **tracemode** atribut. (Podrobné informace o tomto atributu naleznete v [tématu How to: Configure Network Tracing](how-to-configure-network-tracing.md).) Následující příklad trasování byla generována pomocí **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Chcete-li vynechat šestnáctková data, zadejte **protokolpouze** jako hodnotu pro **tracemode** atribut. Následující příklad ukazuje trasování při **protokoluonly** je zadán.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Viz také

- [Povolení trasování sítě](enabling-network-tracing.md)
- [Postupy: Konfigurace trasování sítě](how-to-configure-network-tracing.md)
- [Trasování sítě v rozhraní .NET Framework](network-tracing.md)
