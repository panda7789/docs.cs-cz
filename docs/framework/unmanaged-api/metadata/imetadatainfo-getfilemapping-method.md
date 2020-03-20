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
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175262"
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
 [out] Ukazatel na začátek mapovaného souboru.  
  
 `pcbData`  
 [out] Velikost mapované oblasti. Pokud `pdwMappingType` `fmFlat`je , jedná se o velikost souboru.  
  
 `pdwMappingType`  
 [out] Hodnota [CorFileMapping,](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) která označuje typ mapování. Aktuální implementace cltime společného jazyka (CLR) vždy vrátí `fmFlat`. Ostatní hodnoty jsou vyhrazeny pro budoucí použití. Však měli byste vždy ověřit vrácenou hodnotu, protože jiné hodnoty mohou být povoleny v budoucích verzích nebo vydání služby.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|Všechny výstupy jsou vyplněny.|  
|`E_INVALIDARG`|Hodnota NULL byla předána jako hodnota argumentu.|  
|`COR_E_NOTSUPPORTED`|Implementace CLR nemůže poskytnout informace o oblasti paměti. K tomu může dojít z následujících důvodů:<br /><br /> - Obor metadat byl otevřen `ofWrite` `ofCopyMemory` s příznakem nebo.<br />- Obor metadat byl otevřen `ofReadOnly` bez vlajky.<br />- Metoda [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) byla použita k otevření pouze části souboru metadat.<br />- Soubor není přenosný spustitelný soubor (PE). **Poznámka:**  Tyto podmínky závisí na implementaci CLR a pravděpodobně budou oslabeny v budoucích verzích CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Paměť, `ppvData` která odkazuje na je platný pouze tak dlouho, dokud je otevřen základní obor metadat.  
  
 Aby tato metoda fungovala, při mapování metadat souboru na disku do paměti voláním [metody IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) je nutné zadat `ofReadOnly` příznak a nesmíte zadat `ofWrite` příznak nebo. `ofCopyMemory`  
  
 Volba typu mapování souborů pro každý obor je specifická pro danou implementaci CLR. Nemůže být nastavena uživatelem. Aktuální implementace CLR vždy `fmFlat` vrátí `pdwMappingType`v , ale to může změnit v budoucích verzích CLR nebo v budoucích verzích služby dané verze. Vrácenou hodnotu byste `pdwMappingType`měli vždy zkontrolovat v souboru , protože různé typy budou mít různá rozložení a posuny.  
  
 Předávání hodnoty NULL pro některý ze tří parametrů není podporováno. Metoda vrátí `E_INVALIDARG`a žádný z výstupů jsou vyplněny. Ignorování typu mapování nebo velikosti oblasti může mít za následek abnormální ukončení programu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataInfo – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping – výčet](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
