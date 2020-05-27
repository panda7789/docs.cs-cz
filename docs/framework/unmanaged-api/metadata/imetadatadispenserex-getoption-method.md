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
ms.openlocfilehash: 832adacac4a6df9ccf21578538a1c557150f3ba1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008778"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption – metoda
Získá hodnotu zadané možnosti pro aktuální obor metadat. Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 pro Ukazatel na identifikátor GUID, který určuje možnost, která má být načtena. Seznam podporovaných identifikátorů GUID najdete v části s poznámkami.  
  
 `pValue`  
 mimo Hodnota vrácené možnosti. Typ této hodnoty bude varianta zadaného typu možnosti.  
  
## <a name="remarks"></a>Poznámky  
 V následujícím seznamu jsou uvedeny identifikátory GUID, které jsou pro tuto metodu podporovány. Popisy naleznete v tématu [IMetaDataDispenserEx:: SetOption –](imetadatadispenserex-setoption-method.md) metoda. Pokud není `optionId` v tomto seznamu, tato metoda vrátí hodnotu HRESULT `E_INVALIDARG` , což značí nesprávný parametr.  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck  
  
- MetaDataNotificationForTokenMovement  
  
- MetaDataSetENC  
  
- MetaDataErrorIfEmitOutOfOrder  
  
- MetaDataGenerateTCEAdapters  
  
- MetaDataLinkerOptions  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataDispenserEx – rozhraní](imetadatadispenserex-interface.md)
- [IMetaDataDispenser – rozhraní](imetadatadispenser-interface.md)
