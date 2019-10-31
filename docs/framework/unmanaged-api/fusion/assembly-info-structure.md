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
ms.openlocfilehash: a43d5e15c02a97ff10a6a5afd439cadebb6b33d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109216"
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
|`dwAssemblyFlags`|Příznaky, které označují podrobnosti o instalaci sestavení. Podporovány jsou následující hodnoty:<br /><br /> – Hodnota ASSEMBLYINFO_FLAG_INSTALLED, která označuje, že sestavení je nainstalováno. Aktuální verze .NET Framework vždy nastaví `dwAssemblyFlags` na tuto hodnotu.<br />– Hodnota ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, která označuje, že sestavení je rezidentní v datové části. Aktuální verze .NET Framework nikdy nenastaví `dwAssemblyFlags` na tuto hodnotu.|  
|`uliAssemblySizeInKB`|Celková velikost souborů, které sestavení obsahuje, v kilobajtech.|  
|`pszCurrentAssemblyPathBuf`|Ukazatel na vyrovnávací paměť řetězce, který obsahuje aktuální cestu k souboru manifestu. Cesta musí končit znakem null.|  
|`cchBuf`|Počet velkých znaků, včetně ukončovacího znaku null, který `pszCurrentAssemblyPathBuf` obsahuje.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro fúze](fusion-structures.md)
- [Globální mezipaměť sestavení](../../app-domains/gac.md)
