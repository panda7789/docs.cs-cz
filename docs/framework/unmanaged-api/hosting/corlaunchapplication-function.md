---
title: CorLaunchApplication – funkce
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9861de733a9acb43c7e2a4b4941f9945fc5f0ba7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758370"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication – funkce
Spustí aplikaci v zadané síťové cestě pomocí zadaných manifestů a dalších dat aplikací.  
  
 Tato funkce se již nepoužívá v rozhraní .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwClickOnceHost`  
 [in] Hodnota [host_type –](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) výčet, který určuje typ hostitele, který se spuštěním aplikace.  
  
 `pwzAppFullName`  
 [in] Celý název aplikace, která se spustí.  
  
 `dwManifestPaths`  
 [in] Počet cesty k manifestu aplikace.  
  
 `ppwzManifestPaths`  
 [in] Pole řetězců, z nichž každý Určuje cestu k manifestu pro aplikaci, která se spustí.  
  
 `dwActivationData`  
 [in] Počet datových položek aktivace pro aplikaci, která se spustí.  
  
 `ppwzActivationData`  
 [in] Pole řetězců, z nichž každý je aktivace položka dat pro aplikace, která se spustí.  
  
 `lpProcessInformation`  
 [out] Ukazatel na informace o procesu, ve kterém se načetl aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
