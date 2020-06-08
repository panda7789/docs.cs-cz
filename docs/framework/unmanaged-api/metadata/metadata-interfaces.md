---
title: Rozhraní metadat
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4d947388afb8d7f8f935ae3b8e8aff81efaf2ee4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489588"
---
# <a name="metadata-interfaces"></a>Rozhraní metadat
Tato část popisuje nespravovaná rozhraní, která poskytují přístup k metadatům uvedeným .NET Framework typy, metody, pole a tak dále.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICeeGen – rozhraní](iceegen-interface.md)  
 Poskytuje metody pro kompilaci dynamického kódu.  
  
 [IHostFilter – rozhraní](ihostfilter-interface.md)  
 Poskytuje metodu pro hostitele za běhu k označení tokenů metadat ke zpracování.  
  
 [IMapToken – rozhraní](imaptoken-interface.md)  
 Poskytuje možnosti mapování mezi importovanými a generovanými podpisy metadat.  
  
 [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)  
 Poskytuje metody, které podporují model s obecným popisem používaný modulem CLR (Common Language Runtime) k překladu a spotřebě prostředků.  
  
 [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)  
 Poskytuje metody pro přístup k obsahu manifestu sestavení a jeho prohlížení.  
  
 [IMetaDataConverter – rozhraní](imetadataconverter-interface.md)  
 Poskytuje metody pro mapování knihoven typů na signatury jejich metadat a jejich převod z jednoho na druhý.  
  
 [IMetaDataDispenser – rozhraní](imetadatadispenser-interface.md)  
 `IMetaDataDispenser`je zastaralá. Místo toho použijte `IMetaDataDispenserEx`.  
  
 [IMetaDataDispenserEx – rozhraní](imetadatadispenserex-interface.md)  
 Poskytuje metody, které mapují oblasti paměti pro vytváření a úpravy metadat.  
  
 [IMetaDataEmit – rozhraní](imetadataemit-interface.md)  
 Poskytuje metody pro vytváření, úpravy a ukládání metadat sestavení v aktuálně definovaném oboru.  
  
 [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)  
 Poskytuje metody pro definování a úpravu signatur metadat metod a konstruktorů s parametry typu <xref:System.Type?displayProperty=nameWithType> .  
  
 [IMetaDataError – rozhraní](imetadataerror-interface.md)  
 Poskytuje mechanismus zpětného volání pro hlášení chyb během překladu signatury metadat pro sestavení.  
  
 [IMetaDataFilter – rozhraní](imetadatafilter-interface.md)  
 Poskytuje metody pro označování a filtrování tokenů metadat, aby nedocházelo k opakujícím se akcím, které již byly provedeny.  
  
 [IMetaDataImport – rozhraní](imetadataimport-interface.md)  
 Poskytuje metody pro import a manipulaci s typy z jiných sestavení.  
  
 [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)  
 Rozšiřuje `IMetaDataImport` , aby poskytoval schopnost pracovat s obecnými typy.  
  
 [IMetaDataInfo – rozhraní](imetadatainfo-interface.md)  
 Poskytuje metodu, která získává informace o mapování metadat ze souboru na disku do paměti.  
  
 [IMetaDataTables – rozhraní](imetadatatables-interface.md)  
 Poskytuje metody pro ukládání a načítání informací o metadatech v tabulkách.  
  
 [IMetaDataTables2 – rozhraní](imetadatatables2-interface.md)  
 Rozšiřuje `IMetaDataTables` k zahrnutí metod pro práci s datovými proudy metadat.  
  
 [IMetaDataValidate – rozhraní](imetadatavalidate-interface.md)  
 Poskytuje metody, které slouží k ověřování podpisů metadat.  
  
## <a name="related-sections"></a>Související oddíly  
 [Globální statické funkce pro metadata](metadata-global-static-functions.md)  
  
 [Výčty pro metadata](metadata-enumerations.md)  
  
 [Struktury pro metadata](metadata-structures.md)  
  
 [Sjednocení pro metadata](metadata-unions.md)
