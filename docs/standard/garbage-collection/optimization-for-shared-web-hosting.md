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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140268"
---
# <a name="optimization-for-shared-web-hosting"></a>Optimalizace pro sdílené hostování webů
Pokud jste správcem serveru, který je sdílen hostitelem několika malých webů, můžete optimalizovat výkon a zvýšit kapacitu webu přidáním následujícího nastavení `gcTrimCommitOnLowMemory` do uzlu `runtime` v souboru ASPNET. config v adresáři .NET. :  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> Toto nastavení se doporučuje jenom pro scénáře sdíleného hostování webů.  
  
 Vzhledem k tomu, že systém uvolňování paměti zachovává paměť pro budoucí přidělení, může být jeho přizpůsobený prostor větší, než kolik jich je naprosto potřeba. Tento prostor můžete omezit tak, aby odpovídal času, když dojde k velkému zatížení systémové paměti. Omezením tohoto potvrzeného místa se zlepší výkon a rozšíří se kapacita na hostování více lokalit.  
  
 Pokud je povoleno nastavení `gcTrimCommitOnLowMemory`, systém uvolňování paměti vyhodnotí zatížení systémové paměti a přejde do režimu oříznutí, pokud zatížení dosáhne 90%. Udržuje režim ořezávání, dokud zatížení neklesne pod 85%.  
  
 Když podmínky povolí, systém uvolňování paměti se může rozhodnout, že nastavení `gcTrimCommitOnLowMemory` nepomůže aktuální aplikaci a ignorovat je.  
  
## <a name="example"></a>Příklad  
 Následující fragment kódu XML ukazuje, jak povolit nastavení `gcTrimCommitOnLowMemory`. Tři tečky označují další nastavení, která by byla v `runtime`m uzlu.  
  
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
