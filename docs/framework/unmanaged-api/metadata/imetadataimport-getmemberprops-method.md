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
ms.openlocfilehash: 83dec9b6ed3b1e538e0f1b7d13a33b8bdbc1cf54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200802"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps – metoda
Získá informace uložené v metadatech pro definici zadaného člena, včetně názvu, binární podpis a relativní virtuální adresu, <xref:System.Type> odkazuje token metadat zadaného člena. Toto je jednoduchý Pomocná metoda: Pokud *mb* typu MethodDef, pak je **getmethodprops –** se nazývá; Pokud *mb* FieldDef, pak je **getfieldprops –** je volána. Informace najdete v těchto jiných metod podrobnosti. 
  
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
  
## <a name="parameters"></a>Parametry  
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
 [out] Příznak, který označuje <xref:System.ValueType>. Představuje jednu ze `ELEMENT_TYPE_*` hodnoty.
  
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
