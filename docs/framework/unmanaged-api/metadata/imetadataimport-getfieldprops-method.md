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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04b6c04868efff31253b2d723c5783060382212b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448970"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps – metoda
Získá metadata spojená s polem odkazuje zadaný FieldDef token.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `mb`  
 [v] FieldDef token, který představuje pole, které chcete získat související metadata pro.  
  
 `pClass`  
 [out] Ukazatel na TypeDef token, který představuje typ třídy, která patří pole.  
  
 `szField`  
 [out] Název pole.  
  
 `cchField`  
 [v] Velikost v široké znaky vyrovnávací paměti pro *szField*.  
  
 `pchField`  
 [out] Skutečná velikost vrácený vyrovnávací paměti.  
  
 `pdwAttr`  
 [out] Příznaky přidružená metadata tohoto pole.  
  
 `ppvSigBlob`  
 [v] Ukazatel na hodnotu binární metadata, která popisuje pole.  
  
 `pcbSigBlob`  
 [out] Velikost v bajtech `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 [out] Příznak, který určuje typ hodnoty pole.  
  
 `ppValue`  
 [out] Konstantní hodnota pro pole.  
  
 `pcchValue`  
 [out] Velikost v znaků z `ppValue`, nebo nula, pokud neexistuje žádný řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
