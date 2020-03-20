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
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175496"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls – metoda
Vyjmenovává všechna rozhraní implementovaná zadaným `TypeDef`rozhraním .
  
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
 [dovnitř, ven] Ukazatel na čítač výčtu.  
  
 `td`  
 [v] Token TypeDef, jehož Tokeny MethodDef představující implementace rozhraní mají být uvedeny ve výčtu.  
  
 `rImpls`  
 [out] Pole používané k ukládání tokenů MethodDef.  
  
 `cMax`  
 [v] Maximální délka `rImpls` pole.  
  
 `pcImpls`  
 [out] Skutečný počet tokenů vrácených v `rImpls`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné tokeny MethodDef k výčetu. V takovém `pcImpls` případě je nastavena na nulu.|  

## <a name="remarks"></a>Poznámky

Výčet vrátí kolekci `mdInterfaceImpl` tokenů pro každé rozhraní `TypeDef`implementované zadaným . Tokeny rozhraní jsou vráceny v pořadí, `DefineTypeDef` v `SetTypeDefProps`jakém byla rozhraní zadána (prostřednictvím nebo ). Vlastnosti vrácených `mdInterfaceImpl` tokenů lze dotazovat pomocí [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
