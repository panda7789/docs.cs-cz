---
title: IMetaDataEmit::GetSaveSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d9a65f76aed00e2b848f8603f1fee4d6acc91f99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize – metoda
Získá binární odhadovanou velikost sestavení a jeho metadata v aktuálním oboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fSave`  
 [v] Hodnota [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) výčtu, která určuje, zda chcete-li získat přesné nebo přibližnou velikost. Jsou platné pouze tří hodnot: cssAccurate, cssQuick a cssDiscardTransientCAs:  
  
-   cssAccurate vrací přesnou uložit velikost, ale trvá déle k výpočtu.  
  
-   cssQuick vrátí velikost, vyplní pro zabezpečení, ale zabere to méně času k výpočtu.  
  
-   informuje cssDiscardTransientCAs `GetSaveSize` , můžete vyvolat rychle discardable vlastní atributy.  
  
 `pdwSaveSize`  
 [out] Ukazatel na velikost, který je potřeba soubor uložte.  
  
## <a name="remarks"></a>Poznámky  
 `GetSaveSize` vypočítá na místo, v bajtech pro uložení sestavení a všechny jeho metadata v aktuálním oboru. (Volání [imetadataemit::savetostream –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) metoda by emitování tento počet bajtů.)  
  
 Pokud má volající implementuje [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) rozhraní (prostřednictvím [imetadataemit::sethandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) nebo [imetadataemit::merge –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` provede dvou průchodů přes metadata optimalizace a je komprimovat. Jinak jsou prováděny žádné optimalizace.  
  
 Pokud se provádí optimalizace, první fáze jednoduše seřadí struktury metadat pro optimalizaci výkonu vyhledání v době importu. Tento krok se obvykle výsledkem přesunutí záznamy problému s vedlejším účinkem, že jsou zneplatněny tokeny uchovávají nástrojem pro budoucí použití. Metadata neinformuje volající tyto změny tokenu až po druhé fázi, ale. V druhé fázi se provádí různé optimalizace, které slouží ke snížení celkové velikosti metadata, například pro optimalizaci tokeny (časná vazba) `mdTypeRef` a `mdMemberRef` tokeny, když je odkaz na typ nebo člen, který je v deklarována aktuální obor metadat. V tomto průchodu dojde k jiné zaokrouhlit tokenu mapování. Po tomto průchodu modul metadata upozorní volající, prostřednictvím jeho `IMapToken` rozhraní všech změnit hodnoty tokenu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
