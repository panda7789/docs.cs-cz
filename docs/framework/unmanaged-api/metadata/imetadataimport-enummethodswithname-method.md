---
title: IMetaDataImport::EnumMethodsWithName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: 66a09baea1df2e2de418bdce8821672802f1f51f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491729"
---
# <a name="imetadataimportenummethodswithname-method"></a>IMetaDataImport::EnumMethodsWithName – metoda
Vytvoří výčet metod, které mají zadaný název a které jsou definovány typem, na který odkazuje zadaný token TypeDef.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] Ukazatel na enumerátor. Pro první volání této metody musí mít hodnotu NULL.  
  
 `cl`  
 pro Token TypeDef představující typ, jehož metody se mají vytvořit.  
  
 `szName`  
 pro Název, který omezuje rozsah výčtu.  
  
 `rMethods`  
 mimo Pole použité k uložení tokenů MethodDef  
  
 `cMax`  
 pro Maximální velikost `rMethods` pole.  
  
 `pcTokens`  
 mimo Počet tokenů MethodDef vrácených v `rMethods` .  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytváří výčet polí a metod, ale ne vlastností nebo událostí. Na rozdíl od [IMetaDataImport:: enummethods –](imetadataimport-enummethods-method.md) `EnumMethodsWithName` zahodí všechny tokeny metod, které nemají zadaný název.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName`úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné tokeny k vytvoření výčtu. V takovém případě `pcTokens` je nula.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
