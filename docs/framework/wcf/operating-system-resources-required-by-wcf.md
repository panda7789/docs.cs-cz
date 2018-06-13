---
title: Prostředky operačního systému požadované službou WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 4522f1c59c8f74281a0e197338c6206ab29c229b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498641"
---
# <a name="operating-system-resources-required-by-wcf"></a>Prostředky operačního systému požadované službou WCF
Windows Communication Foundation (WCF) závisí na několika prostředky, které jsou k dispozici v operačním systému funkce. Následující tabulka uvádí tyto prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|Microsoft Distributed Transaction Coordinator služba MSDTC)|Vyžadovaný jako podpora OleTx transakce.|  
|Internet Information Services (IIS)|Vyžaduje, pokud chcete službu IIS použít k hostování vaší aplikace.|  
|Aktivační služba procesů systému Windows (WAS)|Vyžaduje, pokud chcete použít WAS kvůli hostování vaší aplikace.|  
  
## <a name="see-also"></a>Viz také  
 [Požadavky na systém](../../../docs/framework/wcf/wcf-system-requirements.md)
