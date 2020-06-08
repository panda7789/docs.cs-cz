---
title: IMethodMalloc – rozhraní
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 12b97b28383eb7c39f20ee0e88f55d48e60ad956
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494096"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc – rozhraní
Poskytuje metodu pro přidělení paměti pro nové tělo funkce jazyka MSIL (Microsoft Intermediate Language).  
  
> [!NOTE]
> `IMethodMalloc`Rozhraní je jednoduchý Alokátor paměti. Umožňuje přidělit paměť, ale neuvolňuje ji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[Alloc – metoda](imethodmalloc-alloc-method.md)|Pokusí se přidělit určenou velikost paměti pro nové tělo funkce jazyka MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 Každé přidělování je specifické pro modul a zajišťuje, aby tělo funkce bylo kladné posun od základu modulu. Paměť nad základem modulu může být úžasné, takže k přidělení paměti pro tělo funkce by se mělo použít přidělování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
