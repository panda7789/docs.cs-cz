---
title: Prostředky operačního systému požadované službou WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 828d656370efd7638fa4cf367b84ee7b316b89bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100934"
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
