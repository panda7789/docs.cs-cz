---
title: Optimalizace pro sdílené hostování webů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 07a100e2cd6aaff2b54b99144c9d762c8979fb47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140268"
---
# <a name="optimization-for-shared-web-hosting"></a>Optimalizace pro sdílené hostování webů
Pokud jste správcem serveru, který je sdílen hostováním několika malých webů, můžete `gcTrimCommitOnLowMemory` optimalizovat výkon `runtime` a zvýšit kapacitu webu přidáním následujícího nastavení do uzlu v souboru Aspnet.config v adresáři .NET:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> Toto nastavení se doporučuje pouze pro scénáře sdíleného webhostingu.  
  
 Vzhledem k tomu, že systém uvolňování paměti zachová paměť pro budoucí přidělení, jeho potvrzené místo může být více než to, co je nezbytně nutné. Tento prostor můžete zmenšit tak, aby vyhovoval času, kdy dochází k silnému zatížení systémové paměti. Snížení tohoto přiděleného prostoru zvyšuje výkon a rozšiřuje kapacitu pro hostování více webů.  
  
 Pokud `gcTrimCommitOnLowMemory` je toto nastavení povoleno, systém uvolňování paměti vyhodnotí zatížení systémové paměti a přejde do režimu oříznutí, když zatížení dosáhne 90 %. Udržuje režim ořezávání, dokud zatížení neklesne pod 85%.  
  
 Pokud to podmínky dovolí, systém `gcTrimCommitOnLowMemory` uvolňování paměti může rozhodnout, že nastavení nepomůže aktuální aplikaci a ignoruje ji.  
  
## <a name="example"></a>Příklad  
 Následující fragment XML ukazuje, `gcTrimCommitOnLowMemory` jak povolit nastavení. Elipsy označují další nastavení, která `runtime` by byla v uzlu.  
  
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
  
## <a name="see-also"></a>Viz také

- [Kolekce paměti](../../../docs/standard/garbage-collection/index.md)
