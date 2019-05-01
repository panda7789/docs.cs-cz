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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 864a8a4dd9f96da2fd0e0025848a910b4f8b0a70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985527"
---
# <a name="iactiononclrevent-interface"></a>IActionOnCLREvent – rozhraní
Poskytuje [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodu, která provádí zpětná volání na události, které byly zaregistrovány pomocí volání [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OnEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|Provede zpětné volání pro registrované události.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrEvent – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLROnEventManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
