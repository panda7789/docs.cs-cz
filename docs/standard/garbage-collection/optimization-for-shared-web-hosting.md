---
title: Optimalizace pro sdílené hostování webů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: ccaacd44f8aaed9c3178cb94f98b0f58d4d3c7d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285986"
---
# <a name="optimization-for-shared-web-hosting"></a>Optimalizace pro sdílené hostování webů
Pokud jste správcem serveru, který je sdílen hostitelem několika malých webů, můžete optimalizovat výkon a zvýšit kapacitu webu přidáním následujícího `gcTrimCommitOnLowMemory` nastavení do `runtime` uzlu v souboru ASPNET. config v adresáři .NET:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> Toto nastavení se doporučuje jenom pro scénáře sdíleného hostování webů.  
  
 Vzhledem k tomu, že systém uvolňování paměti zachovává paměť pro budoucí přidělení, může být jeho přizpůsobený prostor větší, než kolik jich je naprosto potřeba. Tento prostor můžete omezit tak, aby odpovídal času, když dojde k velkému zatížení systémové paměti. Omezením tohoto potvrzeného místa se zlepší výkon a rozšíří se kapacita na hostování více lokalit.  
  
 Když `gcTrimCommitOnLowMemory` je toto nastavení povoleno, systém uvolňování paměti vyhodnotí zatížení systémové paměti a přejde do režimu oříznutí, pokud zatížení dosáhne 90%. Udržuje režim ořezávání, dokud zatížení neklesne pod 85%.  
  
 Když podmínky povolí, systém uvolňování paměti se může rozhodnout, že `gcTrimCommitOnLowMemory` Nastavení nepomůže aktuální aplikaci a ignorovat je.  
  
## <a name="example"></a>Příklad  
 Následující fragment kódu XML ukazuje, jak povolit `gcTrimCommitOnLowMemory` nastavení. Tři tečky označují další nastavení, která by byla v `runtime` uzlu.  
  
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

- [Uvolňování paměti](index.md)
