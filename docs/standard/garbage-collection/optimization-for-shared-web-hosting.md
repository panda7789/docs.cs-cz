---
title: Optimalizace pro sdílené hostování webů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7831e383a3048523909b79ac5a4706f3c1c48371
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216130"
---
# <a name="optimization-for-shared-web-hosting"></a>Optimalizace pro sdílené hostování webů
Pokud jste správce pro server, které jsou sdíleny několika malými weby hostování, můžete optimalizovat výkon a zvýšit kapacitu webu přidáním následujícího kódu `gcTrimCommitOnLowMemory` nastavení `runtime` uzlu v souboru Aspnet.config v rozhraní .NET adresář:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  Toto nastavení se doporučuje jenom pro sdílený Web scénářích hostování.  
  
 Vzhledem k tomu, že systému uvolňování paměti zachová pro budoucí přidělení paměti, lze jeho potvrzeného místa více než je nezbytně nutné. Můžete snížit toto místo tak, aby vyhovovaly dobu při velkém zatížení na systémové paměti. Zmenšení potvrzené zlepšuje výkon a rozbalí kapacitu pro hostování více webů.  
  
 Když `gcTrimCommitOnLowMemory` nastavení povolené, vyhodnotí zatížení paměti systému uvolňování paměti a přejde do režimu ořezávání, když zatížení dosáhne 90 %. Udržuje oříznutí režimu, dokud se zatížení sníží pod 85 %.  
  
 Při povolení podmínky systému uvolňování paměti může rozhodnout, že `gcTrimCommitOnLowMemory` nastavení nebude nápověda aktuální aplikace a ho ignorovat.  
  
## <a name="example"></a>Příklad  
 Následující fragment XML ukazuje, jak povolit `gcTrimCommitOnLowMemory` nastavení. Symbol tří teček označuje další nastavení, která by byla `runtime` uzlu.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
