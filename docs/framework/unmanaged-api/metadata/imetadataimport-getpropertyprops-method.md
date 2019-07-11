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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e83afcf6c872927e614fce33ca96e93f0da4f497
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778870"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps – metoda
Získá metadata pro vlastnost reprezentována zadaného tokenu.  
  
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
 [in] Token, který představuje vrátit metadata pro vlastnost.  
  
 `pClass`  
 [out] Ukazatel, který představuje typ, který implementuje vlastnost token TypeDef.  
  
 `szProperty`  
 [out] Vyrovnávací paměť pro název vlastnosti.  
  
 `cchProperty`  
 [in] Velikost v širokých znaků `szProperty`.  
  
 `pchProperty`  
 [out] Počet širokých znaků, které jsou vráceny v `szProperty`.  
  
 `pdwPropFlags`  
 [out] Ukazatel na libovolný atribut příznaky použité na vlastnost. Tato hodnota je bitová maska z [corpropertyattr –](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) výčtu.  
  
 `ppvSig`  
 [out] Ukazatel na podpis metadat vlastnosti.  
  
 `pbSig`  
 [out] Počet bajtů vrácených v `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [out] Příznak, který určuje typ konstanty, která je výchozí hodnota vlastnosti. Tato hodnota je z corelementtype – výčet.  
  
 `ppDefaultValue`  
 [out] Ukazatel na počet bajtů, které ukládají výchozí hodnota této vlastnosti.  
  
 `pcchDefaultValue`  
 [out] Velikost v širokých znaků `ppDefaultValue`, pokud `pdwCPlusTypeFlag` je ELEMENT_TYPE_STRING; v opačném případě tato hodnota není relevantní. V takovém případě délka `ppDefaultValue` je odvozen od typu určeného `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 [out] Ukazatel na token MethodDef, který představuje metody přístupového objektu set pro vlastnost.  
  
 `pmdGetter`  
 [out] Ukazatel na token MethodDef, který představuje metodu přístupového objektu get pro vlastnost.  
  
 `rmdOtherMethod`  
 [out] Pole MethodDef tokeny, které představují další metody asociované s vlastností.  
  
 `cMax`  
 [in] Maximální velikost `rmdOtherMethod` pole. Pokud nezadáte pole dostatečně velký pro všechny metody, přeskočí se bez upozornění.  
  
 `pcOtherMethod`  
 [out] Počet tokenů MethodDef vrácené v `rmdOtherMethod`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
