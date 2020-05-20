---
title: ICLRAssemblyReferenceList – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: f1aa40ef868bf6ff7730e01ab66a6fec58af1196
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615875"
---
# <a name="iclrassemblyreferencelist-interface"></a>ICLRAssemblyReferenceList – rozhraní
Spravuje seznam sestavení, která jsou načtena modulem CLR (Common Language Runtime), nikoli hostitelem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IsAssemblyReferenceInList – metoda](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|Získá hodnotu, která označuje, zda zadaný ukazatel odkazuje na sestavení v seznamu.|  
|[IsStringAssemblyReferenceInList – metoda](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|Získá hodnotu, která označuje, zda je zadaný název shodný s názvem sestavení v seznamu.|  
  
## <a name="remarks"></a>Poznámky  
 Voláním metody [ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList –](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) získá ukazatel na instanci `ICLRAssemblyReferenceList` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRAssemblyIdentityManager – rozhraní](iclrassemblyidentitymanager-interface.md)
- [IHostAssemblyStore – rozhraní](ihostassemblystore-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
