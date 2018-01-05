---
title: "CorImportOptions – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorImportOptions
api_location: mscoree.dll
api_type: COM
f1_keywords: CorImportOptions
helpviewer_keywords: CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9af7bbb6dd7cfa488f72ec99f9cfd848f04e72f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions – výčet
Obsahuje příznak hodnoty, které řídí chování při import sestavení v aktuálním oboru.  
  
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
|`MDImportOptionAllTypeDefs`|Označuje, že všechny definice TypeDef, včetně odstraněné ty ve výčtu.|  
|`MDImportOptionAllMethodDefs`|Označuje, že všechny MethodDefs, včetně odstraněné ty ve výčtu.|  
|`MDImportOptionAllFieldDefs`|Označuje, že všechny FieldDefs, včetně odstraněné ty ve výčtu.|  
|`MDImportOptionAllProperties`|Označuje, že všechny PropertyDefs, včetně odstraněné ty ve výčtu.|  
|`MDImportOptionAllEvents`|Označuje, že všechny EventDefs, včetně odstraněné ty ve výčtu.|  
|`MDImportOptionAllCustomAttributes`|Označuje, že všech vlastních atributů, včetně odstraněné ty ve výčtu.|  
|`MDImportOptionAllExportedTypes`|Označuje, že všechny exportovaný typů, včetně odstraněné ty ve výčtu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
