---
title: memberInfoCacheCreation – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
ms.openlocfilehash: e5dbc769bd634afae06582ee614addafd611fad9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217315"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation – pomocník spravovaného ladění (MDA)
Když se vytvoří mezipaměť <xref:System.Reflection.MemberInfo>, aktivuje se pomocníka spravovaného ladění (MDA) `memberInfoCacheCreation`. Toto je silné označení programu, který využívá funkce reflexe náročné na prostředky.  
  
## <a name="symptoms"></a>Příznaky  
 Pracovní sada programu se zvyšuje, protože program používá reflexi náročné na prostředky.  
  
## <a name="cause"></a>Příčina  
 Operace reflexe, které zahrnují <xref:System.Reflection.MemberInfo> objekty, se považují za prostředky nákladné, protože musí číst metadata, která jsou uložená na studených stránkách a obecně označují, že program používá určitý typ scénáře s pozdní vazbou.  
  
## <a name="resolution"></a>Řešení  
 Můžete určit, kde se v programu používá reflexe, povolením tohoto MDA a následným spuštěním kódu v ladicím programu nebo připojením k ladicímu programu při aktivaci MDA. V rámci ladicího programu obdržíte trasování zásobníku, ve kterém se vytvořila mezipaměť <xref:System.Reflection.MemberInfo> a odtud, můžete určit, kde program používá reflexi.  
  
 Řešení je závislé na cílech kódu. Tento MDA vás upozorní, že váš program má scénář s pozdní vazbou. Možná budete chtít určit, jestli můžete dosadit scénář s nejstarším rozsahem, nebo zvážit výkon scénáře s pozdní vazbou.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA se aktivuje pro každou vytvořenou mezipaměť <xref:System.Reflection.MemberInfo>. Dopad na výkon je zanedbatelný.  
  
## <a name="output"></a>Výstup  
 Výstup aplikace MDA vytvoří zprávu oznamující, že byla vytvořena mezipaměť <xref:System.Reflection.MemberInfo>. Použijte ladicí program k získání trasování zásobníku, kde program používá reflexi.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Tento vzorový kód aktivuje `memberInfoCacheCreation` MDA.  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection.MemberInfo>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
