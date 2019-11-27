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
ms.openlocfilehash: 3f840154d472dbcea7dfef7ba93e38c80b836734
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447558"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc – rozhraní
Poskytuje metodu pro přidělení paměti pro nové tělo funkce jazyka MSIL (Microsoft Intermediate Language).  
  
> [!NOTE]
> Rozhraní `IMethodMalloc` je jednoduché přidělování paměti. Umožňuje přidělit paměť, ale neuvolňuje ji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alloc – metoda](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Pokusí se přidělit určenou velikost paměti pro nové tělo funkce jazyka MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 Každé přidělování je specifické pro modul a zajišťuje, aby tělo funkce bylo kladné posun od základu modulu. Paměť nad základem modulu může být úžasné, takže k přidělení paměti pro tělo funkce by se mělo použít přidělování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
