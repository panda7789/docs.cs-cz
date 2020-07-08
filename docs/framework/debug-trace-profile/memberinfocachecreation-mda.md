---
title: memberInfoCacheCreation – pomocník spravovaného ladění (MDA)
description: Pochopení pomocníka spravovaného ladění memberInfoCacheCreation – (MDA) v rozhraní .NET, který se aktivuje při vytvoření mezipaměti MemberInfo.
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
ms.openlocfilehash: c48be7ac8632b8072981be01e01997ee8c34b6b3
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051139"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation – pomocník spravovaného ladění (MDA)
`memberInfoCacheCreation`Při vytvoření mezipaměti se aktivuje pomocník spravovaného ladění (MDA) <xref:System.Reflection.MemberInfo> . Toto je silné označení programu, který využívá funkce reflexe náročné na prostředky.  
  
## <a name="symptoms"></a>Příznaky  
 Pracovní sada programu se zvyšuje, protože program používá reflexi náročné na prostředky.  
  
## <a name="cause"></a>Příčina  
 Operace reflexe, které zahrnují <xref:System.Reflection.MemberInfo> objekty, se považují za prostředky nákladné, protože musí číst metadata, která jsou uložená na studených stránkách a obecně naznačují, že program používá určitý typ scénáře s pozdní vazbou.  
  
## <a name="resolution"></a>Řešení  
 Můžete určit, kde se v programu používá reflexe, povolením tohoto MDA a následným spuštěním kódu v ladicím programu nebo připojením k ladicímu programu při aktivaci MDA. V rámci ladicího programu obdržíte trasování zásobníku, kde se <xref:System.Reflection.MemberInfo> mezipaměť vytvořila, a odtud můžete určit, kde program používá reflexi.  
  
 Řešení je závislé na cílech kódu. Tento MDA vás upozorní, že váš program má scénář s pozdní vazbou. Možná budete chtít určit, jestli můžete dosadit scénář s nejstarším rozsahem, nebo zvážit výkon scénáře s pozdní vazbou.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA je aktivován pro každou <xref:System.Reflection.MemberInfo> vytvořenou mezipaměť. Dopad na výkon je zanedbatelný.  
  
## <a name="output"></a>Výstup  
 Výstup aplikace MDA vytvoří zprávu oznamující, že <xref:System.Reflection.MemberInfo> byla vytvořena mezipaměť. Použijte ladicí program k získání trasování zásobníku, kde program používá reflexi.  
  
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
