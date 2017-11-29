---
title: "IMetaDataImport::EnumUnresolvedMethods – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumUnresolvedMethods
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3c7709180e5b7811379c25977f8a8d23b91adb3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumunresolvedmethods-method"></a>IMetaDataImport::EnumUnresolvedMethods – metoda
Vytvoří výčet MemberDef tokeny představující nerozpoznané metody v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [ve out] Ukazatel na enumerátor. Toto musí mít hodnotu NULL pro první volání této metody.  
  
 `rMethods`  
 [out] Pole používá k ukládání MemberDef tokenů.  
  
 `cMax`  
 [v] Maximální velikost `rMethods` pole.  
  
 `pcTokens`  
 [out] Počet MemberDef tokeny, vrátí se v `rMethods`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods`úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné tokenů pro zobrazení výčtu. V takovém případě `pcTokens` je nulová.|  
  
## <a name="remarks"></a>Poznámky  
 Nerozpoznané metoda je ten, který byl deklarován, ale není implementováno. Metoda je součástí výčtu, pokud je označena jako metodu `miForwardRef` a buď `mdPinvokeImpl` nebo `miRuntime` je nastaven na hodnotu nula. Jinými slovy, nerozpoznané metoda je třída metoda, která je označena `miForwardRef` , ale která není implementována v nespravovaném kódu (dosaženo pomocí služby PInvoke) ani interně implementované samotný modul runtime  
  
 Výčet vyloučí všechny metody, které jsou definované v modulu oboru (globals) nebo rozhraní nebo abstraktní třídy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Imetadataimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
