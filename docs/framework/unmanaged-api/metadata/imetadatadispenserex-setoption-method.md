---
title: IMetaDataDispenserEx::SetOption – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.SetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type:
- apiref
ms.openlocfilehash: f8e85a670d04e5825653864484b7ccd9ce747949
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175899"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption – metoda
Nastaví zadanou možnost na danou hodnotu pro aktuální obor metadat. Tato možnost určuje, jak jsou zpracována volání aktuálního oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 [v] Ukazatel na identifikátor GUID, který určuje možnost, která má být nastavena.  
  
 `pValue`  
 [v] Hodnota, která má být nastavena možnost. Typ této hodnoty musí být variantou typu zadané možnosti.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny `optionId` dostupné identifikátory GUID, na `pValue` které může parametr ukazovat, a odpovídající platné hodnoty parametru.  
  
|GUID|Popis|`pValue`Parametr|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Určuje, které položky jsou kontrolovány na duplikáty. Pokaždé, když zavoláte metodu [IMetaDataEmit,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) která vytvoří novou položku, můžete požádat metodu ke kontrole, zda položka již existuje v aktuálním oboru. Můžete například zkontrolovat existenci `mdMethodDef` položek; v tomto případě při volání [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), zkontroluje, zda metoda již neexistuje v aktuálním oboru. Tato kontrola používá klíč, který jednoznačně identifikuje danou metodu: nadřazený typ, název a podpis.|Musí být varianta typu UI4 a musí obsahovat kombinaci hodnot [CorCheckDuplicatesPro](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) výčet.|  
|MetaDataRefToDefCheck|Ovládací prvky, které jsou odkazované položky převedeny na definice. Ve výchozím nastavení modul metadat optimalizuje kód převedením odkazované položky na její definici, pokud je odkazovaná položka skutečně definována v aktuálním oboru.|Musí být variantou typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorRefToDefCheck.](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)|  
|MetaDataNotificationForTokenMovement|Určuje, které přemapování tokenů, ke kterým dochází během sloučení metadat, generuje zpětná volání. Pomocí metody [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) vytvořte rozhraní [IMapToken.](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)|Musí být variantou typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorNotificationForTokenMovement.](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)|  
|MetaDatasetENC|Řídí chování úprav a pokračování (ENC). Najednou lze nastavit pouze jeden způsob chování.|Musí být varianta typu UI4 a musí obsahovat hodnotu výčtu [CorSetENC.](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) Hodnota není bitová maska.|  
|MetaDataErrorIfEmitOutOfOrder|Ovládací prvky, které vyzařovaly chyby mimo pořadí, generují zpětná volání. Vyzařování metadat mimo pořadí není fatální; pokud však vyzařujete metadata v pořadí, které je upřednostňováno modulem metadat, metadata jsou kompaktnější a proto lze efektivněji prohledávat. Pomocí `IMetaDataEmit::SetHandler` této metody vytvořte rozhraní [IMetaDataError.](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)|Musí být varianta typu UI4 a musí obsahovat kombinaci hodnot [výčtu CorErrorIfEmitOutOfOrder.](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md)|  
|MetaDataImportOption|Určuje, které druhy položek, které byly odstraněny během ENC jsou načteny čítačem výčtu.|Musí být varianta typu UI4 a musí obsahovat kombinaci hodnot výčtu [Výčtu CorImportOptions.](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)|  
|Možnosti zabezpečení vláken MetaDataThread|Určuje, zda modul metadat získá zámky čtečky a zápisu, čímž zajistí bezpečnost podprocesu. Ve výchozím nastavení modul předpokládá, že přístup je jedním zřetězením volajícím, takže jsou získány žádné zámky. Klienti jsou zodpovědní za udržování správné synchronizace vláken při použití rozhraní API metadat.|Musí být varianta typu UI4 a musí obsahovat hodnotu výčtu [CorThreadSafetyOptions.](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) Hodnota není bitová maska.|  
|Adaptéry MetaDataGenerateTCE|Určuje, zda má importér knihovny typů generovat pevně spojené adaptéry událostí (TCE) pro kontejnery spojovacích bodů COM.|Musí být varianta typu BOOL. Pokud `pValue` je `true`nastavena na , import knihovny typů generuje adaptéry TCE.|  
|MetaDataTypeLibImportOborový prostor|Určuje nevýchozí obor názvů pro importovoložnou knihovnu.|Musí být buď nulovou hodnotou, nebo variantou typu BSTR. Pokud `pValue` je hodnota null, aktuální obor názvů je nastavena na null; v opačném případě je aktuální obor názvů nastaven na řetězec, který je držen v typu BSTR varianty.|  
|Možnosti metadatalinkeru|Určuje, zda má propojovací program generovat soubor modulu rozhraní .NET Framework.|Musí být varianta typu UI4 a musí obsahovat kombinaci hodnot [corlinkeroptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) výčtu.|  
|MetaDataRuntimeVerze|Určuje verzi běžného jazykového běhu, proti kterému byla tato bitová kopie vytvořena. Verze je uložena jako řetězec, například "v1.0.3705".|Musí být hodnota null, hodnota VT_EMPTY nebo varianta typu BSTR. Pokud `pValue` je null, verze runtime je nastavena na hodnotu null. Pokud `pValue` je VT_EMPTY, verze je nastavena na výchozí hodnotu, která je čerpána z verze Mscorwks.dll, ve kterém je spuštěn kód metadat. V opačném případě je verze runtime nastavena na řetězec, který je držen v typu BSTR varianty.|  
|Možnosti metadatamerger|Určuje možnosti pro slučování metadat.|Musí být variantou typu UI4 a musí obsahovat `MergeFlags` kombinaci hodnot výčtu, která je popsána v souboru CorHdr.h.|  
|MetaDataPreserveLocalRefs|Zakáže optimalizaci místních odkazů do definic.|Musí obsahovat kombinaci hodnot [corlocalrefpreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) výčtu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
