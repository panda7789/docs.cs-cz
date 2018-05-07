---
title: IMetaDataImport::GetParamProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95850448504fd863f2726a7fb7574436476a6dc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps – metoda
Získá metadata hodnoty pro parametr odkazuje zadaný ParamDef token.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tk`  
 [v] ParamDef token, který představuje parametr vrátit metadata pro.  
  
 `pmd`  
 [out] Ukazatel na MethodDef token představující metodu, která přebírá parametr.  
  
 `pulSequence`  
 [out] Pořadové číslo pozice parametr v seznamu argumentů metoda.  
  
 `szName`  
 [out] Vyrovnávací paměť pro název parametru.  
  
 `cchName`  
 [v] Požadovaná velikost v široké znaky `szName`.  
  
 `pchName`  
 [out] Vrácený velikost v široké znaky `szName`.  
  
 `pdwAttr`  
 [out] Ukazatel na žádné příznaky atribut spojené s parametrem.  
  
 `pdwCPlusTypeFlag`  
 [out] Ukazatel na příznak určující, který je parametr <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Ukazatel na konstantní řetězec vrácený parametr.  
  
 `pcchValue`  
 [out] Velikost `ppValue` v široké znaky, nebo nula, pokud `ppValue` neobsahuje řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
