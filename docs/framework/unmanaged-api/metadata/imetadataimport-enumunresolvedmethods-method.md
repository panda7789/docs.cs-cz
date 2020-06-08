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
ms.openlocfilehash: c991c0af845bc6825db6b3bf258fe0809d5db804
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503690"
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
 pro Maximální velikost `rMethods` pole.  
  
 `pcTokens`  
 mimo Počet vrácených tokenů memberDef či `rMethods` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods`úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné tokeny k vytvoření výčtu. V takovém případě `pcTokens` je nula.|  
  
## <a name="remarks"></a>Poznámky  
 Nerozpoznaná metoda je taková, která je deklarovaná, ale není implementovaná. Metoda je obsažena ve výčtu, pokud je metoda označena `miForwardRef` a buď `mdPinvokeImpl` nebo `miRuntime` je nastavena na hodnotu nula. Jinými slovy, nerozpoznaná metoda je metoda třídy, která je označena, `miForwardRef` ale která není implementována v nespravovaném kódu (prostřednictvím PInvoke), ani implementována interně samotným modulem runtime.  
  
 Výčet vylučuje všechny metody, které jsou definovány buď v oboru modulu (Globals), nebo v rozhraních nebo abstraktních třídách.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
