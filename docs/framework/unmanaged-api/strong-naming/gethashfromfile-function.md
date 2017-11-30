---
title: "GetHashFromFile – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFile
helpviewer_keywords: GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c8e84881822cbafa8c43c3669f7522c390d5c5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromfile-function"></a>GetHashFromFile – funkce
Generuje součet hash přes obsah zadaného souboru.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::gethashfromfile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szFilePath`  
 [v] Název souboru, který se hodnota hash.  
  
 `piHashAlg`  
 [ve out] Algoritmus použitý při generování hodnoty hash. Platný algoritmy jsou definované rozhraní CryptoAPI Win32. Pokud `piHashAlg` je nastaven na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.  
  
 `pbHash`  
 [out] Bajtové pole obsahující generované hodnoty hash.  
  
 `cchHash`  
 [v] Maximální velikost vyrovnávací paměti, `pbHash` odkazuje na.  
  
 `pchHash`  
 [out] Velikost v bajtech vrácený `pbHash`.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je stejný jako [gethashfromfilew –](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)kromě toho, že zadání názvu souboru je ANSI místo kódování Unicode.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Gethashfromfile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [Gethashfromfilew – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [Iclrstrongname – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
