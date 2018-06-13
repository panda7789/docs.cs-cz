---
title: ICLRIoCompletionManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3abb3e80226da909a0c7eb8e4bf54959557dcbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436264"
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager – rozhraní
Implementuje požadavků metoda zpětného volání, která umožňuje hostiteli upozornit modul CLR (CLR) stavu zadaný vstupně-výstupních operací.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OnComplete – metoda](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|Upozorní CLR stavu požadavek vstupně-výstupních operací, která byla vytvořená pomocí volání [ihostiocompletionmanager::Bind –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metoda.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel implementuje abstraktní dokončení vstupně-výstupních operací pomocí [ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) rozhraní. Modul CLR zadává vstupně-výstupních požadavků prostřednictvím tohoto rozhraní a hostitele upozorní modul runtime výsledek takových požadavků pomocí `ICLRIoCompletionManager` rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IHostIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [IHostThreadPoolManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
