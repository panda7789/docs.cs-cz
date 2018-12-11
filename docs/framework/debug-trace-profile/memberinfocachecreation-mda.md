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
ms.openlocfilehash: 5ebc449985a8e2617b278f04c91d243ca11b637e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145199"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation – pomocník spravovaného ladění (MDA)
`memberInfoCacheCreation` Pomocníka spravovaného ladění (MDA) se aktivuje při <xref:System.Reflection.MemberInfo> mezipaměť je vytvořená. Toto je silné údaj o program, který provádí používání funkcí prostředků reflexe.  
  
## <a name="symptoms"></a>Příznaky  
 Program pracovní sadu zvýšení vzhledem k tomu, že program používá prostředků reflexe.  
  
## <a name="cause"></a>příčina  
 Reflexe operací, které se týkají <xref:System.Reflection.MemberInfo> objekty jsou považovány za prostředek nákladné, protože je musí číst metadata, která je uložena v studenou stránky a obecně označují program používá nějaký typ scénář s pozdní vazbou.  
  
## <a name="resolution"></a>Rozlišení  
 Můžete určit, kde reflexe se používá ve svém programu povolením toto MDA a potom spuštěním kódu v ladicí program nebo připojení se ladicí program, když MDA aktivováno. V ladicím programu se zobrazí trasování zásobníku znázorňující, kde <xref:System.Reflection.MemberInfo> mezipaměti byla vytvořena a odtud můžete určit, kde je program pomocí reflexe.  
  
 Rozlišení je závislá na cíli kód. Toto MDA vás upozorní, že váš program obsahuje scénář s pozdní vazbou. Můžete chtít určit, jestli můžete nahradit scénáři časné vazby nebo zvažte výkonu pozdní vazbou scénář.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Je toto MDA aktivováno pro každý <xref:System.Reflection.MemberInfo> mezipaměti, který je vytvořen. Je zanedbatelný dopad na výkon.  
  
## <a name="output"></a>Výstup  
 MDA výstupy zpráva, <xref:System.Reflection.MemberInfo> mezipaměti byl vytvořen. Pomocí ladicího programu můžete získat trasování zásobníku znázorňující, kde je program pomocí reflexe.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Tento ukázkový kód se budou aktivovat `memberInfoCacheCreation` MDA.  
  
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
 <xref:System.Reflection.MemberInfo>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
