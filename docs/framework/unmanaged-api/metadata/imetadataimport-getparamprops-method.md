---
title: IMetaDataImport::GetParamProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: bb73ccdd9eee4b5a655a56b5d6757e0c6003fbc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437122"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps – metoda
Načte hodnoty metadat pro parametr, na který odkazuje zadaný ParamDef token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 pro Token ParamDef, který představuje parametr pro vrácení metadat.  
  
 `pmd`  
 mimo Ukazatel na token MethodDef představující metodu, která přijímá parametr.  
  
 `pulSequence`  
 mimo Pořadové místo parametru v seznamu argumentů metody.  
  
 `szName`  
 mimo Vyrovnávací paměť pro uložení názvu parametru.  
  
 `cchName`  
 pro Požadovaná velikost v různých znacích `szName`.  
  
 `pchName`  
 mimo Vrácená velikost v různých znacích `szName`.  
  
 `pdwAttr`  
 mimo Ukazatel na libovolný příznak atributu přidružený k parametru. Toto je Bitová maska `CorParamAttr` hodnot.  
  
 `pdwCPlusTypeFlag`  
 mimo Ukazatel na příznak určující, že parametr je <xref:System.ValueType>.  
  
 `ppValue`  
 mimo Ukazatel na konstantní řetězec vrácený parametrem.  
  
 `pcchValue`  
 mimo Velikost `ppValue` v rámci velkých znaků nebo nula, pokud `ppValue` nedrží řetězec.  
  
## <a name="remarks"></a>Poznámky

Hodnoty sekvence v `pulSequence` začínají hodnotou 1 pro parametry. Návratová hodnota má pořadové číslo 0.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
