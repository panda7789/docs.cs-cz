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
ms.openlocfilehash: 4c6a9473a698e4635c8b5cc9fb58963334dfd65e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081785"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping – metoda
Získá paměťové oblasti mapovaného souboru a typu mapování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppvData`  
 [out] Ukazatel na začátku mapovaného souboru.  
  
 `pcbData`  
 [out] Velikost oblasti pro mapovanou. Pokud `pdwMappingType` je `fmFlat`, toto je velikost souboru.  
  
 `pdwMappingType`  
 [out] A [corfilemapping –](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) hodnotu, která určuje typ mapování. Aktuální implementace modulu common language runtime (CLR) vždy vrátí `fmFlat`. Další hodnoty jsou vyhrazené pro budoucí použití. Nicméně vždy byste měli zkontrolovat vrácené hodnoty, protože jiné hodnoty může být povoleno v budoucích verzích nebo vydání služby.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|Všechny výstupy jsou vyplněny.|  
|`E_INVALIDARG`|NULL byl předán jako hodnota argumentu.|  
|`COR_E_NOTSUPPORTED`|Implementace CLR nemůže poskytnout informace o paměťové oblasti. Tato situace může nastat z následujících důvodů:<br /><br /> -Oboru metadata byla otevřena s `ofWrite` nebo `ofCopyMemory` příznak.<br />-Oboru metadat byl otevřen bez `ofReadOnly` příznak.<br />– [Imetadatadispenser::openscopeonmemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metoda byla použita k otevření pouze část metadata souboru.<br />– Tento soubor není soubor (PE portable executable). **Poznámka:**  Tyto podmínky závisí na implementaci modulu CLR a mohou být správné provedení příslušných činností v budoucích verzích CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Paměť, která `ppvData` odkazuje je platný pouze jako základní obor metadat je otevřený.  
  
 V pořadí pro tuto metodu za účelem práce při mapování metadat souboru na disku do paměti při volání [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metoda, je nutné zadat `ofReadOnly` příznak a nesmí určovat `ofWrite` nebo `ofCopyMemory` příznak.  
  
 Volba typu souboru mapování pro každý obor je specifické pro danou implementaci modulu CLR. Nejde ji nastavit uživatelem. Vrátí aktuální implementace CLR vždy `fmFlat` v `pdwMappingType`, ale to můžete změnit v budoucích verzí modulu CLR nebo v budoucnu aktualizací service release dané verze. Vrácená hodnota by měla vždy zkontrolujte `pdwMappingType`, protože různé typy budou mít různá rozložení a posun.  
  
 Předání hodnoty NULL pro všechny tři parametry není podporován. Metoda vrátí `E_INVALIDARG`, a jsou vyplněny žádné výstupy. Ignoruje se mapování typu nebo velikosti oblasti může způsobit neobvyklé ukončení programu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataInfo – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping – výčet](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
