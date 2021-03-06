---
title: IMetaDataImport::GetFieldProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 2bd05b49c3d51ac13865997910c99cc0cd5ca2d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491241"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps – metoda
Načte metadata přidružená k poli, na které odkazuje zadaný FieldDef token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mb`  
 pro Token FieldDef, který představuje pole, pro které se mají získat přidružená metadata  
  
 `pClass`  
 mimo Ukazatel na token TypeDef, který představuje typ třídy, do které pole patří.  
  
 `szField`  
 mimo Název pole  
  
 `cchField`  
 pro Velikost vyrovnávací paměti v různých znacích pro *szField*.  
  
 `pchField`  
 mimo Skutečná velikost vrácené vyrovnávací paměti.  
  
 `pdwAttr`  
 mimo Příznaky přidružené k metadatům v poli  
  
 `ppvSigBlob`  
 pro Ukazatel na hodnotu binárních metadat, která popisuje pole.  
  
 `pcbSigBlob`  
 mimo Velikost v bajtech `ppvSigBlob` .  
  
 `pdwCPlusTypeFlag`  
 mimo Příznak, který určuje typ hodnoty pole.  
  
 `ppValue`  
 mimo Konstantní hodnota pro pole.  
  
 `pcchValue`  
 mimo Velikost ve znakech `ppValue` nebo nula, pokud žádný řetězec neexistuje.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
