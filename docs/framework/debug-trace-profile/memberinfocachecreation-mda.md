---
title: "memberInfoCacheCreation – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1aeda59172e52c9880b39d6bf94ea9685a0203c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation – pomocník spravovaného ladění (MDA)
`memberInfoCacheCreation` Pomocník spravovaného ladění (MDA) se aktivuje při <xref:System.Reflection.MemberInfo> mezipaměť je vytvořená. To se silné informace o programu, který je zajistit použití nákladných prostředků reflexe funkcí.  
  
## <a name="symptoms"></a>Příznaky  
 Program je sada zvyšuje pracovat, protože program je pomocí reflexe nákladných prostředků.  
  
## <a name="cause"></a>příčina  
 Reflexe operace, které zahrnují <xref:System.Reflection.MemberInfo> objekty jsou považovány za prostředků náročná, protože budou musí přečíst metadata, která je uložena v cold stránky a obecně indikují program používá nějaký typ scénář pozdní vazbu.  
  
## <a name="resolution"></a>Rozlišení  
 Můžete určit, kde se reflexe používá v programu povolením této (mda) a potom spuštěním kódu v ladicí program nebo připojení s ladicí program, když je aktivován (mda). V části ladicí program bude získejte trasování zásobníku ukazující, kde <xref:System.Reflection.MemberInfo> mezipaměti byl vytvořen a z ní můžete určit, kde je váš program pomocí reflexe.  
  
 Řešení je závislé na cílech kódu. Tato MDA vás upozorní, že má program scénáři pozdní vazbu. Můžete chtít zjistit, zda můžete nahradit scénářem časné vazby či zvažte výkon pozdní vázané scénáře.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA se aktivuje na každých <xref:System.Reflection.MemberInfo> mezipaměti, který je vytvořen. Dopad na výkon je nepatrné.  
  
## <a name="output"></a>Výstup  
 MDA výstupy zpráva označující <xref:System.Reflection.MemberInfo> mezipaměti byla vytvořena. Získejte trasování zásobníku znázorňující, kde je váš program pomocí reflexe pomocí ladicího programu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Tento ukázkový kód se budou aktivovat `memberInfoCacheCreation` (mda).  
  
```  
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
