---
title: "ICLRProbingAssemblyEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRProbingAssemblyEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRProbingAssemblyEnum
helpviewer_keywords: ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31f3bfcb2b70bda952f0e4bb43dd8b0067e6ef1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrprobingassemblyenum-interface"></a>ICLRProbingAssemblyEnum – rozhraní
Poskytuje metody, které umožňují získat zkušební identity sestavení pomocí informace identity je sestavení, která je interní modul CLR (CLR), aniž by museli vytvářet nebo pochopit tuto identitu hostitele.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Get – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|Získá identitu sestavení v zadaném indexu.|  
  
## <a name="remarks"></a>Poznámky  
 Metody, jako [iclrassemblyidentitymanager::getprobingassembliesfromreference –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) vrátit `ICLRProbingAssemblyEnum` instance.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
