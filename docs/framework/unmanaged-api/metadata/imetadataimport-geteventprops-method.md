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
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177272"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps – metoda
Získá informace o metadatech pro událost reprezentovanou zadaným tokenem události, včetně deklarujícího typu, metod add and remove pro delegáty a všech příznaků a dalších přidružených dat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [v] Token metadat události představující událost získat metadata pro.  
  
 `pClass`  
 [out] Ukazatel na token TypeDef představující třídu, která deklaruje událost.  
  
 `szEvent`  
 [out] Název události, na kterou `ev`odkazuje .  
  
 `pchEvent`  
 [v] Požadovaná délka v `szEvent`širokých znaků .  
  
 `pdwEventFlags`  
 [out] Vrácená délka v `szEvent`široké znaky .  
  
 `ptkEventType`  
 [out] Ukazatel na token metadat TypeRef nebo TypeDef <xref:System.Delegate> představující typ události.  
  
 `pmdAddOn`  
 [out] Ukazatel na token metadat představující metodu, která přidává obslužné rutiny pro událost.  
  
 `pmdRemoveOn`  
 [out] Ukazatel na token metadat představující metodu, která odebere obslužné rutiny pro událost.  
  
 `pmdFire`  
 [out] Ukazatel na token metadat představující metodu, která vyvolává událost.  
  
 `rmdOtherMethod`  
 [out] Pole tokenu ukazatele na jiné metody přidružené k události.  
  
 `cMax`  
 [v] Maximální velikost `rmdOtherMethod` pole.  
  
 `pcOtherMethod`  
 [out] Počet tokenů vrácených `rmdOtherMethod`v .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
