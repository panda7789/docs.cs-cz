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
ms.openlocfilehash: 05902436c09d082f90af01f48c7e918650317ce7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009415"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName – metoda
Získá pole sestavení se zadaným `szAssemblyName` parametrem pomocí standardních pravidel používaných modulem CLR (Common Language Runtime) pro překlad odkazů.  
  
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
 pro Kořenový adresář, ve kterém se má vyhledat dané sestavení Pokud je tato hodnota nastavena na `null` , `FindAssembliesByName` bude hledána pouze v globální mezipaměti sestavení (GAC) pro sestavení.  
  
 `szPrivateBin`  
 pro Seznam podadresářů oddělených středníkem (například "bin; BIN2") v kořenovém adresáři, ve kterém chcete vyhledat sestavení. Kromě těch, které jsou zadány ve výchozích pravidlech zjišťování, jsou tyto adresáře zjišťovány.  
  
 `szAssemblyName`  
 pro Název sestavení, které chcete najít. Formát tohoto řetězce je definován na stránce Reference třídy pro <xref:System.Reflection.AssemblyName> .  
  
 `ppIUnk`  
 pro Pole typu [IUnknown](/cpp/atl/iunknown) , do kterého se mají umístit `IMetadataAssemblyImport` ukazatele rozhraní.  
  
 `cMax`  
 mimo Maximální počet ukazatelů rozhraní, které lze umístit do `ppIUnk` .  
  
 `pcAssemblies`  
 mimo Počet vrácených ukazatelů rozhraní. To znamená, že počet ukazatelů rozhraní, které jsou ve skutečnosti umístěny v `ppIUnk` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádná sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 V případě názvu sestavení `FindAssembliesByName` vyhledá metoda sestavení pomocí standardních pravidel pro překlad odkazů na sestavení. (Další informace naleznete v tématu [jak modul runtime vyhledává sestavení](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName`umožňuje volající konfiguraci různých aspektů kontextu překladače sestavení, jako je například základ aplikace a cesta k privátnímu vyhledávání.  
  
 `FindAssembliesByName`Metoda vyžaduje, aby byl modul CLR inicializován v procesu, aby bylo možné vyvolat logiku rozlišení sestavení. Proto je nutné před voláním volat [CoInitializeEE –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (předání COINITEE_DEFAULT) `FindAssembliesByName` a pak sledovat volání [CoUninitializeCor –](../hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName`vrátí ukazatel [IMetaDataImport](imetadataimport-interface.md) na soubor obsahující manifest sestavení pro název sestavení, který je předaný. Pokud zadaný název sestavení není plně zadán (například pokud nezahrnuje verzi), může být vráceno více sestavení.  
  
 `FindAssembliesByName`je běžně používán kompilátorem, který se pokouší najít odkazované sestavení v době kompilace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Jak běhové prostředí vyhledává sestavení](../../deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)
