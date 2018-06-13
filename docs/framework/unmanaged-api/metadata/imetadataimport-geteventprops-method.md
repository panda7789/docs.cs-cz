---
title: IMetaDataImport::GetEventProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ac1ecb73257782888c963082953ed243177a86b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448801"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps – metoda
Získá informace metadat pro událost reprezentována token zadanou událost, včetně deklarující typ, přidat a odebrat metody pro Delegáti a všechny příznaky a další související data.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ev`  
 [v] Metadata události token představující události se získat metadata pro.  
  
 `pClass`  
 [out] Ukazatel na TypeDef token představující třídu, který deklaruje události.  
  
 `szEvent`  
 [out] Název události odkazuje `ev`.  
  
 `pchEvent`  
 [v] Požadovaná délka v široké znaky `szEvent`.  
  
 `pdwEventFlags`  
 [out] Vrácená délka ve znacích široké `szEvent`.  
  
 `ptkEventType`  
 [out] Ukazatel Odkaz TypeRef nebo TypeDef metadata token reprezentující <xref:System.Delegate> typ události.  
  
 `pmdAddOn`  
 [out] Ukazatel na metadata token představující metodu, která přidá obslužné rutiny události.  
  
 `pmdRemoveOn`  
 [out] Ukazatel na metadata token představující metodu, která odebere obslužné rutiny události.  
  
 `pmdFire`  
 [out] Ukazatel na metadata token představující metodu, která vyvolává událost.  
  
 `rmdOtherMethod`  
 [out] Pole tokenu ukazatele na další metody přidružený k události.  
  
 `cMax`  
 [v] Maximální velikost `rmdOtherMethod` pole.  
  
 `pcOtherMethod`  
 [out] Počet tokeny, vrátí se v `rmdOtherMethod`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
