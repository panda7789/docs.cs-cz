---
title: "ICorProfilerInfo::GetObjectSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetObjectSize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9425938042485c4330fe3fbc50cdabde6451b427
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize – metoda
Získá velikost zadaného objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `objectId`  
 [v] ID objektu.  
  
 `pcSize`  
 [out] Ukazatel na objektu velikost v bajtech.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Tato metoda je zastaralá. Vrátí COR_E_OVERFLOW pro objekty větší než 4GB na 64bitových platformách. Použití [icorprofilerinfo4::getobjectsize2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) metoda místo.  
  
 Různé objekty stejné typy často mít stejnou velikost. Některé typy, jako je například pole nebo řetězce, ale může mít různou velikost pro každý objekt.  
  
 Velikost vrácené `GetObjectSize` metoda neobsahuje žádné zarovnání odsazení, který se může zdát po objekt je v haldě kolekce paměti. Pokud použijete `GetObjectSize` metoda pro přechod z objektu na objekt v haldě kolekce paměti přidat zarovnání odsazení ručně, podle potřeby.  
  
-   V systému Windows 32-bit COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 a COR_PRF_GC_GEN_2 používají 4bajtový zarovnání a COR_PRF_GC_LARGE_OBJECT_HEAP používá zarovnání 8 bajtů.  
  
-   Na 64bitovém systému Windows je zarovnání vždy 8 bajtů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
