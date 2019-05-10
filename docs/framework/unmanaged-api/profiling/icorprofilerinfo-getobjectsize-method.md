---
title: ICorProfilerInfo::GetObjectSize – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fb69670d06230c06f1ffc2793b6fa9d45191ca77
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606526"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize – metoda
Získá velikost zadaného objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 [in] ID objektu.  
  
 `pcSize`  
 [out] Ukazatel objekt velikost v bajtech.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Tato metoda je zastaralá. Vrátí COR_E_OVERFLOW pro objekty větší než 4GB na 64bitových platformách. Použití [icorprofilerinfo4::getobjectsize2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) metoda místo.  
  
 Různé objekty stejné typy často mají stejnou velikost. Některé typy, například pole nebo řetězce, ale může mít jinou velikost pro každý objekt.  
  
 Velikost vrácené `GetObjectSize` způsob neobsahuje žádné zarovnání odsazení, který se může zdát, jakmile je objekt na haldě uvolňování paměti. Pokud používáte `GetObjectSize` metoda pro přechod z objektu na haldě uvolňování paměti kolekce přidat zarovnání odsazení ručně, podle potřeby.  
  
- Na Windows 32-bit COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 a COR_PRF_GC_GEN_2 používat 4bajtové zarovnání a COR_PRF_GC_LARGE_OBJECT_HEAP používá zarovnání 8 bajtů.  
  
- Na Windows 64-bit zarovnání je vždy 8 bajtů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
