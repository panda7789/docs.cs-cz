---
title: "Cert2spc.exe (nástroj pro testování certifikátu vydavatele softwaru)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c720da81c63b612201ede5f648f6861470b25bee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (nástroj pro testování certifikátu vydavatele softwaru)
Nástroj Software Publisher Certificate Test vytvoří certifikát Software Publisher's Certificate (SPC) z jednoho nebo více certifikátů X.509. Nástroj Cert2spc.exe slouží pouze k testování. Platný certifikát SPC lze získat od certifikačního úřadu, například VeriSign nebo Thawte. Další informace o vytváření certifikátů X.509 najdete v tématu [Makecert.exe (nástroj pro vytvoření certifikátu)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|`certN.cer`|Název certifikátu X.509, který má být zahrnut do souboru SPC. Můžete zadat více názvů oddělených mezerami.|  
|`crlN.crl`|Název seznamu odvolání certifikátu, který má být zahrnut do souboru SPC. Můžete zadat více názvů oddělených mezerami.|  
|`outputSPCfile.spc`|Název objektu PKCS #7, který bude obsahovat certifikáty X.509.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří SPC z `myCertificate.cer` a umístí jej do `mySPCFile.spc`.  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 Následující příkaz vytvoří SPC z `oneCertificate.cer` a `twoCertificate.cer`a umístí jej do `mySPCFile.spc`.  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [MakeCert.exe (nástroj pro vytvoření certifikátu)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
