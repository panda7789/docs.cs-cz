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
ms.openlocfilehash: cac5aaa7ed13b6a48b36ad550da8b73d0deb2ee7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491040"
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
 pro Velikost v různých znacích `szProperty` .  
  
 `pchProperty`  
 mimo Počet znaků vrácených v rámci `szProperty` .  
  
 `pdwPropFlags`  
 mimo Ukazatel na libovolný příznak atributu aplikovaný na vlastnost. Tato hodnota je Bitová maska z výčtu [CorPropertyAttr –](corpropertyattr-enumeration.md) .  
  
 `ppvSig`  
 mimo Ukazatel na podpis metadat vlastnosti.  
  
 `pbSig`  
 mimo Počet vrácených bajtů `ppvSig` .  
  
 `pdwCPlusTypeFlag`  
 mimo Příznak určující typ konstanty, která je výchozí hodnotou vlastnosti. Tato hodnota pochází z výčtu CorElementType –.  
  
 `ppDefaultValue`  
 mimo Ukazatel na bajty, které ukládají výchozí hodnotu pro tuto vlastnost.  
  
 `pcchDefaultValue`  
 mimo Velikost v různých znacích `ppDefaultValue` , pokud `pdwCPlusTypeFlag` je ELEMENT_TYPE_STRING; jinak tato hodnota není relevantní. V takovém případě `ppDefaultValue` je délka odvozena od typu, který je určen pomocí `pdwCPlusTypeFlag` .  
  
 `pmdSetter`  
 mimo Ukazatel na token MethodDef, který představuje metodu set přístupového objektu pro vlastnost.  
  
 `pmdGetter`  
 mimo Ukazatel na token MethodDef, který představuje metodu Get přístup k vlastnosti.  
  
 `rmdOtherMethod`  
 mimo Pole tokenů MethodDef, které představuje jiné metody přidružené k vlastnosti.  
  
 `cMax`  
 pro Maximální velikost `rmdOtherMethod` pole. Pokud nezadáte pole dostatečně velké pro uložení všech metod, budou vynechána bez upozornění.  
  
 `pcOtherMethod`  
 mimo Počet tokenů MethodDef vrácených v `rmdOtherMethod` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
