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
ms.openlocfilehash: de6d46897f3d3266bf708528efd712ca7db8ea4a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438824"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize – metoda
Získá velikost zadaného objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 pro ID objektu  
  
 `pcSize`  
 mimo Ukazatel na velikost objektu v bajtech.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> Tato metoda je zastaralá. Vrátí COR_E_OVERFLOW pro objekty větší než 4GB na 64 platformách. Místo toho použijte metodu [ICorProfilerInfo4:: getobjectsize2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) .  
  
 Různé objekty stejného typu mají často stejnou velikost. Některé typy, například pole nebo řetězce, mohou mít různé velikosti pro každý objekt.  
  
 Velikost vrácená metodou `GetObjectSize` neobsahuje žádné odsazení zarovnání, které se může zobrazit poté, co je objekt v haldě uvolňování paměti. Použijete-li metodu `GetObjectSize` k přechodu z objektu na objekt v haldě uvolňování paměti, podle potřeby přidejte odsazení zarovnání ručně.  
  
- Na 32 Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 a COR_PRF_GC_GEN_2 použít zarovnání na 4 bajty a COR_PRF_GC_LARGE_OBJECT_HEAP používá zarovnání na 8 bajtů.  
  
- V 64 bitových oknech je zarovnání vždy 8 bajtů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
