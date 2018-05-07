---
title: IMetaDataInfo::GetFileMapping – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 562b6fcd015441ce5eb6b5f0ab7a4f361bb229c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping – metoda
Získá oblasti paměti mapovaný soubor, a typ mapování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppvData`  
 [out] Ukazatel na začátek mapovaný soubor.  
  
 `pcbData`  
 [out] Velikost oblasti namapované. Pokud `pdwMappingType` je `fmFlat`, toto je velikost souboru.  
  
 `pdwMappingType`  
 [out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) hodnotu, která určuje typ mapování. Vrátí aktuální implementace common language runtime (CLR) vždy `fmFlat`. Ostatní hodnoty jsou vyhrazené pro budoucí použití. Však vždy ověřte vrácené hodnoty, protože jiné hodnoty může v budoucích verzích povolené nebo služby verzích.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|Všechny výstupy jsou vyplněny.|  
|`E_INVALIDARG`|Jako hodnota argumentu byla předána hodnota NULL.|  
|`COR_E_NOTSUPPORTED`|Implementace CLR nemůže poskytnout informace o oblasti paměti. Toto může nastat z následujících důvodů:<br /><br /> -Oboru metadata byla otevřena s `ofWrite` nebo `ofCopyMemory` příznak.<br />-Oboru metadata byla otevřena bez `ofReadOnly` příznak.<br />-Na [imetadatadispenser::openscopeonmemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metoda použitý k otevření pouze metadata část souboru.<br />-Soubor není souborem přenosné spustitelný soubor (PE). **Poznámka:** tyto podmínky závisí na implementaci CLR a jsou nejspíš oslabí v budoucích verzích modulu CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Paměť, `ppvData` body, je platný pouze základní obor metadat je otevřený.  
  
 V pořadí pro tuto metodu za účelem pracovat, při mapování metadata soubor na disku do paměti voláním [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metoda, je nutné zadat `ofReadOnly` příznak a nesmí zadáte `ofWrite` nebo `ofCopyMemory` příznak.  
  
 Volba typu souboru mapování pro každý obor je specifická pro danou implementace modulu CLR. Nejde ji nastavit uživatelem. Vrátí aktuální implementace modulu CLR vždy `fmFlat` v `pdwMappingType`, ale toto můžete změnit v budoucích verzích modulu CLR nebo v budoucích verzích služby danou verzi. Vrácená hodnota by měla vždy zkontrolujte v `pdwMappingType`, protože jiné typy bude mít jiné rozložení a odsazení.  
  
 Předání hodnotou NULL pro všechny tři parametry není podporována. Vrátí metoda `E_INVALIDARG`, a jsou vyplněny žádné výstupy. Mapování typu nebo velikosti oblasti je ignorována, může mít za následek neobvyklé ukončení programu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataInfo – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 [CorFileMapping – výčet](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
