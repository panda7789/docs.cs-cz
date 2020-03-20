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
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175327"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps – metoda
Získá metadata pro vlastnost reprezentované zadaný token.  
  
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
 [v] Token, který představuje vlastnost vrátit metadata.  
  
 `pClass`  
 [out] Ukazatel na TypeDef token, který představuje typ, který implementuje vlastnost.  
  
 `szProperty`  
 [out] Vyrovnávací paměť pro uložení názvu vlastnosti.  
  
 `cchProperty`  
 [v] Velikost v široké `szProperty`znaky .  
  
 `pchProperty`  
 [out] Počet širokých znaků `szProperty`vrácených v .  
  
 `pdwPropFlags`  
 [out] Ukazatel na všechny příznaky atributů aplikované na vlastnost. Tato hodnota je bitová maska z [corpropertyattr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) výčtu.  
  
 `ppvSig`  
 [out] Ukazatel na podpis metadat vlastnosti.  
  
 `pbSig`  
 [out] Počet vrácených bajtů `ppvSig`v .  
  
 `pdwCPlusTypeFlag`  
 [out] Příznak určující typ konstanty, která je výchozí hodnotou vlastnosti. Tato hodnota je z CorElementType výčtu.  
  
 `ppDefaultValue`  
 [out] Ukazatel na bajty, které ukládají výchozí hodnotu pro tuto vlastnost.  
  
 `pcchDefaultValue`  
 [out] Velikost v širokých `ppDefaultValue`znaků `pdwCPlusTypeFlag` , pokud je ELEMENT_TYPE_STRING; v opačném případě tato hodnota není relevantní. V takovém případě `ppDefaultValue` je délka odvodit z typu, který je určen `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 [out] Ukazatel na token MethodDef, který představuje metodu přístupového objektu set pro vlastnost.  
  
 `pmdGetter`  
 [out] Ukazatel na Token MethodDef, který představuje metodu get accessor pro vlastnost.  
  
 `rmdOtherMethod`  
 [out] Pole Tokeny MethodDef, které představují jiné metody přidružené k vlastnosti.  
  
 `cMax`  
 [v] Maximální velikost `rmdOtherMethod` pole. Pokud neposkytnete pole dostatečně velké pro všechny metody, jsou přeskočeny bez upozornění.  
  
 `pcOtherMethod`  
 [out] Počet tokenů MethodDef vrácených v `rmdOtherMethod`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
