---
title: Rozhraní metadat
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4672cb813cec4a127f7888a2273eb26c3f34c3d9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431585"
---
# <a name="metadata-interfaces"></a>Rozhraní metadat
Tato část popisuje nespravovaná rozhraní, která poskytují přístup k metadatům uvedeným .NET Framework typy, metody, pole a tak dále.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICeeGen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 Poskytuje metody pro kompilaci dynamického kódu.  
  
 [IHostFilter – rozhraní](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 Poskytuje metodu pro hostitele za běhu k označení tokenů metadat ke zpracování.  
  
 [IMapToken – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 Poskytuje možnosti mapování mezi importovanými a generovanými podpisy metadat.  
  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 Poskytuje metody, které podporují model s obecným popisem používaný modulem CLR (Common Language Runtime) k překladu a spotřebě prostředků.  
  
 [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 Poskytuje metody pro přístup k obsahu manifestu sestavení a jeho prohlížení.  
  
 [IMetaDataConverter – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 Poskytuje metody pro mapování knihoven typů na signatury jejich metadat a jejich převod z jednoho na druhý.  
  
 [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 `IMetaDataDispenser` je zastaralá. Místo nich se používá `IMetaDataDispenserEx`.  
  
 [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 Poskytuje metody, které mapují oblasti paměti pro vytváření a úpravy metadat.  
  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 Poskytuje metody pro vytváření, úpravy a ukládání metadat sestavení v aktuálně definovaném oboru.  
  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 Poskytuje metody pro definování a úpravu signatur metadat metod a konstruktorů s parametry typu <xref:System.Type?displayProperty=nameWithType>.  
  
 [IMetaDataError – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 Poskytuje mechanismus zpětného volání pro hlášení chyb během překladu signatury metadat pro sestavení.  
  
 [IMetaDataFilter – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 Poskytuje metody pro označování a filtrování tokenů metadat, aby nedocházelo k opakujícím se akcím, které již byly provedeny.  
  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 Poskytuje metody pro import a manipulaci s typy z jiných sestavení.  
  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 Rozšiřuje `IMetaDataImport`, aby poskytoval schopnost pracovat s obecnými typy.  
  
 [IMetaDataInfo – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 Poskytuje metodu, která získává informace o mapování metadat ze souboru na disku do paměti.  
  
 [IMetaDataTables – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 Poskytuje metody pro ukládání a načítání informací o metadatech v tabulkách.  
  
 [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 Rozšiřuje `IMetaDataTables`, aby zahrnoval metody pro práci s datovými proudy metadat.  
  
 [IMetaDataValidate – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 Poskytuje metody, které slouží k ověřování podpisů metadat.  
  
## <a name="related-sections"></a>Související oddíly  
 [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [Struktury pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [Sjednocení pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
