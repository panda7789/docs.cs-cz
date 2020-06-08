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
ms.openlocfilehash: 3b47d1559300a462ccda42bc88da43f66c1043ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491300"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps – metoda
Získá informace o metadatech události reprezentované zadaným tokenem události, včetně deklarovaného typu, metod přidání a odebrání delegátů a všech příznaků a dalších přidružených dat.  
  
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
 pro Token metadat události představující událost, pro kterou se mají získat metadata  
  
 `pClass`  
 mimo Ukazatel na token TypeDef představující třídu, která deklaruje událost.  
  
 `szEvent`  
 mimo Název události, na kterou odkazuje `ev` .  
  
 `pchEvent`  
 pro Požadovaná délka v různých znacích `szEvent` .  
  
 `pdwEventFlags`  
 mimo Vrácená délka v různých znacích `szEvent` .  
  
 `ptkEventType`  
 mimo Ukazatel na token metadat TypeRef nebo TypeDef představující <xref:System.Delegate> Typ události.  
  
 `pmdAddOn`  
 mimo Ukazatel na token metadat představující metodu, která přidává obslužné rutiny pro událost.  
  
 `pmdRemoveOn`  
 mimo Ukazatel na token metadat představující metodu, která odebírá obslužné rutiny pro událost.  
  
 `pmdFire`  
 mimo Ukazatel na token metadat představující metodu, která vyvolává událost.  
  
 `rmdOtherMethod`  
 mimo Pole ukazatelů na tokeny na jiné metody přidružené k události.  
  
 `cMax`  
 pro Maximální velikost `rmdOtherMethod` pole.  
  
 `pcOtherMethod`  
 mimo Počet tokenů vrácených v `rmdOtherMethod` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
