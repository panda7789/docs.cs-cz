---
title: IMetaDataAssemblyImport::FindAssembliesByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177804"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName – metoda
Získá pole sestavení se zadaným `szAssemblyName` parametrem pomocí standardních pravidel používaných cltime jazyka (CLR) pro řešení odkazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,
    [in]  LPCWSTR     szPrivateBin,
    [in]  LPCWSTR     szAssemblyName,
    [out] IUnknown    *ppIUnk[],
    [in]  ULONG       cMax,
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szAppBase`  
 [v] Kořenový adresář, ve kterém chcete vyhledat dané sestavení. Pokud je tato `null`hodnota `FindAssembliesByName` nastavena na , bude vypadat pouze v globální mezipaměti sestavení pro sestavení.  
  
 `szPrivateBin`  
 [v] Seznam podadresářů oddělených středníkem (například "bin;bin2") pod kořenovým adresářem, ve kterém lze vyhledat sestavení. Tyto adresáře jsou sondovány kromě těch, které jsou zadány ve výchozím pravidlech zjišťování.  
  
 `szAssemblyName`  
 [v] Název sestavení najít. Formát tohoto řetězce je definován na stránce <xref:System.Reflection.AssemblyName>reference třídy pro .  
  
 `ppIUnk`  
 [v] Pole typu [IUnknown,](/cpp/atl/iunknown) ve kterém `IMetadataAssemblyImport` chcete umístit ukazatele rozhraní.  
  
 `cMax`  
 [out] Maximální počet ukazatelů rozhraní, které lze `ppIUnk`umístit do aplikace .  
  
 `pcAssemblies`  
 [out] Počet ukazatelů rozhraní vrácena. To znamená, že počet ukazatelů rozhraní `ppIUnk`skutečně umístěn v .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádná sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k názvu `FindAssembliesByName` sestavení metoda najde sestavení podle standardních pravidel pro řešení odkazů na sestavení. (Další informace naleznete [v tématu How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umožňuje volajícímu konfigurovat různé aspekty kontextu překládání sestavení, jako je například základna aplikace a soukromá vyhledávací cesta.  
  
 Metoda `FindAssembliesByName` vyžaduje CLR, které mají být inicializovány v procesu za účelem vyvolání logiky rozlišení sestavení. Proto je nutné volat [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (předávání `FindAssembliesByName`COINITEE_DEFAULT) před voláním a potom postupujte s voláním [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName`vrátí ukazatel [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) do souboru obsahujícího manifest sestavení pro název sestavení, který je předán. Pokud daný název sestavení není zcela zadán (například pokud neobsahuje verzi), může být vráceno více sestavení.  
  
 `FindAssembliesByName`je běžně používán kompilátorem, který se pokouší najít odkazované sestavení v době kompilace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Jak běhové prostředí vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
