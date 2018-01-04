---
title: "ICLRPolicyManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager
helpviewer_keywords: ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce37f9beb0901eaf1bc98f5af3f8f99a7fedf1c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanager-interface"></a>ICLRPolicyManager – rozhraní
Poskytuje metody, které umožňují na hostiteli a poté zadejte akce zásad pro případ selhání a vypršení časových limitů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetActionOnFailure – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|Určuje akci zásady, které modul CLR (CLR) má provést, pokud dojde k selhání zadané.|  
|[SetActionOnTimeout – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|Určuje akci zásady, kterou modulu CLR by měla provést, pokud zadaná operace vyprší časový limit.|  
|[SetDefaultAction – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|Určuje akci zásady, kterou modulu CLR má provést, když dojde k zadanou operaci.|  
|[SetTimeout – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|Nastaví hodnotu časového limitu pro danou operaci.|  
|[SetTimeoutAndAction – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|Nastaví hodnotu časového limitu pro zadanou operaci a určí zásad akci, kterou modulu CLR by měla provést, když dojde k operaci.|  
|[SetUnhandledExceptionPolicy – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|Určuje chování modulu CLR, když dojde k neošetřené výjimce.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [EClrOperation – výčet](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
