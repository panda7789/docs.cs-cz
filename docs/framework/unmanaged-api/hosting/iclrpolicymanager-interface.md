---
title: ICLRPolicyManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 631301a10aee96bb00aeda6b0b8695f0aea186a8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703473"
---
# <a name="iclrpolicymanager-interface"></a>ICLRPolicyManager – rozhraní
Poskytuje metody, které umožňují hostiteli určit akce zásad, které mají být provedeny v případě selhání a časových limitů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetActionOnFailure – metoda](iclrpolicymanager-setactiononfailure-method.md)|Určuje akci zásad, kterou by modul CLR (Common Language Runtime) měl provést při výskytu zadaného selhání.|  
|[SetActionOnTimeout – metoda](iclrpolicymanager-setactionontimeout-method.md)|Určuje akci zásad, kterou by měl modul CLR provést po vypršení časového limitu zadané operace.|  
|[SetDefaultAction – metoda](iclrpolicymanager-setdefaultaction-method.md)|Určuje akci zásad, kterou by měl CLR provést, když dojde k zadané operaci.|  
|[SetTimeout – metoda](iclrpolicymanager-settimeout-method.md)|Nastaví hodnotu časového limitu pro zadanou operaci.|  
|[SetTimeoutAndAction – metoda](iclrpolicymanager-settimeoutandaction-method.md)|Nastaví hodnotu časového limitu pro zadanou operaci a určuje akci zásad, kterou by měl CLR provést při výskytu operace.|  
|[SetUnhandledExceptionPolicy – metoda](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|Určuje chování modulu CLR, pokud dojde k neošetřené výjimce.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [EClrFailure – výčet](eclrfailure-enumeration.md)
- [EClrOperation – výčet](eclroperation-enumeration.md)
- [EPolicyAction – výčet](epolicyaction-enumeration.md)
- [ICLRControl – rozhraní](iclrcontrol-interface.md)
