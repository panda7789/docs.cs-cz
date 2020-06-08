---
title: IActionOnCLREvent – rozhraní
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: f577e9252d97ec188ff1076fd8340336b16c8257
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504326"
---
# <a name="iactiononclrevent-interface"></a>IActionOnCLREvent – rozhraní
Poskytuje metodu [IActionOnCLREvent –::](iactiononclrevent-onevent-method.md) ICLROnEventManager, která provádí zpětná volání na události, které byly zaregistrovány pomocí volání metody [:: RegisterActionOnEvent –](iclroneventmanager-registeractiononevent-method.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[OnEvent – metoda](iactiononclrevent-onevent-method.md)|Provede zpětné volání pro registrovanou událost.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrEvent – výčet](eclrevent-enumeration.md)
- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [ICLROnEventManager – rozhraní](iclroneventmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
