---
title: IMetaDataImport::EnumUnresolvedMethods – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: ff9827174e43fd62f3a995e9f477c6fff66b227a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449951"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a>IMetaDataImport::EnumUnresolvedMethods – metoda
Vytvoří výčet tokenů memberDef či představujících nerozpoznané metody v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] Ukazatel na enumerátor. Pro první volání této metody musí mít hodnotu NULL.  
  
 `rMethods`  
 mimo Pole, které se používá k uložení tokenů memberDef či.  
  
 `cMax`  
 pro Maximální velikost `rMethods` pole  
  
 `pcTokens`  
 mimo Počet tokenů memberDef či vrácených v `rMethods`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods` byla úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné tokeny k vytvoření výčtu. V takovém případě je `pcTokens` nula.|  
  
## <a name="remarks"></a>Poznámky  
 Nerozpoznaná metoda je taková, která je deklarovaná, ale není implementovaná. Metoda je obsažena ve výčtu, pokud je metoda označena `miForwardRef` a buď `mdPinvokeImpl` nebo `miRuntime` je nastavena na hodnotu nula. Jinými slovy, nerozpoznaná metoda je metoda třídy, která je označena `miForwardRef`, ale která není implementována v nespravovaném kódu (prostřednictvím PInvoke), ani implementována interně samotným modulem runtime.  
  
 Výčet vylučuje všechny metody, které jsou definovány buď v oboru modulu (Globals), nebo v rozhraních nebo abstraktních třídách.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
