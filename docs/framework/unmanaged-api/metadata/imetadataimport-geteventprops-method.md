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
ms.openlocfilehash: 138be940c6a03fc58e488e344455946bdb832bab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214517"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps – metoda
Získá informace metadat pro událost reprezentována token zadané události, včetně deklarující typ, přidat a odebrat metody pro delegáty a všechny příznaky a další související data.  
  
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
  
## <a name="parameters"></a>Parametry  
 `ev`  
 [in] Událost metadat token reprezentující události se získat metadata pro.  
  
 `pClass`  
 [out] Ukazatel na token TypeDef představující třídu, která deklaruje událost.  
  
 `szEvent`  
 [out] Název události odkazuje `ev`.  
  
 `pchEvent`  
 [in] Požadovaná délka širokých znaků `szEvent`.  
  
 `pdwEventFlags`  
 [out] Vrácená délka v širokých znaků `szEvent`.  
  
 `ptkEventType`  
 [out] Ukazatel Odkaz TypeRef nebo TypeDef metadat token představující <xref:System.Delegate> typ události.  
  
 `pmdAddOn`  
 [out] Ukazatel na token metadat reprezentující metodu, která přidá obslužné rutiny události.  
  
 `pmdRemoveOn`  
 [out] Ukazatel na token metadat reprezentující metodu, která odebere obslužné rutiny události.  
  
 `pmdFire`  
 [out] Ukazatel na token metadat reprezentující metodu, která vyvolává událost.  
  
 `rmdOtherMethod`  
 [out] Pole ukazatelů token jiným metodám přidružený k události.  
  
 `cMax`  
 [in] Maximální velikost `rmdOtherMethod` pole.  
  
 `pcOtherMethod`  
 [out] Počet tokenů vrátil v `rmdOtherMethod`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
