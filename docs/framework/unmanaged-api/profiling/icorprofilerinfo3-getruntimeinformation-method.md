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
ms.openlocfilehash: 5262ba6ef0d2d36372326df24b519072e2aa6fc6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587512"
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
  
#### <a name="parameters"></a>Parametry  
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
