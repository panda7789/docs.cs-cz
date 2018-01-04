---
title: "IMetaDataAssemblyImport::FindAssembliesByName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindAssembliesByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6518fdcf1bef8eaea74818f69f46bb6df26e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName – metoda
Získá pole sestavení se zadaným `szAssemblyName` parametr pomocí standardní pravidla zaměstnaní modul CLR (CLR) pro řešení odkazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szAppBase`  
 [v] Kořenový adresář, do kterého chcete vyhledat zadaného sestavení. Pokud tato hodnota nastavena na `null`, `FindAssembliesByName` hledat pouze v globální mezipaměti sestavení pro sestavení.  
  
 `szPrivateBin`  
 [v] Seznam oddělený středníkem podadresáře (například "bin; přihrádka 2), v kořenovém adresáři, ve kterém se má hledat sestavení. Tyto adresáře jsou zjištěný kromě platformám zadaným v výchozí pravidla zjišťování.  
  
 `szAssemblyName`  
 [v] Název sestavení najít. Formát tohoto řetězce je definována v stránce referenční třídy <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [v] Pole typu <<!--zzxref:IUnknown --> `IUnknown`> ve které se umístí `IMetadataAssemblyImport` rozhraní ukazatele.  
  
 `cMax`  
 [out] Maximální počet ukazatele rozhraní, které mohou být umístěny v `ppIUnk`.  
  
 `pcAssemblies`  
 [out] Vrátí počet ukazatele rozhraní. To znamená, počet ukazatele rozhraní ve skutečnosti umístěných v `ppIUnk`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Název sestavení, `FindAssembliesByName` metoda vyhledá sestavení pomocí následujících standardní pravidla pro řešení odkazy na sestavení. (Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umožňuje volajícímu nakonfigurovat různé aspekty kontextu překladač sestavení, jako je například cesta k aplikaci základní a privátní vyhledávání.  
  
 `FindAssembliesByName` Metoda vyžaduje CLR na inicializaci v procesu k vyvolání logice sestavení řešení. Proto musí volat [coinitializeee –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (předávání COINITEE_DEFAULT) před voláním `FindAssembliesByName`a pak postupujte podle pomocí volání [couninitializecor –](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName`Vrátí [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) ukazatele souboru, který obsahuje manifest sestavení pro název sestavení, který se předává v. Pokud název zadaného sestavení není plně určena (například pokud neobsahuje verze), může být vrácena více sestavení.  
  
 `FindAssembliesByName`běžně používá kompilátoru, která se pokusí najít odkazované sestavení při kompilaci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Jak běhové prostředí vyhledává sestavení](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
