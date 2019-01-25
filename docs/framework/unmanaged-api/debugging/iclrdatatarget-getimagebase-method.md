---
title: ICLRDataTarget::GetImageBase – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ef46c066512caac93f5f0cb189152d2cac6dada
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633840"
---
# <a name="iclrdatatargetgetimagebase-method"></a>ICLRDataTarget::GetImageBase – metoda
Získá adresu základní paměti zadané bitové kopie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `imagePath`  
 [in] Název souboru obrázku, včetně jeho cesty.  
  
 `baseAddress`  
 [out] Ukazatel na CLRDATA_ADDRESS, která ukládá adresu základní Image.  
  
## <a name="remarks"></a>Poznámky  
 Název souboru obrázku může nebo nemusí mít cestu. Pokud je zadána cesta, odpovídající se provádí na celou cestu. v opačném případě odpovídající se provádí pouze na název souboru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
