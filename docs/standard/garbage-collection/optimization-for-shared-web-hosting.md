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
ms.openlocfilehash: affdbb357cac14f258822591c3817c93ce6077f8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915905"
---
# <a name="optimization-for-shared-web-hosting"></a>Optimalizace pro sdílené hostování webů
Pokud jste správcem serveru, který je sdílen hostitelem několika malých webů, můžete optimalizovat výkon a zvýšit kapacitu webu přidáním následujícího `gcTrimCommitOnLowMemory` nastavení `runtime` do uzlu v souboru ASPNET. config v rozhraní .NET. službě  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> Toto nastavení se doporučuje jenom pro scénáře sdíleného hostování webů.  
  
 Vzhledem k tomu, že systém uvolňování paměti zachovává paměť pro budoucí přidělení, může být jeho přizpůsobený prostor větší, než kolik jich je naprosto potřeba. Tento prostor můžete omezit tak, aby odpovídal času, když dojde k velkému zatížení systémové paměti. Omezením tohoto potvrzeného místa se zlepší výkon a rozšíří se kapacita na hostování více lokalit.  
  
 Když je `gcTrimCommitOnLowMemory` toto nastavení povoleno, systém uvolňování paměti vyhodnotí zatížení systémové paměti a přejde do režimu oříznutí, pokud zatížení dosáhne 90%. Udržuje režim ořezávání, dokud zatížení neklesne pod 85%.  
  
 Když podmínky povolí, systém uvolňování paměti se může rozhodnout `gcTrimCommitOnLowMemory` , že nastavení nepomůže aktuální aplikaci a ignorovat je.  
  
## <a name="example"></a>Příklad  
 Následující fragment kódu XML ukazuje, jak povolit `gcTrimCommitOnLowMemory` nastavení. Tři tečky označují další nastavení, která by byla `runtime` v uzlu.  
  
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
