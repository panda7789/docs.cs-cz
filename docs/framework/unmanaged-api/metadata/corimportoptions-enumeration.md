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
ms.openlocfilehash: 3be8a004be752af8a8675a3499bdb6cbfd785840
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009194"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions – výčet
Obsahuje hodnoty příznaků, které řídí chování při dovozu sestavení mimo aktuální rozsah.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
|Člen|Description|  
|------------|-----------------|  
|`MDImportOptionDefault`|Označuje výchozí chování, které má přeskočit odstraněné záznamy.|  
|`MDImportOptionAll`|Označuje, že by měla být vytvořena výčet všech metadat.|  
|`MDImportOptionAllTypeDefs`|Označuje, že by měly být vyčísleny všechny definice typedef, včetně odstraněných.|  
|`MDImportOptionAllMethodDefs`|Označuje, že by měly být vyčísleny všechny MethodDefs, včetně odstraněných.|  
|`MDImportOptionAllFieldDefs`|Označuje, že by měly být vyčísleny všechny FieldDefs, včetně odstraněných.|  
|`MDImportOptionAllProperties`|Označuje, že by měly být vyčísleny všechny PropertyDefs, včetně odstraněných.|  
|`MDImportOptionAllEvents`|Označuje, že by měly být vyčísleny všechny EventDefs, včetně odstraněných.|  
|`MDImportOptionAllCustomAttributes`|Označuje, že by měly být vyčísleny všechny vlastní atributy včetně odstraněných.|  
|`MDImportOptionAllExportedTypes`|Označuje, že by se měly vytvořit výčty všech exportovaných typů, včetně odstraněných.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
