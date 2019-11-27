---
title: IMetaDataImport::GetPropertyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 247a2793bf3806f5ee38585d50b4535820dfcb69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437056"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps – metoda
Získá metadata pro vlastnost představovanou zadaným tokenem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `prop`  
 pro Token, který představuje vlastnost, pro kterou se mají vracet metadata  
  
 `pClass`  
 mimo Ukazatel na token TypeDef, který představuje typ, který implementuje vlastnost.  
  
 `szProperty`  
 mimo Vyrovnávací paměť pro uložení názvu vlastnosti.  
  
 `cchProperty`  
 pro Velikost v různých znacích `szProperty`.  
  
 `pchProperty`  
 mimo Počet velkých znaků vrácených v `szProperty`.  
  
 `pdwPropFlags`  
 mimo Ukazatel na libovolný příznak atributu aplikovaný na vlastnost. Tato hodnota je Bitová maska z výčtu [CorPropertyAttr –](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) .  
  
 `ppvSig`  
 mimo Ukazatel na podpis metadat vlastnosti.  
  
 `pbSig`  
 mimo Počet bajtů vrácených v `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 mimo Příznak určující typ konstanty, která je výchozí hodnotou vlastnosti. Tato hodnota pochází z výčtu CorElementType –.  
  
 `ppDefaultValue`  
 mimo Ukazatel na bajty, které ukládají výchozí hodnotu pro tuto vlastnost.  
  
 `pcchDefaultValue`  
 mimo Velikost v mnoha znacích `ppDefaultValue`, pokud je `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING; v opačném případě tato hodnota není relevantní. V takovém případě je délka `ppDefaultValue` odvozena od typu určeného `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 mimo Ukazatel na token MethodDef, který představuje metodu set přístupového objektu pro vlastnost.  
  
 `pmdGetter`  
 mimo Ukazatel na token MethodDef, který představuje metodu Get přístup k vlastnosti.  
  
 `rmdOtherMethod`  
 mimo Pole tokenů MethodDef, které představuje jiné metody přidružené k vlastnosti.  
  
 `cMax`  
 pro Maximální velikost `rmdOtherMethod` pole Pokud nezadáte pole dostatečně velké pro uložení všech metod, budou vynechána bez upozornění.  
  
 `pcOtherMethod`  
 mimo Počet tokenů MethodDef vrácených v `rmdOtherMethod`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
