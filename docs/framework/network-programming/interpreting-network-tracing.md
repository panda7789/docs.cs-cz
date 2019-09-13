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
ms.openlocfilehash: 09f77a60255accc3e4b1c4fa5ea3d7526444e4cb
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894711"
---
# <a name="interpreting-network-tracing"></a>Interpretace trasování sítě
Pokud je povoleno trasování sítě, můžete použít trasování k zaznamenání volání, která vaše aplikace <xref:System.Net> předává různým členům třídy. Výstup z těchto volání může být podobný jako v následujících příkladech.  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 V předchozím příkladu je [588] jedinečný identifikátor aktuálního vlákna. (4357) a (4387) jsou časová razítka označující počet milisekund, které uplynuly od spuštění aplikace. Data následující za časovým razítkem zobrazí aplikaci, která zadává a ukončuje metodu **Socket. Send**. Objekt, který spouští metodu **Send** , má jako jedinečný identifikátor 33574638. Metoda Exit Trace zahrnuje návratovou hodnotu (61 v předchozím příkladu).  
  
 Trasování sítě mohou zachytit síťový provoz, který je odesílán nebo přijat vaší aplikací pomocí protokolů na úrovni aplikace, jako je protokol HTTP (Hypertext Transfer Protocol). Tato data se můžou zachytit jako text a volitelně také hexadecimální data. Šestnáctková data jsou k dispozici při zadání **includehex** jako hodnoty atributu **TraceMode** . (Podrobné informace o tomto atributu naleznete v tématu [How to: Konfigurace trasování](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)sítě.) Následující příklad trasování byl vygenerován pomocí **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Chcete-li vynechat šestnáctková data, zadejte **protocolonly** jako hodnotu pro atribut **TraceMode** . Následující příklad ukazuje trasování při zadání **protocolonly** .  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Viz také:

- [Povolení trasování sítě](../../../docs/framework/network-programming/enabling-network-tracing.md)
- [Postupy: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)
- [Trasování sítě v rozhraní .NET Framework](../../../docs/framework/network-programming/network-tracing.md)
