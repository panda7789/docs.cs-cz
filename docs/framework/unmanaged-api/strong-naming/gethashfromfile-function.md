---
title: GetHashFromFile – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5774b7cdcfedfc407b626ab5052f5b4a77461e9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049385"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile – funkce
Vygeneruje hodnotu hash nad obsah zadaného souboru.  
  
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
  
## <a name="parameters"></a>Parametry  
 `szFilePath`  
 [in] Název souboru, který má hodnotu hash.  
  
 `piHashAlg`  
 [out v] Algoritmus použitého při generování hodnoty hash. Platné algoritmy jsou těmi definovanými ve Win32 rozhraní CryptoAPI. Pokud `piHashAlg` je nastavena na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.  
  
 `pbHash`  
 [out] Bajtové pole obsahující generované hodnoty hash.  
  
 `cchHash`  
 [in] Maximální velikost vyrovnávací paměti, která `pbHash` odkazuje na.  
  
 `pchHash`  
 [out] Velikost v bajtech, vráceného `pbHash`.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je stejná jako [gethashfromfilew –](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), s tím rozdílem, že je název specifikace souboru ANSI místo Unicode.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetHashFromFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
