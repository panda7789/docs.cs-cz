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
ms.openlocfilehash: 031bfc3d7fcd9f1f04e616e460cb3201813eae55
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616551"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication – funkce
Spustí aplikaci v zadané síťové cestě s použitím zadaných manifestů a dalších aplikačních dat.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
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
 pro Hodnota výčtu [HOST_TYPE](host-type-enumeration.md) , která určuje typ hostitele, který spouští aplikaci.  
  
 `pwzAppFullName`  
 pro Úplný název aplikace, která se spouští.  
  
 `dwManifestPaths`  
 pro Počet cest k manifestu pro aplikaci.  
  
 `ppwzManifestPaths`  
 pro Pole řetězců, z nichž každý Určuje cestu k manifestu pro aplikaci, která se právě spouští.  
  
 `dwActivationData`  
 pro Počet položek aktivačních dat pro aplikaci, která se spouští.  
  
 `ppwzActivationData`  
 pro Pole řetězců, z nichž každá představuje položku aktivační data pro aplikaci, která se spouští.  
  
 `lpProcessInformation`  
 mimo Ukazatel na informace o procesu, ve kterém byla aplikace načtena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
