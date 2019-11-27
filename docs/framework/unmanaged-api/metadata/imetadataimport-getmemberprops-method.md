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
ms.openlocfilehash: bc5bbba2fa4a95955e52a2e083a2097178b5d96a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437517"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps – metoda
Načte informace uložené v metadatech pro zadanou definici člena, včetně názvu, binárního podpisu a relativní virtuální adresy, <xref:System.Type> člena, na který odkazuje zadaný token metadat. Toto je jednoduchá pomocná metoda: Pokud je v *MB* , je zavolána metoda **getmethodprops –** ; Pokud je *MB* FieldDef, pak se zavolá **getfieldprops –** . Podrobnosti najdete v těchto dalších metodách. 
  
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
 pro Token, který odkazuje na člena, aby získal přidružená metadata pro.  
  
 `pClass`  
 mimo Ukazatel na token metadat, který představuje třídu člena.  
  
 `szMember`  
 mimo Název člena.  
  
 `cchMember`  
 pro Velikost v rámci velkých písmen `szMember` vyrovnávací paměti.  
  
 `pchMember`  
 mimo Velikost vráceného názvu v rámci velkých znaků.  
  
 `pdwAttr`  
 mimo Všechny hodnoty příznaků použité u člena.  
  
 `ppvSigBlob`  
 mimo Ukazatel na binární podpis metadat člena.  
  
 `pcbSigBlob`  
 mimo Velikost v bajtech `ppvSigBlob`.  
  
 `pulCodeRVA`  
 mimo Ukazatel na relativní virtuální adresu člena.  
  
 `pdwImplFlags`  
 mimo Jakékoli příznaky implementace metody přidružené ke členu.  
  
 `pdwCPlusTypeFlag`  
 mimo Příznak, který označuje <xref:System.ValueType>. Je to jedna z hodnot `ELEMENT_TYPE_*`.
  
 `ppValue`  
 mimo Hodnota konstanty řetězce vrácená tímto členem.  
  
 `pcchValue`  
 mimo Velikost ve znacích `ppValue`nebo nula, pokud `ppValue` nedrží řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
