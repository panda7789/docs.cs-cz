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
ms.openlocfilehash: 7337222f7f419c68ae21d604d1673158acca85ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777388"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize – metoda
Získá odhadovaná velikost binárního sestavení a jeho metadata v aktuálním oboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fSave`  
 [in] Hodnota [corsavesize –](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) výčet, který určuje, jestli se má získat přesné nebo přibližné velikosti. Platné jsou jenom tři hodnoty: cssAccurate cssQuick a cssDiscardTransientCAs:  
  
- cssAccurate vrátí přesné uložit velikost ale trvá déle k výpočtu.  
  
- cssQuick vrátí velikost, aby bylo vytvořeno pro zabezpečení, ale trvá méně času k výpočtu.  
  
- říká cssDiscardTransientCAs `GetSaveSize` , že může vyvolat okamžitě discardable vlastních atributů.  
  
 `pdwSaveSize`  
 [out] Ukazatel na velikost, která je nutná k uložení souboru.  
  
## <a name="remarks"></a>Poznámky  
 `GetSaveSize` vypočítá prostor, v bajtech, uložte sestavení a všechny jeho metadata v aktuálním oboru. (Volání [imetadataemit::savetostream –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) metody by vygenerovat tento počet bajtů.)  
  
 Pokud volající implementuje [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) rozhraní (prostřednictvím [imetadataemit::sethandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) nebo [imetadataemit::merge –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` provede dva průchody přes metadata k optimalizaci a je komprimovat. V opačném případě jsou prováděny žádné optimalizace.  
  
 Pokud se provádí optimalizace, prvním průchodu jednoduše seřadí struktury metadat pro optimalizaci výkonu hledání v době importu. Tento krok obvykle vytváří při přesouvání záznamy, s vedlejším účinkem, že nejsou zneplatněny tokeny uchovávají nástrojem pro budoucí použití. Metadata neinformuje volající tyto změny tokenu do po druhé fázi, ale. Ve druhé fázi, jsou prováděny různých optimalizací, které slouží ke snížení celkové velikosti metadata, jako je třeba optimalizace tokeny (časná vazba) `mdTypeRef` a `mdMemberRef` tokeny, když je odkaz na typ nebo člen, který je deklarován v aktuální obor metadat. V tomto kroku dojde k další várky token mapování. Po průchodu, upozorní metadata modulu volající, prostřednictvím svých `IMapToken` rozhraní libovolného změnit hodnoty tokenu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
