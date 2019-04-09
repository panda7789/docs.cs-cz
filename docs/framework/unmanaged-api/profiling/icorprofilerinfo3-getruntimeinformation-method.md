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
ms.openlocfilehash: a13e3e525c7f019e7dc49111b88ac374345830af
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164928"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation – metoda
Poskytuje informace o verzi o common language runtime (CLR), která je právě profilována.  
  
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
  
## <a name="parameters"></a>Parametry  
 `pClrInstanceId`  
 [out] Identifikátor zástupce spuštěné instance modulu CLR v procesu. To je stejný jako `ClrInstanceID` , že sestavy trasování událostí pro Windows (ETW) spouštěcí událost.  
  
 `pRuntimeType`  
 [out] Typ modulu runtime. Tento parametr vrátí `COR_PRF_DESKTOP_CLR` pro desktopovou verzi modulu CLR, nebo `COR_PRF_CORE_CLR` základní verze CLR použít v programu Silverlight.  
  
 `pMajorVersion`  
 [out] Číslo hlavní verze modulu CLR.  
  
 `pMinorVersion`  
 [out] Číslo podverze modulu CLR.  
  
 `pBuildVersion`  
 [out] Číslo verze sestavení CLR.  
  
 `pQFEVersion`  
 [out] Číslo verze modulu CLR, který je přiřazen k aktualizaci softwaru.  
  
 `cchVersionString`  
 [in] Délka ve znacích, vyrovnávací paměti, která `szVersionString` odkazuje na.  
  
 `pcchVersionString`  
 [out] Délka ve znacích, z `szVersionString`.  
  
 `szVersionString`  
 [out] Řetězec verze modulu CLR.  
  
## <a name="remarks"></a>Poznámky  
 Můžete předat hodnotu null pro žádné parametry. Ale `pcchVersionString` nemůže být null. Pokud `szVersionString` má hodnotu null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
