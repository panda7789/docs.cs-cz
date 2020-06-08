---
title: IMetaDataEmit2::SaveDeltaToStream – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: a8f46871dde4c664a502c261fc882f3badf0f362
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492743"
---
# <a name="imetadataemit2savedeltatostream-method"></a>IMetaDataEmit2::SaveDeltaToStream – metoda
Uloží změny z aktuální relace úprav a pokračování do zadaného datového proudu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIStream`  
 pro Ukazatel rozhraní na zapisovatelný datový proud, do kterého chcete uložit změny.  
  
 `dwSaveFlags`  
 pro Rezervovaný. Tato hodnota musí být nula.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
