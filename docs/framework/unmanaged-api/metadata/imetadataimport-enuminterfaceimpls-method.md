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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6e4be2e05c573ec93cc23c8dd6eccc834b8b848
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136497"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls – metoda
Vytvoří výčet všech rozhraní implementované zadanou `TypeDef`. 
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [out v] Ukazatel na enumerátor.  
  
 `td`  
 [in] Token TypeDef, jehož MethodDef tokeny představující implementace rozhraní jsou pro provedení výčtu.  
  
 `rImpls`  
 [out] Pole pro ukládání tokenů MethodDef.  
  
 `cMax`  
 [in] Maximální velikost `rImpls` pole.  
  
 `pcImpls`  
 [out] Skutečný počet tokenů vrátil v `rImpls`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` bylo úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné tokeny MethodDef k vytvoření výčtu. V takovém případě `pcImpls` je nastavena na hodnotu nula.|  

## <a name="remarks"></a>Poznámky

Vrátí kolekci výčtu `mdInterfaceImpl` tokeny pro každé rozhraní implementované zadanou `TypeDef`. Rozhraní tokeny jsou vráceny v pořadí, které byly zadány rozhraní (prostřednictvím `DefineTypeDef` nebo `SetTypeDefProps`). Vlastnosti vráceného `mdInterfaceImpl` tokeny, může být dotázán pomocí [getinterfaceimplprops –](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
