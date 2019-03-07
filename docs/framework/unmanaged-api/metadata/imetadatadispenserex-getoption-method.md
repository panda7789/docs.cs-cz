---
title: IMetaDataDispenserEx::GetOption – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5512c503d8b4048c613ab88c2b4d9d19cdbb9dca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479023"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption – metoda
Získá hodnotu zadané možnosti pro aktuální obor metadat. Možnost řídí, jak se zpracovává volání na aktuální metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 [in] Ukazatel na identifikátor GUID, který určuje možnost, která se má načíst. Naleznete v části poznámky pro seznam podporovaných identifikátory GUID.  
  
 `pValue`  
 [out] Hodnota vrácená možnost. Typ této hodnoty bude hodnotu typu variant Zadaná možnost typu.  
  
## <a name="remarks"></a>Poznámky  
 Následující seznam uvádí identifikátory GUID, které jsou podporovány pro tuto metodu. Popisy najdete v [imetadatadispenserex::SetOption –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metody. Pokud `optionId` nejsou v tomto seznamu, tato metoda vrátí hodnotu HRESULT `E_INVALIDARG`, která nesprávný parametr.  
  
-   MetaDataCheckDuplicatesFor  
  
-   MetaDataRefToDefCheck  
  
-   MetaDataNotificationForTokenMovement  
  
-   MetaDataSetENC  
  
-   MetaDataErrorIfEmitOutOfOrder  
  
-   MetaDataGenerateTCEAdapters  
  
-   MetaDataLinkerOptions  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
