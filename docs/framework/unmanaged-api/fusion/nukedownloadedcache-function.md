---
title: NukeDownloadedCache – funkce
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
ms.openlocfilehash: 8f97614412eb2d49b202e86bdabc727159deb5d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131688"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache – funkce
Odstraní mezipaměť pro stažení modulu CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní chybové kódy modelu COM, jak je definováno v WinError. h.  
  
## <a name="remarks"></a>Poznámky  
 Mezipaměť pro stažení CLR je oblast, kde jsou uložena sestavení se silným názvem, která jsou stažena z adresy URL pro možné opakované použití.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Knihovna:** Fusion. dll a knihovny Mscorwks. dll. Použijte knihovnu Fusion. dll namísto knihovny Mscorwks. dll, abyste se ujistili, že cílíte na správnou verzi .NET Framework.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [CreateHistoryReader – funkce](createhistoryreader-function.md)
- [GetHistoryFileDirectory – funkce](gethistoryfiledirectory-function.md)
- [Globální statické funkce pro fúze](fusion-global-static-functions.md)
