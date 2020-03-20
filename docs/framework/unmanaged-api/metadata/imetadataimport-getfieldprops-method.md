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
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177235"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps – metoda
Získá metadata přidružená k poli, na které odkazuje zadaný token FieldDef.  
  
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
 [v] Token FieldDef, který představuje pole získat přidružená metadata.  
  
 `pClass`  
 [out] Ukazatel na token TypeDef, který představuje typ třídy, ke které pole patří.  
  
 `szField`  
 [out] Název pole.  
  
 `cchField`  
 [v] Velikost v široké znaky vyrovnávací paměti pro *szField*.  
  
 `pchField`  
 [out] Skutečná velikost vrácené vyrovnávací paměti.  
  
 `pdwAttr`  
 [out] Příznaky přidružené k metadatům pole.  
  
 `ppvSigBlob`  
 [v] Ukazatel na binární hodnotu metadat, která popisuje pole.  
  
 `pcbSigBlob`  
 [out] Velikost v bajtů `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 [out] Příznak, který určuje typ hodnoty pole.  
  
 `ppValue`  
 [out] Konstantní hodnota pole.  
  
 `pcchValue`  
 [out] Velikost v znaku `ppValue`, nebo nula, pokud neexistuje žádný řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
