---
title: "IAssemblyName – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName
helpviewer_keywords: IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1d11889ab9db408b6e703bbaec17fd0487f142a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblyname-interface"></a>IAssemblyName – rozhraní
Poskytuje metody pro popisující a práci s jedinečnou identitu sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|Vytvoří kopii bez podstruktury tohoto `IAssemblyName` objektu.|  
|[Finalize – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|To umožňuje `IAssemblyName` objektu k uvolnění prostředků a provádění dalších operací čištění před jeho destruktoru.|  
|[Getdisplayname – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|Získá popisný název sestavení odkazuje toto `IAssemblyName` objektu.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|Získá název sestavení odkazuje toto jednoduché, nezašifrované `IAssemblyName` objektu.|  
|[GetProperty – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|Získá ukazatel na vlastnost odkazuje zadaný `PropertyId`.|  
|[GetVersion – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|Získá informace o verzi pro sestavení odkazuje toto `IAssemblyName` objektu.|  
|[Isequal – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|Určuje, zda je zadané `IAssemblyName` objekt rovná to `IAssemblyName`, podle příznaky zadaný porovnání.|  
|[SetProperty – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|Nastaví hodnotu vlastnosti odkazuje zadaný `PropertyId`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Iassemblyenum – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
