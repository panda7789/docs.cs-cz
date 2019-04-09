---
title: CorImportOptions – výčet
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2f71a277484adbbfe3628222c635528cdab03e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156127"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions – výčet
Obsahuje příznak hodnoty, které řídí chování během import sestavení mimo aktuální rozsah.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDImportOptionDefault`|Určuje výchozí chování, které se mají přeskočit odstraněné záznamy.|  
|`MDImportOptionAll`|Označuje, že všechna metadata ve výčtu.|  
|`MDImportOptionAllTypeDefs`|Označuje, že všechny definice TypeDef, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllMethodDefs`|Označuje, že všechny MethodDefs, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllFieldDefs`|Označuje, že všechny FieldDefs, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllProperties`|Označuje, že všechny PropertyDefs, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllEvents`|Označuje, že všechny EventDefs, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllCustomAttributes`|Označuje, že všechny vlastní atributy, včetně odstraněné ty, které jsou ve výčtu.|  
|`MDImportOptionAllExportedTypes`|Označuje, že všechny exportované typy, včetně odstraněné ty, které jsou ve výčtu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
