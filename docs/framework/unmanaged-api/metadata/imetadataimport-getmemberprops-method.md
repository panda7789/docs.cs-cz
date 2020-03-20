---
title: IMetaDataImport::GetMemberProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177233"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps – metoda
Získá informace uložené v metadatech pro definici zadaného člena, včetně názvu, <xref:System.Type> binárního podpisu a relativní virtuální adresy člena, na který odkazuje zadaný token metadat. Toto je jednoduchá pomocná metoda: pokud *mb* je MethodDef, pak **GetMethodProps** je volána; Pokud *mb* je FieldDef, pak **GetFieldProps** je volána. Podrobnosti naleznete v následujících dalších metodách.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mb`  
 [v] Token, který odkazuje na člena získat přidružená metadata.  
  
 `pClass`  
 [out] Ukazatel na token metadat, který představuje třídu člena.  
  
 `szMember`  
 [out] Jméno člena.  
  
 `cchMember`  
 [v] Velikost v široké znaky `szMember` vyrovnávací paměti.  
  
 `pchMember`  
 [out] Velikost širokých znaků vráceného názvu.  
  
 `pdwAttr`  
 [out] Všechny hodnoty příznaku použité na člena.  
  
 `ppvSigBlob`  
 [out] Ukazatel na podpis binárních metadat člena.  
  
 `pcbSigBlob`  
 [out] Velikost v bajtů `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Ukazatel na relativní virtuální adresu člena.  
  
 `pdwImplFlags`  
 [out] Všechny příznaky implementace metody přidružené k členu.  
  
 `pdwCPlusTypeFlag`  
 [out] Příznak, který <xref:System.ValueType>označuje . Je to jedna `ELEMENT_TYPE_*` z hodnot.
  
 `ppValue`  
 [out] Konstantní hodnota řetězce vrácená tímto členem.  
  
 `pcchValue`  
 [out] Velikost ve znacích `ppValue`, `ppValue` nebo nula, pokud není obsahovat řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
