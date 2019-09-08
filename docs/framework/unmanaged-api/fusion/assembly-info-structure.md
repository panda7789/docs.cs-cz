---
title: ASSEMBLY_INFO – struktura
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 390ab4881396bbc01337d087f05b6066153bfed1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795484"
---
# <a name="assembly_info-structure"></a>ASSEMBLY_INFO – struktura
Obsahuje informace o sestavení, které je registrováno v globální mezipaměti sestavení (GAC).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`cbAssemblyInfo`|Velikost struktury v bajtech. Toto pole je vyhrazeno pro budoucí rozšíření.|  
|`dwAssemblyFlags`|Příznaky, které označují podrobnosti o instalaci sestavení. Podporovány jsou následující hodnoty:<br /><br /> – Hodnota ASSEMBLYINFO_FLAG_INSTALLED, která označuje, že sestavení je nainstalováno. Aktuální verze .NET Framework vždy nastavuje `dwAssemblyFlags` na tuto hodnotu.<br />– Hodnota ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, která označuje, že sestavení je rezidentní v datové části. Aktuální verze .NET Framework se nikdy nenastavuje `dwAssemblyFlags` na tuto hodnotu.|  
|`uliAssemblySizeInKB`|Celková velikost souborů, které sestavení obsahuje, v kilobajtech.|  
|`pszCurrentAssemblyPathBuf`|Ukazatel na vyrovnávací paměť řetězce, který obsahuje aktuální cestu k souboru manifestu. Cesta musí končit znakem null.|  
|`cchBuf`|Počet velkých znaků, včetně ukončovacího znaku null, který `pszCurrentAssemblyPathBuf` obsahuje.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro fúze](fusion-structures.md)
- [Globální mezipaměť sestavení](../../app-domains/gac.md)
