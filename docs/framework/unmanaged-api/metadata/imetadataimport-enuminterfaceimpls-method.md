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
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492184"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls – metoda
Vytvoří výčet všech rozhraní implementovaných zadaným `TypeDef` .
  
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
 pro Maximální délka `rImpls` pole.  
  
 `pcImpls`  
 mimo Skutečný počet tokenů vrácených v `rImpls` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`úspěšně vráceno.|  
|`S_FALSE`|Nejsou k dispozici žádné tokeny MethodDef pro zobrazení výčtu. V takovém případě `pcImpls` je nastavena na hodnotu nula.|  

## <a name="remarks"></a>Poznámky

Výčet vrátí kolekci `mdInterfaceImpl` tokenů pro každé rozhraní implementované zadaným `TypeDef` . Tokeny rozhraní jsou vraceny v pořadí, ve kterém byla rozhraní zadána (prostřednictvím `DefineTypeDef` nebo `SetTypeDefProps` ). Dotazy na vlastnosti vrácených `mdInterfaceImpl` tokenů mohou být dotazovány pomocí [getinterfaceimplprops –](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
