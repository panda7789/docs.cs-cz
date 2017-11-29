---
title: "Prostředky operačního systému požadované službou WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cfe114e5e044a6aaa1e356194a46b4a46011aa0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="operating-system-resources-required-by-wcf"></a>Prostředky operačního systému požadované službou WCF
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]závisí na několika prostředky, které jsou k dispozici v operačním systému funkce. Následující tabulka uvádí tyto prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|Microsoft Distributed Transaction Coordinator služba MSDTC)|Vyžadovaný jako podpora OleTx transakce.|  
|Internet Information Services (IIS)|Vyžaduje, pokud chcete službu IIS použít k hostování vaší aplikace.|  
|Aktivační služba procesů systému Windows (WAS)|Vyžaduje, pokud chcete použít WAS kvůli hostování vaší aplikace.|  
  
## <a name="see-also"></a>Viz také  
 [Požadavky na systém](../../../docs/framework/wcf/wcf-system-requirements.md)
