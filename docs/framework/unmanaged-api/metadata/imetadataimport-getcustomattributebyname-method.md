---
title: "IMetaDataImport::GetCustomAttributeByName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetCustomAttributeByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b689c54b5e8d741d32bc941b4e78e6674f15e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetcustomattributebyname-method"></a>IMetaDataImport::GetCustomAttributeByName – metoda
Získá vlastní atribut daného jeho název a vlastníka.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkObj`  
 [v] Metadata token představující objektu, který je vlastníkem vlastních atributů.  
  
 `szName`  
 [v] Název vlastního atributu.  
  
 `ppData`  
 [out] Ukazatel na pole dat, která je hodnota vlastního atributu.  
  
 `pcbData`  
 [out] Velikost v bajtech data v *`ppData`.  
  
## <a name="remarks"></a>Poznámky  
 Je možné definovat více vlastních atributů pro stejného vlastníka; i mohou mít stejný název. Ale `GetCustomAttributeByName` vrátí pouze jedna instance. (`GetCustomAttributeByName` vrátí první instance, který nalezne.) Chcete-li vyhledáte všechny instance vlastních atributů, volejte [imetadataimport::enumcustomattributes –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Imetadataimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
