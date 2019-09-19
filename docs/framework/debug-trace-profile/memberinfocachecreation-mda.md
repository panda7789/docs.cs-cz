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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3b65ecc226c1caf7b53d746f0583e1f57c7d8c1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052467"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation – pomocník spravovaného ladění (MDA)
Při vytvoření `memberInfoCacheCreation` mezipamětiseaktivujepomocníkspravovanéholadění<xref:System.Reflection.MemberInfo> (MDA). Toto je silné označení programu, který využívá funkce reflexe náročné na prostředky.  
  
## <a name="symptoms"></a>Příznaky  
 Pracovní sada programu se zvyšuje, protože program používá reflexi náročné na prostředky.  
  
## <a name="cause"></a>příčina  
 Operace reflexe <xref:System.Reflection.MemberInfo> , které zahrnují objekty, se považují za prostředky nákladné, protože musí číst metadata, která jsou uložená na studených stránkách a obecně naznačují, že program používá určitý typ scénáře s pozdní vazbou.  
  
## <a name="resolution"></a>Řešení  
 Můžete určit, kde se v programu používá reflexe, povolením tohoto MDA a následným spuštěním kódu v ladicím programu nebo připojením k ladicímu programu při aktivaci MDA. V rámci ladicího programu obdržíte trasování zásobníku, kde <xref:System.Reflection.MemberInfo> se mezipaměť vytvořila, a odtud můžete určit, kde program používá reflexi.  
  
 Řešení je závislé na cílech kódu. Tento MDA vás upozorní, že váš program má scénář s pozdní vazbou. Možná budete chtít určit, jestli můžete dosadit scénář s nejstarším rozsahem, nebo zvážit výkon scénáře s pozdní vazbou.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA je aktivován pro každou <xref:System.Reflection.MemberInfo> vytvořenou mezipaměť. Dopad na výkon je zanedbatelný.  
  
## <a name="output"></a>Výstup  
 Výstup aplikace MDA vytvoří zprávu oznamující, <xref:System.Reflection.MemberInfo> že byla vytvořena mezipaměť. Použijte ladicí program k získání trasování zásobníku, kde program používá reflexi.  
  
## <a name="configuration"></a>Konfiguraci  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.MemberInfo>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
