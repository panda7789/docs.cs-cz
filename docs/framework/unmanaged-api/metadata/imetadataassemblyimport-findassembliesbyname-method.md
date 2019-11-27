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
ms.openlocfilehash: c12d3a7a7d1e52529435361aa12e22e4edeecf03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448291"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName – metoda
Získá pole sestavení se zadaným parametrem `szAssemblyName` pomocí standardních pravidel používaných modulem CLR (Common Language Runtime) pro překlad odkazů.  
  
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
 pro Kořenový adresář, ve kterém se má vyhledat dané sestavení Pokud je tato hodnota nastavena na `null`, `FindAssembliesByName` bude hledána pouze v globální mezipaměti sestavení (GAC) pro sestavení.  
  
 `szPrivateBin`  
 pro Seznam podadresářů oddělených středníkem (například "bin; BIN2") v kořenovém adresáři, ve kterém chcete vyhledat sestavení. Kromě těch, které jsou zadány ve výchozích pravidlech zjišťování, jsou tyto adresáře zjišťovány.  
  
 `szAssemblyName`  
 pro Název sestavení, které chcete najít. Formát tohoto řetězce je definován na stránce Reference třídy pro <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 pro Pole typu [IUnknown](/cpp/atl/iunknown) , do kterého chcete umístit ukazatele rozhraní `IMetadataAssemblyImport`.  
  
 `cMax`  
 mimo Maximální počet ukazatelů rozhraní, které lze umístit do `ppIUnk`.  
  
 `pcAssemblies`  
 mimo Počet vrácených ukazatelů rozhraní. To znamená, že počet ukazatelů rozhraní skutečně umístěných v `ppIUnk`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` byla úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádná sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 V případě názvu sestavení vyhledá `FindAssembliesByName` metoda sestavení pomocí standardních pravidel pro překládání odkazů na sestavení. (Další informace naleznete v tématu [jak modul runtime vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umožňuje volající konfiguraci různých aspektů kontextu překladače sestavení, jako je například základ aplikace a cesta k privátnímu vyhledávání.  
  
 Metoda `FindAssembliesByName` vyžaduje, aby byl modul CLR inicializován v procesu, aby bylo možné vyvolat logiku rozlišení sestavení. Proto je nutné před voláním `FindAssembliesByName`volat [CoInitializeEE –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (předávání COINITEE_DEFAULT) a pak sledovat volání [CoUninitializeCor –](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` vrátí ukazatel [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) do souboru obsahujícího manifest sestavení pro název sestavení, který je předaný. Pokud zadaný název sestavení není plně zadán (například pokud nezahrnuje verzi), může být vráceno více sestavení.  
  
 `FindAssembliesByName` se běžně používá kompilátorem, který se pokouší najít odkazované sestavení v době kompilace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Jak běhové prostředí vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
