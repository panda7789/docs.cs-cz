---
title: GetHashFromHandle – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64c71f1263ae6fd2c72126ec83bda74d5902a311
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469102"
---
# <a name="gethashfromhandle-function"></a>GetHashFromHandle – funkce
Vygeneruje hodnotu hash přes obsah souboru pomocí zadaného popisovače souboru, pomocí zadané hashovacího algoritmu.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::gethashfromhandle –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hFile`  
 [in] Popisovač souboru, který má být mají hodnotu hash.  
  
 `piHashAlg`  
 [out v] Konstanta, která určuje algoritmus hash. Použít nulu pro výchozí algoritmus.  
  
 `pbHash`  
 [out] Vrácená hodnota hash vyrovnávací paměti.  
  
 `cchHash`  
 [in] Požadovaná maximální velikost `pbHash`.  
  
 `pchHash`  
 [out] Velikost v bajtech, vráceného `pbHash`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [GetHashFromHandle – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
