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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9869efee18549c3d0c8b9ee9ca27cf31c1ccf452
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197110"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption – metoda
Nastaví zadanou možnost dané hodnotě pro aktuální obor metadat. Možnost řídí, jak se zpracovává volání na aktuální metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 [in] Ukazatel na identifikátor GUID, který určuje možnost, která se má nastavit.  
  
 `pValue`  
 [in] Hodnota, která chcete použít k nastavení možnosti. Hodnotu typu variant Zadaná možnost typu musí být typu tuto hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny dostupné identifikátory GUID, který `optionId` parametr může odkazovat na a odpovídající platné hodnoty pro `pValue` parametru.  
  
|GUID|Popis|`pValue` Parametr|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Ovládací prvky, které položky jsou zkontrolovat duplicitu. Pokaždé, když voláte [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) metodě, která se vytvoří nová položka, můžete požádat o metodu ke kontrole, jestli položka již existuje v aktuálním oboru. Například můžete zkontrolovat existenci `mdMethodDef` položky; v takovém případě při volání [imetadataemit::definemethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), zjistí, že metoda již neexistuje v aktuálním oboru. Tato kontrola používá klíč, který jednoznačně identifikuje dané metody: nadřazený typ, název a podpis.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [corcheckduplicatesfor –](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) výčtu.|  
|MetaDataRefToDefCheck|Ovládací prvky, které odkazuje položky se převedou na definice. Ve výchozím nastavení bude modul metadat optimalizovat kód převedením odkazovaná položka k jeho definici, pokud odkazovaná položka je ve skutečnosti definovány v aktuálním oboru.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [correftodefcheck –](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) výčtu.|  
|MetaDataNotificationForTokenMovement|Ovládací prvky, které token změní, ke kterým došlo během metadat sloučení vygenerujte zpětná volání. Použití [imetadataemit::sethandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metodu pro vytvoření vaší [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) rozhraní.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [cornotificationfortokenmovement –](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) výčtu.|  
|MetaDataSetENC|Řídí chování edit-and-continue (ENC). Najednou lze nastavit pouze jeden režim chování.|Musí být typu variant typu UI4 a musí obsahovat hodnotu [corsetenc –](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) výčtu. Hodnota není bitová maska.|  
|MetaDataErrorIfEmitOutOfOrder|Ovládací prvky, které chyby generované out pořadí generovat zpětná volání. Generování metadat mimo pořadí není závažná; Pokud generování metadat v pořadí, které podporuje modul metadat metadata je však kompaktnějším a proto lze efektivněji prohledávat. Použití `IMetaDataEmit::SetHandler` metodu pro vytvoření vaší [imetadataerror –](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) rozhraní.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [corerrorifemitoutoforder –](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) výčtu.|  
|MetaDataImportOption|Určuje, jaké typy položek, které byly odstraněny během KODÉRU jsou načítána pro enumerátor.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [corimportoptions – výčet](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) výčtu.|  
|MetaDataThreadSafetyOptions|Určuje, zda modul metadat získá čtení/zápis zámky, tím se zajišťuje bezpečný přístup z více vláken. Ve výchozím nastavení modul předpokládá, že přístup je jednovláknový volajícím, takže jsou získány žádné zámky. Klienti jsou odpovědná za správu synchronizace správné vlákno při použití rozhraní API metadat.|Musí být typu variant typu UI4 a musí obsahovat hodnotu [corthreadsafetyoptions –](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) výčtu. Hodnota není bitová maska.|  
|MetaDataGenerateTCEAdapters|Určuje, zda by měl generovat type library importer adaptéry vysoce provázané událostí (TCE) pro kontejnery bodu připojení COM.|Musí být variantou typu BOOL. Pokud `pValue` je nastavena na `true`, type library importer generuje TCE adaptéry.|  
|MetaDataTypeLibImportNamespace|Určuje jiné než výchozí obor názvů pro knihovny typů, která se importují.|Musí být buď hodnotu null, nebo hodnotu typu variant typu BSTR. Pokud `pValue` je hodnota null, aktuální obor názvů je nastavena na hodnotu null; jinak vrátí hodnotu, aktuální obor názvů je nastavena na řetězec, který se nachází v typu typ variant BSTR.|  
|MetaDataLinkerOptions|Určuje, zda propojovací program by měl generovat sestavení nebo souboru modulu rozhraní .NET Framework.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [corlinkeroptions –](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) výčtu.|  
|MetaDataRuntimeVersion|Určuje verzi modulu common language runtime, proti kterému byl vytvořen tento obrázek. Verze je uloženo jako řetězec, například "v1.0.3705".|Musí být hodnota null, VT_EMPTY hodnotu nebo hodnotu typu variant typu BSTR. Pokud `pValue` je null, verze modulu runtime je nastavena na hodnotu null. Pokud `pValue` je VT_EMPTY, verze je nastavená na výchozí hodnotu, která pochází z verzi knihovny Mscorwks.dll, ve kterém je spuštěn kód metadat. Verze modulu runtime je jinak nastavte na řetězec, který se nachází v typu typ variant BSTR.|  
|MetaDataMergerOptions|Určuje možnosti pro slučování metadat.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot `MergeFlags` výčtu, která je popsána v souboru Comimage_flags.|  
|MetaDataPreserveLocalRefs|Zakáže optimalizace místní odkazů na definice.|Musí obsahovat kombinaci hodnot [corlocalrefpreservation –](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) výčtu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
