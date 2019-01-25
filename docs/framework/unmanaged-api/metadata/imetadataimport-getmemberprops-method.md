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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98d7be5adc81cff09b121265e7d5b5f712122607
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611407"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps – metoda
Získá informace o metadata, včetně názvu, binární podpis a relativní virtuální adresu, <xref:System.Type> odkazuje token metadat zadaného člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `mb`  
 [in] Token, který odkazuje na člen, který chcete získat související metadata pro.  
  
 `pClass`  
 [out] Ukazatel na token metadat, který představuje třídu člena.  
  
 `szMember`  
 [out] Název člena.  
  
 `cchMember`  
 [in] Velikost v širokých znaků `szMember` vyrovnávací paměti.  
  
 `pchMember`  
 [out] Velikost v široké znaky vrácený název.  
  
 `pdwAttr`  
 [out] Žádné příznak hodnoty použité k členu.  
  
 `ppvSigBlob`  
 [out] Ukazatel na binární metadat podpisu člena.  
  
 `pcbSigBlob`  
 [out] Velikost v bajtech `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Ukazatel na relativní virtuální adresu člena.  
  
 `pdwImplFlags`  
 [out] Žádné příznaky implementace spojených se členem.  
  
 `pdwCPlusTypeFlag`  
 [out] Příznak, který označuje <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Hodnota konstanty typu řetězec vrácený tohoto člena.  
  
 `pcchValue`  
 [out] Velikost ve znacích `ppValue`, nebo nula, pokud `ppValue` neobsahuje řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
