---
title: ICorProfilerInfo3::GetRuntimeInformation – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67e1d20f7faf38fa37083f1a5b1cc0c1060b7a32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation – metoda
Poskytuje informace o verzi o common language runtime (CLR), který je profilovaný.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pClrInstanceId`  
 [out] ID zástupce spuštěné instance CLR v procesu. Je to stejné jako `ClrInstanceID` , sestavy trasování událostí pro událost spuštění systému Windows (ETW).  
  
 `pRuntimeType`  
 [out] Typ modulu runtime. Tento parametr vrátí `COR_PRF_DESKTOP_CLR` pro plochy verzi modulu CLR, nebo `COR_PRF_CORE_CLR` pro základní verzi modulu CLR použít v programu Silverlight.  
  
 `pMajorVersion`  
 [out] Hlavní číslo verze modulu CLR.  
  
 `pMinorVersion`  
 [out] Číslo podverze modulu CLR.  
  
 `pBuildVersion`  
 [out] Číslo verze sestavení CLR.  
  
 `pQFEVersion`  
 [out] Číslo verze modulu CLR, který je přidružen aktualizace softwaru.  
  
 `cchVersionString`  
 [v] Délka ve znacích vyrovnávací paměti, `szVersionString` odkazuje na.  
  
 `pcchVersionString`  
 [out] Délka ve znacích, z `szVersionString`.  
  
 `szVersionString`  
 [out] Řetězec verze CLR.  
  
## <a name="remarks"></a>Poznámky  
 Vám může předat hodnotu null pro libovolný parametr. Ale `pcchVersionString` nemůže být null. Pokud `szVersionString` má hodnotu null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
