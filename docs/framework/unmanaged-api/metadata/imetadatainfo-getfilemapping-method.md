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
ms.openlocfilehash: 0cd2071d4410615a08e774ba30e0e8fe8d1fa7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436171"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping – metoda
Získá oblast paměti mapovaného souboru a typ mapování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppvData`  
 mimo Ukazatel na začátek mapovaného souboru.  
  
 `pcbData`  
 mimo Velikost mapované oblasti Pokud je `pdwMappingType` `fmFlat`, jedná se o velikost souboru.  
  
 `pdwMappingType`  
 mimo Hodnota [CorFileMapping –](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) , která určuje typ mapování. Aktuální implementace modulu CLR (Common Language Runtime) vždy vrací `fmFlat`. Jiné hodnoty jsou vyhrazeny pro budoucí použití. Měli byste však vždy ověřit vrácenou hodnotu, protože jiné hodnoty mohou být povoleny v budoucích verzích nebo verzích služeb.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|Všechny výstupy jsou vyplněny.|  
|`E_INVALIDARG`|Jako hodnota argumentu byla předána hodnota NULL.|  
|`COR_E_NOTSUPPORTED`|Implementace CLR nemůže poskytovat informace o oblasti paměti. Tato situace může mít následující důvody:<br /><br /> – Obor metadat byl otevřen pomocí příznaku `ofWrite` nebo `ofCopyMemory`.<br />– Obor metadat byl otevřen bez příznaku `ofReadOnly`.<br />– Metoda [IMetaDataDispenser:: OpenScopeOnMemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) byla použita k otevření pouze části metadat v souboru.<br />– Soubor není soubor přenositelného spustitelného souboru (PE). **Poznámka:**  Tyto podmínky závisí na implementaci CLR a jsou pravděpodobně oslabeny v budoucích verzích CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Paměť, na kterou `ppvData` odkazuje, je platná pouze tak dlouho, dokud je otevřený obor metadat.  
  
 Aby tato metoda fungovala, Pokud namapujete metadata souboru na disku do paměti voláním metody [IMetaDataDispenser:: OpenScope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) , je nutné zadat příznak `ofReadOnly` a není nutné zadat `ofWrite` nebo `ofCopyMemory` příznak.  
  
 Volba typu mapování souborů pro každý obor je specifická pro danou implementaci CLR. Tuto hodnotu nemůže nastavit uživatel. Aktuální implementace CLR vždy vrátí `fmFlat` v `pdwMappingType`, ale to se může v budoucích verzích CLR nebo v budoucích vydáních této verze změnit. Vždy byste měli kontrolovat vrácenou hodnotu v `pdwMappingType`, protože různé typy budou mít různá rozložení a posuny.  
  
 Předání hodnoty NULL pro některý ze tří parametrů není podporováno. Metoda vrátí `E_INVALIDARG`a žádný z výstupů není vyplněn. Ignorování typu mapování nebo velikost oblasti může způsobit neobvyklé ukončení programu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataInfo – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping – výčet](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
