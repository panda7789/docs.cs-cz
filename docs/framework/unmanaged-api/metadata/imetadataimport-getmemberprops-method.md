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
ms.openlocfilehash: 0357444aa8fa38bce5a7175cf6aacfe1a2b2b16e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503637"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps – metoda
Načte informace uložené v metadatech pro zadanou definici člena, včetně názvu, binárního podpisu a relativní virtuální adresy, člena, na <xref:System.Type> který odkazuje zadaný token metadat. Toto je jednoduchá pomocná metoda: Pokud je v *MB* , je zavolána metoda **getmethodprops –** ; Pokud je *MB* FieldDef, pak se zavolá **getfieldprops –** . Podrobnosti najdete v těchto dalších metodách.
  
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
 pro Velikost vyrovnávací paměti v různých znacích `szMember` .  
  
 `pchMember`  
 mimo Velikost vráceného názvu v rámci velkých znaků.  
  
 `pdwAttr`  
 mimo Všechny hodnoty příznaků použité u člena.  
  
 `ppvSigBlob`  
 mimo Ukazatel na binární podpis metadat člena.  
  
 `pcbSigBlob`  
 mimo Velikost v bajtech `ppvSigBlob` .  
  
 `pulCodeRVA`  
 mimo Ukazatel na relativní virtuální adresu člena.  
  
 `pdwImplFlags`  
 mimo Jakékoli příznaky implementace metody přidružené ke členu.  
  
 `pdwCPlusTypeFlag`  
 mimo Příznak označující <xref:System.ValueType> . Je to jedna z `ELEMENT_TYPE_*` hodnot.
  
 `ppValue`  
 mimo Hodnota konstanty řetězce vrácená tímto členem.  
  
 `pcchValue`  
 mimo Velikost ve znacích `ppValue` nebo nula, pokud `ppValue` řetězec nedrží.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
