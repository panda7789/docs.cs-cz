---
title: IMetaDataImport::GetCustomAttributeByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
ms.openlocfilehash: e6921a0f6420546ba1e866e37a7a7cb129a77c67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491456"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a>IMetaDataImport::GetCustomAttributeByName – metoda
Získá vlastní atribut, který je dán jménem a vlastníkem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tkObj`  
 pro Token metadat představující objekt vlastnící vlastní atribut.  
  
 `szName`  
 pro Název vlastního atributu  
  
 `ppData`  
 mimo Ukazatel na pole dat, které je hodnotou vlastního atributu.  
  
 `pcbData`  
 mimo Velikost v bajtech dat vrácených v * `ppData` .  
  
## <a name="remarks"></a>Poznámky  
 Je právní pro stejného vlastníka definovat více vlastních atributů; můžou mít i stejný název. Ale `GetCustomAttributeByName` vrátí jenom jednu instanci. ( `GetCustomAttributeByName` vrátí první instanci, kterou nalezne.) Chcete-li najít všechny instance vlastního atributu, zavolejte metodu [IMetaDataImport:: EnumCustomAttributes –](imetadataimport-enumcustomattributes-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
