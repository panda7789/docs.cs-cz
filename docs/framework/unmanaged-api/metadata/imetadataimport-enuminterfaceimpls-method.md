---
title: IMetaDataImport::EnumInterfaceImpls – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 4c819bff50e6644a733374e9863d670d3323ee68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449532"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls – metoda
Vytvoří výčet všech rozhraní implementovaných specifikovaným `TypeDef`. 
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] Ukazatel na enumerátor.  
  
 `td`  
 pro Token TypeDef, jehož tokeny MethodDef představují implementaci rozhraní, mají být vyčísleny.  
  
 `rImpls`  
 mimo Pole použité k uložení tokenů MethodDef  
  
 `cMax`  
 pro Maximální velikost `rImpls` pole  
  
 `pcImpls`  
 mimo Skutečný počet tokenů vrácených v `rImpls`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` byla úspěšně vrácena.|  
|`S_FALSE`|Nejsou k dispozici žádné tokeny MethodDef pro zobrazení výčtu. V takovém případě je `pcImpls` nastavena na hodnotu nula.|  

## <a name="remarks"></a>Poznámky

Výčet vrátí kolekci `mdInterfaceImpl`ch tokenů pro každé rozhraní implementované určeného `TypeDef`. Tokeny rozhraní jsou vraceny v pořadí, ve kterém byla rozhraní zadána (prostřednictvím `DefineTypeDef` nebo `SetTypeDefProps`). K vlastnostem vrácených tokenů `mdInterfaceImpl` se dá dotázat pomocí [getinterfaceimplprops –](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
