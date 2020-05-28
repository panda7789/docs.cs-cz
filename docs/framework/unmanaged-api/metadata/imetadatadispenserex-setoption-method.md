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
ms.openlocfilehash: 0cb0dee7db7faa4c1324d705218934489ec6a4b6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005853"
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
 V následující tabulce jsou uvedeny dostupné identifikátory GUID, `optionId` na které může parametr odkazovat, a odpovídající platné hodnoty pro `pValue` parametr.  
  
|Identifikátor GUID|Description|`pValue`Ukazatele|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Určuje, které položky jsou kontrolovány duplicity. Pokaždé, když zavoláte metodu [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) , která vytvoří novou položku, můžete požádat o metodu, aby zkontrolovala, jestli už položka v aktuálním oboru existuje. Můžete například kontrolovat existenci `mdMethodDef` položek; v tomto případě, když zavoláte [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), zkontroluje, že metoda ještě v aktuálním oboru neexistuje. Tato kontrolu používá klíč, který jednoznačně identifikuje danou metodu: nadřazený typ, název a podpis.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorCheckDuplicatesFor –](corcheckduplicatesfor-enumeration.md) .|  
|MetaDataRefToDefCheck|Ovládací prvky, které odkazované položky jsou převedeny na definice. Ve výchozím nastavení modul metadat optimalizuje kód tím, že převede odkazovanou položku na její definici, pokud je odkazovaná položka ve skutečnosti definována v aktuálním oboru.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorRefToDefCheck –](correftodefcheck-enumeration.md) .|  
|MetaDataNotificationForTokenMovement|Určuje, které nové mapy tokenů dochází během sloučení metadat při vytváření zpětných volání. Pro vytvoření rozhraní [IMapToken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) použijte metodu [IMetaDataEmit:: SetHandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) .|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorNotificationForTokenMovement –](cornotificationfortokenmovement-enumeration.md) .|  
|MetaDataSetENC|Řídí chování funkce Edit-and-Continue (ENC). V jednom okamžiku lze nastavit pouze jeden režim chování.|Musí se jednat o variantu typu UI4 a musí obsahovat hodnotu výčtu [CorSetENC –](corsetenc-enumeration.md) . Hodnota není Bitová maska.|  
|MetaDataErrorIfEmitOutOfOrder|Ovládací prvky, které emitují chyby mimo pořadí generují zpětná volání. Vygenerování metadat mimo pořadí není závažné; Pokud však vygenerujete metadata v pořadí, které je na něj přizpůsobeno modulem metadat, metadata jsou kompaktnější a je proto možné je prohledávat efektivněji. Použijte `IMetaDataEmit::SetHandler` metodu pro vytvoření rozhraní [IMetaDataError –](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) .|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorErrorIfEmitOutOfOrder –](corerrorifemitoutoforder-enumeration.md) .|  
|MetaDataImportOption|Určuje, které typy položek, které byly odstraněny během objektu ENC, jsou načteny enumerátorem.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [výčtu CorImportOptions –](corimportoptions-enumeration.md) .|  
|MetaDataThreadSafetyOptions|Určuje, zda modul metadat získá zámky pro čtení a zápis, což zajišťuje bezpečnost vlákna. Ve výchozím nastavení modul předpokládá, že je přístup jediným vláknem volajícího, takže se nezískají žádné zámky. Za údržbu správné synchronizace vláken při použití rozhraní API metadat zodpovídá klienti.|Musí se jednat o variantu typu UI4 a musí obsahovat hodnotu výčtu [CorThreadSafetyOptions –](corthreadsafetyoptions-enumeration.md) . Hodnota není Bitová maska.|  
|MetaDataGenerateTCEAdapters|Určuje, zda má nástroj pro import knihovny typů generovat pevně spárované adaptéry událostí (TCE) pro kontejnery přípojných bodů COM.|Musí se jednat o variantu typu BOOL. Pokud `pValue` je nastaveno na `true` , modul pro import knihovny typů vygeneruje adaptéry TCE.|  
|MetaDataTypeLibImportNamespace|Určuje nevýchozí obor názvů pro importovanou knihovnu typů.|Musí být buď hodnota null, nebo varianta typu BSTR. Pokud `pValue` je hodnota null, aktuální obor názvů je nastaven na hodnotu null. v opačném případě je aktuální obor názvů nastaven na řetězec, který je uložen v typu BSTR typu variant.|  
|MetaDataLinkerOptions|Určuje, zda má linker generovat sestavení nebo soubor .NET Framework modulu.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot výčtu [CorLinkerOptions –](corlinkeroptions-enumeration.md) .|  
|MetaDataRuntimeVersion|Určuje verzi modulu CLR (Common Language Runtime), vůči kterému byla tato image sestavena. Verze je uložena jako řetězec, například "v 1.0.3705".|Musí se jednat o hodnotu null, hodnotu VT_EMPTY nebo variantu typu BSTR. Pokud `pValue` má hodnotu null, verze modulu runtime je nastavena na hodnotu null. Pokud `pValue` je VT_EMPTY, verze je nastavena na výchozí hodnotu, která je vykreslena z verze souboru knihovny Mscorwks. dll, ve kterém je spuštěn kód metadat. V opačném případě je verze modulu runtime nastavena na řetězec, který je uložen v typu BSTR typu variant.|  
|MetaDataMergerOptions|Určuje možnosti pro sloučení metadat.|Musí se jednat o variantu typu UI4 a musí obsahovat kombinaci hodnot `MergeFlags` výčtu, která je popsána v souboru corhdr. h.|  
|MetaDataPreserveLocalRefs|Zakáže optimalizaci místních odkazů na definice.|Musí obsahovat kombinaci hodnot výčtu [CorLocalRefPreservation –](corlocalrefpreservation-enumeration.md) .|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataDispenserEx – rozhraní](imetadatadispenserex-interface.md)
- [IMetaDataDispenser – rozhraní](imetadatadispenser-interface.md)
