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
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177722"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption – metoda
Získá hodnotu zadané možnosti pro aktuální obor metadat. Tato možnost určuje, jak jsou zpracována volání aktuálního oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 [v] Ukazatel na identifikátor GUID, který určuje možnost, která má být načtena. Seznam podporovaných identifikátorů GUID naleznete v části Poznámky.  
  
 `pValue`  
 [out] Hodnota vrácené možnosti. Typ této hodnoty bude variantou typu zadané možnosti.  
  
## <a name="remarks"></a>Poznámky  
 V následujícím seznamu jsou uvedeny identifikátory GUID, které jsou pro tuto metodu podporovány. Popisy naleznete v metodě [IMetaDataDispenserEx::SetOption.](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) Pokud `optionId` není v tomto seznamu, tato `E_INVALIDARG`metoda vrátí HRESULT , označující nesprávný parametr.  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck  
  
- MetaDataNotificationForTokenMovement  
  
- MetaDatasetENC  
  
- MetaDataErrorIfEmitOutOfOrder  
  
- Adaptéry MetaDataGenerateTCE  
  
- Možnosti metadatalinkeru  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
