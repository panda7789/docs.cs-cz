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
ms.openlocfilehash: e9cbf4551c2f8b183e9e6c37a74b13aff3a19ec1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860966"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc – rozhraní
Poskytuje metodu pro přidělení paměti pro nové tělo funkce jazyka MSIL (Microsoft Intermediate Language).  
  
> [!NOTE]
> Rozhraní `IMethodMalloc` je jednoduché přidělování paměti. Umožňuje přidělit paměť, ale neuvolňuje ji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alloc – metoda](imethodmalloc-alloc-method.md)|Pokusí se přidělit určenou velikost paměti pro nové tělo funkce jazyka MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 Každé přidělování je specifické pro modul a zajišťuje, aby tělo funkce bylo kladné posun od základu modulu. Paměť nad základem modulu může být úžasné, takže k přidělení paměti pro tělo funkce by se mělo použít přidělování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
