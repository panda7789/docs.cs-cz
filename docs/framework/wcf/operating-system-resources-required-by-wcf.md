---
title: Prostředky operačního systému požadované službou WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 759ab099066e300484860cf3f91d6d084ba1d339
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527078"
---
# <a name="operating-system-resources-required-by-wcf"></a>Prostředky operačního systému požadované službou WCF
Windows Communication Foundation (WCF) závisí na několika prostředcích, které jsou k dispozici v operačním systému na funkci. V následující tabulce jsou uvedeny tyto prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|Microsoft distribuované transakce koordinátor (MSDTC)|Vyžadovaný jako podpora OleTx transakce.|  
|Internet Information Services (IIS)|Povinné, pokud chcete použít k hostování vaší aplikace služby IIS.|  
|Aktivační služba procesů Windows (WAS)|Povinné, pokud chcete používat WAS k hostování vaší aplikace.|  
  
## <a name="see-also"></a>Viz také:
- [Požadavky na systém](../../../docs/framework/wcf/wcf-system-requirements.md)
