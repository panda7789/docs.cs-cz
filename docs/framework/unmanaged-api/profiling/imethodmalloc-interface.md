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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969803"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc – rozhraní
Poskytuje metodu, jak přidělit paměť pro nové tělo funkce Microsoft intermediate language (MSIL).  
  
> [!NOTE]
>  `IMethodMalloc` Rozhraní je jednoduché paměti alokátoru. Je možné přidělit paměť, ale nechcete ho zdarma.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alloc – metoda](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Pokusí se přidělit zadanou velikost paměti pro nové tělo funkce jazyka MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 Každý allocator je modulů a zajistí, že tělo funkce bude kladné posunem od báze modulu. Paměť nad základní modul může být účely, proto alokátoru by měla sloužit pouze pro tělo funkce přidělení paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
