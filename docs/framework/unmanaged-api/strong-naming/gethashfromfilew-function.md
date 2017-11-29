---
title: "GetHashFromFileW – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFileW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFileW
helpviewer_keywords: GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c19047f03279b1284ea8b5b8f99785cfaff5146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW – funkce
Generuje součet hash přes obsah soubor určený touto řetězec znaků Unicode.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::gethashfromfilew –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [v] Unicode název souboru, který se hodnota hash.  
  
 `piHashAlg`  
 [ve out] Algoritmus použitý při generování hodnoty hash. Platný algoritmy jsou definované rozhraní CryptoAPI Win32. Pokud `piHashAlg` je nastaven na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.  
  
 `pbHash`  
 [out] Bajtové pole obsahující generované hodnoty hash.  
  
 `cchHash`  
 [v] Maximální velikost vyrovnávací paměti, na kterou odkazuje `pbHash`.  
  
 `pchHash`  
 [out] Velikost v bajtech z `pbHash`.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je stejný jako [gethashfromfile –](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)kromě toho, že zadání názvu souboru je Unicode místo ANSI.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Gethashfromfilew – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [Gethashfromfile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [Iclrstrongname – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
