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
ms.openlocfilehash: c4e4b163cc783ccd01bc406789f5bf92448c697c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685526"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps – metoda
Získá metadata hodnot pro parametr odkazuje zadaný ParamDef token.  
  
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
 [in] ParamDef token, který představuje parametr a vrátit metadata pro.  
  
 `pmd`  
 [out] Ukazatel na token MethodDef představující metodu, která přebírá parametr.  
  
 `pulSequence`  
 [out] Pořadové číslo pozice parametru v seznamu argumentů metody.  
  
 `szName`  
 [out] Vyrovnávací paměti, která bude uchovávat název parametru.  
  
 `cchName`  
 [in] Požadovaná velikost v širokých znaků `szName`.  
  
 `pchName`  
 [out] Velikost vrácené v širokých znaků `szName`.  
  
 `pdwAttr`  
 [out] Ukazatel na libovolný atribut příznaky spojené s parametrem.  
  
 `pdwCPlusTypeFlag`  
 [out] Ukazatel na příznak určující, který je parametr <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Ukazatel na konstantní řetězec vrácený funkcí parametru.  
  
 `pcchValue`  
 [out] Velikost `ppValue` v široké znaky, nebo nula, pokud `ppValue` neobsahuje řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
