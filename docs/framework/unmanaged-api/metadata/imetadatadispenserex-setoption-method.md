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
ms.openlocfilehash: bc30f9fb120db92ccfc1e7dd0560b3fe18c54b29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432726"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption – metoda
Nastaví zadanou možnost na danou hodnotu pro aktuální obor metadat. Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 pro Ukazatel na identifikátor GUID, který určuje možnost, která má být nastavena.  
  
 `pValue`  
 pro Hodnota, která se má použít k nastavení možnosti Typ této hodnoty musí být typ variant zadaného typu možnosti.  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulka obsahuje seznam dostupných identifikátorů GUID, na které parametr `optionId` může ukazovat, a odpovídající platné hodnoty pro parametr `pValue`.  
  
|GUID|Popis|`pValue` parametr|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Určuje, které položky jsou kontrolovány duplicity. Pokaždé, když zavoláte metodu [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) , která vytvoří novou položku, můžete požádat o metodu, aby zkontrolovala, jestli už položka v aktuálním oboru existuje. Můžete například kontrolovat existenci `mdMethodDef`ch položek; v tomto případě, při volání [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), zkontroluje, že metoda ještě v aktuálním oboru neexistuje. Tato kontrolu používá klíč, který jednoznačně identifikuje danou metodu: nadřazený typ, název a podpis.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorCheckDuplicatesFor –](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) .|  
|MetaDataRefToDefCheck|Ovládací prvky, které odkazované položky jsou převedeny na definice. Ve výchozím nastavení modul metadat optimalizuje kód tím, že převede odkazovanou položku na její definici, pokud je odkazovaná položka ve skutečnosti definována v aktuálním oboru.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorRefToDefCheck –](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) .|  
|MetaDataNotificationForTokenMovement|Určuje, které nové mapy tokenů dochází během sloučení metadat při vytváření zpětných volání. Pro vytvoření rozhraní [IMapToken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) použijte metodu [IMetaDataEmit:: SetHandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) .|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorNotificationForTokenMovement –](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) .|  
|MetaDataSetENC|Řídí chování funkce Edit-and-Continue (ENC). V jednom okamžiku lze nastavit pouze jeden režim chování.|Musí se jednat o variantu typu UI4 a musí obsahovat hodnotu výčtu [CorSetENC –](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) . Hodnota není Bitová maska.|  
|MetaDataErrorIfEmitOutOfOrder|Ovládací prvky, které emitují chyby mimo pořadí generují zpětná volání. Vygenerování metadat mimo pořadí není závažné; Pokud však vygenerujete metadata v pořadí, které je na něj přizpůsobeno modulem metadat, metadata jsou kompaktnější a je proto možné je prohledávat efektivněji. K vytvoření rozhraní [IMetaDataError –](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) použijte metodu `IMetaDataEmit::SetHandler`.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorErrorIfEmitOutOfOrder –](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) .|  
|MetaDataImportOption|Určuje, které typy položek, které byly odstraněny během objektu ENC, jsou načteny enumerátorem.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [výčtu CorImportOptions –](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) .|  
|MetaDataThreadSafetyOptions|Určuje, zda modul metadat získá zámky pro čtení a zápis, což zajišťuje bezpečnost vlákna. Ve výchozím nastavení modul předpokládá, že je přístup jediným vláknem volajícího, takže se nezískají žádné zámky. Za údržbu správné synchronizace vláken při použití rozhraní API metadat zodpovídá klienti.|Musí se jednat o variantu typu UI4 a musí obsahovat hodnotu výčtu [CorThreadSafetyOptions –](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) . Hodnota není Bitová maska.|  
|MetaDataGenerateTCEAdapters|Určuje, zda má nástroj pro import knihovny typů generovat pevně spárované adaptéry událostí (TCE) pro kontejnery přípojných bodů COM.|Musí se jednat o variantu typu BOOL. Pokud je `pValue` nastaveno na `true`, modul pro import knihovny typů vygeneruje adaptéry TCE.|  
|MetaDataTypeLibImportNamespace|Určuje nevýchozí obor názvů pro importovanou knihovnu typů.|Musí být buď hodnota null, nebo varianta typu BSTR. Pokud `pValue` je hodnota null, aktuální obor názvů je nastaven na hodnotu null; v opačném případě je aktuální obor názvů nastaven na řetězec, který je uložen v typu BSTR typu variant.|  
|MetaDataLinkerOptions|Určuje, zda má linker generovat sestavení nebo soubor .NET Framework modulu.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorLinkerOptions –](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) .|  
|MetaDataRuntimeVersion|Určuje verzi modulu CLR (Common Language Runtime), vůči kterému byla tato image sestavena. Verze je uložena jako řetězec, například "v 1.0.3705".|Musí se jednat o hodnotu null, hodnotu VT_EMPTY nebo variantu typu BSTR. Pokud je `pValue` null, verze modulu runtime je nastavena na hodnotu null. Pokud je `pValue` VT_EMPTY, verze je nastavena na výchozí hodnotu, která je vykreslena z verze souboru knihovny Mscorwks. dll, ve kterém je spuštěn kód metadat. V opačném případě je verze modulu runtime nastavena na řetězec, který je uložen v typu BSTR typu variant.|  
|MetaDataMergerOptions|Určuje možnosti pro sloučení metadat.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu `MergeFlags`, který je popsán v souboru CorHdr. h.|  
|MetaDataPreserveLocalRefs|Zakáže optimalizaci místních odkazů na definice.|Musí obsahovat kombinaci hodnot výčtu [CorLocalRefPreservation –](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) .|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
