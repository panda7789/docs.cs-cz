---
title: StrongNameGetBlobFromImage – funkce
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b076c39ccf40ca5b613cab94ecc75716158d97a9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780126"
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage – funkce
Získá binární vyjádření této bitové kopie sestavení na adrese zadaná paměťová.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnamegetblobfromimage –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbBase`  
 [in] Adresa paměti pro manifest sestavení pro mapovanou.  
  
 `dwLength`  
 [in] Velikost v bajtech bitové kopie `pbBase`.  
  
 `pbBlob`  
 [in] Vyrovnávací paměť obsahuje binární vyjádření této image.  
  
 `pcbBlob`  
 [out v] Požadovanou maximální velikost v bajtech, `pbBlob`. Po návratu, skutečná velikost v bajtech, z `pbBlob`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Při úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `StrongNameGetBlobFromImage` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameGetBlobFromImage – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [StrongNameGetBlob – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
